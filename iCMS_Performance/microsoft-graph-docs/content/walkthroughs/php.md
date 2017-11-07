# <a name="call-microsoft-graph-in-a-php-app"></a>在 PHP 应用程序中调用 Microsoft Graph 

在本文中我们获取访问令牌从 Azure 活动目录 (AD)，调用 Microsoft Graph API 所需的最小任务。 我们使用从[使用 Microsoft Graph 的 Office 365 PHP 连接示例](https://github.com/microsoftgraph/php-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

![Office 365 PHP 连接示例屏幕快照](./images/web-screenshot.png)

## <a name="overview"></a>概述

若要调用 Microsoft Graph API，您的 PHP 应用程序必须完成以下任务。

1. 在 Azure Active Directory 中注册应用程序
2. 将浏览器重定向到登录页
3. 收到答复的 URL 页面中的授权码
4. 请求访问令牌从令牌的终结点
5. 在 Microsoft Graph api 请求中使用的访问令牌

<!--<a name="register"/>-->
## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

或者，请参见一节[注册您的 web 服务器应用程序，使用 Azure 管理门户](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp)的说明如何手动注册该应用程序，请记住以下详细信息︰

* 第 6 步中的**登录 URL**为您的 PHP 应用程序中指定的页。 此页是在连接示例中， [`Callback.php`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/app/callback.php)。
* 您的应用程序要求的[配置**委派权限**](https://github.com/microsoftgraph/php-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure)。 连接示例需要**发送电子邮件时已登录的用户**权限。

记下 Azure 应用程序的**配置**页中的以下值。

* 客户机 ID
* 有效的密钥
* 回复 URL

这些值作为参数在 OAuth 流程中需要您的应用程序。

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>将浏览器重定向到登录页

您的应用程序需要将浏览器重定向到登录页面，以获得授权码，然后继续 OAuth 流程。

连接示例，在将浏览器重定向的代码位于[`AuthenticationManager.connect`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/src/AuthenticationManager.php#L41)函数。

```php
// Redirect the browser to the authorization endpoint. Auth endpoint is
// https://login.microsoftonline.com/common/oauth2/authorize
$redirect = Constants::AUTHORITY_URL . Constants::AUTHORIZE_ENDPOINT . 
            '?response_type=code' . 
            '&client_id=' . urlencode(Constants::CLIENT_ID) . 
            '&redirect_uri=' . urlencode(Constants::REDIRECT_URI);
header("Location: {$redirect}");
exit();
```

> **注意︰** <br />
> 您必须在编写任何输出到页面之前发送**位置**标头。

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>收到答复的 URL 页面中的授权码

在符号中的用户之后, 流到您的应用程序中的答复 URL 返回浏览器。 Azure 将授权码添加到查询字符串。 连接示例使用[`Callback.php`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/app/callback.php)页上的实现此目的。

中提供的授权码`code`查询字符串变量。 连接示例将代码保存到会话变量以供以后使用它。

```php
if (isset($_GET['code'])) {
    $_SESSION['code'] =  $_GET['code'];
}
```

<!--<a name="accesstoken"/>-->
## <a name="request-an-access-token-from-the-token-endpoint"></a>请求访问令牌从令牌的终结点

授权码之后，您可以使用它的客户机 ID，键，并回复你从 Azure 的广告请求访问令牌的 URL 值。 

> **注意︰** <br />
> 该请求必须同时指定我们正在使用的资源。 如果 Microsoft Graph API 的资源值是`https://graph.microsoft.com`。

连接示例请求的标记中的代码使用[`AuthenticationManager.acquireToken`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/src/AuthenticationManager.php#L62)函数。 下面是最相关的代码。

```php
$tokenEndpoint = Constants::AUTHORITY_URL . Constants::TOKEN_ENDPOINT;

// Send a POST request to the token endpoint to retrieve tokens.
// Token endpoint is:
// https://login.microsoftonline.com/common/oauth2/token
$response = RequestManager::sendPostRequest(
    $tokenEndpoint, 
    array(),
    array(
        'client_id' => Constants::CLIENT_ID,
        'client_secret' => Constants::CLIENT_SECRET,
        'code' => $_SESSION['code'],
        'grant_type' => 'authorization_code',
        'redirect_uri' => Constants::REDIRECT_URI,
        'resource' => Constants::RESOURCE_ID
    )

// Store the raw response in JSON format.
$jsonResponse = json_decode($response, true);

// The access token response has the following parameters:
// access_token - The requested access token.
// expires_in - How long the access token is valid.
// expires_on - The time when the access token expires.
// id_token - An unsigned JSON Web Token (JWT).
// refresh_token - An OAuth 2.0 refresh token.
// resource - The App ID URI of the web API (secured resource).
// scope - Impersonation permissions granted to the client application.
// token_type - Indicates the token type value.
foreach ($jsonResponse as $key=>$value) {
    $_SESSION[$key] = $value;
}
```

> **注意︰** <br />
> 响应提供了比刚刚访问令牌的详细信息，例如，您的应用程序可以获取刷新令牌无需用户进行显式的登录请求新的访问令牌。

您的 PHP 应用程序现在可以使用会话变量`access_token`向 Microsoft Graph API 发出身份验证的请求。

<!--<a name="request"/>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。 您的应用程序必须提供每个请求的**授权**标头中的访问令牌。

连接示例发送一封电子邮件，在 Microsoft Graph API 使用**sendMail**终结点。 中的代码是[`MailManager.sendWelcomeMail`](https://github.com/microsoftgraph/php-connect-rest-sample/blob/master/src/MailManager.php#L40)函数。 这是演示如何授权标头中发送访问代码的代码。

```php
// Send the email request to the sendmail endpoint, 
// which is in the following URI:
// https://graph.microsoft.com/v1.0/me/microsoft.graph.sendMail
// Note that the access token is attached in the Authorization header
RequestManager::sendPostRequest(
    Constants::RESOURCE_ID . Constants::SENDMAIL_ENDPOINT,
    array(
        'Authorization: Bearer ' . $_SESSION['access_token'],
        'Content-Type: application/json;' . 
                      'odata.metadata=minimal;' .
                      'odata.streaming=true'
    ),
    $email
);
```

> **注意︰** <br />
> 请求必须还发送**内容类型**标头值接受 Microsoft Graph API，例如， `application/json;odata.metadata=minimal;odata.streaming=true`。

Microsoft Graph API 是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出 API 参考研究使用 Microsoft Graph API 可以完成些什么。

<!--## Additional resources

-  [Office 365 PHP Connect sample using Microsoft Graph API](https://github.com/OfficeDev/O365-PHP-Unified-API-Connect)-->
