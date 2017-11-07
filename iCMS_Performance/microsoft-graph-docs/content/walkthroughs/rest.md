# <a name="platform-specific-walkthroughs"></a>平台特定演练

尝试我们的[API 资源管理器](https://graph.microsoft.io/graph-explorer)中的示例 REST 调用。

完成后，该 API 返回此处，选择在左边您最喜爱的平台。 我们将指导您完成编写一个简单的应用程序来检索电子邮件使用 Microsoft Graph 的步骤。

如果没有尚未列出您的首选的平台，继续阅读此页。 我们接下来通过一组相同的步骤使用原始 HTTP 请求。

## <a name="getting-started-with-the-microsoft-graph-api-and-rest"></a>Microsoft Graph API 和其余入门

本指南的目的是逐步完成的过程调用来检索电子邮件在 Office 365 和 Outlook.com Microsoft Graph。 与不同的特定于平台的演练中，本指南着重的 OAuth，剩余部分的请求和响应。 它将涵盖请求和响应的应用程序用来验证和检索消息的序列。

## <a name="using-oauth-20-to-authenticate"></a>使用 OAuth 2.0 进行身份验证

若要调用 Microsoft Graph，您的应用程序需要访问令牌从 Azure 活动目录 (AD Azure)。 在下面的示例应用程序实现授权代码授予流从 Azure AD，下列标准[OAuth 2.0 协议](http://tools.ietf.org/html/rfc6749)获取访问令牌。

### <a name="registering-an-app"></a>注册应用程序

目前有两个选项来注册您的应用程序︰

  1. 注册应用程序使用的模型，支持 Office 365 的商业用户，只占工作或学校。
 
  这种模型只适用于 Office 365 的商业产品中。 一旦您已经注册了您的应用程序，您可以通过[Azure 管理门户](https://manage.windowsazure.com)来进行管理。

  2. 消费者和商业 Office 365 提供服务 （我们叫它验证终结点 v2.0） 使用最新功能的工作方式进行注册。
 
  工作或学校和个人帐户的单一身份验证服务现已推出。 此模型提供学校 (Azure AD)、 工作以及个人 (Microsoft) 标识的单一身份验证服务。 现在，您只需在您的应用程序，以使用户能够使用工作或学校的科目，如 Office 365 或 OneDrive 的业务或如 Outlook.com 或 OneDrive 的个人帐户中实现一个身份验证流。
   
使用[应用程序注册门户](https://apps.dev.microsoft.com/)来注册您的应用程序和支持工作，学校和个人帐户。

请注意 v2.0 终结点逐渐发展涵盖从早期验证端点的所有方案。 若要选择是否最适合您阅读[此文章](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/)

在注册后，您将得到一个客户端 ID 和密码。 授权代码授予流中将使用这些值。

本文档的其余部分假定在 2.0 版模型上的进行登记。 在 v2.0 终结点支持的流的完整指南，请参阅[这篇文章](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-flows/)，有关授权代码授予流的完整指南，请参阅[本文](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-protocols-oauth-code/)

### <a name="getting-an-authorization-code"></a>获得授权码

授权代码授予流中的第一步是获得授权码。 用户登录并同意的访问级别到请求的应用程序时，该代码由授权服务器返回到应用程序中。

首先，应用程序构造用户的登录 URL。 必须在浏览器中打开此 URL，以便用户可以登录并提供同意。

登录的基 URL 看起来像`https://login.microsoftonline.com/common/oauth2/v2.0/authorize`。

该应用程序将查询参数追加到此来让知道哪些应用程序正在请求的登录和身份验证服务器的基 URL 请求它的权限。

- `client_id`的通过注册该应用程序生成客户端 ID。 这样可以知道哪些应用程序正在请求登录的 Azure 广告。
- `redirect_uri`的 Azure 将重定向到一次用户位置已授予同意该应用程序。 此值必须对应于**重定向 URI**注册应用程序时使用的值。
- `response_type`的预期响应应用程序类型。 这个值是`code`授权代码授予流。
- `scope`-以空格分隔列表的应用程序正在请求的范围。 在[这篇文章](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-scopes/)中的详细信息
- `state`的包含在请求中也将标记的响应中返回值。

例如，我们需要对邮件的读访问权限的应用程序的请求 URL 可能如下所示。

```http
GET https://login.microsoftonline.com/common/oauth2/v2.0/authorize?client_id=<CLIENT ID>&redirect_uri=http%3A%2F%2Flocalhost/myapp%2F&response_type=code&state=1234&scope=https%3A%2F%2Fgraph.microsoft.com%2Fmail.read
```

接下来，将用户重定向到登录 URL。 用户将会看到登录屏幕，其中显示应用程序的名称。 他们登录后，用户将看到的应用程序要求，并要求以允许或拒绝的权限的列表中。 假设它们允许所需的访问，浏览器将重定向到重定向 URI 指定初始请求中的查询字符串中的授权代码。

```http
http://localhost/myapp/?code=AwABAAAA...cZZ6IgAA&state=1234
```

如果还使用 OpenId 连接的单一登录，则需要附加参数，[这篇文章](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-protocols-oidc/)的详细信息，请参阅。 

下一步是要交换的访问令牌返回的授权代码。

### <a name="getting-an-access-token"></a>获取一个访问令牌

若要获取一个访问令牌，该应用程序发表单编码的参数到令牌请求 URL (`https://login.microsoftonline.com/common/oauth2/v2.0/token`) 和下列参数。

- `client_id`: 通过注册该应用程序生成的客户端 ID。
- `client_secret`︰ 通过注册该应用程序生成客户端密钥。
- `code`: 在上一步中获得的授权码。
- `redirect_uri`︰ 此值必须是授权代码请求中使用的值相同。
- `grant_type`︰ 使用授予该应用程序的类型。 这个值是`code`授权代码授予流。
- `scope`-以空格分隔列表的应用程序正在请求的范围。 在[这篇文章](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-scopes/)中的详细信息

我们的应用程序请求 URL 使用上一步中的代码应如下所示。

```http
POST https://login.microsoftonline.com/common/oauth2/v2.0/token
Content-Type: application/x-www-form-urlencoded

{
  grant_type=authorization_code
  &code=AwABAAAA...cZZ6IgAA
  &redirect_uri=http%3A%2F%2Flocalhost%2Fmyapp%2F
  &resource=https%3A%2F%2Fgraph.microsoft.com%2F
  &scope=https%3A%2F%2Fgraph.microsoft.com%2Fmail.read
  &client\_id=<CLIENT ID>
  &client\_secret=<CLIENT SECRET>
}
```

服务器响应的 JSON 负载，其中包括访问令牌。

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "token_type":"Bearer",
  "expires_in":"3600",
  "access_token":"eyJ0eXAi...b66LoPVA",
  "scope":"https://graph.microsoft.com/mail.read",
  ...
}
```

访问令牌位于`access_token`的 JSON 负载字段。 该应用程序使用此值来设置授权标头进行 REST 调用 API 时。

## <a name="calling-the-microsoft-graph"></a>调用 Microsoft Graph

应用程序具有一个访问令牌，它就可以调用 Microsoft Graph。 由于此示例应用程序中检索消息时，它将使用 HTTP GET 请求的`https://graph.microsoft.com/v1.0/me/messages`终结点。

### <a name="refining-the-request"></a>精炼的请求

应用程序可以通过使用 OData 查询参数控制 GET 请求的行为。  建议应用程序使用这些参数，来限制返回结果的数目，并限制为每个项返回的字段。 

我们的示例应用程序将显示主题、 发件人，以及日期和时间接收消息的表中显示的消息。 表显示最多 25 行，并进行排序以使最近收到的邮件顶端。 该应用程序使用下面的查询参数来得到这些结果。

- `$select`参数用于仅指定`subject`， `sender`，和`dateTimeReceived`字段。
- `$top`参数用于指定最多的 25 个项目。
- `$orderby`参数用于对结果进行排序`dateTimeReceived`字段。

这会导致下面的请求。

```http
GET https://graph.microsoft.com/v1.0/me/messages?$select=subject,from,receivedDateTime&$top=25&$orderby=receivedDateTime%20DESC
Accept: application/json
Authorization: Bearer eyJ0eXAi...b66LoPVA
```

现在，您已经看到如何拨打 Microsoft Graph，可以使用 API 参考来构造的调用您的应用程序需要的任何其他类型。 但是，请记住，您的应用程序都需要有这样的调用的应用程序注册上配置适当的权限。


