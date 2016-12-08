# <a name="call-microsoft-graph-in-a-service-or-daemon-app"></a>服务或守护程序的应用程序中调用 Microsoft Graph

在这篇文章我们查看连接到 Office 365 的单租户服务或守护程序应用程序和 Microsoft Graph API 调用所需的最小任务。

## <a name="overview"></a>概述

若要调用 Microsoft Graph API 服务或守护程序的应用程序中，您必须完成以下任务。

1. 在 Azure Active Directory 中注册应用程序。
2. 从终结点颁发令牌请求访问令牌。
3. 在 Microsoft Graph api 请求中使用的访问令牌。

## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册您的应用程序使用的[应用程序注册工具](https://dev.office.com/app-registration)。 您需要转到[Microsoft Azure 管理门户网站](https://manage.windowsazure.com)对其进行管理。

或者，请参见一节[注册您的 web 服务器应用程序，使用 Azure 管理门户](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp)的说明如何手动注册该应用程序，请记住以下详细信息︰

* 注册应用程序之后，配置服务或守护程序的应用程序所需的**应用程序的权限**。

记下以下值 Azure 应用程序的配置页面中因为需要服务或守护程序的应用程序中配置的 OAuth 流程这些值。

* 客户端 ID （特定于您的应用程序）
* 应用程序键 （唯一的应用程序）
* 您的应用程序 OAuth 2.0 令牌终结点
  * 通过单击*查看终结点*在 Azure 管理门户中应用程序的页面底部找到此值。 终结点将看起来像`https://login.microsoftonline.com/<tenantId>/oauth2/token`。

## <a name="request-an-access-token-from-the-token-issuing-endpoint"></a>从终结点颁发的令牌请求访问令牌

与不同的客户端应用程序服务或守护程序的应用程序不能具有用户登录和授权您的应用程序。 相反，应用程序必须实现 OAuth 2.0 客户端凭据授予流动，让它使用自己的凭据、 其客户机 ID 和应用程序键时调用图表而不是模拟用户进行身份验证。 有关身份验证流的详细信息，请参阅[服务调用使用客户端凭据的服务](https://msdn.microsoft.com/en-us/library/azure/dn645543.aspx)。

对颁发使用下面的参数替换终结点标记进行 HTTP POST 请求`<clientId>`，`<clientSecret>`与您的应用程序的客户端 ID 和应用程序键，分别。

```http
POST https://login.microsoftonline.com/<tenantId>/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
&client_id=<clientId>
&client_secret=<clientSecret>
&resource=https://graph.microsoft.com
```

响应将包含访问令牌和过期信息。

```json
{ 
  "token_type": "Bearer",
  "expires_in": "3599",
  "scope": "User.Read",
  "expires_on": "1449685363",
  "not_before": "1449681463",
  "resource": "https://graph.microsoft.com",
  "access_token": "<token>"
}
```

## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。 您的应用程序必须为每个请求的**授权**标头添加访问令牌。

例如，服务或守护程序的应用程序可以检索组织中的所有用户是否选择 Azure 管理门户中*所有用户的完整配置文件中读取*权限。 

```http
GET https://graph.microsoft.com/v1.0/users
Authorization: Bearer <token>
```

Microsoft 图表是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出要探索使用 Microsoft Graph API 可以完成什么的[API 参考](http://graph.microsoft.io/docs/api-reference/v1.0)。
