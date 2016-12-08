# <a name="microsoft-graph-release-notes-and-known-issues"></a>已知的问题和 Microsoft Graph 发行说明

本文提供有关新功能的信息以及 Microsoft Graph API，至 11 月 2015年版中可用的开发人员可能想要知道的任何已知的问题。 


## <a name="ga-features-in-microsoft-graph-api"></a>GA Microsoft Graph API 中的功能

以下 Microsoft Graph API 功能一般有︰

* 用户
* 组
* 文件
* 邮件
* 日历
* 个人联系人 
* 创建、 读取、 更新和删除 (CRUD) 操作
* 跨原始资源共享 (CORS) 支持。

    
## <a name="preview-features-in-microsoft-graph-api"></a>在 Microsoft Graph API 中的预览功能

以下 Microsoft Graph API 预览功能均可用︰

* 注释 
* 任务
* Excel
* 人脉
* 组织联系人
* 应用程序
* 服务主体
* 目录架构扩展
* Webhook
* 见解和关系︰ 围绕趋势分析与处理
* 组内容在创建后的即时访问
* 个人帐户的混合身份验证模型以及工作和学校的科目。 虽然这是一个预览功能，适用于的两个`/v1.0`和`/beta`版本。


## <a name="microsoft-graph-known-issues"></a>Microsoft Graph 的已知问题

下面是已知与 Microsoft Graph 的问题。

### <a name="users"></a>用户
#### <a name="no-instant-access-after-creation"></a>在创建后没有即时访问
用户可以通过在用户实体的公告立即创建。 Office 365 必须首先分配许可给用户，才能访问 Office 365 提供服务。 即使这样，由于该服务的分布式特性，文件之前可能需要 15 分钟，消息和事件的实体是可用于该用户，通过 Microsoft Graph API。 在此期间，应用程序将收到一个 404 的 HTTP 错误响应。 

#### <a name="photo-restrictions"></a>照片的限制
读取和更新用户的个人资料照片才可以，如果用户具有邮箱。  此外，任何相片*可能*使用**thumbnailPhoto**属性已以前存储 (使用 Office 365 统一 API 预览或 Azure 广告图中，或通过 AD 连接同步) 将不再可通过 Microsoft Graph 用户照片属性。  未能读取或更新照片，在这种情况下，将导致以下错误︰

```javascript
    {
      "error": {
        "code": "ErrorNonExistentMailbox",
        "message": "The SMTP address has no mailbox associated with it."
      }
    }
```

 > **注意**︰ 不久前正式上市时，存储和检索用户配置文件的照片将被启用，即使用户没有邮箱，并且此错误将会消失。

#### <a name="default-contacts-folder"></a>默认联系人文件夹

在`/v1.0`版本中，`GET /me/contactFolders`不包括用户的默认联系人文件夹。 

修复将陆续提供。 同时，您可以使用下面的[联系人列表](http://graph.microsoft.io/docs/api-reference/v1.0/api/user_list_contacts)查询，并将**parentFolderId**属性作为一种变通方法以获取默认的联系人文件夹的文件夹 ID:

```
GET https://graph.microsoft.com/v1.0/me/contacts?$top=1&$select=parentFolderId
```
在上面的查询︰
1. `/me/contacts?$top=1`获取默认的联系人文件夹中的[联系人](http://graph.microsoft.io/docs/api-reference/v1.0/resources/contact)属性。
2. 将附加`&$select=parentFolderId`返回仅联系人的**parentFolderId**属性，该属性为默认的联系人文件夹的标识符。

#### <a name="adding-and-accessing-ics-based-calendars-in-users-mailbox"></a>添加和访问用户的邮箱中基于 ICS 日历
目前，还有部分支持基于 Internet 日历订阅 (ICS) 在上一个日历︰
* 您可以通过用户界面，而不是通过 Microsoft Graph API 用户邮箱添加基于 ICS 日历。 
* [列出用户的日历](http://graph.microsoft.io/docs/api-reference/v1.0/api/user_list_calendars)，可获取每个用户的默认日历组或指定的日历组，包括所有基于 ICS 日历中的[日历](http://graph.microsoft.io/docs/api-reference/v1.0/resources/calendar)的**名称**、**颜色**和**id**属性。 您无法存储或访问 ICS 日历资源中的 URL。
* 您还可以基于 ICS 日历的[列出的事件](http://graph.microsoft.io/docs/api-reference/v1.0/api/calendar_list_events)。

### <a name="groups"></a>组
#### <a name="policy"></a>策略
使用 Microsoft Graph 创建并命名统一的组绕过通过 Outlook Web App 配置任何统一的组策略。 

#### <a name="group-permission-scopes"></a>组的权限范围
Microsoft Graph 公开组 Api 访问两个权限范围 （*Group.Read.All*和*Group.ReadWrite.All*）。  必须由管理员 （即从预览更改） 同意这些权限范围。  我们计划在将来添加新的作用域的组可以由用户许可的。

#### <a name="adding-and-getting-attachments-of-group-posts"></a>添加和获取组帖子的附件
向组[添加](http://graph.microsoft.io/docs/api-reference/v1.0/api/post_post_attachments)附件发送，[列出](http://graph.microsoft.io/docs/api-reference/v1.0/api/post_list_attachments)和组帖子的附件目前返回的错误消息"OData 请求不支持获取。" 两个已推出修补程序`/v1.0`和`/beta`版本中，并期望 1 月 2016年年底可广泛用于。

### <a name="contacts"></a>联系人
* 目前支持的只有个人联系人。 组织联系人当前不支持在`/v1.0`，但可以在中找到`/beta`。
* 个人联系人的移动电话不会被返回联系人。 它将很快被添加。 在此期间，它可以通过 Outlook Api 访问。

### <a name="drives-files-and-content-streaming"></a>驱动器、 文件和流式传输的内容
* 首次通过 Microsoft Graph 之前 401 响应会导致浏览器通过其个人网站的用户访问用户的个人驱动器的访问。
* 上载和下载的文件 （在 Office 组、 驱动器或邮件文件附件中的文件） 被限制为 4 MB。

### <a name="functionality-available-only-in-existing-office-365-rest-apis"></a>仅在现有 Office 365 REST Api 中可用的功能
#### <a name="synchronization"></a>同步
（这也称为是差异查询 Azure 广告） 中的 outlook、 OneDrive 和 Azure AD 同步功能在中不可用`/v1.0`或`/beta`。  如果您的应用程序需要同步功能，请继续使用现有的 Office 365 和 Azure AD REST Api，也可以浏览新的 webhooks 预览功能通过 Microsoft Graph 提供的事件、 消息和联系人。

> **注意**︰ 它是一个目标，尽快，包括同步关闭现有的 Api 和 Microsoft Graph 之间的差距。

#### <a name="batching"></a>批处理
Microsoft Graph 不支持批处理。 但是，可以使用 Outlook beta 终结点和[批次 Outlook REST 调用](https://msdn.microsoft.com/en-us/office/office365/api/batch-outlook-rest-requests)。 

#### <a name="availability-in-china"></a>在中国的可用性
Microsoft Graph 服务是由 21Vianet 操作 （和现已在中国）。 请有关包括限制的详细信息，查看[Microsoft Graph sovereign 云部署](http://graph.microsoft.io/docs/overview/deployments)。

#### <a name="service-actions-and-functions"></a>服务操作和功能
`isMemberOf`和`getObjectsById`在 Microsoft Graph 中不可用

### <a name="microsoft-graph-permissions"></a>Microsoft Graph 权限
请检查[权限范围主题](http://graph.microsoft.io/docs/authorization/permission_scopes)有关 Microsoft Graph 支持应用程序和委派的权限的最新详细信息。  此外，还有以下限制的`v1.0`:

|权限 |   权限类型 | 限制 |  替代方法 |
|-----------|-----------------|------------|--------------|
|_User.ReadWrite_| 委托	    | 无法更新移动电话号码|    同时选择`Directory.AccessAsUser.All`| 
|_User.ReadWrite.All_|  委托	|  不能执行任何 CRUD 操作`User`而不更新用户高清晰度照片和扩展配置文件属性| 选择`Directory.ReadWrite.All`或`Directory.AccessAsUser.All`是否需要删除用户。|
|_User.Read.All_|   应用程序	 |不能执行任何其他用户的读取的操作| 同时选择`Directory.Read.All`|
| _User.ReadWrite.All_ |    应用程序	 |   不能执行任何 CRUD 操作`User`而不更新用户高清晰度照片和扩展配置文件属性 |    选择`Directory.ReadWrite.All`。 **注意**︰ 不能删除用户。|
|_Group.Read.All_   | 应用程序	 | 无法枚举组或组成员身份。  仍可以为 Office 组读取内容分组   | 同时选择`Directory.Read.All` |
|_Group.ReadWrite.All_  | 应用程序	   | 不能枚举组或组成员身份、 创建组、 更新组成员身份或删除组。  可仍然读取和更新办公组的组内容。   | 选择`Directory.ReadWrite.All`。 **注意**︰ 不能删除组。|

另外还有以下`/beta`限制︰

|权限 |   权限类型 | 限制 |  替代方法 |
|-----------|-----------------|------------|--------------|
| _Group.ReadWrite.All_ | 委托	 | 无法读取或更新 Office 组计划任务  | 同时选择`Tasks.ReadWrite`|
|_Tasks.ReadWrite_  | 委托	 | 无法读取或更新中已登录的用户的任务| 同时选择`Group.ReadWrite.All`|

### <a name="odata-related-limitations"></a>OData 相关的限制
* **$expand**限制︰ 
 * 不支持`nextLink`
 * 不支持多个级别展开的
 * 不支持具有额外的参数 （**$filter**， **$select**）
* 不支持多个命名空间
* 获取上`$ref`和用户、 组、 设备、 服务主体和应用程序不支持强制转换。
* `@odata.bind`不受支持。  这意味着，开发人员不能正确地设置`Accepted`或`RejectedSenders`在一组。
* `@odata.id`上不存在 （如消息） 非包容导航时使用最少的元数据
* 跨工作负载/过滤搜索不可用。 
* （使用**$search**） 的全文搜索功能仅适用于某些实体，如消息。

  >  您的反馈对我们很重要。 与我们连接上[堆栈溢出](http://stackoverflow.com/questions/tagged/office365)。 标记您的问题 [MicrosoftGraph] 和 [office365]。

  
             .

