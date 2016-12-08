# <a name="sovereign-cloud-deployments"></a>Sovereign 云部署


本文提供了有关 Microsoft Graph 和它们的功能可供开发人员使用不同的 sovereign 云实例的信息。 


## <a name="microsoft-graph-operated-by-21vianet-in-china"></a>Microsoft Graph 由中国 21Vianet

本部分提供有关 Microsoft Graph 由 21Vianet，以及开发人员可用的功能的信息。

### <a name="service-root-endpoints"></a>服务根终结点
| Microsoft Graph 由 21Vianet | Microsoft Graph|
|---------------------------|----------------|
| https://microsoftgraph.chinacloudapi.cn | https://graph.microsoft.com|

### <a name="microsoft-graph-explorer"></a>Microsoft Graph 资源管理器
| Microsoft Graph 由 21Vianet | Microsoft Graph|
|---------------------------|----------------|
|https://graphexplorerchina.azurewebsites.net| https://graphexplorer2.azurewebsites.net|

### <a name="azure-openid-connect-and-oauth20"></a>Azure OpenID 连接和 OAuth2.0
与其他产品不同用于获取登录令牌或调用由 21Vianet Microsoft Graph 的终结点。 

| Microsoft Graph 由 21Vianet | Microsoft Graph|
|---------------------------|----------------|
| https://login.chinacloudapi.cn | https://login.microsoftonline.com|
 
使用 https://login.chinacloudapi.cn/common/oauth2/authorize 进行身份验证的用户和 https://login.chinacloudapi.cn/common/oauth2/token 以获取为您的应用程序的标记来调用由 21Vianet Microsoft Graph。

> **注意**︰ 不是最新的[2.0 版授权并标记终结点](https://azure.microsoft.com/en-us/documentation/articles/active-directory-appmodel-v2-overview/)可用于 Microsoft Graph 由 21Vianet。  应用程序只能访问组织的数据并不是使用者的数据。 

### <a name="service-capabilities-offered-by-microsoft-graph-operated-by-21vianet"></a>由 21Vianet Microsoft Graph 提供的服务功能
将通常有以下的 Microsoft Graph 功能 (在`/v1.0`终结点):

* 用户
* 组
* 文件
* 邮件
* 日历
* 个人联系人 
* 创建、 读取、 更新和删除 (CRUD) 操作
* 跨原始资源共享 (CORS) 支持。

以下 Microsoft Graph 功能也都可以在预览 (在`/beta`终结点):

* 组织联系人
* 应用程序
* 服务主体
* 目录架构扩展
