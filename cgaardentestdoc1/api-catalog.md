<<<<<<< 头 ms。TocTitle: Office 365 API 参考标题︰ Office 365 API 参考说明︰ 查找 Office 365 API 引用和其余部分和客户端库 Api 的邮件、 联系人和日历数据文件进行交互和发现服务有关的信息。
ms。ContentId: 6736150c-641e-4e1b-bcc0-6cce0996779d ms.topic︰ 参考 (API) ms.date: 2016，4 月 21=======
---
ms。Toctitle: Office 365 API 引用标题︰ Office 365 API 参考描述︰ 查找 Office 365 API 引用和有关其余部分和客户端库的 Api 的信息。
ms。ContentId: 6736150c-641e-4e1b-bcc0-6cce0996779d ms.date: 2016，9 月 20
>>>>>>> 转移

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="office-365-api-reference"></a>Office 365 API 参考 
    
 _**适用于︰**联机交换 |Office 365 |OneDrive 为公司的_

<<<<<<< 头
<a name="p-classpreviewnotethis-documentation-covers-features-that-are-currently-in-preview-for-information-about-working-with-preview-features-see-preview-developer-features-on-the-office-365-platformhowtoplatform-development-preview-features-overviewmdp"></a><p class="previewnote">本文档介绍当前正在预览的功能。 有关如何使用预览功能的信息，请参阅[在 Office 365 的平台上的预览开发功能](..\howto\platform-development-preview-features-overview.md)。</p>
=======
[!INCLUDE [Use Microsoft Graph](../includes/use-msgraph-note.md)]

Office 365 Api 使您可以访问到您的客户的 Office 365 提供数据，包括它们最 — 其邮件、 日历、 联系人、 用户和组、 文件和文件夹，所有直接从您的应用程序本身中关注的事情。 
            
您可以从解决方案跨所有移动、 web 应用程序和桌面平台访问 Office 365 Api。 无论您开发平台或工具。 因此是否正在生成 web 应用程序使用 Rails，.NET、 PHP、 Java、 Python 或拼音或创建应用程序的 Windows 通用应用程序，iOS 中，Android，或在另一台设备平台上，它是您的选择。
    
### <a name="office-365-sdks-make-app-development-easier"></a>Office 365 的 Sdk 简化应用程序开发

您可以直接针对 REST Api 与 Office 365 交互、 编写和维护代码周围管理身份验证令牌，您要访问的 API 构建正确的 Url 和查询和其他任务进行编程。 Visual Studio、 Eclipse 和 Android Studio，或 Xcode，Office 365 Sdk 帮助减少需要为访问 Office 365 Api 编写的代码的复杂性。

[Visual Studio 为 Office 开发人员工具](http://aka.ms/OfficeDevToolsForVS2013)包括提供.NET 的 Sdk 和 JavaScript 库包装 Office 365 REST 服务，并提供一种更容易的方法来连接到您的 Office 365 提供数据。 Sdk 是可供 ASP.NET MVC、 ASP.NET Web 窗体、 WPF，赢得窗体、 通用的应用程序，Cordova 和 Xamarin 在 Visual Studio 中的项目类型。 

对于 Android 开发人员来说，Android SDK 的 Eclipse 和 Android 的工作室现在上市也是。  请参阅[Office 365 的 Android SDK](https://github.com/OfficeDev/Office-365-SDK-for-Android)。 
>>>>>>> 转移

对于 iOS 应用 iOS Xcode （预览） 的 SDK 支持目标 C 和 Swift [Xcode 6](https://developer.apple.com/xcode/)内的语言。 请参阅[Office 365 的 iOS 的 SDK](https://github.com/OfficeDev/Office-365-SDK-for-iOS)。 


<!--
<a href="#bk_groups"><img alt="Groups API (preview) icon" src="office/office365/api/images/O365APIs_REST_Reference_icons_groups.png" /></a>
-->

<!--
<a href="#bk_mail" id="Mail">
    <img title="Mail API" src="http://i.imgur.com/qhjA7Qy.png" onmouseover="this.src='http://i.imgur.com/s5rJ51y.png'" onmouseout="this.src='http://i.imgur.com/qhjA7Qy.png'" />
</a>
<a href="#bk_contacts" id="Contacts">
    <img title="Contacts API" src="http://i.imgur.com/xJbLQcp.png" onmouseover="this.src='http://i.imgur.com/idZpJmq.png'" onmouseout="this.src='http://i.imgur.com/xJbLQcp.png'" />
</a>
<a href="#bk_calendar" id="Calendar">
    <img title="Calendar API" src="http://i.imgur.com/dKrWDZ2.png" onmouseover="this.src='http://i.imgur.com/9D0eQGe.png'" onmouseout="this.src='http://i.imgur.com/dKrWDZ2.png'" />
</a>
-->


## <a name="batching-outlook-rest-requests-preview"></a>批处理的 Outlook 其余请求 （预览）

[分批发送 Outlook 其余请求](..\api\batch-outlook-rest-requests.md)


## <a name="outlook-task"></a>Outlook 任务
[任务 API](..\api\task-rest-operations.md)

**任务操作**&nbsp; 
[创建任务](..\api\task-rest-operations.md#CreateTasks) | [获取任务](..\api\task-rest-operations.md#GetTasks) | [更新任务](..\api\task-rest-operations.md#UpdateTasks) | [删除任务](..\api\task-rest-operations.md#DeleteTasks) | 
[完成任务](..\api\task-rest-operations.md#CompleteTasks) | [同步任务或任务文件夹](..\api\task-rest-operations.md#SyncTasks) 


**任务文件夹操作**&nbsp; 
[创建的任务文件夹](..\api\task-rest-operations.md#CreateTaskFolders) | [获取任务文件夹](..\api\task-rest-operations.md#GetTaskFolders) | [更新任务文件夹](..\api\task-rest-operations.md#UpdateTaskFolders) | 
[删除任务文件夹](..\api\task-rest-operations.md#DeleteTaskFolders) | [同步任务或任务文件夹](..\api\task-rest-operations.md#SyncTasks) 


**任务组的操作**&nbsp; 
[创建任务组](..\api\task-rest-operations.md#CreateTaskGroups) | [获取任务组](..\api\task-rest-operations.md#GetTaskGroups) | [更新任务组](..\api\task-rest-operations.md#UpdateTaskGroups) | 
[删除任务组](..\api\task-rest-operations.md#DeleteTaskGroups)


<a name="bk_people"> </a>

##<a name="outlook-people-preview"></a>Outlook 的人 （预览）

[API 的人](..\api\people-rest-operations.md)

**浏览︰**&nbsp;  
[浏览](..\api\people-rest-operations.md#BrowsePeople) | [页面](..\api\people-rest-operations.md#BrowsePaging) | 
[排序](..\api\people-rest-operations.md#BrowseSort) | [限制](..\api\people-rest-operations.md#BrowsePageSize) |
[选择](..\api\people-rest-operations.md#BrowseSelecting) | [筛选](..\api\people-rest-operations.md#BrowseFiltering) |
[筛选和选择](..\api\people-rest-operations.md#BrowseSelectingAndFiltering)

**搜索︰**&nbsp; 
[选择主题](..\api\people-rest-operations.md#SearchTopic) |
[筛选搜索](..\api\people-rest-operations.md#SearchFilter) |
[模糊搜索](..\api\people-rest-operations.md#FuzzySearch)



## <a name="office-365-data-extensions"></a>Office 365 数据扩展插件

[数据扩展插件 API](..\api\extensions-rest-operations.md)

**打开类型扩展︰**&nbsp; [在现有物料创建](..\api\extensions-rest-operations.md#CreateExtensionInExistingItem) | [创建新项](..\api\extensions-rest-operations.md#CreateExtensionInNewItem) |
[获得](..\api\extensions-rest-operations.md#GetExtension) | [获取项扩展](..\api\extensions-rest-operations.md#GetExpandedExtension) |
[更新](..\api\extensions-rest-operations.md#UpdateExtension) | [删除](..\api\extensions-rest-operations.md#DeleteExtension)


## <a name="outlook-extended-properties"></a>Outlook 的扩展属性

[扩展属性 API](..\api\extended-properties-rest-operations.md)

**扩展属性**  &nbsp;  [在现有物料创建](..\api\extended-properties-rest-operations.md#CreateExtendedPropertyInExistingItem) | 
[创建新项](..\api\extended-properties-rest-operations.md#CreateExtendedPropertyInNewItem) | 
[获取项扩展](..\api\extended-properties-rest-operations.md#GetExpandedExtendedProperty) | 
[筛选器](..\api\extended-properties-rest-operations.md#GetItemByFilteringExtendedProperty)



<a name="bk_mail"> </a>

##<a name="outlook-mail"></a>Outlook 邮件

[邮件 API](..\api\mail-rest-operations.md) 

**的邮件︰**&nbsp; [获得](..\api\mail-rest-operations.md#Getmessages) | [创建和发送](..\api\mail-rest-operations.md#Sendmessages) |
 [答复](..\api\mail-rest-operations.md#Replytomessages) | [向前](..\api\mail-rest-operations.md#Forwardmessages) |
 [更新](..\api\mail-rest-operations.md#Updatemessages) | [删除](..\api\mail-rest-operations.md#DeleteMessages) |
 [移动或复制](..\api\mail-rest-operations.md#MoveCopymessages)

**附件︰**&nbsp;  [获得](..\api\mail-rest-operations.md#GetAttachments) |
 [创建](..\api\mail-rest-operations.md#CreateAttachments) | [删除](..\api\mail-rest-operations.md#DeleteAttachments)

**文件夹︰**&nbsp;  [获得](..\api\mail-rest-operations.md#GetFolders) | [创建](..\api\mail-rest-operations.md#CreateFolders) | [更新](..\api\mail-rest-operations.md#UpdateFolders) |
 [删除](..\api\mail-rest-operations.md#DeleteFolders) | [移动或复制](..\api\mail-rest-operations.md#MoveCopyFolders)


<a name="bk_contacts"> </a>

##<a name="outlook-contacts"></a>Outlook 联系人

[联系人 API](..\api\contacts-rest-operations.md)

**联系人︰**&nbsp;  [获得](..\api\contacts-rest-operations.md#GetContacts) | [创建](..\api\contacts-rest-operations.md#CreateContacts) |
 [更新](..\api\contacts-rest-operations.md#UpdateContacts) | [删除](..\api\contacts-rest-operations.md#DeleteContacts) 
 

**联系人文件夹︰**&nbsp;  [获取](..\api\contacts-rest-operations.md#GetContactFolders)


<a name="bk_calendar"> </a>

##<a name="outlook-calendar"></a>Outlook 日历

[API 的日历](..\api\calendar-rest-operations.md)

**日历视图︰**  &nbsp;  [获得](..\api\calendar-rest-operations.md#GetCalendarView) | [同步](..\api\calendar-rest-operations.md#SyncCalendarView)

**事件︰**&nbsp;[获得](..\api\calendar-rest-operations.md#GetEvents) | [同步](..\api\calendar-rest-operations.md#SyncCalendarView) |
 [创建](..\api\calendar-rest-operations.md#CreateEvents) |
 [更新](..\api\calendar-rest-operations.md#UpdateEvents) | [响应](..\api\calendar-rest-operations.md#RespondToEvents) | 
 [删除](..\api\calendar-rest-operations.md#DeleteEvents)  

**附件︰**&nbsp; 
 [Get](..\api\calendar-rest-operations.md#GetAttachments) | [Create](..\api\calendar-rest-operations.md#reateAttachments) |
 [Delete](..\api\calendar-rest-operations.md#DeleteAttachments)
 
 **提醒︰**&nbsp; 
 [获得](..\api\calendar-rest-operations.md#GetReminders) | 
 [暂停](..\api\calendar-rest-operations.md#SnoozeReminders) | 
 [关闭](..\api\calendar-rest-operations.md#DismissReminders)

**日历︰**&nbsp;[获得](..\api\calendar-rest-operations.md#GetCalendars) |
 [创建](..\api\calendar-rest-operations.md#CreateCalendars) | [更新](..\api\calendar-rest-operations.md#UpdateCalendars) |
 [删除](..\api\calendar-rest-operations.md#DeleteCalendars)  

**日历组︰**&nbsp;   [获得](..\api\calendar-rest-operations.md#GetCalendarGroups) |
 [创建](..\api\calendar-rest-operations.md#CreateCalendarGroups) | [更新](..\api\calendar-rest-operations.md#UpdateCalendarGroups) |
 [删除](..\api\calendar-rest-operations.md#DeleteCalendarGroups)



##<a name="resource-reference-for-the-mail-calendar-contacts-and-task-apis"></a>资源引用的邮件、 日历、 联系人和任务的 Api

[资源引用](..\API\complex-types-for-mail-contacts-calendar.md) 
 
 **的实体︰**&nbsp;[日历](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource) |
 [CalendarGroup](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource) | [联系人](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource) |
 [ContactFolder](..\api\complex-types-for-mail-contacts-calendar.md#ContactFolderResource) | [事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) |
 [EventMessage](..\api\complex-types-for-mail-contacts-calendar.md#EventMessageResource) | [扩展属性](..\api\complex-types-for-mail-contacts-calendar.md#ExtendedProperties) | 
 [FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource) | [文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource) |
 [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource) | [消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) |
 [任务 （预览）](..\api\complex-types-for-mail-contacts-calendar.md#TaskResource) | [TaskFolder （预览）](..\api\complex-types-for-mail-contacts-calendar.md#TaskFolderResource) | 
 [TaskGroup （预览）](..\api\complex-types-for-mail-contacts-calendar.md#TaskGroupResource) | 
 [用户](..\api\complex-types-for-mail-contacts-calendar.md#UserResource)   
 
 **复杂类型︰**&nbsp;[与会者](..\api\complex-types-for-mail-contacts-calendar.md#Attendee) | 
 [AttendeeBase](..\api\complex-types-for-mail-contacts-calendar.md#AttendeeBase) （预览） | [AttendeeAvailability](..\api\complex-types-for-mail-contacts-calendar.md#AttendeeAvailability)（预览） | [DateTimeTimeZone](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZoneBeta) | 
 [电子邮件地址](..\api\complex-types-for-mail-contacts-calendar.md#EmailAddress) | 
 [GeoCoordinates](..\api\complex-types-for-mail-contacts-calendar.md#GeoCoordinates) | 
 [ItemBody](..\api\complex-types-for-mail-contacts-calendar.md#ItemBody)  | 
 [位置](..\api\complex-types-for-mail-contacts-calendar.md#Location)（预览） | [LocationConstraint](..\api\complex-types-for-mail-contacts-calendar.md#LocationConstraint)（预览） | [MeetingTimeCandidate](..\api\complex-types-for-mail-contacts-calendar.md#MeetingTimeCandidate)（预览） | [PatternedRecurrence](..\api\complex-types-for-mail-contacts-calendar.md#PatternedRecurrence) | 
  [PhysicalAddress](..\api\complex-types-for-mail-contacts-calendar.md#PhysicalAddress) | 
 [收件人](..\api\complex-types-for-mail-contacts-calendar.md#Recipient) | 
 [RecurrencePattern](..\api\complex-types-for-mail-contacts-calendar.md#RecurrencePattern) | 
 [RecurrenceRange](..\api\complex-types-for-mail-contacts-calendar.md#RecurrenceRange) | 
 [ResponseStatus](..\api\complex-types-for-mail-contacts-calendar.md#ResponseStatus) | 
 [TimeConstraint](..\api\complex-types-for-mail-contacts-calendar.md#TimeConstraint) （预览） | [时间段](..\api\complex-types-for-mail-contacts-calendar.md#TimeSlot)（预览） | [时间戳](..\api\complex-types-for-mail-contacts-calendar.md#TimeStamp)（预览）    
 
 
 **OData 查询参数︰**&nbsp; [$search](..\api\complex-types-for-mail-contacts-calendar.md#Search) | 
 [$filter](..\api\complex-types-for-mail-contacts-calendar.md#Filter) | [$select](..\api\complex-types-for-mail-contacts-calendar.md#Select) | 
 [$orderby](..\api\complex-types-for-mail-contacts-calendar.md#OrderBy) | [$top 和 $skip](..\api\complex-types-for-mail-contacts-calendar.md#TopSkip)  | 
 $expand |[$count](..\api\complex-types-for-mail-contacts-calendar.md#Count)   

<a name="bk_notify"> </a>

##<a name="outlook-notifications"></a>Outlook 的通知

[推式通知 API](../api/notify-rest-operations.md)

[流式传输通知 API](../api/notify-streaming-rest-operations.md)（预览）


<a name="bk_photo"> </a>

##<a name="outlook-user-photo"></a>Outlook 用户照片

[用户照片 API](../api/photo-rest-operations.md)
 

<a name="bk_discovery"> </a>

##<a name="discovery-service"></a>发现服务

[发现服务 API](..\api\discovery-service-rest-operations.md)

[初始登录](..\api\discovery-service-rest-operations.md#DiscoveryServiceoperationsInitialsignin) |
 [发现特定服务](..\api\discovery-service-rest-operations.md#DiscoveryServiceoperationsDiscoverspecificservices) | [了解哪些服务是可以被发现](..\api\discovery-service-rest-operations.md#DiscoveryServiceoperationsLearnwhatservicesarediscoverable)


<a name="bk_files"> </a>

##<a name="files"></a>文件

[OneDrive API](https://dev.onedrive.com/)


<a name="bk_video"> </a>

##<a name="video"></a>视频 

[视频的 API](../api/video-rest-operations.md)

**视频门户网站︰**&nbsp;  
  [获取信息](..\api\video-rest-operations.md#GetPortalInformation)
  
**通道︰**&nbsp;  
  [获取信息](..\api\video-rest-operations.md#GetChannelsInfo) 
  
**视频信息︰**&nbsp;  
  [获得](..\api\video-rest-operations.md#GetVideoInfo) | [更新视频元数据](..\api\video-rest-operations.md#UpdateVideo) 
  
**的视频︰**&nbsp;  
  [上载](..\api\video-rest-operations.md#UploadVideos) | [删除](..\api\video-rest-operations.md#DeleteVideos) 

##<a name="api-resource-and-service-endpoints-of-office-365-operated-by-21vianet"></a>API 的由 21Vianet Office 365 的资源和服务端点
[由 21Vianet Office 365 的 API 端点](..\api\o365-china-endpoints.md)

##<a name="office-365-management-apis"></a>Office 365 管理 Api
[入门 》](https://msdn.microsoft.com/library/office/dn707383.aspx) | [服务通信 API （预览）](https://msdn.microsoft.com/EN-US/library/dn707386.aspx) | [管理活动 API 参考 （预览）](https://msdn.microsoft.com/library/office/mt227394.aspx) | [报告 web 服务](https://msdn.microsoft.com/en-us/library/office/jj984325.aspx) 

##<a name="additional-resources"></a>其他资源

###<a name="api-sandbox"></a>API 沙盒
[了解 Office 365 Api 使用该交互控制台](http://apisandbox.msdn.microsoft.com/)

###<a name="rest-api-response-status-codes"></a>REST API，响应状态代码

[HTTP 响应状态代码](..\howto\http-response-status-codes.md)


<<<<<<< 头
<!--
**Get started:** &nbsp; <a href="setup-development-environment?aspnet"> ASP.NET MVC apps </a> | <a href="setup-development-environment?javascript"> JavaScript web apps </a> | <a href="setup-development-environment?iOS"> iOS </a> | <a href="setup-development-environment?android"> Android </a>
-->


<a name="get-started-nbsp-aspnet-mvc-appshowtogetting-started-office-365-apismdaspnet-javascript-web-appshowtogetting-started-office-365-apismdjavascript-ioshowtogetting-started-office-365-apismdios-androidhowtogetting-started-office-365-apismdandroid"></a>**开始︰**&nbsp; [ASP.NET MVC 应用程序](..\howto\getting-started-Office-365-APIs.md?aspnet) | [JavaScript web 应用程序](..\howto\getting-started-Office-365-APIs.md?javascript) | [iOS](..\howto\getting-started-Office-365-APIs.md?iOS) | [Android](..\howto\getting-started-Office-365-APIs.md?android)  
=======
###<a name="office-365-platform-overview"></a>Office 365 平台概述
>>>>>>> 转移

[在 Office 365 的平台上开发的概述](..\howto\platform-development-overview.md) | [设置 Office 365 开发环境](..\howTo\setup-development-environment.md) 

[快速入门办公室 365APIs](..\howto\getting-started-Office-365-APIs.md) 

###<a name="office-365-permission-scopes"></a>Office 365 的权限范围
[所有 Office 365 的权限范围的详细信息](..\howto\application-manifest.md)

###<a name="microsoft-partner-center-api-reference"></a>Microsoft 合作伙伴中心 API 参考
合作伙伴可以使用[CSP 商务 REST API](https://msdn.microsoft.com/en-us/library/partnercenter/dn974944.aspx)来创建客户帐户、 管理客户配置文件，Microsoft 商务平台，在采购和管理订单和客户的 Microsoft 产品预订。 



