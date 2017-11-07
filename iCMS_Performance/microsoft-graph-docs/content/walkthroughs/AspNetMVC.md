# <a name="call-microsoft-graph-in-an-aspnet-mvc-app"></a>在 ASP.NET MVC 应用程序中调用 Microsoft Graph

在本文中我们了解到 Office 365 将应用程序连接和调用 Microsoft Graph API 所需的最小任务。 本主题不会从头开始创建应用程序。 我们使用从[使用 Microsoft Graph 的 Office 365 ASP.NET MVC 连接示例](https://github.com/microsoftgraph/aspnet-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

以下是发送邮件页的一个屏幕快照。

![Office 365 ASP.NET MVC 示例屏幕快照](./images/O365AspNetMVCSendMailPageScreenshot.png)

## <a name="overview"></a>概述

若要调用 Microsoft Graph API，您必须完成以下任务。

1. 在 Azure Active Directory 中注册应用程序
2. 对用户进行身份验证并通过针对.NET Azure AD 身份验证库调用方法获取访问令牌。 (ADAL)
3. 使用 ADAL 来获取访问令牌
4. 在 Microsoft Graph api 请求中使用的访问令牌
5. 断开会话连接

<!--<a name="register"></a>-->
## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

有关可选的说明，请参阅[注册 Azure 管理门户与基于浏览器的 web 应用程序](https://msdn.microsoft.com/office/office365/HowTo/add-common-consent-manually#bk_RegisterWebApp)，请记住以下详细信息。

* 请确保 http://localhost:55065 /**登录 URL**。
* 之后您注册该应用程序，[配置**委派权限**的](https://github.com/microsoftgraph/aspnet-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure)角度应用程序要求。 该连接示例需要**发送电子邮件时已登录的用户**权限。

注意下面的值 Azure 应用程序的**配置**页面中因为您需要在您的应用程序中配置这些值。

* 客户端 ID （特定于您的应用程序）
* 密钥 （也称为客户端机密）
* 回复 URL （也称作为重定向的 URL）。 对于本示例，它是 http://localhost:55065 /。

  > 注意︰ 回复 URL 值是使用的登录 URL 值，指定注册应用程序时自动填充。

<!--<a name="#auth"></a>-->
## <a name="authentication-in-the-connect-sample"></a>连接示例中的身份验证

为使.NET Azure AD 身份验证库 (ADAL) 使客户端应用程序开发人员可以对用户进行身份验证，然后获取访问令牌进行 API 调用。  您可以通过在 Visual Studio 中**管理 NuGet 程序包**ASP.NET MVC 项目中包含此库。

以下是主页页面的屏幕快照。

![Office 365 ASP.NET MVC 示例屏幕快照](./images/O365AspNetMVCHomePageScreenshot.png)

身份验证流可以分解为两个基本步骤︰

1. 请求授权码
2. 授权码用于请求的访问令牌。

>  **注意**︰ 您也会刷新访问令牌和令牌。 可以使用刷新标记当前存取令牌到期时获得一个新的访问令牌。

连接示例使用 Azure 应用程序注册值和用户的 ID 进行身份验证。 ADAL 身份验证流量需求的客户端 ID 键，回复的 URL (也称为重定向 URL) 在 Azure 的注册过程中获得。

要请求的授权码，请首先重定向应用程序到 Azure 广告授权请求的 URL 如下所示 （请参阅 HomeController.cs 文件）。


```c#
        public ActionResult Login()
        {
            if (string.IsNullOrEmpty(Settings.ClientId) || string.IsNullOrEmpty(Settings.ClientSecret))
            {
                ViewBag.Message = "Please set your client ID and client secret in the Web.config file";
                return View();
            }


            var authContext = new AuthenticationContext(Settings.AzureADAuthority);

            // Generate the parameterized URL for Azure login.
            Uri authUri = authContext.GetAuthorizationRequestURL(
                Settings.O365UnifiedAPIResource,
                Settings.ClientId,
                loginRedirectUri,
                UserIdentifier.AnyUser,
                null);

            // Redirect the browser to the login page, then come back to the Authorize method below.
            return Redirect(authUri.ToString());
        }

```
此**登录**方法调用时，应用程序将用户重定向到登录页。 这将应用程序的登录页。 一旦成功通过身份验证的用户凭据，Azure 将重定向到该应用程序用*loginRedirectUri*提到在代码中的重定向 URL。 此重定向 URL 是在 ASP.NET MVC 应用程序中所示的其他操作的 URL。

```c#

 Uri loginRedirectUri => new Uri(Url.Action(nameof(Authorize), "Home", null, Request.Url.Scheme));

```
该 URL 还将包含在步骤 1 和 2，上面提到的授权码。  这将从请求参数来获得授权码。 使用 authorizationn 代码，应用程序将调用 Azure 的广告以获取访问令牌。 一旦我们得到的访问令牌，我们将它存储在会话中，这样我们可以将其用于多个请求。

重定向 URL 操作中提到的授权操作如下所示。

```c#
        public async Task<ActionResult> Authorize()
        {
            var authContext = new AuthenticationContext(Settings.AzureADAuthority);


            // Get the token.
            var authResult = await authContext.AcquireTokenByAuthorizationCodeAsync(
                Request.Params["code"],                                         // the auth 'code' parameter from the Azure redirect.
                loginRedirectUri,                                               // same redirectUri as used before in Login method.
                new ClientCredential(Settings.ClientId, Settings.ClientSecret), // use the client ID and secret to establish app identity.
                Settings.O365UnifiedAPIResource);

            // Save the token in the session.
            Session[SessionKeys.Login.AccessToken] = authResult.AccessToken;

            // Get info about the current logged in user.
            Session[SessionKeys.Login.UserInfo] = await UnifiedApiHelper.GetUserInfoAsync(authResult.AccessToken);

            return RedirectToAction(nameof(Index), "Message");

        }

```
>  **注意**︰ 有关授权流程的详细信息，请参阅 [授权代码授予流] (https://msdn.microsoft.com/en-US/library/azure/dn645542.aspx)

<!--<a name="request"></a>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

在符号中的用户之后, 连接示例发送电子邮件活动显示的用户。  使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。

例如，UnifiedApiHelper.cs 文件包含的代码中︰

1)  获取有关当前登录用户的信息。  ``GetUserInfoAsync``方法接受单个参数 （访问令牌值） 进行对**https://graph.microsoft.com/v1.0/me**的调用来获取有关当前登录用户的信息。

 ```c#

        public static async Task<UserInfo> GetUserInfoAsync(string accessToken)
        {
            UserInfo myInfo = new UserInfo();

            using (var client = new HttpClient())
            {
                using (var request = new HttpRequestMessage(HttpMethod.Get, Settings.GetMeUrl))
                {
                    request.Headers.Accept.Add(Json);
                    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);

                    using (var response = await client.SendAsync(request))
                    {
                        if (response.StatusCode == HttpStatusCode.OK)
                        {
                            var json = JObject.Parse(await response.Content.ReadAsStringAsync());
                            myInfo.Name = json?["displayName"]?.ToString();
                            myInfo.Address = json?["mail"]?.ToString().Trim().Replace(" ", string.Empty);

                        }
                    }
                }
            }

            return myInfo;
        }

```



2)  构造并发送登录的用户想要通过电子邮件发送的消息。 ``SendMessageAsync``方法构造并发送 POST 请求到**https://graph.microsoft.com/v1.0/me/microsoft.graph.sendmail**资源 URL，使用访问令牌值作为一个参数。


```c#

        public static async Task<SendMessageResponse> SendMessageAsync(string accessToken, SendMessageRequest sendMessageRequest)
        {
            var sendMessageResponse = new SendMessageResponse { Status = SendMessageStatusEnum.NotSent };

            using (var client = new HttpClient())
            {
                using (var request = new HttpRequestMessage(HttpMethod.Post, Settings.SendMessageUrl))
                {
                    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", accessToken);
                    request.Content = new StringContent(JsonConvert.SerializeObject(sendMessageRequest), Encoding.UTF8, "application/json");
                    using (HttpResponseMessage response = await client.SendAsync(request))
                    {
                        if (response.IsSuccessStatusCode)
                        {
                            sendMessageResponse.Status = SendMessageStatusEnum.Sent;
                            sendMessageResponse.StatusMessage = null;
                        }
                        else
                        {
                            sendMessageResponse.Status = SendMessageStatusEnum.Fail;
                            sendMessageResponse.StatusMessage = response.ReasonPhrase;
                        }
                    }
                }
            }

            return sendMessageResponse;
        }

```


``MessageController.cs ``文件包含管理电子邮件的代码。 例如，**发送邮件**按钮。``SendMessageSubmit ``方法发送消息，当用户单击**发送邮件**按钮。


```c#

        public async Task<ActionResult> SendMessageSubmit(UserInfo userInfo)
        {
            // After Index method renders the View, user clicks Send Mail, which comes in here.
            EnsureUser(ref userInfo);

            // Send email using O365 unified API.
            var sendMessageResult = await UnifiedApiHelper.SendMessageAsync(
                (string)Session[SessionKeys.Login.AccessToken],
                GenerateEmail(userInfo));

            // Reuse the Index view for messages (sent, not sent, fail) .
            // Redirect to tell the browser to call the app back via the Index method.
            return RedirectToAction(nameof(Index), new RouteValueDictionary(new Dictionary<string,object>{
                { "Status", sendMessageResult.Status },
                { "StatusMessage", sendMessageResult.StatusMessage },
                { "Address", userInfo.Address },
            }));
        }

```


``CreateEmailObject``方法创建发布正文要求所需的请求每个数据的格式合同中的电子邮件对象︰


  ```c#

        private SendMessageRequest CreateEmailObject(UserInfo to, string subject, string body)
        {
            return new SendMessageRequest
            {
                Message = new Message
                {
                    Subject = subject,
                    Body = new MessageBody
                    {
                        ContentType = "Html",
                        Content = body
                    },
                    ToRecipients = new List<Recipient>
                    {
                        new Recipient
                        {
                            EmailAddress = new UserInfo
                            {
                                 Name =  to.Name,
                                 Address = to.Address
                            }
                        }
                    }
                },
                SaveToSentItems = true
            };

```

另一项任务就是构建有效的 JSON 消息字符串并将其发送给``https://graph.microsoft.com/v1.0/me/microsoft.graph.sendmail``使用 HTTP POST 请求的端点。 由于 HTML 文档作为电子邮件正文，请求设置``ContentType``值的 HTML 电子邮件并将该内容作为 JSON 编码 HTTP POST 请求。 UnifiedApiMessageModels.cs 文件中包含的数据或架构这个应用程序与 Office 365 之间的合同统一 API 服务器。



```c#


    public class SendMessageResponse
    {
        public SendMessageStatusEnum Status { get; set; }
        public string StatusMessage { get; set; }
    }

    public class SendMessageRequest
    {
        public Message Message { get; set; }

        public bool SaveToSentItems { get; set; }
    }

    public class Message
    {
        public string Subject { get; set; }
        public MessageBody Body { get; set; }
        public List<Recipient> ToRecipients { get; set; }
    }
    public class Recipient
    {
        public UserInfo EmailAddress { get; set; }
    }

    public class MessageBody
    {
        public string ContentType { get; set; }
        public string Content { get; set; }
    }

    public class UserInfo
    {
        public string Name { get; set; }
        public string Address { get; set; }
    }

}

```
<!--<a name="logout"></a>-->
## <a name="disconnect-the-session"></a>断开会话

当用户单击发送邮件页中**断开**时，用户将会话注销。 该代码通过实现此
* 清除本地会话
* 将浏览器重定向到注销的终结点 （因此 Azure 可以清除自己 cookie）

**Logout**方法 （请参阅 HomeController.cs 文件） 显示如何做到这一点。


```c#
        public ActionResult Logout()
        {
            Session.Clear();
            return Redirect(Settings.LogoutAuthority + logoutRedirectUri.ToString());
        }

```

##<a name="next-steps"></a>下一步行动
Microsoft Graph API 是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出 API 参考研究使用 Microsoft Graph API 可以完成些什么。
在[GitHub](http://aka.ms/aspnetgraphsamples)上浏览我们的其他 ASP.NET 示例。


