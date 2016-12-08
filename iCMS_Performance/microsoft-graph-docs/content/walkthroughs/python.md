# <a name="call-microsoft-graph-in-a-python-app"></a>在 Python 应用程序中调用 Microsoft Graph 

在本文中我们了解到 Office 365 将应用程序连接和调用 Microsoft Graph API 所需的最小任务。 我们使用从[使用 Microsoft Graph 的 Office 365 Python 连接示例](https://github.com/microsoftgraph/python3-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

![Office 365 Python 连接示例屏幕快照](./images/web-screenshot.png)

##  <a name="prerequisites"></a>先决条件

本主题假定如下︰

* 您习惯阅读 Python 代码。
* 您熟悉 OAuth 的概念。

## <a name="overview"></a>概述

若要调用 Microsoft Graph API，Python 应用程序必须完成以下任务。

1. 在 Azure Active Directory 中注册应用程序
2. 将浏览器重定向到登录页面
3. 收到答复的 URL 页面中的授权码
4. 从终结点颁发的令牌请求访问令牌
5. 在 Microsoft Graph api 请求中使用的访问令牌 

<!--<a name="register"></a>-->
## <a name="register-the-application-in-azure-active-directory"></a>在 Azure Active Directory 中注册应用程序

在可以开始使用 Office 365 之前，您需要注册您的应用程序并设置权限以使用 Microsoft Graph 服务。
只需几次单击，您可以注册应用程序以访问用户的工作或学校帐户使用的[应用程序注册工具](https://dev.office.com/app-registration)。 它将需要转到[Microsoft Azure 管理门户](https://manage.windowsazure.com)管理

或者，请参见一节[注册您的 web 服务器应用程序，使用 Azure 管理门户](https://msdn.microsoft.com/en-us/office/office365/HowTo/add-common-consent-manually#bk_RegisterServerApp)的说明如何手动注册该应用程序，请记住以下详细信息︰

* 请确保**登录 URL**。
* 在您注册该应用程序，[配置**委派权限**](https://github.com/microsoftgraph/python3-connect-rest-sample/wiki/Grant-permissions-to-the-Connect-application-in-Azure)，Python 应用程序要求。 该连接示例需要**发送电子邮件时已登录的用户**权限。

注意下面的值 Azure 应用程序的**配置**页面中因为需要这些值的 Python 应用程序中配置的 OAuth 流程。

* 客户端 ID （特定于您的应用程序）
* 回复 URL (http://127.0.0.1:8000/连接/get_token /)
* 应用程序键 （唯一的应用程序）

<!--<a name="redirect"></a>-->
## <a name="redirect-the-browser-to-the-sign-in-page"></a>将浏览器重定向到登录页面

您的应用程序需要将浏览器重定向到登录页面开始的 OAuth 流程并获得授权码。 

在连接的示例，下面的代码 （位于[*connect/auth_helper.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/auth_helper.py)） 生成需要重定向到用户的应用程序，并输送到视图，它可用于重定向的 URL。 

```python
# This function creates the signin URL that the app will
# direct the user to in order to sign in to Office 365 and
# give the app consent.
def get_signin_url(redirect_uri):
  # Build the query parameters for the signin URL.
  params = { 'client_id': client_id,
             'redirect_uri': redirect_uri,
             'response_type': 'code'
           }

  authorize_url = '{0}{1}'.format(authority, '/common/oauth2/authorize?{0}')
  signin_url = authorize_url.format(urlencode(params))
  return signin_url
```

<!--<a name="authCode"></a>-->
## <a name="receive-an-authorization-code-in-your-reply-url-page"></a>收到答复的 URL 页面中的授权码

用户登录后，浏览器被重定向到您回复的 URL， ```get_token``` [*connect/views.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/views.py)，与附加查询字符串作为授权代码中的函数```code```变量。 

连接示例获取的代码从查询字符串，以便它可以访问符号再交换。

```python
auth_code = request.GET['code']
```

<!--<a name="accessToken"></a>-->
## <a name="request-an-access-token-from-the-token-issuing-endpoint"></a>从终结点颁发的令牌请求访问令牌

授权码之后，您可以使用它的客户机 ID，键，并回复你从 Azure Active Directory 请求访问令牌的 URL 值。 

> **请注意**该请求还必须指定要使用的资源。 如果 Microsoft Graph 的资源值是`https://graph.microsoft.com`。

连接示例请求中的标记```get_token_from_code``` [*connect/auth_helper.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/auth_helper.py)文件中的函数。

```python
# This function passes the authorization code to the token
# issuing endpoint, gets the token, and then returns it.
def get_token_from_code(auth_code, redirect_uri):
  # Build the post form for the token request
  post_data = { 'grant_type': 'authorization_code',
                'code': auth_code,
                'redirect_uri': redirect_uri,
                'client_id': client_id,
                'client_secret': client_secret,
                'resource': 'https://graph.microsoft.com'
              }
              
  r = requests.post(token_url, data = post_data)
  
  try:
    return r.json()
  except:
    return 'Error retrieving token: {0} - {1}'.format(r.status_code, r.text)
```

> **请注意**响应提供了比刚刚访问令牌的详细信息。 例如，您的应用程序可以获取刷新令牌，而不用显式重新登录用户请求新的访问令牌。

<!--<a name="request"></a>-->
## <a name="use-the-access-token-in-a-request-to-the-microsoft-graph-api"></a>在 Microsoft Graph api 请求中使用的访问令牌

使用访问令牌，您的应用程序可以对 Microsoft Graph API 进行身份验证的请求。 您的应用程序必须为每个请求的**授权**标头添加访问令牌。

连接示例发送电子邮件使用```me/microsoft.graph.sendMail```Microsoft Graph API 中的终结点。 中的代码是```call_sendMail_endpoint``` [*connect/graph_service.py*](https://github.com/microsoftgraph/python3-connect-rest-sample/blob/master/connect/graph_service.py)文件中的函数。 这是代码，以演示如何将访问代码附加到授权标头。

```python
# Set request headers.
headers = { 
  'User-Agent' : 'python_tutorial/1.0',
  'Authorization' : 'Bearer {0}'.format(access_token),
  'Accept' : 'application/json',
  'Content-Type' : 'application/json'
}
```

> **请注意**请求必须还发送**内容类型**标头值由图形 API，例如，接受`application/json`。

Microsoft Graph API 是非常强大，unifiying 可用于所有类型的 Microsoft 数据进行都交互的 API。 签出 API 参考研究使用 Microsoft Graph API 可以完成些什么。

<!--
## Additional resources

-  [Office 365 Python Connect sample using Microsoft Graph](https://github.com/OfficeDev/O365-Python-Microsoft-Graph-Connect)
-  [Office Dev Center](http://dev.office.com) 
-  [Microsoft Graph API reference]()-->
