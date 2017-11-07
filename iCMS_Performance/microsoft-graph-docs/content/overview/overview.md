


# <a name="overview-of-microsoft-graph"></a>Microsoft Graph 的概述

Microsoft Graph （以前称为的 Office 365 提供统一的 API） 公开从 Microsoft 云服务通过一个 REST API，终结点 (**https://graph.microsoft.com**) 的多个 Api。 使用 Microsoft Graph，可以打开简单的导航到以前困难或复杂的查询。 
 
Microsoft Graph 提供了︰

- 统一的 API 端点来从单个响应中的多个 Microsoft 云服务访问聚合的数据 
- 实体和它们之间的关系之间的无缝导航 
- 对情报和见解来自 Microsoft 云访问

而且所有这些都使用单一身份验证令牌。

可以使用 API 来访问固定的实体，如用户、 组、 邮件、 消息、 日历、 任务和来自 Outlook、 OneDrive、 Azure Active Directory、 进度表、 OneNote 和其他类似服务的说明。 您还可以与您正在使用的用户或趋势分析围绕您的文档的列表获取办公室关系图 （仅适用于专业用户） 所采用的计算的关系。

Microsoft Graph 提供两个终结点。 通常可用的终结点 /v1.0 和预览终结点 /beta。  您可以使用在您的生产应用程序但不是 /beta /v1.0。  预览终结点 /beta 为我们提供最新的功能，开发人员用来试验并提供反馈，在 beta 版中的 Api 可能会随时更改而且尚未准备好用于生产环境的位置。

<!--<a name="msg_queries"> </a>-->

##<a name="common-queries"></a>公共查询

以下是使用 Microsoft Graph API 的通用查询的一些示例︰

| **操作** | **服务终结点** |
|:--------------------------|:----------------------------------------|
|   获取我的个人资料 |    `https://graph.microsoft.com/v1.0/me` |
|   获取我的文件|   `https://graph.microsoft.com/v1.0/me/drive/root/children` |
|   收到我的照片     | `https://graph.microsoft.com/v1.0/me/photo/$value` |
|   收到我的邮件 |   `https://graph.microsoft.com/v1.0/me/messages` |
|   让电子高重要性的邮件 | `https://graph.microsoft.com/v1.0/me/messages?$filter=importance%20eq%20'high'` |
|   获取我的日历 |   `https://graph.microsoft.com/v1.0/me/calendar` |
|   获取我的经理  | `https://graph.microsoft.com/v1.0/me/manager` |
|   获取最后一个用户修改文件命名为 foo.txt |  `https://graph.microsoft.com/v1.0/me/drive/root/children/foo.txt/lastModifiedByUser` |
|   获取我的成员统一的组|   `https://graph.microsoft.com/v1.0/me/memberOf/$/microsoft.graph.group?$filter=groupTypes/any(a:a%20eq%20'unified')` |
|   在我的组织中获取用户     | `https://graph.microsoft.com/v1.0/users` |
|   获取组对话 |   `https://graph.microsoft.com/v1.0/groups/<id>/conversations` |
|   获取与我有关的人    | `https://graph.microsoft.com/beta/me/people` |
|   获取趋势环绕在我的文件 |  `https://graph.microsoft.com/beta/me/trendingAround` |
|   让我带的工作的人员     | `https://graph.microsoft.com/beta/me/workingWith` |
|   获取我的任务    | `https://graph.microsoft.com/beta/me/tasks` |
|   获取我的便笺 |  `https://graph.microsoft.com/beta/me/notes/notebooks` |

<!-- <a name="msg_roof"> </a> -->

## <a name="all-office-365-data-under-one-roof"></a>在一个屋顶下的所有 Office 365 提供数据

下图显示了 Microsoft Graph 开发堆栈和它的工作原理。

![Microsoft Graph API 开发堆栈。](./images/MicrosoftGraph_DevStack.png)

 >  您的反馈对我们很重要。 与我们连接上[堆栈溢出](http://stackoverflow.com/questions/tagged/office365+or+microsoftgraph)。 标记您的问题 [MicrosoftGraph] 和 [office365]。



