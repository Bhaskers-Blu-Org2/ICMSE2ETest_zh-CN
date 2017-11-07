# <a name="call-microsoft-graph-in-an-ios-app"></a>在 iOS 应用程序中调用 Microsoft Graph

本文中我们了解到 Office 365 和调用 Microsoft Graph API 将应用程序连接所需的最小任务。 我们使用从[ios-objectivec-连接的其余部分的示例](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。 此示例介绍了核心基本身份验证与 Microsoft Azure 活动目录 (AAD)，并做出一个简单的服务调用针对 Office 365 提供邮件服务使用 Microsoft Graph API （发送邮件）。 建议您复制或从该资料库伴随本文下载的项目。 


本文引用了[Microsoft Azure 活动目录身份验证库 (ADAL) 为 iOS 和 OSX](https://github.com/AzureAD/azure-activedirectory-library-for-objc)，和[ios-objectivec-连接的其余部分的示例](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample)示例身份验证使用此库。 使用量以及 iOS 项目中的实现，请参阅此存储库的详细信息。


## <a name="overview"></a>概述

若要调用 Microsoft Graph API，您的 iOS 应用程序必须完成以下任务︰

1. 注册应用程序从 Microsoft Azure 活动目录 (AD)。
2. 请求并获取一个访问令牌从 Azure 的广告。
3. 到 Microsoft Graph API 的其余请求中使用的访问令牌。 



## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

另外，请参见**注册 Azure 管理门户与本机应用程序**[手动注册您的应用程序使用 Azure 的广告，这样它可以访问 Office 365 Api](https://msdn.microsoft.com/en-us/office/office365/howto/add-common-consent-manually)的说明文章如何手动注册该应用程序，请记住以下详细信息︰

* 注册将需要提供重定向 URI。 这所需的值，用于指定在用户将被重定向后的成功的身份验证尝试。 如果没有指定正确的重定向 URI，身份验证请求将失败。
* 在注册时，该应用程序必须被授予**发送电子邮件时已登录的用户权限** **Microsoft Graph**。  


记下 Azure 应用程序的**配置**页中的以下值。

* 客户机 ID
* 重定向 URI

您需要这些值可在您的应用程序中配置的 OAuth 流程。 

## <a name="request-and-acquire-an-access-token-from-azure-ad"></a>请求并获取一个访问令牌从 Azure 的广告

若要请求并获取调用 Microsoft Graph API 访问令牌，可以使用**acquireAuthTokenWithResource:clientId:redirectUri:completionBlock:**提供的[Microsoft Azure 活动目录身份验证库 (ADAL) 为 iOS 和 OSX](https://github.com/AzureAD/azure-activedirectory-library-for-objc)。 此 SDK 为应用程序提供了 Microsoft Azure 的广告，包括 OAuth2，与用户级别同意的 Web API 集成的行业标准协议支持的全部功能和两因素身份验证支持。

此方法的参数如下︰

1. **资源 Id** -这是您要访问所需的资源。 例如，我们想要访问 Microsoft Graph API，因此此值将为"https://graph.microsoft.com"。
2. **客户机 Id** -来完成 AAD 注册标识您的应用程序的给定值。
3. **redirectURI** -再次，这一个必需的值，用于指定在用户将被重定向后的成功的身份验证尝试。


首先，您需要指定身份验证上下文。 这只是定义要用来获取您的访问令牌中的颁发机构。 在我们的例子中是从 AAD 租户，您将需要将其声明为︰

    @property (strong,    nonatomic) ADAuthenticationContext *context;

然后将其初始化与主管机构 ("https://login.microsoftonline.com/common") 的位置︰

    self.context = [ADAuthenticationContext authenticationContextWithAuthority:self.authority]; 


[Ios-objectivec-连接的其余部分的示例](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample)中我们创建演示的单一身份验证类 (**AuthenticationManager**) 的示例目的使用的主管机构和所需的参数。 同样，此类是只是有关如何进行身份验证工作流的示例。 利息代码段︰ 



    - (void)acquireAuthTokenWithResource:(NSString *)resourceID
                            clientID:(NSString*)clientID
                         redirectURI:(NSURL*)redirectURI
                          completion:(void (^)(ADAuthenticationError *error))completion {
    
    NSLog(@"acquireAuthTokenWithResource");
    [self.context acquireTokenWithResource:resourceID
                                  clientId:clientID
                               redirectUri:redirectURI
                           completionBlock:^(ADAuthenticationResult *result) {
                               NSLog(@"Completion");
                               
                               if (result.status !=AD_SUCCEEDED){
                                   NSLog(@"error");
                                   completion(result.error);
                               }
                               
                               else{
                                   NSLog(@"complete!");
                                   self.accessToken = result.accessToken;
                                   self.userID = result.tokenCacheStoreItem.userInformation.userId;
                                   completion(nil);
                               }
                           }];


第一次运行此应用程序时，身份验证管理器将向它将重定向到登录页的机构发送请求。 将提供您的凭据，该响应将包含身份验证结果。 如果成功，它还将包含刷新和访问令牌。 第二次此应用程序运行时，并假定您没有清除您的令牌缓存和 cookie 身份验证管理器将使用的访问权限或刷新缓存客户端请求进行身份验证的令牌。 如果您需要获取一个访问令牌，这将导致对服务的调用。 


## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。 您的应用程序必须向**授权**下的 HTTP 请求标头添加访问令牌。

[Ios-objectivec-连接的其余部分的示例](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample)示例发送一封电子邮件，在 Microsoft Graph API 使用 sendMail 终结点。 再次，我们我们可以在我们的示例来创建访问令牌初始化的单一身份验证类 (AuthenticationManager)。 我们将需要访问令牌来构建我们的请求。



    - (void)sendMailREST {
    
    AuthenticationManager *authManager = [AuthenticationManager sharedInstance];

    //Helper method used to construct the email message
    NSData *postData = [self mailContent];
    
    //Microsoft Graph API endpoint for sending mail
    NSMutableURLRequest *request = [[NSMutableURLRequest alloc] initWithURL:[NSURL URLWithString:@"https://graph.microsoft.com/v1.0/me/microsoft.graph.sendmail"]];

    [request setHTTPMethod:@"POST"];
    [request setValue:@"application/json" forHTTPHeaderField:@"Content-Type"];
    [request setValue:@"application/json, text/plain, */*" forHTTPHeaderField:@"Accept"];
    
    // Access token required for request header
    NSString *authorization = [NSString stringWithFormat:@"Bearer %@", authManager.accessToken];
    [request setValue:authorization forHTTPHeaderField:@"Authorization"];
    [request setHTTPBody:postData];

    NSURLConnection *conn = [[NSURLConnection alloc] initWithRequest:request delegate:self];
    
    if(conn) {
        NSLog(@"Connection Successful");
    } else {
        NSLog(@"Connection could not be made");
    }
    
    [conn start];

正如您所看到的 NSURLConnection 委托，即 NSURLConnectionDelegate 和 NSURLConnectionDataDelegate 处理的响应。

## <a name="next-steps"></a>下一步行动

如果访问令牌过期或将要过期，您可以使用 ADAuthenticationContext 的**acquireTokenSilentWithResource:clientId:redirectUri:completionBlock:**以获取新的访问令牌。 [Ios-objectivec-连接的其余部分的示例](https://github.com/microsoftgraph/ios-objectivec-connect-rest-sample)示例中介绍了它的用法。 另外，您可以找到要清除您的令牌缓存和存储的 cookie 的代码。  

Microsoft Graph API 是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出要探索使用 Microsoft Graph API 可以完成什么的[API 参考](http://graph.microsoft.io/docs/api-reference/v1.0)。

