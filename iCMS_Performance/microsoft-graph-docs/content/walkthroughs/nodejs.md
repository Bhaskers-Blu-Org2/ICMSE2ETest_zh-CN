# <a name="call-microsoft-graph-with-a-nodejs-app"></a>与 Node.js 应用程序调用 Microsoft Graph

在本文中我们了解到 Office 365 将应用程序连接和调用 Microsoft Graph API 所需的最小任务。 我们使用从[使用 Microsoft Graph 的 Office 365 Node.js 连接示例](https://github.com/microsoftgraph/nodejs-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

![Office 365 Node.js 连接示例屏幕快照](./images/web-screenshot.png)

## <a name="overview"></a>概述

若要调用 Microsoft Graph API，您的 web 应用程序必须完成以下任务。

1. 在 Azure Active Directory 中注册应用程序 
2. 为节点安装 Azure 的活动目录客户端库
3. 将浏览器重定向到登录页
4. 收到答复的 URL 页面中的授权码
5. 使用`adal-node`请求访问令牌
6. 对 Microsoft Graph API 发出请求

<!--<a name="register"/>-->
## <a name="register-your-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

或者，请参见一节[注册您的 web 服务器应用程序，使用 Azure 管理门户](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp)的说明如何手动注册该应用程序，请记住以下详细信息︰

* 为在步骤 6 中的**登录 URL** Node.js 应用程序中指定的页。 如果连接的示例中，URL 是 http://localhost:8080/登录，映射到的[/login](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/routes/index.js#L33)路由。
* 您的应用程序要求的[配置**委派权限**](https://github.com/microsoftgraph/nodejs-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure)。 连接示例需要**发送电子邮件时已登录的用户**权限。

记下 Azure 应用程序的**配置**页中的以下值。

* 客户机 ID
* 有效的密钥
* 回复 URL

这些值作为参数在 OAuth 流程中需要您的应用程序。

<!--<a name="adal">-->
## <a name="install-the-azure-active-directory-client-library-for-node"></a>为节点安装 Azure 的活动目录客户端库

Node.js 库 ADAL 轻松 Node.js 应用程序进行身份验证才能访问受保护的 AAD web 资源 AAD。
将 adal 节点添加到您现有的`package.json`首选终端输入以下。

`npm install adal-node --save`

Adal 节点客户端库的详细信息，请参阅上[npm](https://www.npmjs.com/package/adal-node)的其包信息。
问题，源代码以及最新的近期功能和修复程序，请参阅 adal 节点的项目在[Github](https://github.com/AzureAD/azure-activedirectory-library-for-nodejs)上。

<!--<a name="redirect"/>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>将浏览器重定向到登录页

您的应用程序需要将浏览器重定向到登录页面，以获得授权码，然后继续 OAuth 2.0 流。

在连接示例中，身份验证 URL 从[`authHelper.js#getAuthUrl`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/authHelper.js#L17)重定向[`login.hbs#login`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/views/login.hbs#L2)函数通过客户端`onclick`事件。

**authHelper.js#getAuthUrl**
```javascript
/**
 * Generate a fully formed uri to use for authentication based on the supplied resource argument
 * @return {string} a fully formed uri with which authentcation can be completed
 */
function getAuthUrl() {
    return credentials.authority + "/oauth2/authorize" +
        "?client_id=" + credentials.client_id +
        "&response_type=code" +
        "&redirect_uri=" + credentials.redirect_uri;
};
```

**login.hbs#login**
```javascript
function login() {
    window.location = '{{auth_url}}'.replace(/&amp;/g, '&'); // transform HTML special char from .hbs template rendering
}
```

<!--<a name="authcode"/>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>收到答复的 URL 页面中的授权码

用户登录后，流将返回到您的应用程序中的答复 URL 的浏览器。 中提供的授权码`code`查询字符串变量。

```javascript
router.get('/<application reply url>', function (req, res, next) {
  var authCode = req.query.code;
  // your router's implementation
});
```

请参见[相关的代码](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/routes/index.js#L34)中的连接示例

<!--<a name="accesstoken"/>-->
## <a name="use-adal-node-to-request-an-access-token"></a>使用`adal-node`请求访问令牌

现在，我们已经通过身份验证使用 Azure Active Directory，我们下一步是获取 adal 节点通过访问令牌。 我们所做的之后，我们就会准备对 Microsoft Graph API 发出其他请求。

若要请求一个访问令牌，adal 节点提供了两个回调函数。

|                          函数                         |                                      参数                                      | 说明                                                                                             |
|:---------------------------------------------------------:|:--------------------------------------------------------------------------------:|---------------------------------------------------------------------------------------------------------|
| `AuthenticationContext.acquireTokenWithAuthorizationCode` | `authCode`, `redirect_uri`, `resource`, `client_id`, `client_secret`, `callback` | 根据在登录过程中返回的授权代码的指定资源提供访问令牌 |
| `AuthenticationContext.acquireTokenWithRefreshToken`      | `token`, `client_id`, `client_secret`, `resource`, `callback`                    | 提供访问标记为指定资源根据刷新令牌                             |

在连接的示例中，将请求路由到[`authHelper.js`](https://github.com/microsoftgraph/nodejs-connect-rest-sample/blob/master/authHelper.js)，`client_id`和`client_secret`可以添加。

```javascript
// The application registration (must match Azure AD config)
var credentials = {
    authority: "https://login.microsoftonline.com/common",
    client_id: "<your client id here>",
    client_secret: "<your client secret>",
    redirect_uri: "http://localhost:8080/login"
};

/**
 * Gets a token for a given resource.
 * @param {string} code An authorization code returned from a client.
 * @param {string} res A URI that identifies the resource for which the token is valid.
 * @param {AcquireTokenCallback} callback The callback function.
 */
function getTokenFromCode(res, code, callback) {
    var authContext = new AuthenticationContext(credentials.authority);
    authContext.acquireTokenWithAuthorizationCode(code, credentials.redirect_uri, res, credentials.client_id, credentials.client_secret, function (err, response) {
        if (err) {
            callback(null);
        }
        else {
            callback(response);
        }
    });
};
```

<!--<a name="request"/>-->
## <a name="make-a-request-to-the-microsoft-graph-api"></a>对 Microsoft Graph API 发出请求

要确定我们对图形 API 的请求，我们请求必须使用签名`Authorization`标头包含任何 web 的访问令牌提供服务请求的资源。 正确的身份验证头将包括从 adal 节点的访问令牌，将采用以下格式。

`Authorization: Bearer <access token>`

使用`adal-node`，再加上与前一节我们身份验证逻辑，我们现在可以使用我们的访问令牌请求签名。

```javascript
/* GET home page. */
router.get('/<application reply url>', function (req, res, next) {
    var authCode = req.query.code;
    authHelper.getTokenFromCode('https://graph.microsoft.com/', req.query.code, function (token) {
        if (token !== null) {
            // Use this token to sign requests
            var headers = {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer ' + token
                };
            // request implementation...
        } else {
            // error handling
        }
    });
});
```

Microsoft 图表是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出要探索使用 Microsoft Graph API 可以完成什么的[API 参考](http://graph.microsoft.io/docs/api-reference/v1.0)。

<!--## Additional resources

- [Office 365 Node.js Connect sample using Microsoft Graph](https://github.com/OfficeDev/O365-Nodejs-Unified-API-Connect)-->

