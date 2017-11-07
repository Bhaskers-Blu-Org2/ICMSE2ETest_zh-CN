
# <a name="microsoft-graph-frequently-asked-questions-faqs"></a>Microsoft Graph 常见问题 (Faq)

## <a name="what-platforms-are-supported-by-microsoft-graph-api"></a>Microsoft Graph API 支持哪些平台？
<!--
Apps can use the Microsoft Graph API to perform create, read, update, and delete (CRUD) operations on data sources and entities, giving them seamless access to work data. 

**Ease of use--one endpoint, all Office 365 data under one roof**

You can use the API in four steps:
1.  Select your programming language and development environment.
2.  Build your app.
3.  Optionally, host your app in Microsoft Azure or any cloud platform you choose.
4.  Authenticate your users by using single sign-on with Azure AD.

As a developer you can use the API to create custom apps that access and interact with all the richness of enterprise and productivity data--users, groups, organizational contacts, files, folders, mail, calendar, insights and relationships--and build apps across all mobile, web, and desktop platforms. No matter your development platform or tools. Using a single service endpoint to access those entities and data. And a single authentication flow.  -->

您可以：

<!--Just like in Office 365 APIs, Office 365 unified endpoint API  allows you to build apps using any development environment of your choice:  -->

- 使用任何开发环境比较熟悉，像.NET、 PHP、 Java、 Python 或拼音
- 使用任何编程语言，开发平台和宿主环境
- 构建访问 API 使用任何 web 语言，包括 JavaScript，HTML5，Python、 拼音、 PHP 和 ASP.NET 应用程序  
- 使用您选择的 IDE，不管是 Visual Studio，Eclipse、 Android Studio、 Xcode 或别的选择
- 主机在 Microsoft Azure 或任何云平台应用程序
- 为 Windows 通用，iOS 开发应用 Android，或在另一台设备平台
- 从 Office 加载项 （以前的 Office 的应用程序） 或 SharePoint 外接程序 （以前为 SharePoint 的应用程序） 调用 API
 


## <a name="why-use-microsoft-graph-api"></a>为什么使用 Microsoft Graph API？

假设您要以编程方式检索用户的文件，配置文件图片和最后编辑该文件在您的组织中的用户管理器中找到。 因为信息存储在多个服务 Azure Active Directory，SharePoint 和 Exchange 任务涉及到多个步骤使用 Office 365 的 Api: 

1. 搜索服务用于查找各种服务终结点 
2. 确定您的 Office 365 提供应用程序要连接到的服务的 URL
3. 然后获取并管理每个服务的访问令牌，并直接向服务发出请求

现在，使用 Microsoft Graph API 可用于执行相同的复杂操作，通过一个 REST API，终结点。 您没有发现和定位为每项服务的不同终结点、 获取和管理每个服务的单独的访问令牌、 面对孤立的服务和各种不同的数据模型。

##<a name="sample-queries"></a>示例查询

下面的示例显示当前模型与 Office 365 API 使用不同的服务终结点进行交互和多么简单这变得与 Microsoft Graph API。

**不同的服务终结点**

|   **操作**                  |  **API**                          |  **服务终结点** |
|:-----------------------------|:-----------------------------------------|:-----------------|
| 对于 Office 365 API 中发现服务终结点               |     `Discovery Service`           | _https://_**api.office.com**_/discovery/v1.0/me/services_ |
| 获取用户           |     `Azure AD Graph API` | _https://_**graph.windows.net**_/contoso.com/users?api-version=2013-04-05_|
| 从收件箱获取消息集合       |     `Office 365 API`           | _https://_**outlook.office365.com**_/api/v1.0/me/messages_  |
| 乔的文件   |     `Office 365 API`  | _https://_**contoso my.sharepoint.com**_ /_个人/joe_contoso_com/api/v1.0/files_ |


使用 Microsoft Graph API，您无需首先发现服务终结点，然后遍历不同的终结点来获取用户的文件，邮件，等等。 您只需与一个其他 URL 命名空间，这是_**graph.microsoft.com**_。

**Microsoft Graph API**

|   **操作**                  |  **API**                          |  **服务终结点** |
|:-----------------------------|:-----------------------------------------|:-----------------|
| 对于 Office 365 API 中发现服务终结点                |     `Microsoft Graph`           | 不需要 |
| 获取用户           |     `Microsoft Graph` | _https://_**graph.microsoft.com**_/v1.0/contoso.onmicrosoft.com/users_ |
| 从收件箱获取消息集合       |     `Microsoft Graph`           | _https://_**graph.microsoft.com**_/v1.0/me/messages_  |
| 乔的文件   |     `Microsoft Graph `  | _https://_**graph.microsoft.com**_/v1.0/me/drive/root/children_ |


## <a name="whatre-the-benefits-of-using-microsoft-graph-api"></a>什么是使用 Microsoft Graph API 的好处？

一些使用 Microsoft Graph API 的优点如下所示︰

**使用 Microsoft 云服务一致和简化的开发人员体验**

-   所有的服务终结点的单个命名空间。 没有需要的服务终结点的发现。
-   一个令牌来访问所有资源
-   目前各自为政的服务之间的集成和直接导航 （例如，获取编写特定的文档的用户部门和管理链）
-   只需要使用一个 API 集，即，只需要使用 Microsoft Graph API 连接到多个服务
-   REST API 和整个 Office 平台实体统一和扩展 
-   一致的属性命名和跨实体，包括实体之间的导航属性的方案

**启用更高效使用 Office 的工作和生活经验**

-   上下文相关的内容。 例如，查找文档组、 项目、 团队或趋势
-   上下文的用户关系。 例如，您可以找到用户的组成员身份、 兴趣、 技能和专业知识。  您还可以获取组织结构图的关系

**启用在任何平台上的任何编程语言开发的应用程序**

-   开发工具和资源的所有开发人员。 您可以使用任何平台和语言来开发 
-   移动所有平台使用的开放技术开发  
-   不需要任何专门的交换、 SharePoint 或 Azure 广告知识，以访问 Microsoft Graph API 实体

<!---<a name="msg_v2auth"> </a>-->

## <a name="does-microsoft-graph-api-support-v20-app-authentication-endpoint"></a>Microsoft Graph API 不支持 2.0 版应用程序身份验证终结点？

是。 详细信息请参阅[身份验证 Microsoft Graph 使用 v2 身份验证终结点的终结点](http://graph.microsoft.io/docs/authorization/converged_auth)。



  > 您的反馈对我们很重要。 与我们连接上[堆栈溢出](http://stackoverflow.com/questions/tagged/office365)。 标记您的问题 [MicrosoftGraph] 和 [office365]。








