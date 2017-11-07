# <a name="call-microsoft-graph-in-a-ruby-app"></a>在 Ruby 应用程序中调用 Microsoft Graph 

在本文中我们获取访问令牌从 Azure 活动目录 (AD)，调用 Microsoft Graph API 所需的最小任务。 我们使用从[使用 Microsoft Graph 的 Office 365 Ruby 连接示例](https://github.com/microsoftgraph/ruby-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

![Office 365 Ruby 连接示例屏幕快照](./images/web-screenshot.png)

## <a name="overview"></a>概述

若要调用 Microsoft Graph API，Ruby 应用程序必须完成以下任务。

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

* 第 6 步中的**登录 URL**作为 Ruby 应用程序中指定的路由。 如果连接的示例中，这是[`/auth/azureactivedirectory/callback`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L41)。
* 您的应用程序要求的[配置**委派权限**](https://github.com/microsoftgraph/ruby-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure)。 连接示例需要**发送电子邮件时已登录的用户**权限。

记下 Azure 应用程序的**配置**页中的以下值。

* 客户机 ID
* 有效的密钥
* 回复 URL

这些值作为参数在 OAuth 流程中需要您的应用程序。

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>将浏览器重定向到登录页

您的应用程序需要将浏览器重定向到登录页面，以获得授权码，然后继续 OAuth 流程。

在连接的示例中，OmniAuth 库处理重定向。 我们的应用程序只是委托给执行[`/auth/azureactivedirectory`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L30)由 OmniAuth 管理的工艺路线。

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>收到答复的 URL 页面中的授权码

在符号中的用户之后, 流到您的应用程序中的答复 URL 返回浏览器。 Azure 将授权码添加到查询字符串。 连接示例使用[`/auth/azureactivedirectory/callback`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L38)为此目的的工艺路线。

中提供的授权码`code`查询字符串变量。 连接示例将代码保存到一个本地变量以供以后使用它。

```ruby
code = params[:code]
```

<!--<a name="accesstoken"/>-->
## <a name="request-an-access-token-from-the-token-endpoint"></a>请求访问令牌从令牌的终结点

授权码之后，您可以使用它的客户机 ID，键，并回复你从 Azure 的广告请求访问令牌的 URL 值。 

> **注意︰** <br />
> 该请求必须同时指定我们正在使用的资源。 如果 Microsoft Graph 的资源值是`https://graph.microsoft.com`。

再次，连接示例将委托 OmniAuth 库到此任务。 [`acquire_access_token`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L65)函数调用库，并传递身份验证代码保存在上一节以及回复 URL，客户机 ID，客户的机密和资源 id。

```ruby
def acquire_access_token(auth_code, reply_url)
    AUTH_CTX.acquire_token_with_authorization_code(
                  auth_code,
                  reply_url,
                  CLIENT_CRED,
                  GRAPH_RESOURCE)
end
```

> **注意︰** <br />
> 中提供了客户机 ID 和客户端密钥`CLIENT_CRED`在上面的代码片断中的参数。

<!--<a name="request"/>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。 您的应用程序必须提供每个请求的**授权**标头中的访问令牌。

连接示例发送一封电子邮件，在 Microsoft Graph API 使用**sendMail**终结点。 中的代码是[`send_mail`](https://github.com/microsoftgraph/ruby-connect-rest-sample/blob/master/app/controllers/pages_controller.rb#L82)函数。 这是演示如何授权标头中发送访问代码的代码。

```ruby
def send_mail
  # Used in the template
  @name = session[:name]
  @email = params[:specified_email]
  @recipient = params[:specified_email]
  @mailSent = false
  
  sendMailEndpoint = URI("#{GRAPH_RESOURCE}#{SENDMAIL_ENDPOINT}")
  http = Net::HTTP.new(sendMailEndpoint.host, sendMailEndpoint.port)
  http.use_ssl = true
  
  emailBody = File.read("app/assets/MailTemplate.html")
  emailBody.sub! "{given_name}", @name
  
  emailMessage = "{
          Message: {
          Subject: 'Welcome to Office 365 development with Ruby',
          Body: {
              ContentType: 'HTML',
              Content: '#{emailBody}'
          },
          ToRecipients: [
              {
                  EmailAddress: {
                      Address: '#{@recipient}'
                  }
              }
          ]
          },
          SaveToSentItems: true
          }"

  response = http.post(
    SENDMAIL_ENDPOINT, 
    emailMessage, 
    initheader = 
    {
      "Authorization" => "Bearer #{session[:access_token]}", 
      "Content-Type" => CONTENT_TYPE
    }
  )

  # The send mail endpoint returns a 202 - Accepted code on success
  if response.code == "202"
    @mailSent = true
  else
    @mailSent = false
    flash[:httpError] = "#{response.code} - #{response.message}"
  end
  
  render "callback"
end
```

> **注意︰** <br />
> 请求必须还发送**内容类型**标头值接受 Microsoft Graph API，例如， `application/json;odata.metadata=minimal;odata.streaming=true`。

Microsoft Graph API 是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出 API 参考研究使用 Microsoft Graph API 可以完成些什么。

<!--## Additional resources

-  [Office 365 Ruby Connect sample using Microsoft Graph](https://github.com/microsoftgraph/ruby-connect-rest-sample)
-  [Office Dev Center](http://dev.office.com) 
-  [Microsoft Graph API reference](http://graph.microsoft.io/en-us/docs)-->
