# <a name="call-microsoft-graph-in-an-angular-app"></a>角度的应用程序中调用 Microsoft Graph 

在本文中我们了解到 Office 365 将应用程序连接和调用 Microsoft Graph API 所需的最小任务。 我们使用从[使用 Microsoft Graph 的 Office 365 角度连接示例](https://github.com/microsoftgraph/angular-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

![Office 365 角度连接示例屏幕快照](./images/web-screenshot.png)

## <a name="prerequisites"></a>先决条件  

本主题假定以下。

* 您是舒适阅读 JavaScript 和[AngularJS](https://angularjs.org/)代码。

## <a name="overview"></a>概述

若要调用 Microsoft Graph API，您必须完成以下任务。

1. 在 Azure Active Directory 中注册应用程序
2. 将 Azure Active Directory 库配置的 JavaScript (ADAL JS)
3. 使用 ADAL 的 JS 来获取访问令牌
4. 在 Microsoft Graph api 请求中使用的访问令牌

<!--<a name="register"></a>-->
## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

或者，请参阅[注册 Azure 管理门户与基于浏览器的 web 应用程序](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterWebApp)说明的文章如何手动注册该应用程序，请记住以下详细信息︰

* 请确保 http://127.0.0.1:8080 /**登录 URL**。
* 之后您注册该应用程序，[配置**委派权限**的](https://github.com/microsoftgraph/angular-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure)角度应用程序要求。 该连接示例需要**发送电子邮件时已登录的用户**权限。

注意下面的值 Azure 应用程序的**配置**页面中因为需要这些值的角度应用程序中配置[ADAL JS](https://github.com/AzureAD/azure-activedirectory-library-for-js) 。

* 客户端 ID （特定于您的应用程序）
* 回复 URL (http://127.0.0.1:8080 /)

<!--<a name="adal"></a>-->
## <a name="configure-azure-active-directory-library-for-javascript-adal-js"></a>将 Azure Active Directory 库配置的 JavaScript (ADAL JS)

[JS ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-js)是 JavaScript 库，从而为您提供完整的支持在 Azure AD 用户在类似连接示例和令牌管理，以及其他功能的单页面应用程序 (SPAs) 上签名。 要利用此库，角度应用程序必须包括并对其进行配置。

只包含库和使用 Microsoft CDN 及其角特定模块。

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.7/js/adal.min.js"></script>
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.7/js/adal-angular.min.js"></script>
```

接下来，您必须配置 ADAL JS 服务配置角度应用程序的依赖项的任何地方。 此连接示例执行其配置， [*public/app.js*](https://github.com/microsoftgraph/angular-connect-rest-sample/blob/master/public/scripts/app.js)。 

要配置 ADAL JS，首先包括对 ADAL 的模块引用加上```AdalAngular```模块的需要将组和传递```adalAuthenticationServiceProvider```为您```config```函数。 配置库与```init```函数，传递该应用程序的客户机 ID 和```endpoints```声明的角度应用程序需要 CORS Api 请求的对象。

```javascript
// Initialize the ADAL provider with your clientID (found in the Azure Management Portal) and 
// the API URL (to enable CORS requests).
adalAuthenticationServiceProvider.init(
  {
    clientId: clientId,
    // The endpoints here are resources for cross origin requests.
    endpoints: {
      'https://graph.microsoft.com': 'https://graph.microsoft.com'
    }
  },
  $httpProvider
);
```

<!--<a name="accessToken"></a>-->
## <a name="use-adal-js-to-get-an-access-token"></a>使用 ADAL 的 JS 来获取访问令牌

您的应用程序需要将浏览器重定向到登录页面以便用户可以登录并授予您对其数据的应用程序访问权限。 连接示例利用 JS ADAL，来处理此任务。 

在其中一个应用程序的控制器，首先添加引用 ADAL 服务通过注入```adalAuthenticationService```插入您的控制器，然后定义一个函数，使用该服务的```login```您的 UI 可以调用的函数。 连接示例执行此任务的[*controllers/mainController.js*](https://github.com/microsoftgraph/angular-connect-rest-sample/blob/master/public/controllers/mainController.js)文件中。 

```javascript
/**
  * Expose the login method from ADAL to the view.
  */
function connect() {
  adalAuthenticationService.login();
};
```

调用此函数时，您的应用程序将用户重定向到登录页。 他们登录和授权您的应用程序后，它们将返回您的应用程序与 ADAL JS 将检索和存储的查询字符串中的访问令牌。 

<!--<a name="request"></a>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。 JS ADAL 自动截获所有 HTTP 请求，并使您不必手动设置该标题在使用库时向它们添加访问令牌。 

连接示例发送电子邮件使用```me/sendMail``` [*controllers/mainController.js*](https://github.com/microsoftgraph/angular-connect-rest-sample/blob/master/public/controllers/mainController.js)文件中 Microsoft Graph API 中的终结点。 

Microsoft 图表是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出要探索使用 Microsoft Graph API 可以完成什么的[API 参考](http://graph.microsoft.io/docs/api-reference/v1.0)。

