
# <a name="microsoft-graph-app-authorization"></a>Microsoft Graph 应用程序授权


本文讨论了如何对用户进行身份验证、 获取一个访问令牌和续订使用刷新令牌访问令牌。
身份验证流可以分解为两个基本步骤︰

1. 请求授权码
2. 使用授权代码请求访问令牌并刷新令牌。 

>  **注意**︰ 您可以使用刷新标记当前存取令牌到期时获得一个新的访问令牌。

<!--To call the Microsoft Graph API, you have to complete the following tasks.

1. Register the application in Azure Active Directory
2. Authenticate a user and get an access token by calling methods on the Azure AD Authentication Library (ADAL)
3. Use ADAL to get an access token
4. Use the access token in a request to the Microsoft Graph API
5. Disconnect the session

In this article:

- [Authenticate a user and get app authorized](#msg_get_app_authorized)
- [Acquire access token](#msg_get_app_authenticated)
- [Renew access token using refresh token](#msg_renew_access_token)

 <a name="msg_get_app_authorized"> </a> -->
 
###<a name="authenticate-a-user-and-get-app-authorized"></a>验证用户身份和获得授权的应用程序
若要获取您授权的应用程序，则必须获得先经过身份验证的用户。 通过将用户重定向到 Azure 活动目录 (AD Azure) 授权终结点，以及您的应用程序信息，登录到他们的 Office 365 帐户执行此操作。 一旦用户登录，并同意权限请求的应用程序 （如果该用户已没试过），您的应用程序会收到获得 OAuth 访问令牌所需的授权代码。

> **注意**︰ 要做到这一点在[Azure AD 身份验证库 (ADAL)](https://msdn.microsoft.com/en-us/library/azure/jj573266.aspx)上调用的方法。 有关授权流程的详细信息，请参阅[授权代码授予流](https://msdn.microsoft.com/en-us/library/azure/dn645542.aspx)。

使用下面的 URL 获取 HTTPS 请求中提交将授权应用程序启动︰
 
```GET https://login.microsoftonline.com/common/oauth2/authorize?response_type=code&redirect_uri=<uri>&client_id=<id>```

**所需的查询字符串参数**

| 参数名称  | 值  | 说明                                                                                            |
|:----------------|:-------|:-------------------------------------------------------------------------------------------------------|
| *client_id*     | string | 为您的应用程序创建的客户端 ID。 这是您的应用程序的**客户端 ID**值在 Azure 租户应用程序注册表中设置。                                                                  |
| *response_type* | string | 指定请求的响应类型。 在授权代码的授权请求，该值必须是代码。 |
| *redirect_uri*  | string | 浏览器发送到身份验证完成时重定向 URL。  此值必须与应用程序的预配置的**回复 URL**值匹配                        |
 


以下显示正在运行的应用程序中实现此类请求的示例︰


```GET https://login.microsoftonline.com/common/oauth2/authorize?response_type=code&redirect_uri=http%3a%2f%2flocalhost:1339/auth/azureoauth/callback&client_id=8b8539cd-7b75-427f-bef1-4a6264fd4940``` 

此请求将返回`200 OK`响应和礼物的 Azure 的广告帐户登录页。 

使用有效的凭据并同意授予对该应用程序，登录页发送的权限的用户信号后`POST`请求到 Azure。 如果请求成功，Azure 的响应与`302 Found`消息转发到应用程序的重定向 URI 调用应用程序以接收所需的访问令牌。 转发的 URI，在响应中指定`Location`标头，对应于应用程序的答复 URL，包含两个查询参数， `code=...` ，`session_state=...`追加到该日志。 下面的示例演示此类举措的一段摘录︰ 

```no-highlight 
HTTP/1.1 302 Found
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: text/html; charset=utf-8
Expires: -1
Location: http://localhost:1339/auth/azureoauth/callback?code=AAABAAAAvPM...&session_state=a9556cd3-cae6-4bc9-bf51-672f7b79b7c6
Server: Microsoft-IIS/8.5
P3P: CP="DSP CUR OTPi IND OTRi ONL FIN"

..... 
```

在此示例中，应用程序的答复 URL 是`http://localhost:1339/auth/azureoauth/callback`。 在处理此响应，您必须提取`code`参数值，并使用它来获取初始的 OAuth 2.0 访问并刷新的标记 （请参见下一节）。

> `302 Found`以上的响应是不同于`302 Found`响应如果启动针对登录过程将得到`https://login.windows.net/<tenantId>/oauth2/authorize?...`URL。 在后一种情况下，`302 Found`响应您将请求转发到`login.microsoftonline.com`。
 
<!---<a name="msg_get_app_authenticated"> </a> -->

###<a name="acquire-an-access-token"></a>获取一个访问令牌
访问 Microsoft Graph API 资源，您的应用程序必须在每个 HTTP 请求中包含有效的 OAuth 2.0 访问令牌。 可以使用下面的 POST 请求的访问令牌︰

```no-highlight 
POST https://login.microsoftonline.com/common/oauth2/token HTTP/1.1
content-type : application/x-www-form-urlencoded
content-length : 144
```
 
该请求需要以下格式的 URL 编码负载︰
 
```no-highlight 
grant_type=authorization_code
&redirect_uri=<uri>
&client_id=<id>
&client_secret=<secret_key>
&code=<code>
&resource=https%3A%2F%2Fgraph.microsoft.com%2F
```

**所需的查询字符串参数**

| 参数名称  | 值  | 说明                                                                                            |
|:----------------|:-------|:-------------------------------------------------------------------------------------------------------|
| *client_id*     | string | 为您的应用程序创建的客户端 ID。  |
| *client_secret*  | string | 为您的应用程序创建的项。 此值是 Azure 管理门户上的应用程序配置页面的**键**部分中的相同值|
| *redirect_uri*  | string | 浏览器发送到身份验证完成时重定向 URL。  |
| *代码*  | string | 授权码。 `code`查询从授权请求的响应中返回的参数值。 |
| *资源*   | string | 您要访问的资源。 若要调用 Microsoft Graph API，此参数将值设置为"https://graph.microsoft.com/"。|

下面的代码段举例说明的请求负载，用来获得初始 OAuth 2.0 访问令牌︰

```no-highlight  
grant_type=authorization_code&
redirect_uri=http%3A%2F%2Flocalhost%3A1339%2Fauth%2Fazureoauth%2Fcallback&
client_id=8b8539cd-7b75-427f-bef1-4a6264fd4940&client_secret=PJW3dznGfyNSm3rM9aHeXWGKsTMepKXT1Eqy45XXdU4%3D&
code=AAABAAAAvPM1KaPlrEqdFSBzjqfTGBLRVQc6BtQmJ_9DQZUg8Tb7TJgTmbTE7AHM93qB5EKc4Bf-bOgzt3mebAywK-09X1uBHwOluuqSWfd9LU2HHgZtxcZFIYI5UL7L1UEvhrJRvX2iHhfz9ZSRMZMVL55n_K79gCOxtSATeCUw52zPk5ZaQ87Y42SCLsRZN4Y_zddhD3mMpkObiHVT8HzfhBUiT0oX0e-Q439vkbZoKiq1HaqMR3IPHiCXDbPPH5u7a4NTe5xAhh-o2MUIe6s4Xqql86sv1-IwyroOJJMueGUarkfbgwqmYL9Tm-jWab8o-BAK_plVsN73GU8cXO8ts30wa2YmNR5ZxSkw8oiB4mSZwGzGQlch55DRnucDs0SZBgj5etGi3SeXv5jhKlDU2S0bAPnGxF3QAH0N_zBpfakETVlcsHKi714u-tn9da6aTPQsE0IYKTAYgxjTMei6zfRFvCZi-tKdFR6X9TvvmF2iPdGQGWKeLw8CMWUzU8VmOhiHc0aBKG6RaXAOTM067J_9WKYPxMopcytD2z8HVkL1QhggAA&
resource=https%3A%2F%2Fgraph.microsoft.com%2F
```

如果此请求成功，`200 OK`将返回的响应。 示例如下所示︰

```no-highlight  
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 2978
Access-Control-Allow-Origin: *

{
    "token_type":"Bearer",
    "expires_in":"3599",
    "expires_on":"1426551729",
    "not_before":"1426547829",
    "resource":"https://graph.microsoft.com/",
    "access_token":"eyJ0eXAiOiJKV1QiLCJhb...",
    "refresh_token":"AAABAAAAvPM1KaPlrEqd...",
    "scope": "Calendar.ReadWrite Directory.Read.All Files.ReadWrite Group.ReadWrite.All Mail.ReadWrite Mail.Send User.ReadBasic.All",
    "id_token":"eyJ0eXAiOiJKV1QiLCJhbGci..."
}
```

 
响应正文是 JSON 格式的字符串，其中包含访问令牌 (`access_token`)。 您需要提供此令牌与任何后续的 HTTP 请求，从而访问 Microsoft Graph API 资源。 

`scope`属性值应与在应用程序的注册过程为应用程序授予的权限。

在指定的时间间隔内保持有效的访问令牌 (`3599`在上面的示例) 秒 （或 1 小时） 从发放的时间，作为中指定`expires_in`属性。 结果还包含刷新令牌 (`refresh_token`) 必须用于续订的到期或已过期的访问令牌。 

在成品代码中，您的应用程序需要监视这些令牌到期并刷新令牌到期之前续订过期的访问令牌。 


<!---<a name="msg_renew_access_token using refresh token"> </a> -->

###<a name="renew-expiring-access-token-using-refresh-token"></a>续订过期的访问令牌使用刷新令牌
若要刷新过期的访问令牌，使用 POST 请求与以下示例类似 （前提是没有过期的刷新标记）︰

```no-highlight  
POST https://login.microsoftonline.com/common/oauth2/token HTTP/1.1
Host: login.microsoftonline.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 897


grant_type=refresh_token
&redirect_uri=http%3A%2F%2Flocalhost%3A1339%2Fauth%2Fazureoauth%2Fcallback
&client_id=8b8539cd-7b75-427f-bef1-4a6264fd4940
&client_secret=PJW3dznGfyNSm3rM9aHeXWGKsTMepKXT1Eqy45XXdU4%3D
&refresh_token=AAABAAAAvPM1KaPlrEqdFSBzjqfTGM74--...
&resource=https%3A%2F%2Fgraph.microsoft.com%2F
```

**所需的查询字符串参数**

| 参数名称  | 值  | 说明                                                                                                                                         |
|:----------------|:-------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| *client_id*     | string | 为您的应用程序创建的客户端 ID。  |
| *redirect_uri*  | string | 浏览器发送到身份验证完成时重定向 URL。 这应与第一个请求中使用的*redirect_uri*值相匹配。 |
| *client_secret* | string | 为您的应用程序创建的密钥值之一。                                                                                                     |
| *refresh_token* | string | 以前收到刷新令牌。    |
| *资源*      | string | 您要访问的资源。|

请注意，此请求是几乎完全相同的初始标记的收购请求。 有两个不同的请求负载，即、`grant_type`参数现在包含的值的`refresh_token`(而不是`code`)。
 
成功的响应将返回一个 JSON 字符串的有效负载部分类似于下面的输出︰

```no-highlight 
{
    "token_type":"Bearer",
    "expires_in":"3600",
    "expires_on":"1426561346",
    "not_before":"1426557446",
    "resource":"https://graph.microsoft.com/",
    "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOi...", 
    "refresh_token":"AAABAAAAvPM1KaPlrEqdFSBzj...",
   "scope":"Graph.Read",
    "pwd_exp":"6553342",
    "pwd_url":"https://portal.microsoftonline.com/ChangePassword.aspx"
}
```
 
除缺少`id_token`属性，该响应正文具有相同的语法和语义的初始标记获取响应。 返回新的生命时间`access_token`和`refresh_token`的扩展值。 访问令牌的新过期时间是指定的秒数，在`expires_in`值，当刷新令牌的请求已成功提交的时间。 
 
当刷新令牌到期时，无法更新使用上述 POST 请求任何过期的访问令牌。 相反，您必须重新启动[应用程序授权和身份验证](#msg_get_app_authorized)过程。


<!--##Additional Resources##

- [Hands on lab: Deep dive into the Office 365 unified API](http://dev.office.com/hands-on-labs/4585)  -->

