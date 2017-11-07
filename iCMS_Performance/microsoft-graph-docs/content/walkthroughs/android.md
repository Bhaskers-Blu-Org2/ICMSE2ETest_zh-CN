# <a name="call-microsoft-graph-in-an-android-app"></a>Android 应用程序中调用 Microsoft Graph

在本文中我们获取访问令牌从 Azure 活动目录 (AD)，调用 Microsoft Graph 所需的最小任务。 我们使用从[使用 Microsoft Graph 的 Office 365 Android 连接示例](https://github.com/microsoftgraph/android-java-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

下图显示了用户已连接到 Office 365 后出现的示例应用程序发送邮件活动。

![Office 365 Android 统一 API 连接示例屏幕快照](./images/AndroidConnect.png)

## <a name="overview"></a>概述

若要调用 Microsoft Graph API， [Office 365 Android 连接示例](https://github.com/microsoftgraph/android-java-connect-rest-sample)，请完成下列任务。

1. 对用户进行身份验证并通过 Azure Active Directory 库调用方法获取访问令牌。
2. 为其余操作 Microsoft Graph API 端点上创建邮件消息请求。

<!--<a name="register"/>-->
## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

另外，请参见**注册 Azure 管理门户与本机应用程序**[手动注册您的应用程序使用 Azure 的广告，这样它可以访问 Office 365 Api](https://msdn.microsoft.com/en-us/office/office365/howto/add-common-consent-manually)的说明文章如何手动注册该应用程序，请记住以下详细信息︰

* 配置您的应用程序需要**委派权限**。 连接示例需要**发送电子邮件时已登录的用户**权限。

记下 Azure 应用程序的**配置**页中的以下值。

* 客户机 ID
* 重定向 URL

您需要这些值可在您的应用程序中配置身份验证代码。

## <a name="gradle-dependencies-in-the-connect-sample"></a>在连接的示例 Gradle 依赖项
此示例采用下面的 build.gradle 段所示的库依赖项

```gradle
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:22.1.1'

    // Azure Active Directory Library
    compile 'com.microsoft.aad:adal:1.1.7'

    // Retrofit + custom HTTP
    compile 'com.squareup.okhttp:okhttp-urlconnection:2.0.0'
    compile 'com.squareup.okhttp:okhttp:2.0.0'
    compile 'com.squareup.retrofit:retrofit:1.9.0'
}

```
<!--<a name="authenticate"/>-->
## <a name="authentication-in-the-connect-sample"></a>连接示例中的身份验证
连接示例使用 Azure 应用程序注册值和用户的 ID 进行身份验证。 有两种连接示例所支持的身份验证行为。

* 提示的身份验证。 使用时的用户 ID 不会缓存在 Android 设备上存储首选项
* 静默式身份验证。 时使用缓存的用户 ID 并提示不是必需的。

[AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java)类提供`isConnected()`帮助器方法来找到任何缓存的用户 ID，并确定要使用的身份验证行为。


```java
    private boolean isConnected(){
        SharedPreferences settings = this
                .mContextActivity
                .getSharedPreferences(PREFERENCES_FILENAME, Context.MODE_PRIVATE);

        return settings.contains(USER_ID_VAR_NAME);
    }

```

这两种行为，ADAL 身份验证流需要的客户端 ID 和重定向的 URL 在 Azure 的注册过程中获得。 此示例源代码中保留这些字符串并检索它们之前验证用户的身份验证管理器对象。

[Constants.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/Constants.java)接口公开两个静态字符串的客户机 ID 和重定向 URL。

```java
interface Constants {
    String AUTHORITY_URL = "https://login.microsoftonline.com/common";
    // Update these two constants with the values for your application:
    String CLIENT_ID = "<Your client id here>";
    String REDIRECT_URI = "<Your redirect uri here>";
    String UNIFIED_API_ENDPOINT = "https://graph.microsoft.com/v1.0/";
    String UNIFIED_ENDPOINT_RESOURCE_ID = "https://graph.microsoft.com/";
}
```
### <a name="construct-the-authenticationmanager-class"></a>AuthenticationManager 类构造
[AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java)构造函数没有参数，但从 Constants.java 文件的图形的终结点的 url 设置类字符串字段。 此资源字符串用于这两种身份验证行为。

```java
    private AuthenticationManager() {
        mResourceId = Constants.UNIFIED_ENDPOINT_RESOURCE_ID;
    }
```

### <a name="prompted-authentication"></a>提示的身份验证

[AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java)类提供`authenticatePrompt()`方法来获取用于统一终结点上的其余部分调用访问令牌。

ADAL 库`acquireToken()`方法是异步的。 方法参数包括对当前活动的资源，客户机 ID，以及上下文的引用，然后重定向 URL。 当前活动的引用允许凭据质询页显示活动的 ADAL 库。
如果身份验证成功，ADAL 库调用`onSuccess()`回调。 此回调完成两件事情

* 存储的访问令牌中`mAccessToken`。 在发送电子邮件的其余部分调用时，示例在身份验证头放入该访问令牌。
* 将该用户的 ID 存储在存储首选项。


```java
    /**
     * Calls acquireToken to prompt the user for credentials.
     *
     * @param authenticationCallback The callback to notify when the processing is finished.
     */
    private void authenticatePrompt(final AuthenticationCallback<AuthenticationResult> authenticationCallback) {
        getAuthenticationContext().acquireToken(
                this.mContextActivity,
                this.mResourceId,
                Constants.CLIENT_ID,
                Constants.REDIRECT_URI,
                PromptBehavior.Always,
                new AuthenticationCallback<AuthenticationResult>() {
                    @Override
                    public void onSuccess(final AuthenticationResult authenticationResult) {
                        if (authenticationResult != null) {
                            if (authenticationResult.getStatus() == AuthenticationStatus.Succeeded) {
                                setUserId(authenticationResult.getUserInfo().getUserId());
                                mAccessToken = authenticationResult.getAccessToken();
                                authenticationCallback.onSuccess(authenticationResult);
                            } else {
                                // We need to make sure that there is no data stored with the failed auth
                                AuthenticationManager.getInstance().disconnect();
                                // This condition can happen if user signs in with an MSA account
                                // instead of an Office 365 account
                                authenticationCallback.onError(
                                        new AuthenticationException(
                                                ADALError.AUTH_FAILED,
                                                authenticationResult.getErrorDescription()));
                            }
                        } else {
                            // I could not authenticate the user silently,
                            // falling back to prompt the user for credentials.
                            authenticatePrompt(authenticationCallback);
                        }
                    }

                    @Override
                    public void onError(Exception e) {
                        // We need to make sure that there is no data stored with the failed auth
                        AuthenticationManager.getInstance().disconnect();
                        authenticationCallback.onError(e);
                    }
                }
        );
    }

```

###<a name="silent-authentication"></a>无提示的身份验证
[AuthenticationManager.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/AuthenticationManager.java)类提供`authenticateSilent()`方法来获取用于统一终结点上的其余部分调用访问令牌。

ADAL 库`acquireTokenSilent()`方法是异步的。 除了 Azure 注册客户机 ID 和资源 id，它将存储在首选项中共享的用户 ID。 帮助器方法，`getUserId()`从存储区获取用户 ID。

如果身份验证成功，`onSuccess()`调用方法。 `onSuccess`存储的访问令牌中`mAccessToken`。 在发送电子邮件的其余部分调用时，示例在身份验证头放入该访问令牌。
```java
    /**
     * Calls acquireTokenSilent with the user id stored in shared preferences.
     * In case of an error, it falls back to {@link AuthenticationManager#authenticatePrompt(AuthenticationCallback)}.
     *
     * @param authenticationCallback The callback to notify when the processing is finished.
     */
    private void authenticateSilent(final AuthenticationCallback<AuthenticationResult> authenticationCallback) {
        getAuthenticationContext().acquireTokenSilent(
                this.mResourceId,
                Constants.CLIENT_ID,
                getUserId(),
                new AuthenticationCallback<AuthenticationResult>() {
                    @Override
                    public void onSuccess(final AuthenticationResult authenticationResult) {
                        if (authenticationResult != null) {
                            if (authenticationResult.getStatus() == AuthenticationStatus.Succeeded) {
                                mAccessToken = authenticationResult.getAccessToken();
                                authenticationCallback.onSuccess(authenticationResult);
                            } else {
                                authenticationCallback.onError(
                                        new Exception(authenticationResult.getErrorDescription()));

                            }
                        } else {
                            // I could not authenticate the user silently,
                            // falling back to prompt the user for credentials.
                            authenticatePrompt(authenticationCallback);
                        }
                    }

                    @Override
                    public void onError(Exception e) {
                        // I could not authenticate the user silently,
                        // falling back to prompt the user for credentials.
                        authenticatePrompt(authenticationCallback);
                    }
                }
        );
    }

```
<!--<a name="sendmail"/>-->
## <a name="send-an-email-message-using-office-365"></a>发送电子邮件使用 Office 365

后到 Azure 的迹象中的用户，连接示例显示用户活动发送一封邮件。 连接示例使用[MSGraphAPIController.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/MSGraphAPIController.java)类发送消息，当用户单击发送邮件按钮。

### <a name="rest-adapter-helper-class"></a>其余适配器帮助器类
[RESTHelper.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/RESTHelper.java)类提供的方法注入到每个其余部分调用示例授权标头使。 它使用身份验证管理器提供的访问令牌。

```java
       //This method catches outgoing REST calls and injects the Authorization and host headers before
        //sending to REST endpoint
        RequestInterceptor requestInterceptor = new RequestInterceptor() {
            @Override
            public void intercept(RequestFacade request) {
                final String token = mAccessToken;
                if (null != token) {
                    request.addHeader("Authorization", "Bearer " + token);
                }
            }
        };
```
### <a name="unifiedapicontroller-class"></a>UnifiedAPIController 类
[MSGraphAPIController.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/MSGraphAPIController.java)类生成中的其他请求`sendMail()`方法。


```java
    /**
     * Sends an email message using the Unified API on Office 365. The mail is sent
     * from the address of the signed in user.
     *
     * @param emailAddress The recipient email address.
     * @param subject      The subject to use in the mail message.
     * @param body         The body of the message.
     * @param callback     UI callback to be invoked by Retrofit call when
     *                     operation completed
     */
    public void sendMail(
            final String emailAddress,
            final String subject,
            final String body,
            Callback<Void> callback) {
        ensureService();
        // Use the Unified API service on Office 365 to create the message.
        mUnifiedAPIService.sendMail(
                "application/json",
                createMailPayload(
                        subject,
                        body,
                        emailAddress),
                callback);
    }

```
### <a name="the-unifiedapiservice-interface"></a>UnifiedAPIService 接口
[MSGraphAPIController.java](https://github.com/microsoftgraph/android-java-connect-rest-sample/blob/master/app/src/main/java/com/microsoft/office365/connectmicrosoftgraph/MSGraphAPIController.java)接口提供示例使用改进的批注所做的其余部分调用方法的签名。

```java
    @POST("/me/sendMail")
    void sendMail(
            @Header("Content-type") String contentTypeHeader,
            @Body TypedString mail,
            Callback<Void> callback);


```

## <a name="next-steps"></a>下一步行动
Microsoft Graph API 是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 了解[Microsoft 关系图文档](http://graph.microsoft.io/docs)以探索使用 Microsoft Graph API 可以完成些什么。

我们已经为 Office 365 发布许多 Android 的示例。 每个这些示例生成连接的示例中，我们介绍的概念。 如果您想要做更多的 Android 应用程序，看到[更多针对 Office 365 提供我们 Android 样本](http://aka.ms/androidgraphsamples)办公室 GitHub 组织中。
 
