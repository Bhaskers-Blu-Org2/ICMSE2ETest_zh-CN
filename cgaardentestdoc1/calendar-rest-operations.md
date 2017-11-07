ms。TocTitle: Outlook 日历 REST API 引用标题︰ Outlook 日历 REST API 参考说明︰ 引用与 REST API，日历和客户端库提供对事件、 日历和日历组，在 Exchange 在线访问的 Api 进行交互的方式。
ms。ContentId: 443f1cdf-1adb-46a2-b299-228c6f429954 ms.topic︰ 参考 (API) ms.date: 6 月 29，2016年

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyleshtml)]

# <a name="outlook-calendar-rest-api-reference"></a>Outlook 日历 REST API 参考


[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookVersion_v2defaulthtml)]

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<p class="previewnote">本文档介绍了用于查找会议时间、 取消事件，并引用附件预览中的 API。 预览功能可能会发生更改之前终止的对象，并使用它们的代码都可能会断开。 因此，一般情况下应使用 API 的生产版本在生产代码中 如果可用，2.0 版目前的首选的版本。</p>

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

   
 _**适用于︰**联机交换 |Office 365 |Hotmail.com |Live.com |MSN.com |Outlook.com |Passport.com_

该日历 API 提供对事件、 日历和日历组数据受 Azure 上 Office 365 的 Active Directory 和 Microsoft 专门在这些域中的帐户中的类似数据访问︰ Hotmail.com，Live.com，MSN.com、 Outlook.com 和 Passport.com。 
  

<!-- Can add the following sentence back once the client libraries have been updated for converged auth and outlook.com

You can access the Calendar API by calling the corresponding REST APIs directly in your apps, or by using the Office 365 client libraries and SDKs.
-->

**请注意** 

- 例外情况是 API 对[查找会议时间](#FindMeetingTimesPreview)，这取决于 Office 365 邮箱 （在 Azure AD)，而不到 Microsoft 帐户。 
- 为引用的简单起见，本文的其余部分使用**"Outlook.com"，包括上面列出的 Microsoft 帐户域**。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

**在 beta 版本的 api 不感兴趣？** 使用该控件，在右上角并选择所需的版本。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

**在 2.0 版的 api 中不感兴趣？** 使用该控件，在右上角并选择所需的版本。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->




<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

**在 1.0 版的 api 不感兴趣？** 使用该控件，在右上角并选择所需的版本。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->
 
 
 
## <a name="all-calendar-api-operations"></a>所有日历 API 操作

<a name="EventOperations"></a> 
**事件操作**事件表示约会或在用户的日历上的会议。 事件可以是 （对于定期事件） 系列主、 次、 单个实例或异常。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

[获取事件](#GetEvents) | [同步事件](#SyncCalendarView) | [查找会议时间 （预览）](#FindMeetingTimesPreview) | [创建事件](#CreateEvents) | 
[更新事件](#UpdateEvents) | [对事件作出响应](#RespndToEvents) | [中删除事件](#DeleteEvents) | [取消事件 （预览）](#CancelEvents) | 
[获取附件](#GetAttachments) | [创建附件](#CreateAttachments) | [删除附件](#DeleteAttachments) | 
[获得提醒](#GetReminders) | [暂停提醒](#SnoozeReminders)] |[消除的提醒](#DismissReminders)


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

[获取事件](#GetEvents) | [同步事件](#SyncCalendarView) | [创建事件](#CreateEvents) | 
[更新事件](#UpdateEvents) | [对事件作出响应](#RespndToEvents) | [中删除事件](#DeleteEvents) | 
[获取附件](#GetAttachments) | [创建附件](#CreateAttachments) | [删除附件](#DeleteAttachments) | 
[获得提醒](#GetReminders) | [暂停提醒](#SnoozeReminders)] |[消除的提醒](#DismissReminders)


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

[获取事件](#GetEvents) | [同步事件](#SyncCalendarView) | [创建事件](#CreateEvents) | 
[更新事件](#UpdateEvents) | [对事件作出响应](#RespndToEvents) | [中删除事件](#DeleteEvents) | 
[获取附件](#GetAttachments) | [创建附件](#CreateAttachments) | [删除附件](#DeleteAttachments) | 
[获得提醒](#GetReminders) | [暂停提醒](#SnoozeReminders)] |[消除的提醒](#DismissReminders)

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->




<a name="CalendarOperations"> </a>
**日历操作**日历可作为容器的事件。 用户可以具有多个日历。 Office 365 中的每个日历可以赋予一个日历组。

[获取日历](#GetCalendars) | [创建日历](#CreateCalendars) | [更新日历](#UpdateCalendars) | [删除日历](#DeleteCalendars) 

<a name="CalendarGroupOperations"></a> 
**日历组操作**日历组是一种方法来组织多个日历。 用户可以添加到 Outlook 或 Outlook Web App 中的单个日历组的多个日历。 这使得用户更方便地快速查看组内的所有日历。


**请注意**Outlook.com 支持仅可通过访问默认日历组`../me/calendars`快捷方式。 您不能删除该日历组，或创建其他日历组。


[获取日历组](#GetCalendarGroups) | [创建日历组](#CreateCalendarGroups) | 
[更新日历组](#UpdateCalendarGroups) | [删除日历组](#DeleteCalendarGroups)  

另请参见︰

[REST API，事件资源](..\api\complex-types-for-mail-contacts-calendar.md#EventResource) | 
[REST API，日历资源](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource) |
[REST API，日历组资源](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)



<a name="Overview"> </a>
## <a name="using-the-calendar-rest-api"></a>使用日历 REST API，

### <a name="authentication"></a>身份验证

像其他[Outlook REST API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)，用于日历 api，每个请求应包括有效的访问令牌。 获取一个访问令牌要求您注册并标识您的应用程序，并获得相应的授权。 您可以有关某些简化的注册和授权选项，让您[了解详细信息](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)。 继续在日历 API 中的特定操作，请记住这一点。

<a name="SupportedVersions"> </a>

###<a name="version-of-api"></a>API 版本

在所有版本的 Outlook REST API 支持日历 REST API。 根据的特定版本，功能可能会有所不同。

###<a name="target-user"></a>目标用户

代表当前用户始终执行日历 API 请求。 

Outlook 的 REST API 的通用于所有子集的详细信息，请参阅[使用 Outlook REST API](..\api\use-outlook-rest-api.md) 。

****

<a name="GetEvents"> </a>
## <a name="get-events"></a>获取事件

获取事件集合或一个事件。 

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

获取日历事件的所有操作均可都使用_更愿意︰ outlook.timezone_ HTTP 标头，指定响应中的开始和结束时间时区的时间。 例如，以下_更愿意︰ outlook.timezone_标头设置开始和结束时间为美国东部标准时间响应中。

```
Prefer: outlook.timezone="Eastern Standard Time"
``` 

如果没有指定_更愿意︰ outlook.timezone_在响应中的开始和结束时间以 UTC 返回的标头。

可用于_OriginalStartTimeZone_和_OriginalEndTimeZone_属性_事件_资源上找出创建事件时所使用的时区。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->
<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

获取日历事件的所有操作均可都使用_更愿意︰ outlook.timezone_ HTTP 标头，指定响应中的开始和结束时间时区的时间。 例如，以下_更愿意︰ outlook.timezone_标头设置开始和结束时间为美国东部标准时间响应中。

```
Prefer: outlook.timezone="Eastern Standard Time"
``` 

如果没有指定_更愿意︰ outlook.timezone_在响应中的开始和结束时间以 UTC 返回的标头。 请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 

可用于_OriginalStartTimeZone_和_OriginalEndTimeZone_属性_事件_资源上找出创建事件时所使用的时区。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->


REST API︰[获取日历视图 (REST)](#GetCalendarView) |  
[获取系列主服务器和单个事件 (REST)](#GetEventCollection) |
 [获得事件实例 (REST)](#GetEventInstances) | [获取事件 (REST)](#GetEvent) 

客户端库︰[获取用户的日历 （客户端） 中的事件](#GetEventsClient)

****

<a name="GetCalendarView"> </a>
###<a name="get-a-calendar-view-rest"></a>获取日历视图 (REST) 

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

在定义的时间范围，从用户的主日历的日历视图中获取事件、 异常和事件的单个实例 (`../me/calendarview`) 或从不同的日历。
   

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
GET https://outlook.office.com/api/beta/me/calendars/{calendar_id}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应中的事件默认时区。|
|_URL 参数_|
|calendar_id|string|如果您收到来自特定日历的日历视图的日历 ID。|
|start_datetime|方法|日期和事件开始的时间。|
|end_datetime|方法|日期和事件结束的时间。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

**请注意**默认情况下，在响应每个事件包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

例如，得到的 10 月，当月的日历视图返回只为每个事件的主题属性。 假设_更愿意︰ outlook.timezone_标头不包含在请求中，将 UTC 时区。。 

```
GET https://outlook.office.com/api/beta/me/calendarview?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject
```

 **响应类型**

在指定的时间范围内展开的[的事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
GET https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应中的事件默认时区。|
|_URL 参数_|
|calendar_id|string|如果您收到来自特定日历的日历视图的日历 ID。|
|start_datetime|方法|日期和事件开始的时间。|
|end_datetime|方法|日期和事件结束的时间。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

**请注意**默认情况下，在响应每个事件包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

例如，得到的 10 月，当月的日历视图返回只为每个事件的主题属性。 假设_更愿意︰ outlook.timezone_标头不包含在请求中，将 UTC 时区。。 

```
GET https://outlook.office.com/api/v2.0/me/calendarview?startDateTime=2014-10-01T01:00:00&endDateTime=2014-10-31T23:00:00&$select=Subject
```

 **响应类型**

在指定的时间范围内展开的[的事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendarview?start={start_datetime}&end={end_datetime}
GET https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|如果您收到来自特定日历的日历视图的日历 ID。|
|start_datetime|方法|日期和事件开始的时间。|
|end_datetime|方法|日期和事件结束的时间。|

**请注意**默认情况下，在响应每个事件包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

例如，得到的 10 月，当月的日历视图返回的主题属性将为每个事件︰ 

```
GET https://outlook.office.com/api/v1.0/me/calendarview?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject
```

 **响应类型**

在指定的时间范围内展开的[的事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="GetEventCollection"> </a>
###<a name="get-series-master-and-single-events-rest"></a>获取系列主服务器和单个事件 (REST) 

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

从用户的主日历中获得系列主和单一实例的事件的集合 (`../me/events`) 或从不同的日历。 若要获取扩展的事件实例，您可以 [获得日历视图](#GetCalendarView)或[获得的事件实例](#GetEventInstances)。



<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
GET https://outlook.office.com/api/beta/me/events
GET https://outlook.office.com/api/beta/me/calendars/{calendar_id}/events
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_Header 参数|
|喜欢︰|outlook.timezone|在响应中的事件默认时区。|
|_URL 参数_|
|calendar_id|string|如果您收到来自特定日历事件日历 ID。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_头未指定，则返回 UTC 时间开始和结束时间。

**请注意**在响应每个事件包括它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 下一步的示例，请参阅。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**在响应中返回仅**者**、**组织者**、 **Start**和**End**属性的每个事件指定。 如果不使用**$select**将返回的事件的属性的完整列表的第一个示例响应中[获取事件 (REST)](#GetEvent)是指。


**示例请求**

```
GET https://outlook.office.com/api/beta/me/events?$select=Subject,Organizer,Start,End
```

**响应示例**

状态代码︰ 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events(Subject,Organizer,Start,End)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyDAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWw==\"",
            "Id": "AAMkAGI28tEyDAAA=",
            "Subject": "Scrum",
            "Start": {
                "DateTime": "2015-11-02T17:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-02T17:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyCAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWg==\"",
            "Id": "AAMkAGI28tEyCAAA=",
            "Subject": "team lunch",
            "Start": {
                "DateTime": "2015-11-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-03T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2ADTG93AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49w==\"",
            "Id": "AAMkAGI2G93AAA=",
            "Subject": "Weekly Meeting on Contoso Project",
            "Start": {
                "DateTime": "2014-10-13T21:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T22:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG92AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49g==\"",
            "Id": "AAMkAGI2TG92AAA=",
            "Subject": "Daily Team Meeting",
            "Start": {
                "DateTime": "2014-10-13T18:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T18:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG91AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==\"",
            "Id": "AAMkAGI2TG91AAA=",
            "Subject": "Rob:Alex 1:1",
            "Start": {
                "DateTime": "2014-10-15T16:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-15T17:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG90AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46g==\"",
            "Id": "AAMkAGI2TG90AAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2015-11-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-27T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9zAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==\"",
            "Id": "AAMkAGI2TG9zAAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2014-11-27T00:00:00"
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-11-28T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9yAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49Q==\"",
            "Id": "AAMkAGI2TG9yAAA=",
            "Subject": "New Year's Day Holiday",
            "Start": {
                "DateTime": "2015-01-01T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-01-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9xAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x45w==\"",
            "Id": "AAMkAGI2TG9xAAA=",
            "Subject": "Christmas Holiday",
            "Start": {
                "DateTime": "2014-12-25T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-12-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events
GET https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}/events
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应中的事件默认时区。|
|_URL 参数_|
|calendar_id|string|如果您收到来自特定日历事件日历 ID。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

**请注意**在响应每个事件包括它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 下一步的示例，请参阅。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**在响应中返回仅**者**、**组织者**、 **Start**和**End**属性的每个事件指定。 如果不使用**$select**将返回的事件的属性的完整列表的第一个示例响应中[获取事件 (REST)](#GetEvent)是指。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/events?$select=Subject,Organizer,Start,End
```

**响应示例**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events(Subject,Organizer,Start,End)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyDAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWw==\"",
            "Id": "AAMkAGI28tEyDAAA=",
            "Subject": "Scrum",
            "Start": {
                "DateTime": "2015-11-02T17:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-02T17:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI28tEyCAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAA/LpDWg==\"",
            "Id": "AAMkAGI28tEyCAAA=",
            "Subject": "team lunch",
            "Start": {
                "DateTime": "2015-11-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-03T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "user0TestUser",
                    "Address": "user0@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2ADTG93AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49w==\"",
            "Id": "AAMkAGI2G93AAA=",
            "Subject": "Weekly Meeting on Contoso Project",
            "Start": {
                "DateTime": "2014-10-13T21:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T22:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG92AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49g==\"",
            "Id": "AAMkAGI2TG92AAA=",
            "Subject": "Daily Team Meeting",
            "Start": {
                "DateTime": "2014-10-13T18:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-10-13T18:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG91AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==\"",
            "Id": "AAMkAGI2TG91AAA=",
            "Subject": "Rob:Alex 1:1",
            "Start": {
                "DateTime": "2014-10-15T16:30:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": "2014-10-15T17:30:00Z",
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG90AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46g==\"",
            "Id": "AAMkAGI2TG90AAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2015-11-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-11-27T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9zAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==\"",
            "Id": "AAMkAGI2TG9zAAA=",
            "Subject": "Thanksgiving Holiday",
            "Start": {
                "DateTime": "2014-11-27T00:00:00"
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-11-28T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9yAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x49Q==\"",
            "Id": "AAMkAGI2TG9yAAA=",
            "Subject": "New Year's Day Holiday",
            "Start": {
                "DateTime": "2015-01-01T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2015-01-02T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG9xAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x45w==\"",
            "Id": "AAMkAGI2TG9xAAA=",
            "Subject": "Christmas Holiday",
            "Start": {
                "DateTime": "2014-12-25T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "End": {
                "DateTime": "2014-12-26T00:00:00",
                "TimeZone": "Pacific Standard Time"
            },
            "Organizer": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events
GET https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}/events
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|如果您收到来自特定日历事件日历 ID。|

**请注意**在响应每个事件包括它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 下一步的示例，请参阅。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**在响应中返回仅**者**、**组织者**、 **Start**和**End**属性的每个事件指定。 如果不使用**$select**将返回的事件的属性的完整列表的第一个示例响应中[获取事件 (REST)](#GetEvent)是指。


```REST-i
{
   "method": "GET",
   "resourceFormat": "https://outlook.office.com/api/v1.0/me/events?$select=Subject,Organizer,Start,End",
   "requestUrl": "https://outlook.office.com/api/v1.0/me/events?$select=Subject,Organizer,Start,End",
   "requestHeaders": {
      "Accept": "application/json"
   },
   "parameterDetails": [],
   "statusCode": 200,
   "responseBody": {
    "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T23:13:47.3959685Z",
            "DateTimeLastModified": "2014-10-19T23:13:47.6772234Z",
            "Subject": "Weekly Meeting on Contoso Project",
            "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-10-13T21:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2014-10-13T22:00:00Z",
            "EndTimeZone": "Pacific Standard Time",           
            "Location": {
                "DisplayName": "Alex's Office"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SeriesMaster",
            "SeriesMasterId": null,
            "Attendees": [
                {
                    "EmailAddress": {
                        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Janet Schorr"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Pavel Bansky"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                }
            ],
            "Recurrence": {
                "Pattern": {
                    "Type": "Weekly",
                    "Interval": 1,
                    "Month": 0,
                    "Index": "First",
                    "FirstDayOfWeek": "Sunday",
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Monday"
                    ]
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2014-10-13T00:00:00-07:00",
                    "EndDate": "0001-01-01T00:00:00Z",
                    "NumberOfOccurrences": 0
                }
            },
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG92AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48A==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG92AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48A==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T23:13:01.9733945Z",
            "DateTimeLastModified": "2014-10-19T23:13:02.426753Z",
            "Subject": "Daily Team Meeting",
            "BodyPreview": "Daily sync on project progress and team member status",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nDaily sync on project progress and team member status\r\n</body>\r\n</html>\r\n"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-10-13T18:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2014-10-13T18:30:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": "Team Room"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SeriesMaster",
            "SeriesMasterId": null,
            "Attendees": [
                {
                    "EmailAddress": {
                        "Address": "roby@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Rob Young"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Pavel Bansky"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Janet Schorr"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Garth Fort"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                },
                {
                    "EmailAddress": {
                        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Katie Jordan"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                }
            ],
            "Recurrence": {
                "Pattern": {
                    "Type": "Weekly",
                    "Interval": 1,
                    "Month": 0,
                    "Index": "First",
                    "FirstDayOfWeek": "Sunday",
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Monday",
                        "Tuesday",
                        "Wednesday",
                        "Thursday",
                        "Friday"
                    ]
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2014-10-13T00:00:00-07:00",
                    "EndDate": "0001-01-01T00:00:00Z",
                    "NumberOfOccurrences": 0
                }
            },
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG91AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG91AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x47Q==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T23:12:40.7543183Z",
            "DateTimeLastModified": "2014-10-19T23:12:41.0043215Z",
            "Subject": "Rob:Alex 1:1",
            "BodyPreview": "Let's meet every month to engage in project review and career discussion",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none\"><!-- p { margin-top: 0px; margin-bottom: 0px; }--></style>\r\n</head>\r\n<body dir=\"ltr\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>Let's meet every month to engage in project review and career discussion<br>\r\n</p>\r\n</body>\r\n</html>\r\n"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-10-15T16:30:00Z",
            "StartTimeZone": "Pacific Standard Time",            
            "End": "2014-10-15T17:30:00Z",
            "EndTimeZone": "Pacific Standard Time",                      
            "Location": {
                "DisplayName": "Alex's Office"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SeriesMaster",
            "SeriesMasterId": null,
            "Attendees": [
                {
                    "EmailAddress": {
                        "Address": "roby@a830edad9050849NDA1.onmicrosoft.com",
                        "Name": "Rob Young"
                    },
                    "Status": {
                        "Response": "None",
                        "Time": "0001-01-01T00:00:00Z"
                    },
                    "Type": "Required"
                }
            ],
            "Recurrence": {
                "Pattern": {
                    "Type": "RelativeMonthly",
                    "Interval": 1,
                    "Month": 0,
                    "Index": "Third",
                    "FirstDayOfWeek": "Sunday",
                    "DayOfMonth": 0,
                    "DaysOfWeek": [
                        "Wednesday"
                    ]
                },
                "Range": {
                    "Type": "NoEnd",
                    "StartDate": "2014-10-15T00:00:00-07:00",
                    "EndDate": "0001-01-01T00:00:00Z",
                    "NumberOfOccurrences": 0
                }
            },
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG90AAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46g==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG90AAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x46g==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:48:13.6271741Z",
            "DateTimeLastModified": "2014-10-19T08:48:13.6427985Z",
            "Subject": "Thanksgiving Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2015-11-26T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2015-11-27T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9zAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9zAAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x46Q==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:46:18.8700566Z",
            "DateTimeLastModified": "2014-10-19T08:46:18.8856803Z",
            "Subject": "Thanksgiving Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-11-27T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2014-11-28T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x46A==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x46A==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:43:37.2138006Z",
            "DateTimeLastModified": "2014-10-19T08:43:37.2450436Z",
            "Subject": "New Year's Day Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2015-01-01T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",            
            "End": "2015-01-02T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9xAAA=')",
            "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x45w==\"",
            "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9xAAA=",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x45w==",
            "Categories": [],
            "DateTimeCreated": "2014-10-19T08:33:45.1538198Z",
            "DateTimeLastModified": "2014-10-19T08:33:45.200696Z",
            "Subject": "Christmas Holiday",
            "BodyPreview": "",
            "Body": {
                "ContentType": "HTML",
                "Content": ""
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2014-12-25T00:00:00Z",
            "StartTimeZone": "Pacific Standard Time",            
            "End": "2014-12-26T00:00:00Z",
            "EndTimeZone": "Pacific Standard Time",            
            "Location": {
                "DisplayName": ""
            },
            "ShowAs": "Free",
            "IsAllDay": true,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Alex D"
                }
            }
        }
    ]
}
}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****


<a name="GetEventInstances"></a>
###<a name="get-event-instances-rest"></a>获取事件实例 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

指定的时间范围内，可以获得事件的实例 （实例）。 **SeriesMaster**类型的事件时，这将返回的次数和异常的事件在指定的时间范围内。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应事件的默认时区。|
|_URL 参数_|
|event_id|string|事件 id。|
|start_datetime|方法|UTC 日期和事件开始的时间。|
|end_datetime|方法|UTC 日期和事件结束的时间。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

 **响应类型**

请求的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)集合。

**请注意**默认情况下，在响应每个事件包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。  
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

例如，10 月当月获得特定事件的实例，仅包含**主题**、 **Start**和**End**属性的每个实例︰ 

<!--don't use httprequest for this because it renders as lowercase, which breaks the call-->
```
GET https://outlook.office.com/api/beta/me/events/AAMkAGE0MGM1Y2M5LWEAAA=/instances?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject,Start,End
```



[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应中的事件默认时区。|
|_URL 参数_|
|event_id|string|事件 id。|
|start_datetime|方法|UTC 日期和事件开始的时间。|
|end_datetime|方法|UTC 日期和事件结束的时间。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

 **响应类型**

请求的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)集合。

**请注意**默认情况下，在响应每个事件包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。  
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

例如，10 月当月获得特定事件的实例，仅包含**主题**、 **Start**和**End**属性的每个实例︰ 

<!--don't use httprequest for this because it renders as lowercase, which breaks the call-->
```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGE0MGM1Y2M5LWEAAA=/instances?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject,Start,End
```



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|start_datetime|方法|UTC 日期和事件开始的时间。|
|end_datetime|方法|UTC 日期和事件结束的时间。|


 **响应类型**

请求的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)集合。

**请注意**默认情况下，在响应每个事件包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。  
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

例如，10 月当月获得特定事件的实例，仅包含**主题**、 **Start**和**End**属性的每个实例︰ 

<!--don't use httprequest for this because it renders as lowercase, which breaks the call-->
```
GET https://outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEAAA=/instances?startDateTime=2014-10-01T01:00:00Z&endDateTime=2014-10-31T23:00:00Z&$select=Subject,Start,End
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****


<a name="GetEvent"> </a>
###<a name="get-an-event-rest"></a>获取事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

获取事件的 id。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应事件的默认时区。|
|_URL 参数_|
|event_id|string|事件 id。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

**示例请求**

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2TG93AAA=
```

**响应示例**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
        "Categories": [],
        "CreatedDateTime": "2014-10-19T23:13:47.3959685Z",
        "LastModifiedDateTime": "2014-10-19T23:13:47.6772234Z",
        "Subject": "Weekly Meeting on Contoso Project",
        "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        },        
        "Location": {
            "DisplayName": "Alex's Office",
            "Address": null,
            "Coordinates": null,
            "LocationEmailAddress": "",
            "LocationUri": ""
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SeriesMaster",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            },
            {
                "EmailAddress": {
                    "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Pavel Bansky"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": {
            "Pattern": {
                "Type": "Weekly",
                "Interval": 1,
                "Month": 0,
                "Index": "First",
                "FirstDayOfWeek": "Sunday",
                "DayOfMonth": 0,
                "DaysOfWeek": [
                    "Monday"
                ]
            },
            "RecurrenceTimeZone": "Pacific Standard Time",
            "Range": {
                "Type": "NoEnd",
                "StartDate": "2014-10-13",
                "EndDate": "2014-11-13",
                "NumberOfOccurrences": 0
            }
        },
        "OriginalEndTimeZone": "Pacific Standard Time",
        "OriginalStartTimeZone": "Pacific Standard Time",
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        },
        "OnlineMeetingUrl": null
    }
```


**响应类型**

请求的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

**请注意**默认情况下，该响应包括该事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定返回仅**者**、**组织者**、**开始**和**结束**事件的属性。 


**示例请求**

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2TG93AAA=?$select=Subject,Organizer,Start,End
```

**响应示例**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "Subject": "Weekly Meeting on Contoso Project",
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        }, 
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应中的事件默认时区。|
|_URL 参数_|
|event_id|string|事件 id。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2TG93AAA=
```

**响应示例**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
        "Categories": [],
        "CreatedDateTime": "2014-10-19T23:13:47.3959685Z",
        "LastModifiedDateTime": "2014-10-19T23:13:47.6772234Z",
        "Subject": "Weekly Meeting on Contoso Project",
        "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        },        
        "Location": {
            "DisplayName": "Alex's Office",
            "Address": null
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SeriesMaster",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            },
            {
                "EmailAddress": {
                    "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Pavel Bansky"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": {
            "Pattern": {
                "Type": "Weekly",
                "Interval": 1,
                "Month": 0,
                "Index": "First",
                "FirstDayOfWeek": "Sunday",
                "DayOfMonth": 0,
                "DaysOfWeek": [
                    "Monday"
                ]
            },
            "RecurrenceTimeZone": "Pacific Standard Time",
            "Range": {
                "Type": "NoEnd",
                "StartDate": "2014-10-13",
                "EndDate": "2014-11-13",
                "NumberOfOccurrences": 0
            }
        },
        "OriginalEndTimeZone": "Pacific Standard Time",
        "OriginalStartTimeZone": "Pacific Standard Time",
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
```


**响应类型**

请求的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

**请注意**默认情况下，该响应包括该事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定返回仅**者**、**组织者**、**开始**和**结束**事件的属性。 

**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2TG93AAA=?$select=Subject,Organizer,Start,End
```

**响应示例**

```
    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2TG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2TG93AAA=",
        "Subject": "Weekly Meeting on Contoso Project",
        "Start": {
            "DateTime": "2014-10-13T21:00:00",
            "TimeZone": "Pacific Standard Time"
        },
        "End": {
            "DateTime": "2014-10-13T22:00:00",
            "TimeZone": ""Pacific Standard Time"
        }, 
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|

```REST-i
[!INCLUDE [calendar_api_get_event_by_id](./_data/calendar_api_get_event_by_id.json)]
```


**响应类型**

请求的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

**请注意**默认情况下，该响应包括该事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定返回仅**者**、**组织者**、**开始**和**结束**事件的属性。 

```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}?$select=Subject,Organizer,Start,End",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=?$select=Subject,Organizer,Start,End",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x48w==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG93AAA=",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x48w==",
        "Categories": [],
        "DateTimeCreated": "2014-10-19T23:13:47.3959685Z",
        "DateTimeLastModified": "2014-10-19T23:13:47.6772234Z",
        "Subject": "Weekly Meeting on Contoso Project",
        "BodyPreview": "Setting up some time to review the budget and planning on the Contoso Project",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nSetting up some time to review the budget and planning on the Contoso Project\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": "2014-10-13T21:00:00Z",
        "StartTimeZone": "Pacific Standard Time",        
        "End": "2014-10-13T22:00:00Z",
        "EndTimeZone": "Pacific Standard Time",        
        "Location": {
            "DisplayName": "Alex's Office"
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SeriesMaster",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            },
            {
                "EmailAddress": {
                    "Address": "pavelb@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Pavel Bansky"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": {
            "Pattern": {
                "Type": "Weekly",
                "Interval": 1,
                "Month": 0,
                "Index": "First",
                "FirstDayOfWeek": "Sunday",
                "DayOfMonth": 0,
                "DaysOfWeek": [
                    "Monday"
                ]
            },
            "Range": {
                "Type": "NoEnd",
                "StartDate": "2014-10-13T00:00:00-07:00",
                "EndDate": "0001-01-01T00:00:00Z",
                "NumberOfOccurrences": 0
            }
        },
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "Alex D"
            }
        }
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="GetEventsClient"></a>
### <a name="get-events-from-the-users-calendar-client"></a>获取事件的用户的日历 （客户端）

获取用户的默认日历事件。 若要获取不同日历中的事件，调用日历的**事件**属性。

示例︰`outlookClient.Me.Calendars[calendarId].Events.ExecuteAsync()`


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


若要获取某个特定事件，可以指定事件 ID 的**事件**集合的索引或使用**GetById**方法。

**请注意**事件集合支持**选择**、**排序**，并**执行**查询表达式。

本示例将调用方法[创建 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar" -->

```cs-i
var outlookClient = await CreateOutlookClientAsync("Calendar");
var events = await outlookClient.Me.Events
  .Take(10)
  .ExecuteAsync();
 
foreach(var calendarEvent in events.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Event '{0}'.", calendarEvent.Subject);
}
 
```

```javascript-i
outlookClient.me.events.getEvents().fetch().then(function (result) {
    result.currentPage.forEach(function (event) {
console.log('Event "' + event.subject + '"')
    });
}, function(error) {
    console.log(error);
});
```

<!-- ENDSECTION -->


此调用返回事件序列，不定期 （如每周一次的小组会议） 事件的个体扩展实例。

目前在客户端库不支持查询事件实例。 REST API，可用于查询该 [日历](..\api\calendar-rest-operations.md#CalendarResource)资源的**日历视图**属性或[事件](..\api\calendar-rest-operations.md#EventResource)资源的**实例**属性︰


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/instances?startDateTime={start_datetime}&endDateTime={end_datetime}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->
 
<!--Update c# example to get instance-->
<!--Update js example and remove note when this works in js-->

****

<a name="SyncCalendarView"> </a>
##<a name="sync-events"></a>同步事件  

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

同步和获取新的更新，或删除用户的主日历中指定的时间范围的事件 (`../me/calendarview`) 或从不同的日历。 此类中的时间范围的事件集也称为是日历视图。 返回的事件可能包括事件和异常的定期系列，以及一个实例。 

同步日历视图通常需要两个或多个同步请求，其中每个是一个 GET 调用一轮。 同步日历视图，使用 GET 方法类似的方法[获取日历视图](#GetCalendarView)，只不过包含某些请求标头，并_deltaToken_或_skipToken_在适当的时候。  

**请求标头**

- 必须指定"更愿意︰ odata.track 更改"标题在所有同步请求除包括`skipToken`返回前一个同步请求。 在第一个响应中，寻找_首选项应用︰ odata.track 更改_标头，以确认该资源支持同步之前。 (有关详细信息`skipToken`在下面的[示例的第二个响应数据](#SyncCalendarViewSampleSecondResponse)。)
- 您可以指定"更愿意︰ odata.maxpagesize={x}"标头指示的最大同步请求返回的事件数。

下面是典型倒圆角的同步事件在日历视图中︰

1. 使带有强制性的初始 GET 请求_更愿意︰ odata.track 更改_头。 初始同步请求响应始终返回_deltaToken_。 （第二个和后续 GET 请求不同于第一个 GET 请求包括_deltaToken_或_skipToken_在以前的响应中收到的。）

2. 如果第一个响应返回_首选项应用︰ odata.track 更改_标头，则可以进行同步。

  - 进行第二个 GET 请求。 指定_更愿意︰ odata.track 更改_标头和_deltaToken_将返回从第一个 GET 操作以确定是否有任何其他事件。 第二个请求将返回附加的事件和任何一个_skipToken_ ，如果有更多的事件或_deltaToken_如果已同步的最后一个事件，在这种情况下，您可以停止。

  - 继续通过发送一个 GET 调用并将包括从以前的调用中返回_skipToken_同步。 停止时获得最终的响应，其中包含_@odata.deltaLink_ _deltaToken_同样的标头，它表示同步已完成。

看一下在一轮同步初始和后续调用的语法。

<!-- ==================================== Begin beta content ======================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

**若要在默认日历同步**

初始请求︰ 

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```

第二个请求或下一轮的第一次请求︰

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```

第三个或后续的请求，在同一圈  

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**若要同步特定日历中**

初始请求︰

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


第二个请求或下一轮的第一次请求︰

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```


在同一轮中的第三个或后续请求︰

```no-highlight
GET https://outlook.office.com/api/beta/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**参数**

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应事件的默认时区。|
|_URL 参数_|
|user_context|string|用户上下文。 '我' 的值用于指示当前用户的上下文。 您还可以使用用户 / {upn} 格式**upn**所在的用户主体名称这通常是用户的电子邮件地址。|
|calendar_id|string|如果您收到来自特定日历的日历视图的日历 ID。|
|start_datetime|方法|日期和事件开始的时间。|
|end_datetime|方法|日期和事件结束的时间。|
|delta_token|string|`deltaToken`返回的值作为字符串@odata.deltaLink在前一个同步响应。|
|skip_token|string|`skipToken`返回的值作为字符串@odata.nextLink在前一个同步响应。 |

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。如果_更愿意︰ outlook.timezone_不指定标头，开始和结束时间以返回 UTC。

**请注意** 

- 当指定"更愿意︰ odata.track 更改"中的初始请求，如果响应支持同步，响应将包含"首选项应用︰ odata.track 更改"标头中。
- 如果您试图同步的资源，不受支持，或者如果这不是初始的同步请求，您不会看到在响应中的"首选项应用"标题。
- 您可以通过更改开始日期时间和 enddatetime 查询参数修改变更的时间窗口。  
- 在响应每个事件包括它的所有属性。 
- 对于定期系列，同步响应包括定期主的整个事件和异常事件。 
- 定期系列的实例缩写，并且包含只有**Start**和**End**属性。 您可以捕获从定期主事件事件事件信息的其余部分。 参考信息，请参阅[事件资源](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。
- 您不能使用 $filter、 $count、 $select、 $skip、 $top 和 $search 查询参数。 

**响应类型**

扩展的[的事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)和缩写的事件在指定的时间范围内。

**示例**

下面的示例演示了初始和第二个同步请求进行同步用户的默认日历。 每个请求指定返回一次只能有一个完整的事件︰
- 最初的响应返回一个事件中， `deltaLink` ， `deltaToken`。 
- 第二个请求使用的`deltatoken`。 第二个响应返回一个事件中， `nextLink` ， `skipToken`。 

要完成同步，使用`skipToken`归来前一个同步请求，直到同步响应返回`deltaLink`， `deltaToken`，在这种情况下此轮同步已完成。 保存`deltaToken`的同步的下一轮。 

有关详细信息，请参阅[Outlook 日历视图中的同步事件](..\howto\sync-calendar-view.md)。
 
<a name="SyncCalendarViewSampleInitialRequest"></a>

**初始请求的示例**

```
    GET https://outlook.office.com/api/beta/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z HTTP/1.1
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
    Prefer: outlook.timezone="Pacific Standard Time"
```

**初始响应的示例数据**

```
Preference-Applied: odata.track-changes

    {
        "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarView",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/beta/Users('user0@contoso.com')/Events('asdas==')",
                "@odata.etag": "W/\"L8Z+4Y4u7k+97uRKg==\"",
                "Id": "AQMkANJAAAAA==",
                "ChangeKey": "L8Z+AAAAARKg==",
                "Categories": [
                ],
                "DateTimeCreated": "2015-04-10T17:54:49.2725912Z",
                "DateTimeLastModified": "2015-04-10T17:54:49.3038538Z",
                "Subject": "Discuss the Calendar REST API",
                "BodyPreview": "I think it will meet our requirements!",
                "Body": {
                    "ContentType": "HTML",
                    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
                },
                "Importance": "Normal",
                "HasAttachments": false,
                "Start": {
                    "DateTime": "2015-04-05T18:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "End": {
                    "DateTime": "2015-04-05T19:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "ReminderMinutesBeforeStart": "15",
                "IsReminderOn": "true",
                "Location": {
                    "DisplayName": "",
                    "Address": null,
                    "Coordinates": null,
                    "LocationEmailAddress": "",
                    "LocationUri": ""
                },
                "ResponseStatus": {
                    "Response": "Organizer",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "ShowAs": "Busy",
                "IsAllDay": false,
                "IsCancelled": false,
                "IsOrganizer": true,
                "ResponseRequested": true,
                "Type": "SingleInstance",
                "SeriesMasterId": null,
                "Attendees": [
                ],
                "Recurrence": null,
                "OriginalEndTimeZone": "Pacific Standard Time",
                "OriginalStartTimeZone": "Pacific Standard Time",
                "Organizer": {
                    "EmailAddress": {
                        "Address": "user0@contoso.com",
                        "Name": "user0"
                    }
                },
                "iCalUId": "040000008200E9888E07599CCFA23",
                "WebLink": "https://outlook.office.com/owa/?ItemID=AAAINJAAAAA%3D%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
                "OnlineMeetingUrl": null
            }
        ],
        "@odata.deltaLink": "https://outlook.office.com/api/beta/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-04-10T00%3a00%3a00Z&%24deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c"
    }
```

**示例的第二个请求**

```
    GET https://outlook.office.com/api/beta/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z&$deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
    Prefer: outlook.timezone="Pacific Standard Time"
```

<a name="SyncCalendarViewSampleSecondResponse"></a>

**示例的第二个响应数据**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarView/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('user0@contoso.com')/Events('AAMkAD0jAAA=')",
            "@odata.etag": "W/\"P2fd7QAAAAAVFA==\"",
            "Id": "AAMkADNkNmVlOTITVAAAAAA0jAAA=",
            "ChangeKey": "P2fdmIU1QAAAAAVFA==",
            "Categories": [
            ],
            "DateTimeCreated": "2015-04-15T18:59:11.0226221Z",
            "DateTimeLastModified": "2015-04-15T18:59:11.0694979Z",
            "Subject": "1 hour",
            "BodyPreview": "\u200b",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html><body>content</body></html>"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": {
                "DateTime": "2015-04-16T18:00:00",
                "TimeZone": "Pacific Standard Time"
            }
            "End": {
                "DateTime": "2015-04-16T19:00:00",
                "TimeZone": Pacific Standard Time"
            }
            "ReminderMinutesBeforeStart": "15",
            "IsReminderOn": "true",
            "Location": {
                "DisplayName": "",
                "Address": {
                    "Street": "",
                    "City": "",
                    "State": "",
                    "CountryOrRegion": "",
                    "PostalCode": ""
                },
                "Coordinates": {
                    "Accuracy": "NaN",
                    "Altitude": "NaN",
                    "AltitudeAccuracy": "NaN",
                    "Latitude": "NaN",
                    "Longitude": "NaN"
                },
                "LocationEmailAddress": "",
                "LocationUri": ""
            },
            "ResponseStatus": {
                "Response": "Organizer",
                "Time": "0001-01-01T00:00:00Z"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [
            ],
            "Recurrence": null,
            "OriginalEndTimeZone": "Pacific Standard Time",
            "OriginalStartTimeZone": "Pacific Standard Time",
            "Organizer": {
                "EmailAddress": {
                    "Address": "user0@contoso.com",
                    "Name": "user0"
                }
            },
            "iCalUId": "040000008200E09BB89A316862",
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADNkNmVlOAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
            "OnlineMeetingUrl": null
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/beta/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-08-10T00%3a00%3a00Z&%24skipToken=530c9d02ae1a4d96804538bd4d381546"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


**若要在默认日历同步**

初始请求︰ 

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```

第二个请求或下一轮的第一次请求︰

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```

第三个或后续的请求，在同一圈  

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**若要同步特定日历中**

初始请求︰

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


第二个请求或下一轮的第一次请求︰

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```


在同一轮中的第三个或后续请求︰

```no-highlight
GET https://outlook.office.com/api/v2.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**参数**

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|user_context|string|用户上下文。 '我' 的值用于指示当前用户的上下文。 您还可以使用用户 / {upn} 格式**upn**所在的用户主体名称这通常是用户的电子邮件地址。|
|calendar_id|string|如果您收到来自特定日历的日历视图的日历 ID。|
|start_datetime|方法|日期和事件开始的时间。|
|end_datetime|方法|日期和事件结束的时间。|
|delta_token|string|`deltaToken`返回的值作为字符串@odata.deltaLink在前一个同步响应。|
|skip_token|string|`skipToken`返回的值作为字符串@odata.nextLink在前一个同步响应。 |

**请注意** 

- 当指定"更愿意︰ odata.track 更改"中的初始请求，如果响应支持同步，响应将包含"首选项应用︰ odata.track 更改"标头中。
- 如果您试图同步的资源，不受支持，或者如果这不是初始的同步请求，您不会看到在响应中的"首选项应用"标题。
- 您可以通过更改开始日期时间和 enddatetime 查询参数修改变更的时间窗口。  
- 在响应每个事件包括它的所有属性。 
- 对于定期系列，同步响应包括定期主的整个事件和异常事件。 
- 定期系列的实例缩写，并且包含只有**Start**和**End**属性。 您可以捕获从定期主事件事件事件信息的其余部分。 参考信息，请参阅[事件资源](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。
- 您不能使用 $filter、 $count、 $select、 $skip、 $top 和 $search 查询参数。 

**响应类型**

扩展的[的事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)和缩写的事件在指定的时间范围内。

**示例**

下面的示例演示了初始和第二个同步请求进行同步用户的默认日历。 每个请求指定返回一次只能有一个完整的事件︰
- 最初的响应返回一个事件中， `deltaLink` ， `deltaToken`。 
- 第二个请求使用的`deltatoken`。 第二个响应返回一个事件中， `nextLink` ， `skipToken`。 

要完成同步，使用`skipToken`归来前一个同步请求，直到同步响应返回`deltaLink`， `deltaToken`，在这种情况下此轮同步已完成。 保存`deltaToken`的同步的下一轮。 

有关详细信息，请参阅[Outlook 日历视图中的同步事件](..\howto\sync-calendar-view.md)。
 
<a name="SyncCalendarViewSampleInitialRequest"></a>

**初始请求的示例**

```
    GET https://outlook.office.com/api/v2.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z HTTP/1.1
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

**初始响应的示例数据**

```
Preference-Applied: odata.track-changes

    {
        "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarView",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v2.0/Users('user0@contoso.com')/Events('asdas==')",
                "@odata.etag": "W/\"L8Z+4Y4u7k+97uRKg==\"",
                "Id": "AQMkANJAAAAA==",
                "ChangeKey": "L8Z+AAAAARKg==",
                "Categories": [
                ],
                "DateTimeCreated": "2015-04-10T17:54:49.2725912Z",
                "DateTimeLastModified": "2015-04-10T17:54:49.3038538Z",
                "Subject": "Discuss the Calendar REST API",
                "BodyPreview": "I think it will meet our requirements!",
                "Body": {
                    "ContentType": "HTML",
                    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
                },
                "Importance": "Normal",
                "HasAttachments": false,
                "Start": {
                    "DateTime": "2015-04-05T18:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "End": {
                    "DateTime": "2015-04-05T19:00:00",
                    "TimeZone": "Pacific Standard Time"
                }
                "ReminderMinutesBeforeStart": "15",
                "IsReminderOn": "true",
                "Location": {
                    "DisplayName": "",
                    "Address": null
                },
                "ResponseStatus": {
                    "Response": "Organizer",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "ShowAs": "Busy",
                "IsAllDay": false,
                "IsCancelled": false,
                "IsOrganizer": true,
                "ResponseRequested": true,
                "Type": "SingleInstance",
                "SeriesMasterId": null,
                "Attendees": [
                ],
                "Recurrence": null,
                "OriginalEndTimeZone": "Pacific Standard Time",
                "OriginalStartTimeZone": "Pacific Standard Time",
                "Organizer": {
                    "EmailAddress": {
                        "Address": "user0@contoso.com",
                        "Name": "user0"
                    }
                },
                "iCalUId": "040000008200E9888E07599CCFA23",
                "WebLink": "https://outlook.office.com/owa/?ItemID=AAAINJAAAAA%3D%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
            }
        ],
        "@odata.deltaLink": "https://outlook.office.com/api/v2.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-04-10T00%3a00%3a00Z&%24deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c"
    }
```

**示例的第二个请求**

```
    GET https://outlook.office.com/api/v2.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z&$deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

<a name="SyncCalendarViewSampleSecondResponse"></a>

**示例的第二个响应数据**

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarView/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('user0@contoso.com')/Events('AAMkAD0jAAA=')",
            "@odata.etag": "W/\"P2fd7QAAAAAVFA==\"",
            "Id": "AAMkADNkNmVlOTITVAAAAAA0jAAA=",
            "ChangeKey": "P2fdmIU1QAAAAAVFA==",
            "Categories": [
            ],
            "DateTimeCreated": "2015-04-15T18:59:11.0226221Z",
            "DateTimeLastModified": "2015-04-15T18:59:11.0694979Z",
            "Subject": "1 hour",
            "BodyPreview": "\u200b",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html><body>content</body></html>"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": {
                "DateTime": "2015-04-16T18:00:00",
                "TimeZone": "Pacific Standard Time"
            }
            "End": {
                "DateTime": "2015-04-16T19:00:00",
                "TimeZone": Pacific Standard Time"
            }
            "ReminderMinutesBeforeStart": "15",
            "IsReminderOn": "true",
            "Location": {
                "DisplayName": "",
                "Address": {
                    "Street": "",
                    "City": "",
                    "State": "",
                    "CountryOrRegion": "",
                    "PostalCode": ""
                }
             },
            "ResponseStatus": {
                "Response": "Organizer",
                "Time": "0001-01-01T00:00:00Z"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [
            ],
            "Recurrence": null,
            "OriginalEndTimeZone": "Pacific Standard Time",
            "OriginalStartTimeZone": "Pacific Standard Time",
            "Organizer": {
                "EmailAddress": {
                    "Address": "user0@contoso.com",
                    "Name": "user0"
                }
            },
            "iCalUId": "040000008200E09BB89A316862",
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADNkNmVlOAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/v2.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-08-10T00%3a00%3a00Z&%24skipToken=530c9d02ae1a4d96804538bd4d381546"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


**若要在默认日历同步**

初始请求︰ 

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```

第二个请求或下一轮的第一次请求︰

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```

第三个或后续的请求，在同一圈  

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**若要同步特定日历中**

初始请求︰

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}
```


第二个请求或下一轮的第一次请求︰

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$deltatoken={delta_token}
```


在同一轮中的第三个或后续请求︰

```no-highlight
GET https://outlook.office.com/api/v1.0/{user_context}/calendars('{calendar_id}')/calendarview?startDateTime={start_datetime}&endDateTime={end_datetime}&$skiptoken={skip_token}
```

**参数**

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|user_context|string|用户上下文。 '我' 的值用于指示当前用户的上下文。 您还可以使用用户 / {upn} 格式**upn**所在的用户主体名称这通常是用户的电子邮件地址。|
|calendar_id|string|如果您收到来自特定日历的日历视图的日历 ID。|
|start_datetime|方法|日期和事件开始的时间。|
|end_datetime|方法|日期和事件结束的时间。|
|delta_token|string|`deltaToken`返回的值作为字符串@odata.deltaLink在前一个同步响应。|
|skip_token|string|`skipToken`返回的值作为字符串@odata.nextLink在前一个同步响应。 |

**请注意** 

- 当指定"更愿意︰ odata.track 更改"中的初始请求，如果响应支持同步，响应将包含"首选项应用︰ odata.track 更改"标头中。
- 如果您试图同步的资源，不受支持，或者如果这不是初始的同步请求，您不会看到在响应中的"首选项应用"标题。
- 您可以通过更改开始日期时间和 enddatetime 查询参数修改变更的时间窗口。  
- 在响应每个事件包括它的所有属性。 
- 对于定期系列，同步响应包括定期主的整个事件和异常事件。 
- 定期系列的实例缩写，并且包含只有**Start**和**End**属性。 您可以捕获从定期主事件事件事件信息的其余部分。 参考信息，请参阅[事件资源](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。
- 您不能使用 $filter、 $count、 $select、 $skip、 $top 和 $search 查询参数。 

**响应类型**

扩展的[的事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)和缩写的事件在指定的时间范围内。

**示例**

下面的示例演示了初始和第二个同步请求进行同步用户的默认日历。 每个请求指定返回一次只能有一个完整的事件︰
- 最初的响应返回一个事件中， `deltaLink` ， `deltaToken`。 
- 第二个请求使用的`deltatoken`。 第二个响应返回一个事件中， `nextLink` ， `skipToken`。 

要完成同步，使用`skipToken`归来前一个同步请求，直到同步响应返回`deltaLink`， `deltaToken`，在这种情况下此轮同步已完成。 保存`deltaToken`的同步的下一轮。 

有关详细信息，请参阅[Outlook 日历视图中的同步事件](..\howto\sync-calendar-view.md)。
 
<a name="SyncCalendarViewSampleInitialRequest"></a>

**初始请求的示例**

```
    GET https://outlook.office.com/api/v1.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z HTTP/1.1
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

**初始响应的示例数据**

```
Preference-Applied: odata.track-changes

    {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarView",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('user0@contoso.com')/Events('asdas==')",
                "@odata.etag": "W/\"L8Z+4Y4u7k+97uRKg==\"",
                "Id": "AQMkANJAAAAA==",
                "ChangeKey": "L8Z+AAAAARKg==",
                "Categories": [
                ],
                "DateTimeCreated": "2015-04-10T17:54:49.2725912Z",
                "DateTimeLastModified": "2015-04-10T17:54:49.3038538Z",
                "Subject": "Discuss the Calendar REST API",
                "BodyPreview": "I think it will meet our requirements!",
                "Body": {
                    "ContentType": "HTML",
                    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
                },
                "Importance": "Normal",
                "HasAttachments": false,
                "Start": "2015-04-05T18:00:00Z",
                "StartTimeZone": "Pacific Standard Time",
                "End": "2015-04-05T19:00:00Z",
                "EndTimeZone": "Pacific Standard Time",
                "Reminder": 15,
                "Location": {
                    "DisplayName": "",
                    "Address": null
                },
                "ResponseStatus": {
                    "Response": "Organizer",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "ShowAs": "Busy",
                "IsAllDay": false,
                "IsCancelled": false,
                "IsOrganizer": true,
                "ResponseRequested": true,
                "Type": "SingleInstance",
                "SeriesMasterId": null,
                "Attendees": [
                ],
                "Recurrence": null,
                "Organizer": {
                    "EmailAddress": {
                        "Address": "user0@contoso.com",
                        "Name": "user0"
                    }
                },
                "iCalUId": "040000008200E9888E07599CCFA23",
                "WebLink": "https://outlook.office.com/owa/?ItemID=AAAINJAAAAA%3D%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
            }
        ],
        "@odata.deltaLink": "https://outlook.office.com/api/v1.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-04-10T00%3a00%3a00Z&%24deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c"
    }
```

**示例的第二个请求**

```
    GET https://outlook.office.com/api/v1.0/me/calendarview?startdatetime=2015-01-01T00:00:00Z&enddatetime=2015-04-10T00:00:00Z&$deltatoken=v2%2cH4roCAAA%3d%2c1.0%2cFalse%2cA00%2c
    Authorization: Bearer <token>
    Prefer: odata.track-changes
    Prefer: odata.maxpagesize=1
```

<a name="SyncCalendarViewSampleSecondResponse"></a>

**示例的第二个响应数据**

```
{
    "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarView/$delta",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v1.0/Users('user0@contoso.com')/Events('AAMkAD0jAAA=')",
            "@odata.etag": "W/\"P2fd7QAAAAAVFA==\"",
            "Id": "AAMkADNkNmVlOTITVAAAAAA0jAAA=",
            "ChangeKey": "P2fdmIU1QAAAAAVFA==",
            "Categories": [
            ],
            "DateTimeCreated": "2015-04-15T18:59:11.0226221Z",
            "DateTimeLastModified": "2015-04-15T18:59:11.0694979Z",
            "Subject": "1 hour",
            "BodyPreview": "\u200b",
            "Body": {
                "ContentType": "HTML",
                "Content": "<html><body>content</body></html>"
            },
            "Importance": "Normal",
            "HasAttachments": false,
            "Start": "2015-04-16T18:00:00Z",
            "StartTimeZone": "Pacific Standard Time",
            "End": "2015-04-16T19:00:00Z",
            "EndTimeZone": "Pacific Standard Time",
            "Reminder": 15,
            "Location": {
                "DisplayName": "",
                "Address": {
                    "Street": "",
                    "City": "",
                    "State": "",
                    "CountryOrRegion": "",
                    "PostalCode": ""
                }
            },
            "ResponseStatus": {
                "Response": "Organizer",
                "Time": "0001-01-01T00:00:00Z"
            },
            "ShowAs": "Busy",
            "IsAllDay": false,
            "IsCancelled": false,
            "IsOrganizer": true,
            "ResponseRequested": true,
            "Type": "SingleInstance",
            "SeriesMasterId": null,
            "Attendees": [
            ],
            "Recurrence": null,
            "Organizer": {
                "EmailAddress": {
                    "Address": "user0@contoso.com",
                    "Name": "user0"
                }
            },
            "iCalUId": "040000008200E09BB89A316862",
            "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADNkNmVlOAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory"
        }
    ],
    "@odata.nextLink": "https://outlook.office.com/api/v1.0/me/calendarview/?startdatetime=2015-01-01T00%3a00%3a00Z&enddatetime=2015-08-10T00%3a00%3a00Z&%24skipToken=530c9d02ae1a4d96804538bd4d381546"
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="FindMeetingTimesPreview"></a>
## <a name="find-meeting-times-preview"></a>查找会议时间 （预览）

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

查找会议时间的建议基于组织者和与会者的可用性，以及时间或地点指定为参数的约束。 

此操作目前在预览和仅 beta 版本中可用。 它适用于 Office 365 邮箱 （在 Azure AD) 而不适用于 Microsoft 帐户。

```no-highlight
POST https://outlook.office.com/api/{version}/me/findmeetingtimes
```

下面列出了所有受支持的参数。 这取决于您的方案，在请求正文中**FindMeetingTimes**操作中指定必需的参数。 

|**参数**|**类型**|**说明**|**必填？**|
|:-----|:-----|:-----|:-----|
| 与会者 | 集合 ([AttendeeBase](complex-types-for-mail-contacts-calendar.md#AttendeeBase)) | 与会者或资源的会议。 空集合会导致**FindMeetingTimes**查找可用时间段只有组织者。 | 可选 |
| LocationConstraint | [LocationConstraint](complex-types-for-mail-contacts-calendar.md#LocationConstraint) | 关于会议地点的组织者的要求，如会议地点有关的建议是否必需的或有特定的位置，只在其中可以召开会议。 | 可选 |
| TimeConstraint | [TimeConstraint](complex-types-for-mail-contacts-calendar.md#TimeConstraint) | 应会议开始和结束的时间范围。 | 可选 |
| MeetingDuration | Edm.Duration |以 ISO 8601 格式表示的持续时间，例如，会议的时间长度`PT1H`表示 1 小时。 如果不指定任何会议持续时间，则**FindMeetingTimes**将使用默认值为 30 分钟。 | 可选 |
| MaxCandidates | Edm.Int32 |会议建议在响应中返回的最大数目。 | 可选 |
| IsOrganizerOptional | Edm.Boolean | 指定`true`如果组织者不一定要参加。 默认值是`false`。 | 可选 |
| ReturnSuggestionHints | Edm.Boolean | 指定`true`在**SuggestionHint**属性中返回每个会议的建议的原因。 默认值是`false`不能返回该属性。 | 可选 |

根据指定的参数，则**FindMeetingTimes**检查中的主要组织者和与会者的日历的忙/闲状态。 该操作计算最佳会议时间，并返回任何会议的建议。

**响应类型**

[MeetingTimeCandidatesResult](complex-types-for-mail-contacts-calendar.md#MeetingTimeCandidatesResult)包括会议的建议，每一个集合键入[MeetingTimeCandidate](#MeetingTimeCandidate)和**EmptySuggestionsHint**属性。

<!-- Location suggestions are based on the organizer's booking history during the past 7 days and next 2 days. If the organizer doesn't have sufficient booking history 
in the corresponding time window, the request returns HTTP 200 OK, but does not include any meeting suggestions in the response. -->

每个建议被指[MeetingTimeCandidate](complex-types-for-mail-contacts-calendar.md#MeetingTimeCandidate)，[平均置信度或更高，参加会议的 50%的机会](complex-types-for-mail-contacts-calendar.md#ConfidenceScoreDetails)让与会者。 默认情况下，每个会议时间的建议将以返回 UTC。 应用`Prefer: outlook.timezone`请求标头有会议，例如在不同的时区，所返回的时间建议︰

```no-highlight
Prefer: outlook.timezone="Pacific Standard Time"
```

如果**FindMeetingTimes**不能返回任何会议的建议，响应将指示中**EmptySuggestionsHint**属性的原因。 根据此值，您可以更好地调整参数并重新调用**FindMeetingTimes** 。


**请注意**

目前， **FindMeetingTimes**的假设如下︰

- 是个人 （而不是资源） 的任何[与会者](..\api\complex-types-for-mail-contacts-calendar.md#Attendee)是必须出席的与会者。 因此，指定`Required`人和`Resource`为相应的**类型**属性，作为**与会者**集合参数的一部分中的资源。
- 仅组织者或与会者的工作时间内发生任何会议的建议。 您可以忽略指定[TimeConstraint](..\api\complex-types-for-mail-contacts-calendar.md#TimeConstraint)的**ActivityDomain**属性。 

以下每个示例调用**FindMeetingTimes**，并因与会者可用性、 时间和地点的限制如下所述︰

- [查找时间和地点，以满足与会者 (REST)](#FindTimeToMeet) 
- [查找时间，以满足在一个已知的位置，并获得每个建议 (REST) 的原因](#FindTimeToMeetAtKnownLocation) 
- [查找时间见面，但没有与会者是可用的 （其它）](#FindTimeToMeetButNobodyAvailable) 
- [查找时间见面，但只有一些与会者可用 (REST)](#FindTimeToMeetSomeAvailable)
- [已登录的用户 (REST) 中查找可用时间段](#FindFreeSlots)


<a name="FindTimeToMeet"></a>

### <a name="find-time-and-location-to-meet-with-specific-attendees-rest"></a>查找时间和地点，以满足特定的与会者 (REST)

发现时间和位置，以满足通过在请求正文中指定以下参数︰
- **与会者**
- **TimeConstraint**
- **MeetingDuration**

**示例请求**

下面的示例提供建议的会议时间和地点，其中考虑了组织者的并请求会议期间与会者的可用性的时间范围和请求的时间长度。

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "TimeConstraint": { 
    "Timeslots": [ 
       { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT1H" 
} 
```



**响应示例**

状态代码︰ 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "10:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "11:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
                {
                    "Attendee": {
                        "Type": "Required",
                        "EmailAddress": {
                            "Address": "fannyd@prosewareltd.onmicrosoft.com"
                        }
                    },
                    "Availability": "Free"
                }
            ],
            "Locations": [
               {
                    "DisplayName": "Tokyo conference room",
                    "LocationEmailAddress": "",
                    "LocationUri": "",
                    "Address": null,
                    "Coordinates": null
                }
            ]
        },
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "11:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "12:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
                {
                    "Attendee": {
                        "Type": "Required",
                        "EmailAddress": {
                            "Address": "fannyd@prosewareltd.onmicrosoft.com"
                        }
                    },
                    "Availability": "Free"
                }
            ],
            "Locations": [
               {
                    "DisplayName": "Paris conference room",
                    "LocationEmailAddress": "",
                    "LocationUri": "",
                    "Address": null,
                    "Coordinates": null
                }
            ]
        }
    ],
    "EmptySuggestionsHint": ""
}
```


****

<a name="FindTimeToMeetAtKnownLocation"></a>

### <a name="find-time-to-meet-at-a-known-location-and-get-a-reason-for-each-suggestion-rest"></a>查找时间，以满足在一个已知的位置，并获得每个建议 (REST) 的原因

查找时间，以满足在一个预先确定的位置，并请求原因的所有建议，通过在请求正文中指定以下参数︰
- **与会者**
- **LocationConstraint**
- **TimeConstraint**
- **MeetingDuration**
- **ReturnSuggestionHints**

通过设置**ReturnSuggestionHints**参数，也获得在**SuggestionHint**属性中，每个建议的说明**FindMeetingTimes**返回的任何建议。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "LocationConstraint": { 
    "IsRequired": "false",  
    "SuggestLocation": "false",  
    "Locations": [ 
      { 
        "DisplayName": "Conf room Hood" 
      } 
    ] 
  },  
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT2H",
  "ReturnSuggestionHints": "true"
} 
```



**响应示例**

状态代码︰ 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "10:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "12:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
                {
                    "Attendee": {
                        "Type": "Required",
                        "EmailAddress": {
                            "Address": "fannyd@prosewareltd.onmicrosoft.com"
                        }
                    },
                    "Availability": "Free"
                }
            ],
            "Locations": [
                {
                    "DisplayName": "Conf room Hood"
                }
            ],
            "SuggestionHint": "Suggested because it is one of the nearest times when all attendees are available."
        }
    ],
    "EmptySuggestionsHint": ""
}
```


****

<a name="FindTimeToMeetButNobodyAvailable"></a>

### <a name="find-time-to-meet-but-no-attendee-is-available-rest"></a>查找时间见面，但没有与会者是可用的 （其它）

查找时间，以满足在一个预先确定的位置，通过在请求正文中指定以下参数︰
- **与会者**
- **LocationConstraint**
- **TimeConstraint**
- **MeetingDuration**

在此示例中，根据指定的参数和与会者可行性**FindMeetingTimes**无法返回任何建议，并改为返回一个原因`AttendeesUnavailable`在**EmptySuggestionsHint**属性中。 

请参阅其他[原因未返回任何会议的建议](..\api\complex-types-for-mail-contacts-calendar.md#ReasonsNoMeetingSuggestion)。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "LocationConstraint": { 
    "IsRequired": "false",  
    "SuggestLocation": "false",  
    "Locations": [ 
      { 
        "DisplayName": "Conf room Hood" 
      } 
    ] 
  },  
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "14:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT2H" 
}
```



**响应示例**

状态代码︰ 200

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
    ],
    "EmptySuggestionsHint": "AttendeesUnavailable"
}
```

****

<a name="FindTimeToMeetSomeAvailable"></a>
### <a name="find-time-to-meet-but-only-some-attendees-are-available-rest"></a>查找时间见面，但只有一些与会者都可用 (REST)

查找时间，以满足在一个预先确定的位置，通过在请求正文中指定以下参数︰
- **与会者**
- **LocationConstraint**
- **TimeConstraint**
- **MeetingDuration**
- **ReturnSuggestionHints**

在此示例中，仅 2 与会者之一是可用的。 **FindMeetingTimes**返回每个会议建议包括︰
- 每个与会者的可用性
- 50%的计算的会议有信心
- **SuggestionHInt**，因为**ReturnSuggestionHints**参数设置。 

查找有关[信心的会议](..\api\complex-types-for-mail-contacts-calendar.md#ConfidenceScoreDetails)的详细信息。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [ 
    { 
      "Type": "Required",  
      "EmailAddress": { 
        "Address": "fannyd@prosewareltd.onmicrosoft.com" 
      } 
    },
   { 
      "Type": "Optional",  
      "EmailAddress": { 
        "Address": "danas@prosewareltd.onmicrosoft.com" 
      } 
    } 
  ],  
  "LocationConstraint": { 
    "IsRequired": "false",  
    "SuggestLocation": "false",  
    "Locations": [ 
      { 
        "DisplayName": "Conf room Hood" 
      } 
    ] 
  },  
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "9:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT1H",
  "ReturnSuggestionHints": "true"
}
```



**响应示例**

状态代码︰ 200
```
{
   "@odata.context":"https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
   "MeetingTimeSlots":[
      {
         "MeetingTimeSlot":{
            "Start":{
               "Date":"2016-05-20",
               "Time":"10:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            },
            "End":{
               "Date":"2016-05-20",
               "Time":"11:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            }
         },
         "Confidence":50.0,
         "OrganizerAvailability":"Free",
         "AttendeeAvailability":[
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"fannyd@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Free"
            },
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"danas@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Busy"
            }
         ],
         "Locations":[
            {
               "DisplayName":"Conf room Hood"
            }
         ],
         "SuggestionHint":"Suggested because it is one of the nearest times when most attendees are available."
      },
      {
         "MeetingTimeSlot":{
            "Start":{
               "Date":"2016-05-20",
               "Time":"11:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            },
            "End":{
               "Date":"2016-05-20",
               "Time":"12:00:00.0000000",
               "TimeZone":"Pacific Standard Time"
            }
         },
         "Confidence":50.0,
         "OrganizerAvailability":"Free",
         "AttendeeAvailability":[
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"fannyd@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Free"
            },
            {
               "Attendee":{
                  "Type":"Required",
                  "EmailAddress":{
                     "Address":"danas@prosewareltd.onmicrosoft.com"
                  }
               },
               "Availability":"Busy"
            }
         ],
         "Locations":[
            {
               "DisplayName":"Conf room Hood"
            }
         ],
         "SuggestionHint":"Suggested because it is one of the nearest times when most attendees are available."
      }
   ],
   "EmptySuggestionsHint":""
}
```

****

<a name="FindFreeSlots"></a>
###<a name="find-free-time-slots-for-just-the-signed-in-user-rest"></a>只是已登录的用户 (REST) 中查找可用时间段

通过在请求正文中指定以下参数在已登录的用户主日历中的日期范围内查找可用时间段︰

- **TimeConstraint**
- **MeetingDuration**

**示例请求**

本示例查找 1 小时空闲时间槽，由**MeetingDuration**，由**TimeConstraint**指定的时间段内已登录的用户主日历中。

```
POST https://outlook.office.com/api/beta/me/findmeetingtimes

Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json 

{ 
  "Attendees": [],
  "TimeConstraint": { 
    "Timeslots": [ 
      { 
        "Start": { 
          "Date": "2016-05-20",  
          "Time": "7:00:00",  
          "TimeZone": "Pacific Standard Time" 
        },  
        "End": { 
          "Date": "2016-05-20",  
          "Time": "17:00:00",  
          "TimeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "MeetingDuration": "PT1H"
}
```



**响应示例**

状态代码︰ 200
```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Microsoft.OutlookServices.MeetingTimeCandidatesResult",
    "MeetingTimeSlots": [
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "08:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "09:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
            ],
            "Locations": [
            ]
        },
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "09:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "10:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
            ],
            "Locations": [
            ]
        },
        {
            "MeetingTimeSlot": {
                "Start": {
                    "Date": "2016-05-20",
                    "Time": "12:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                },
                "End": {
                    "Date": "2016-05-20",
                    "Time": "13:00:00.0000000",
                    "TimeZone": "Pacific Standard Time"
                }
            },
            "Confidence": 100.0,
            "OrganizerAvailability": "Free",
            "AttendeeAvailability": [
            ],
            "Locations": [
            ]
        }
    ],
    "EmptySuggestionsHint": ""
}
```

****


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。 

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->




****

<a name="CreateEvents"> </a>
## <a name="create-events"></a>创建事件

REST API︰[创建日历事件](#CreateAnEvent)

客户端库︰[创建日历事件 （客户端）](#CreateEventsClient)

<a name="CreateAnEvent"></a>
###<a name="create-a-calendar-event-rest"></a>创建日历事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

创建用户的主日历或特定日历中的事件，由过账到日历的`events`终结点。 创建事件时，服务器将发送给所有与会者的邀请。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events
POST https://outlook.office.com/api/beta/me/calendars/{calendar_id}/events
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|

**示例请求**

```
POST https://outlook.office.com/api/beta/me/events
Content-Type: application/json
```

```
{
  "Subject": "Discuss the Calendar REST API",
  "Body": {
    "ContentType": "HTML",
    "Content": "I think it will meet our requirements!"
  },
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Type": "Required"
    }
  ]
}
```

**响应示例**

状态代码︰ 201

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE4v1RAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==\"",
  "Id": "AAMkAGE4v1RAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:56:10.1058291Z",
  "LastModifiedDateTime": "2014-01-22T20:56:10.3402186Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "",
    "Address": null,
    "Coordinates": null,
    "LocationEmailAddress": "",
    "LocationUri": ""
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Status": {
        "Response": "None",
        "Time": "0001-01-01T00:00:00Z"
      },
      "Type": "Required"
    }
  ],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  },
  "OnlineMeetingUrl": null
}
```


**响应类型**

新的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

默认情况下，响应包含新事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 以下是一个示例，以仅包含的**Start**和**End**属性新事件的响应中。

```
POST https://outlook.office.com/api/beta/me/events?$Select=Start,End
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/events
POST https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}/events
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/events
Content-Type: application/json
```

```
{
  "Subject": "Discuss the Calendar REST API",
  "Body": {
    "ContentType": "HTML",
    "Content": "I think it will meet our requirements!"
  },
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Type": "Required"
    }
  ]
}
```

**响应示例**

状态代码︰ 201

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE4v1RAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==\"",
  "Id": "AAMkAGE4v1RAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:56:10.1058291Z",
  "LastModifiedDateTime": "2014-01-22T20:56:10.3402186Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "",
    "Address": null
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Janet Schorr"
      },
      "Status": {
        "Response": "None",
        "Time": "0001-01-01T00:00:00Z"
      },
      "Type": "Required"
    }
  ],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  }
}
```


**响应类型**

新的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

默认情况下，响应包含新事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 以下是一个示例，以仅包含的**Start**和**End**属性新事件的响应中。

```
POST https://outlook.office.com/api/v2.0/me/events?$Select=Start,End
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->

<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


默认情况下，**开始**和**结束**时间值是以 utc 格式。 可以指定时区的**开始**和**结束**时，快速相应时区中的时间并包含时间从 UTC 偏移量。 下面的示例演示如何指定在太平洋标准时间的时间值。 请注意，是否您指定一个时区，您必须指定一个值为另一个也。


```no-highlight
POST https://outlook.office.com/api/v1.0/me/events
POST https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}/events
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|

```REST
{
    "method": "POST",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 529
    },
    "parameterDetails": [],
    "requestBody": {
        "Subject": "Discuss the Calendar REST API",
        "Body": {
            "ContentType": "HTML",
            "Content": "I think it will meet our requirements!"
        },
        "Start": "2014-02-02T18:00:00-08:00",
        "StartTimeZone": "Pacific Standard Time",
        "End": "2014-02-02T19:00:00-08:00",
        "EndTimeZone": "Pacific Standard Time",
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Type": "Required"
            }
        ]
    },
    "statusCode": 201,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1RAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1RAAA=",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheA==",
        "Categories": [],
        "DateTimeCreated": "2014-01-22T20:56:10.1058291Z",
        "DateTimeLastModified": "2014-01-22T20:56:10.3402186Z",
        "Subject": "Discuss the Calendar REST API",
        "BodyPreview": "I think it will meet our requirements!",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": "2014-02-02T18:00:00-08:00",
        "StartTimeZone": "Pacific Standard Time",
        "End": "2014-02-02T19:00:00-08:00",
        "EndTimeZone": "Pacific Standard Time",
        "Location": {
            "DisplayName": ""
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SingleInstance",
        "SeriesMasterId": null,
        "Attendees": [
            {
                "EmailAddress": {
                    "Address": "janets@a830edad9050849NDA1.onmicrosoft.com",
                    "Name": "Janet Schorr"
                },
                "Status": {
                    "Response": "None",
                    "Time": "0001-01-01T00:00:00Z"
                },
                "Type": "Required"
            }
        ],
        "Recurrence": null,
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "alexd"
            }
        }
    }
}
```


**响应类型**

新的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。

默认情况下，响应包含新事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 以下是一个示例，以仅包含的**Start**和**End**属性新事件的响应中。

```
POST https://outlook.office.com/api/v1.0/me/events?$Select=Start,End
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="CreateEventsClient"></a>
### <a name="create-a-calendar-event-client"></a>创建日历事件 （客户端）

创建事件。 若要将事件添加到另一个日历，使用目标日历的**事件**属性。

示例︰`await client.Me.Calendars["AQMkADE3..."].Events.AddEventAsync(newEvent);`


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- CHUCK, feel free to provide client library example that reflects the event breaking changes for beta.  --> 

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Create a location for the event
Location location = new Location 
{ 
    DisplayName = "Water cooler" 
}; 

// Create a description for the event   
ItemBody body = new ItemBody 
{ 
    Content = "Status updates, blocking issues, and next steps", 
    ContentType = BodyType.Text 
}; 
    
// Create an attendee for the event 
Attendee[] attendees =  
{  
    new Attendee  
    {  
        Type = AttendeeType.Required,  
        EmailAddress = new EmailAddress  
        {  
            Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"  
        },  
    },  
}; 
    
// Create the event object
Event newEvent = new Event 
{ 
    Subject = "Sync up", 
    Location = location, 
    Attendees = attendees, 
    Start = new DateTimeTimeZone()
    {
        TimeZone = TimeZoneInfo.Local.Id,
        DateTime = new DateTime(2015, 12, 1, 9, 30, 0).ToString("s")
    },
    End = new DateTimeTimeZone()
    {
        TimeZone = TimeZoneInfo.Local.Id,
        DateTime = new DateTime(2015, 12, 1, 10, 30, 0).ToString("s")
    },    
    Body = body 
};
    
// Add the event to the default calendar
await client.Me.Events.AddEventAsync(newEvent);

// Get the event ID.
string eventId = newEvent.Id;
```
```javascript
        var event = new Microsoft.OutlookServices.Event();
        event.subject = 'Your Subject';
        event.start = new Date("October 30, 2014 11:13:00").toISOString();
        event.end = new Date("October 30, 2014 12:13:00").toISOString();

        // Body
        event.body = new Microsoft.OutlookServices.ItemBody();
        event.body.content = 'Body Content';
        event.body.contentType = Microsoft.OutlookServices.BodyType.Text;

        // Location
        event.location = new Microsoft.OutlookServices.Location();
        event.location.displayName = 'Location';

        // Attendee
        var attendee1 = new Microsoft.OutlookServices.Attendee();
        var emailAddress1 = new Microsoft.OutlookServices.EmailAddress();
        emailAddress1.name = "Katie Jordan";
        emailAddress1.address = "katiej@a830edad9050849NDA1.onmicrosoft.com";

        attendee1.emailAddress = emailAddress1;

        event.attendees.push(attendee1);
        
        outlookClient.me.calendar.events.addEvent(event)
        .then(function (response) {
            console.log(response._Id);
        });    

```
<!-- ENDSECTION -->


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Create a location for the event
Location location = new Location 
{ 
    DisplayName = "Water cooler" 
}; 

// Create a description for the event   
ItemBody body = new ItemBody 
{ 
    Content = "Status updates, blocking issues, and next steps", 
    ContentType = BodyType.Text 
}; 
    
// Create an attendee for the event 
Attendee[] attendees =  
{  
    new Attendee  
    {  
        Type = AttendeeType.Required,  
        EmailAddress = new EmailAddress  
        {  
            Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"  
        },  
    },  
}; 
    
// Create the event object
Event newEvent = new Event 
{ 
    Subject = "Sync up", 
    Location = location, 
    Attendees = attendees, 
    Start = new DateTimeOffset(new DateTime(2014, 12, 1, 9, 30, 0)), 
    End = new DateTimeOffset(new DateTime(2014, 12, 1, 10, 0, 0)), 
    Body = body 
}; 
    
// Add the event to the default calendar
await client.Me.Events.AddEventAsync(newEvent);

// Get the event ID.
string eventId = newEvent.Id;
```
```javascript
        var event = new Microsoft.OutlookServices.Event();
        event.subject = 'Your Subject';
        event.start = new Date("October 30, 2014 11:13:00").toISOString();
        event.end = new Date("October 30, 2014 12:13:00").toISOString();

        // Body
        event.body = new Microsoft.OutlookServices.ItemBody();
        event.body.content = 'Body Content';
        event.body.contentType = Microsoft.OutlookServices.BodyType.Text;

        // Location
        event.location = new Microsoft.OutlookServices.Location();
        event.location.displayName = 'Location';

        // Attendee
        var attendee1 = new Microsoft.OutlookServices.Attendee();
        var emailAddress1 = new Microsoft.OutlookServices.EmailAddress();
        emailAddress1.name = "Katie Jordan";
        emailAddress1.address = "katiej@a830edad9050849NDA1.onmicrosoft.com";

        attendee1.emailAddress = emailAddress1;

        event.attendees.push(attendee1);
        
        outlookClient.me.calendar.events.addEvent(event)
        .then(function (response) {
            console.log(response._Id);
        });    

```
<!-- ENDSECTION -->

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->






****


<a name="UpdateEvents"> </a>
## <a name="update-events"></a>更新事件

REST API︰[更新日历事件](#UpdateAnEvent)

客户端库︰[更新日历事件 （客户端）](#UpdateEventsClient)

<a name="UpdateAnEvent"></a>
###<a name="update-a-calendar-event-rest"></a>更新日历事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

更改事件。 您指定的属性被更改。 如果用户是组织者，服务器将向所有与会者发送会议更新。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/beta/me/events/{event_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|

指定请求主体中的任何可写的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)属性。

```
PATCH https://outlook.office.com/api/beta/me/events/AAMkAGE1MFKPQWAAA=?$select=Location
```

**示例请求**

```
PATCH https://outlook.office.com/api/beta/me/events/AAMkAGE0M4v1OAAA=
Content-Type: application/json

{
  "Location": {
    "DisplayName": "Your office",
    "Address": null,
    "Coordinates": null,
    "LocationEmailAddress": "",
    "LocationUri": ""
  }
}
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE0M4v1OAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==\"",
  "Id": "AAMkAGE0M4v1OAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:49:05.5657528Z",
  "LastModifiedDateTime": "2014-01-22T21:14:17.4886416Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "Your office",
    "Address": null,
    "Coordinates": null,
    "LocationEmailAddress": "",
    "LocationUri": ""
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  },
  "OnlineMeetingUrl": null
}
```

**响应类型**

已更新的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。 如果用户是组织者，服务器将向所有与会者发送会议更新。

默认情况下，该响应包括更新事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 




[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/events/{event_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|

指定请求主体中的任何可写的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)属性。

**示例请求**

```
PATCH https://outlook.office.com/api/v2.0/me/events/AAMkAGE0M4v1OAAA=
Content-Type: application/json

{
  "Location": {
    "DisplayName": "Your office",
    "Address": null
  }
}
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGE0M4v1OAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==\"",
  "Id": "AAMkAGE0M4v1OAAA=",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==",
  "Categories": [],
  "CreatedDateTime": "2014-01-22T20:49:05.5657528Z",
  "LastModifiedDateTime": "2014-01-22T21:14:17.4886416Z",
  "Subject": "Discuss the Calendar REST API",
  "BodyPreview": "I think it will meet our requirements!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "Start": {
      "DateTime": "2014-02-02T18:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2014-02-02T19:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Location": {
    "DisplayName": "Your office",
    "Address": null
  },
  "ShowAs": "Busy",
  "IsAllDay": false,
  "IsCancelled": false,
  "IsOrganizer": true,
  "ResponseRequested": true,
  "Type": "SingleInstance",
  "SeriesMasterId": null,
  "Attendees": [],
  "Recurrence": null,
  "OriginalEndTimeZone": "Pacific Standard Time",
  "OriginalStartTimeZone": "Pacific Standard Time",
  "Organizer": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "alexd"
    }
  }
}
```

**响应类型**

已更新的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。 如果用户是组织者，服务器将向所有与会者发送会议更新。

默认情况下，该响应包括更新事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 

```
PATCH https://outlook.office.com/api/v2.0/me/events/AAMkAGE1MFKPQWAAA=?$select=Location
```




[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/events/{event_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|

指定请求主体中的任何可写的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)属性。

```REST
{
    "method": "PATCH",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 62
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA="
        }
    ],
    "requestBody": {
        "Location": {
            "DisplayName": "Your office"
        }
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Events/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Events('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeNheQ==",
        "Categories": [],
        "DateTimeCreated": "2014-01-22T20:49:05.5657528Z",
        "DateTimeLastModified": "2014-01-22T21:14:17.4886416Z",
        "Subject": "Discuss the Calendar REST API",
        "BodyPreview": "I think it will meet our requirements!",
        "Body": {
            "ContentType": "HTML",
            "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nI think it will meet our requirements!\r\n</body>\r\n</html>\r\n"
        },
        "Importance": "Normal",
        "HasAttachments": false,
        "Start": "2014-02-02T18:00:00-08:00",
        "StartTimeZone": "Pacific Standard Time",
        "End": "2014-02-02T19:00:00-08:00",
        "EndTimeZone": "Pacific Standard Time",
        "Location": {
            "DisplayName": "Your office"
        },
        "ShowAs": "Busy",
        "IsAllDay": false,
        "IsCancelled": false,
        "IsOrganizer": true,
        "ResponseRequested": true,
        "Type": "SingleInstance",
        "SeriesMasterId": null,
        "Attendees": [],
        "Recurrence": null,
        "Organizer": {
            "EmailAddress": {
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
                "Name": "alexd"
            }
        }
    }
}
```

**响应类型**

已更新的[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)。 如果用户是组织者，服务器将向所有与会者发送会议更新。

默认情况下，该响应包括更新事件的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 

```
PATCH https://outlook.office.com/api/v1.0/me/events/AAMkAGE1MFKPQWAAA=?$select=Location
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->






****

<a name="UpdateEventsClient"></a>
### <a name="update-a-calendar-event-client"></a>更新日历事件 （客户端）

更改事件。

您可以定义多个更新客户端，发送请求所有次 （批它们） 通过使用以下模式︰
1. 调用`UpdateAsync(true)`为每个您想要更新的实体。 指定`true`注册客户端在本地更新但不将其发布到服务器。
2. 调用`client.Context.SaveChangesAsync()`将本地注册的所有更新。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

<!-- CHUCK, feel free to provide client library example that reflects the event breaking changes for beta.  --> 

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


该示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)[收到事件 ID](#GetEvents)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing event by ID
IEvent eventToUpdate = await client.Me.Events[eventId].ExecuteAsync();

// Add attendees
eventToUpdate.Attendees.Add(new Attendee
{
    Type = AttendeeType.Required,
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com",
    },
});

// Make other changes
eventToUpdate.Start = new DateTimeOffset(new DateTime(2014, 12, 1, 14, 30, 0));
eventToUpdate.End = new DateTimeOffset(new DateTime(2014, 12, 1, 15, 0, 0));
eventToUpdate.Subject = "New event name";
    
// Commit all changes to the event
await eventToUpdate.UpdateAsync();

// Get an updated property.
string newEventName = eventToUpdate.Subject;
```

<!-- ENDSECTION -->


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

该示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)[收到事件 ID](#GetEvents)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing event by ID
IEvent eventToUpdate = await client.Me.Events[eventId].ExecuteAsync();

// Add attendees
eventToUpdate.Attendees.Add(new Attendee
{
    Type = AttendeeType.Required,
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com",
    },
});

// Make other changes
eventToUpdate.Start = new DateTimeOffset(new DateTime(2014, 12, 1, 14, 30, 0));
eventToUpdate.End = new DateTimeOffset(new DateTime(2014, 12, 1, 15, 0, 0));
eventToUpdate.Subject = "New event name";
    
// Commit all changes to the event
await eventToUpdate.UpdateAsync();

// Get an updated property.
string newEventName = eventToUpdate.Subject;
```

<!-- ENDSECTION -->

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->








****

<a name="RespndToEvents"></a>
## <a name="respond-to-events"></a>对事件作出响应

REST API︰[接受事件 (REST)](#AcceptEvent) | [暂时接受事件 (REST)](#TentAcceptEvent) | [拒绝事件 (REST)](#DeclineEvent)

<a name="AcceptEvent"></a>
###<a name="accept-event-rest"></a>接受事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

接受指定的事件。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/accept
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/accept

Content-Type: application/json

{
  "Comment": "Great idea!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/accept
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/accept

Content-Type: application/json

{
  "Comment": "Great idea!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/accept
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/v1.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/accept

Content-Type: application/json

{
  "Comment": "Great idea!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->





****

<a name="TentAcceptEvent"></a>
###<a name="tentatively-accept-event-rest"></a>暂时接受事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

暂定接受指定的事件。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/tentativelyaccept
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/tentativelyaccept

Content-Type: application/json

{
  "Comment": "I'll confirm later!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/tentativelyaccept
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/tentativelyaccept

Content-Type: application/json

{
  "Comment": "I'll confirm later!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/tentativelyaccept
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/v1.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/tentativelyaccept

Content-Type: application/json

{
  "Comment": "I'll confirm later!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


****

<a name="DeclineEvent"></a>
###<a name="decline-event-rest"></a>谢绝事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

拒绝邀请到指定的事件。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]



```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/decline
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/decline

Content-Type: application/json

{
  "Comment": "Sorry, maybe next time!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]



```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/decline
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/decline

Content-Type: application/json

{
  "Comment": "Sorry, maybe next time!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/decline
```


|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。 必需。|
|_正文参数_|
|注释|string|在响应中包含的文本。 可选项。|
|SendResponse|布尔| `true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|
 
**示例请求**

```
POST https://outlook.office.com/api/v1.0/me/events('AAMkAGE1M2IyNGNmLTI5MT_bs88AAAXDJwEAAA=')/decline

Content-Type: application/json

{
  "Comment": "Sorry, maybe next time!",
  "SendResponse": "true"
}
```

**响应**

HTTP 202 接受响应代码指示成功的响应。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****

<a name="DeleteEvents"> </a>
## <a name="delete-events"></a>删除事件

[删除日历事件 (REST)](#DeleteAnEvent)的 REST API︰

客户端库︰[删除日历事件 （客户端）](#DeleteEventsClient)

<a name="DeleteAnEvent"></a>
###<a name="delete-a-calendar-event-rest"></a>删除日历事件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

将事件移至已登录的用户的已删除的邮件文件夹中。 如果该事件是一个会议，并且已登录的用户是组织者，服务器将向所有与会者发送取消通知。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

因为**删除**也是可用的组织者和与会者的会议，此操作不同于[取消](#CancelEvents)。 如果签名用户是会议组织者，用户只需不给与会者提供自定义取消邮件取消会议。

```no-highlight
DELETE https://outlook.office.com/api/beta/me/events/{event_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|


**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/events/AAMkAGE0M4v1OAAA=
```

**响应示例**

状态代码︰ 204


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/events/{event_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|

**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/events/AAMkAGE0M4v1OAAA=
```

**响应示例**

状态代码︰ 204



[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/events/{event_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|

```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [ 
                {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA="
        }
    ],
    
    "statusCode": 204
    
}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****

<a name="DeleteEventsClient"></a>
### <a name="delete-a-calendar-event-client"></a>删除日历事件 （客户端）

将事件移至已删除邮件文件夹中。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


该示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)[收到事件 ID](#GetEvents)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing event by ID
IEvent eventToDelete = await client.Me.Events[eventId].ExecuteAsync();

//Delete the event
await eventToDelete.DeleteAsync();
```

<!-- ENDSECTION -->

****

<a name="CancelEvents"> </a>
## <a name="cancel-events-preview"></a>取消事件 （预览）

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

此操作允许会议发送取消邮件和取消事件的组织者。 

此操作将事件移至已删除邮件文件夹。 组织者还可以取消定期会议的实例通过提供事件的事件 id。 与会者调用此操作获取错误 （HTTP 400 错误的请求），并显示以下错误消息︰

"不能完成您的请求。 您需要被组织者取消会议。

在于**取消**供只有组织者，并允许取消有关与会者发送自定义信息管理器，则此操作不同于[删除](#DeleteEvents)。

```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/Cancel
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|_正文参数_|
|注释|string|向所有与会者发送取消通知有关的注释。|

**示例请求**

```
POST https://outlook.office.com/api/beta/me/events/AAMkAGE0M4v1OAAA=/Cancel

Content-Type: application/json
{
  "Comment": "Cancelling this meeting as there is a time conflict for most folks."
}
```

**响应示例**

状态代码︰ 202 已接受


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。 

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。 

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="GetAttachments"> </a>
## <a name="get-attachments"></a>获取附件

您可以获取附件集合或获取附件。

REST API︰[获取附件集合 (REST)](#GetAttachmentCollection) | [获取附件 (REST)](#GetAttachment)

<a name="GetAttachmentCollection"> </a>
###<a name="get-an-attachment-collection-rest"></a>获取附件集合 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

从某个特定事件中获取附件。

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|


**响应类型**

它可以是类型[FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)， [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)或[ReferenceAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)的附件集合。


**示例请求**

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2NGTG9yAAA=/attachments
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events('AAMkAGI2NG9yAAA%3D')/Attachments",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2NGTG9yAAA=')/Attachments('AAMkAGI2NGLwydGuOzcHf1FBlo=')",
            "Id": "AAMkAGI2NGLwydGuOzcHf1FBlo=",
            "LastModifiedDateTime": "2014-10-22T00:30:26Z",
            "Name": "Company Party.docx",
            "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
            "Size": 11647,
            "IsInline": false,
            "ContentId": null,
            "ContentLocation": null,
            "ContentBytes": "UEsDBBQABgAIAAAAIQDfpNJs...AAF4pAAAAAA=="
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|


**响应类型**

它可以是[FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)类型的附件集合。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2NGTG9yAAA=/attachments
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events('AAMkAGI2NG9yAAA%3D')/Attachments",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2NGTG9yAAA=')/Attachments('AAMkAGI2NGLwydGuOzcHf1FBlo=')",
            "Id": "AAMkAGI2NGLwydGuOzcHf1FBlo=",
            "LastModifiedDateTime": "2014-10-22T00:30:26Z",
            "Name": "Company Party.docx",
            "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
            "Size": 11647,
            "IsInline": false,
            "ContentId": null,
            "ContentLocation": null,
            "ContentBytes": "UEsDBBQABgAIAAAAIQDfpNJs...AAF4pAAAAAA=="
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|


**响应类型**

它可以是[FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)类型的附件集合。


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=/attachments",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
        "Name": "My Calendars",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
        "ClassId": "0006f0b7-0000-0000-c000-000000000046"
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****


<a name="GetAttachment"> </a>
###<a name="get-an-attachment-rest"></a>获取附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

从某个特定事件中获取附件。

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
GET https://outlook.office.com/api/beta/me/events/{event_id}/attachments/{attachment_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|attachment_id|string|附件 id。|

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

请求的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)、[项附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)或[引用附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)。


**示例请求**

下面的示例获取附加到某个特定事件的文件。

```
GET https://outlook.office.com/api/beta/me/events/AAMkAGI2WRAAADTG9yAAA=/attachments/AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events('AAMkAGI2WRAAADTG9yAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2WRAAADTG9yAAA=')/Attachments('AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=')",
    "Id": "AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=",
    "LastModifiedDateTime": "2014-10-22T00:30:26Z",
    "Name": "Company Party.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11647,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQD...AAF4pAAAAAA=="
}
```

**示例请求 （参考附件）**

下面的示例获取事件的引用附件。

```
GET https://outlook.office.com/api/beta/me/events('AAMkAGE1Mbs88AADggYEcAAA=')/attachments('AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=')
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADggYEcAAA%3D')/attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
    "id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=",
    "lastModifiedDateTime": "2016-03-22T22:27:20Z",
    "name": "Hydrangea picture",
    "contentType": null,
    "size": 412,
    "isInline": false,
    "sourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
    "providerType": "oneDriveBusiness",
    "thumbnailUrl": null,
    "previewUrl": null,
    "permission": "edit",
    "isFolder": false
}

```


**示例请求 ($expand 附件)**

下面的示例获取并扩展事件属性 2 引用附件嵌入。

```
GET https://outlook.office.com/api/beta/me/events('AAMkAGE1Mbs88AADggYEcAAA=')?$expand=attachments
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events/$entity",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAA4KZrtA==\"",
    "id": "AAMkAGE1Mbs88AADggYEcAAA=",
    "createdDateTime": "2016-03-22T22:19:58.1359352Z",
    "lastModifiedDateTime": "2016-03-22T22:39:09.9335289Z",
    "changeKey": "mODEKWhc/Um6lA3uPm7PPAAA4KZrtA==",
    "categories": [
    ],
    "originalStartTimeZone": "Pacific Standard Time",
    "originalEndTimeZone": "Pacific Standard Time",
    "responseStatus": {
        "response": "organizer",
        "time": "0001-01-01T00:00:00Z"
    },
    "iCalUId": "040000008200E00074C5B7101A82E008000000005895FCF78884D10100000000000000001000000099DD7CA6BCF37C4F9F7DAACCADDD6B89",
    "reminderMinutesBeforeStart": 15,
    "isReminderOn": true,
    "hasAttachments": true,
    "subject": "Plan Easter egg hunt!",
    "body": {
        "contentType": "html",
        "content": "<html>\r\n<body>\r\nLet's get organized for this weekend's gathering.\r\n</body>\r\n</html>\r\n"
    },
    "bodyPreview": "Let's get organized for this weekend's gathering.",
    "importance": "normal",
    "sensitivity": "normal",
    "start": {
        "dateTime": "2016-03-26T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2016-03-26T18:00:00.0000000",
        "timeZone": "UTC"
    },
    "location": {
        "displayName": "",
        "address": {
            "type": "unknown"
        },
        "coordinates": {
        }
    },
    "isAllDay": false,
    "isCancelled": false,
    "isOrganizer": true,
    "recurrence": null,
    "responseRequested": true,
    "seriesMasterId": null,
    "showAs": "busy",
    "type": "singleInstance",
    "attendees": [
        {
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "type": "required",
            "emailAddress": {
                "name": "Randi Welch",
                "address": "randiw@contoso.onmicrosoft.com"
            }
        }
    ],
    "organizer": {
        "emailAddress": {
            "name": "Dana Swope",
            "address": "danas@contoso.onmicrosoft.com"
        }
    },
    "webLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADggYEcAAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
    "onlineMeetingUrl": null,
    "attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADggYEcAAA%3D')/attachments",
    "attachments": [
        {
            "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"",
            "id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=",
            "lastModifiedDateTime": "2016-03-22T22:27:20Z",
            "name": "Hydrangea picture",
            "contentType": null,
            "size": 412,
            "isInline": false,
            "sourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
            "providerType": "oneDriveBusiness",
            "thumbnailUrl": null,
            "previewUrl": null,
            "permission": "edit",
            "isFolder": false
        },
        {
            "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"",
            "id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAE1rHHth7YNLlR9WsgnODy0=",
            "lastModifiedDateTime": "2016-03-22T22:39:09Z",
            "name": "Koala picture",
            "contentType": null,
            "size": 382,
            "isInline": false,
            "sourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
            "providerType": "oneDriveBusiness",
            "thumbnailUrl": null,
            "previewUrl": null,
            "permission": "edit",
            "isFolder": false
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments/{attachment_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|attachment_id|string|附件 id。|

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

请求的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)的[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/events/AAMkAGI2WRAAADTG9yAAA=/attachments/AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Events('AAMkAGI2WRAAADTG9yAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Events('AAMkAGI2WRAAADTG9yAAA=')/Attachments('AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=')",
    "Id": "AAMkAGI2TG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=",
    "LastModifiedDateTime": "2014-10-22T00:30:26Z",
    "Name": "Company Party.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11647,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQD...AAF4pAAAAAA=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|attachment_id|string|附件 id。|

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

请求的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)的[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/events/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=/attachments/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA="
        },
        {
            "name": "attachment_id",
            "type": "string",
            "description": "The attachment ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAABEgAQALxJtn1LwydGuOzcHf1FBlo="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
        "Name": "My Calendars",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
        "ClassId": "0006f0b7-0000-0000-c000-000000000046"
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->




****


<a name="CreateAttachments"> </a>
## <a name="create-attachments"></a>创建附件
您可以创建一个文件附件或事件[创建项附件](#CreateItemAttachment)。

REST API︰[创建一个文件附件 (REST)](#CreateFileAttachment) | [创建一个项目附件 (REST)](#CreateItemAttachment) | 
[创建一个引用附件 (REST)](#CreateReferenceAttachment)


<a name="CreateFileAttachment"></a>
###<a name="create-a-file-attachment-rest"></a>创建一个文件附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

文件将附件添加到事件。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|_正文参数_|
|@odata.type| string | #Microsoft.OutlookServices.FileAttachment |
|名称|string|附件的名称。|
|ContentBytes|二进制文件|要附加的文件。|
 
<!-- Add post GA
```REST
[!INCLUDE [calendar_api_create_file_attachment](./_data/calendar_api_create_file_attachment.json)]
``` -->

**响应类型**

新[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)。

****


<a name="CreateItemAttachment"></a>
###<a name="create-an-item-attachment-rest"></a>创建项附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

项目将附件添加到事件。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|_正文参数_|
|@odata.type| string | #Microsoft.OutlookServices.ItemAttachment |
|名称|string|附件的名称。|
|项目|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)、[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)或[联系人](..\api\complex-types-for-mail-contacts-calendar.md#ContactResource)实体中。|若要将附加项。|
 

<!--Post GA
```REST
[!INCLUDE [calendar_api_create_item_attachment](./_data/calendar_api_create_item_attachment.json)]
``` -->


**响应类型**

新[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

****

<a name="CreateReferenceAttachment"></a>

###<a name="create-a-reference-attachment-rest"></a>创建一个引用附件 (REST)

<!-- ==================================== Start beta content ====================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

_**所需范围**︰ https://outlook.office.com/mail.readwrite_

引用将附件添加到事件。

```no-highlight
POST https://outlook.office.com/api/beta/me/events/{event_id}/attachments
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|String|事件 id。|
|_正文参数_|
|@odata.type|String|```#Microsoft.OutlookServices.ReferenceAttachment```|
|Name|字符串|附件的显示名称。 必需。|
|SourceUrl|String | 若要获取附件内容的 URL。 如果这是一个文件夹的 URL，然后在 Outlook 或 web 上的 Outlook 中正确显示的文件夹设置**IsFolder**为 true。 必需。|

指定的**名称**和**SourceUrl**参数和任何可写的[引用附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)属性请求主体中。



**响应类型**

请[参考附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)。


**示例请求**

下面的示例将添加到现有事件的引用附件。 附件是一个链接到 OneDrive 上的文件进行业务。

```
POST https://outlook.office.com/api/beta/me/events('AAMkAGE1Mbs88AADggYEcAAA=')/attachments
Content-Type: application/json

{
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"", 
    "Name": "Hydrangea picture", 
    "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg", 
    "ProviderType": "oneDriveBusiness", 
    "Permission": "Edit", 
    "IsFolder": "False" 
 }
```


**响应示例**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADggYEcAAA%3D')/attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"",
    "Id": "AAMkAGE1Mbs88AADggYEcAAABEgAQAABWAoLgP3REt_LWRG8ORv4=",
    "LastModifiedDateTime": "2016-03-22T22:27:20Z",
    "Name": "Hydrangea picture",
    "ContentType": null,
    "Size": 412,
    "IsInline": false,
    "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
    "ProviderType": "oneDriveBusiness",
    "ThumbnailUrl": null,
    "PreviewUrl": null,
    "Permission": "edit",
    "IsFolder": false
}
```


**示例请求**

下面的示例创建事件作为同一个调用中添加引用附件。 附件是一个链接到 OneDrive 上的文件进行业务。

```
POST https://outlook.office.com/api/beta/me/events
Content-Type: application/json

{
  "Subject": "Plan Easter egg hunt!",
  "Body": {
    "ContentType": "HTML",
    "Content": "Let's get organized for this weekend's gathering."
  },
  "Start": {
      "DateTime": "2016-03-25T10:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "End": {
      "DateTime": "2016-03-25T11:00:00",
      "TimeZone": "Pacific Standard Time"
  },
  "Attendees": [
    {
      "EmailAddress": {
        "Address": "randiw@contoso.onmicrosoft.com",
        "Name": "Randi Welch"
      },
      "Type": "Required"
    }
  ],
  "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment"", 
        "Name": "Hydrangea picture", 
        "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg", 
        "ProviderType": "oneDriveBusiness", 
        "Permission": "Edit", 
        "IsFolder": "False" 
      }
  ]
}
```


**响应示例**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events/$entity",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAA4KZrrg==\"",
    "Id": "AAMkAGE1Mbs88AADggYEbAAA=",
    "CreatedDateTime": "2016-03-22T22:09:26.2918604Z",
    "LastModifiedDateTime": "2016-03-22T22:09:27.0754806Z",
    "ChangeKey": "mODEKWhc/Um6lA3uPm7PPAAA4KZrrg==",
    "Categories": [
    ],
    "OriginalStartTimeZone": "Pacific Standard Time",
    "OriginalEndTimeZone": "Pacific Standard Time",
    "ResponseStatus": {
        "Response": "Organizer",
        "Time": "0001-01-01T00:00:00Z"
    },
    "iCalUId": "040000008200E00074C5B7101A82E0080000000043FB607F8784D101000000000000000010000000B3A31CD7479252448ECE77242DE92587",
    "ReminderMinutesBeforeStart": 15,
    "IsReminderOn": true,
    "HasAttachments": true,
    "Subject": "Plan Easter egg hunt!",
    "Body": {
        "contentType": "html",
        "content": "<html>\r\n<body>\r\nLet's get organized for this weekend's gathering.\r\n</body>\r\n</html>\r\n"
    },
    "BodyPreview": "Let's get organized for this weekend's gathering.",
    "Importance": "normal",
    "Sensitivity": "normal",
    "Start": {
        "DateTime": "2016-03-25T10:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "End": {
        "DateTime": "2016-03-25T11:00:00.0000000",
        "TimeZone": "Pacific Standard Time"
    },
    "Location": {
        "DisplayName": "",
        "Address": {
            "Type": "unknown"
        },
        "Coordinates": {
        }
    },
    "IsAllDay": false,
    "IsCancelled": false,
    "IsOrganizer": true,
    "Recurrence": null,
    "ResponseRequested": true,
    "SeriesMasterId": null,
    "ShowAs": "busy",
    "Type": "singleInstance",
    "Attendees": [
        {
            "Status": {
                "Response": "none",
                "Time": "0001-01-01T00:00:00Z"
            },
            "Type": "required",
            "EmailAddress": {
                "Name": "Randi Welch",
                "Address": "randiw@contoso.onmicrosoft.com"
            }
        }
    ],
    "Organizer": {
        "EmailAddress": {
            "Name": "Dana Swope",
            "Address": "danas@contoso.onmicrosoft.com"
        }
    },
    "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADggYEbAAA%3D&exvsurl=1&viewmodel=ICalendarItemDetailsViewModelFactory",
    "OnlineMeetingUrl": null,
    "Attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/events('AAMkAGE1Mbs88AADZ0CU9AAA%3D')/attachments",
    "Attachments": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADZ0CU9AAABEgAQAGe4H1iqXwtLsrCCLLkDxqo=",
      "LastModifiedDateTime": null,
      "Name": Hydrangea picture,
      "ContentType": null,
      "Size": 0,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
      "ProviderType": "oneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    }
    ]
}

```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End beta content ====================================================== -->

<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->



****


<a name="DeleteAttachments"> </a>
## <a name="delete-attachments"></a>删除附件

删除的附件的事件。

REST API︰[删除事件附件 (REST)](#DeleteAnEventAttachment)

<a name="DeleteAnEventAttachment"></a>
###<a name="delete-an-event-attachment-rest"></a>删除事件附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

删除指定的附件的事件。 附件可以是[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)、[项附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)或[引用附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)。

```no-highlight
DELETE https://outlook.office.com/api/beta/me/events/{event_id}/attachments/{attachment_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|attachment_id|string|附件 id。|

**示例请求**

```
DELETE https:/outlook.office.com/api/beta/me/events/AAMkAGE0MG4v1OAAA=/attachments/AAMkAGITG9yAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

删除指定的附件的事件。 附件可以是[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/events/{event_id}/attachments/{attachment_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|attachment_id|string|附件 id。|

**示例请求**

```
DELETE https:/outlook.office.com/api/v2.0/me/events/AAMkAGE0MG4v1OAAA=/attachments/AAMkAGITG9yAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

删除指定的附件的事件。 附件可以是[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|event_id|string|事件 id。|
|attachment_id|string|附件 id。|

```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/events/{event_id}/attachments/{attachment_id}",
    "requestUrl": "https:/outlook.office.com/api/v1.0/me/events/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA=/attachments/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "event_id",
            "type": "string",
            "description": "The event ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAENAAAmP1Ln1wcHRariNdTMGAO9AAAV4v1OAAA="
        },
        {
            "name": "event_id",
            "type": "string",
            "description": "The attachment ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAENAACd9nJ-tVysQos2hTfspaWRAAADTG9yAAA="
        }
    ],
    "statusCode": 204

}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

<a name="GetReminders" > </a>
##获得提醒

从日历中获得两个日期和时间之间的事件提醒的列表。

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
GET https://outlook.office.com/api/beta/me/ReminderView(StartDateTime='{DateTime}',EndDateTime='{DateTime}')
```
|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应事件的默认时区。|
|_URL 参数_|
|开始日期时间|string|开始日期和时间返回提醒。|
|EndDateTime|string|结束日期和返回的提醒时间。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_头未指定，则设置为 UTC 时区。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/ReminderView(StartDateTime='{DateTime}',EndDateTime='{DateTime}')
```
|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|喜欢︰ |outlook.timezone|在响应事件的默认时区。|
|_URL 参数_|
|开始日期时间|string|开始日期和时间返回提醒。|
|EndDateTime|string|结束日期和返回的提醒时间。|

使用_更愿意︰ outlook.timezone_标头，指定时区的时间使用有关的事件的开始和结束时间在响应中。
如果该事件在不同的时区中创建的开始和结束时间将被调整为指定的时区中。
请参阅[此列表中](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)的受支持的时区名称。 如果_更愿意︰ outlook.timezone_头未指定，则设置为 UTC 时区。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

此功能可用于仅测试版和 2.0 版的版本。 若要了解详细信息，请在右上角的文章，并选择**2.0 版**或**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ==================================== End v1 content ======================================================== -->


<a name="SnoozeReminders"> </a>
##暂停的提醒

暂停的提醒，直到新的时间延迟提醒。

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events('{id}')/SnoozeReminder
```

|**必需的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|事件 ID。|
|_正文参数_|
|NewReminderTime|[DateTimeTimeZone](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)|新的日期和时间触发提醒。|

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events('{id}')/SnoozeReminder
```

|**必需的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|事件 ID。|
|_正文参数_|
|NewReminderTime|[DateTimeTimeZone](..\api\complex-types-for-mail-contacts-calendar.md#DateTimeTimeZone)|新的日期和时间触发提醒。|

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

此功能可用于仅测试版和 2.0 版的版本。 若要了解详细信息，请在右上角的文章，并选择**2.0 版**或**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

<a name="DismissReminders"> </a>
##关闭提醒

Dissmiss 已触发提醒。

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events({id})/DismissReminder
```

|**必需的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|事件 ID。|


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/Events({id})/DismissReminder
```

|**必需的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|事件 ID。|

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

此功能可用于仅测试版和 2.0 版的版本。 若要了解详细信息，请在右上角的文章，并选择**2.0 版**或**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


<a name="GetCalendars"> </a>
##获取日历

您可以获取日历集合或获取日历。

REST API︰[获取日历集合 (REST)](#GetCalendarCollection) | [获取日历 (REST)](#GetCalendar)

客户端库︰[获取日历集合或一个日历 （客户端）](#GetCalendarsClient)

<a name="GetCalendarCollection"> </a>
###<a name="get-a-calendar-collection-rest"></a>获取日历集合 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

获取所有用户的日历 (`calendars`) 或从一个特定的日历组获取日历。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]



```no-highlight
GET https://outlook.office.com/api/beta/me/calendars
GET https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}/calendars
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#UseOdataQueryParameters)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calender_group_id|string|日历组 id。|


**示例请求**

```
https://outlook.office.com/api/beta/me/calendars
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
            "Id": "AAMkAGI2TGuLAAA=",
            "Name": "Calendar",
            "Color": "Auto",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]



```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendars
GET https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}/calendars
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#UseOdataQueryParameters)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calender_group_id|string|日历组 id。|

**示例请求**

```
https://outlook.office.com/api/v2.0/me/calendars
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
            "Id": "AAMkAGI2TGuLAAA=",
            "Name": "Calendar",
            "Color": "Auto",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendars
GET https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}/calendars
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#UseOdataQueryParameters)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calender_group_id|string|日历组 id。|


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=')",
                "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+w==\"",
                "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=",
                "Name": "Calendar",
                "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
            }
        ]
    }
}
```

**响应类型**

[日历](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)的请求的集合中。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



****

<a name="GetCalendar"> </a>
###<a name="get-a-calendar-rest"></a>获取日历 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

获取日历的标识。 您可以通过获取用户的主日历`../me/calendar`终结点。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendars/{calendar_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|


**示例请求**

```
GET https://outlook.office.com/api/beta/me/calendars/AAMkAGI2TGuLAAA=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
    "Id": "AAMkAGI2TGuLAAA=",
    "Name": "Calendar",
    "Color": "Auto",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/calendars/AAMkAGI2TGuLAAA=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGI2TGuLAAA=')",
    "Id": "AAMkAGI2TGuLAAA=",
    "Name": "Calendar",
    "Color": "Auto",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_id",
            "type": "string",
            "description": "The calendar ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+w==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuLAAA=",
        "Name": "Calendar",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+w=="
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

**响应类型**

所请求的[日历](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)。

****

<a name="GetCalendarsClient"> </a>
###<a name="get-a-calendar-collection-or-a-calendar-client"></a>获取日历集合或一个日历 （客户端）

获取用户的日历。 若要获取用户的默认日历，请使用`client.Me.Calendar`快捷键属性。 若要获取不同的日历，**日历**集合的索引指定的日历 ID 或使用**GetById**方法。

示例︰`client.Me.Calendars[calendarId].ExecuteAsync()`


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


**请注意**日历集合支持**选择**、**排序**，并**执行**查询表达式。

本示例将调用方法[获取 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar" -->

```cs-i
var outlookClient = await CreateOutlookClientAsync("Calendar");
var calendars = await outlookClient.Me.Calendars
  .Take(10)
  .ExecuteAsync();

foreach(var calendar in calendars.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Calendar '{0}'.", calendar.Name);
}

```
```javascript-i
outlookClient.me.calendars.getCalendars().fetchAll(100).then(function(result) {
    result.forEach(function (calendar) {
        console.log('Calendar "' + calendar.name + '", URL ' + calendar.path)
    });
}, function(error) {
    console.log(error);
});
```

<!-- ENDSECTION -->

****

<a name="CreateCalendars"> </a>
## <a name="create-calendars"></a>创建日历

REST API︰[创建一个日历 (REST)](#CreateACalendar)

客户端库︰[创建一个日历 （客户端）](#CreateCalendarsClient)

<a name="CreateACalendar"></a>
###<a name="create-a-calendar-rest"></a>创建一个日历 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

通过使用默认日历组中创建一个日历`../me/calendars`快捷方式，或按特定日历组由过账到组的`calendars`终结点。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
POST https://outlook.office.com/api/beta/me/calendars
POST https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}/calendars
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calender_group_id|string|日历的组 ID，如果您收到来自某个特定组的日历。|
|_正文参数_|
|名称|string|新日历的名称。|
 

**示例请求**

```
POST https://outlook.office.com/api/beta/me/calendars
Content-Type: application/json

{
  "Name": "Social"
}

```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLHAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ==\"",
  "Id": "AAMkAGE4xLHAAA=",
  "Name": "Social",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/calendars
POST https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}/calendars
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calender_group_id|string|日历的组 ID，如果您收到来自某个特定组的日历。|
|_正文参数_|
|名称|string|新日历的名称。|
 

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/calendars
Content-Type: application/json

{
  "Name": "Social"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLHAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ==\"",
  "Id": "AAMkAGE4xLHAAA=",
  "Name": "Social",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/calendars
POST https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}/calendars
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calender_group_id|string|日历的组 ID，如果您收到来自某个特定组的日历。|
|_正文参数_|
|名称|string|新日历的名称。|
 


```REST
{
    "method": "POST",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 22
    },
    "parameterDetails": [],
    "requestBody": {
        "Name": "Social"
    },
    "statusCode": 201,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLHAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLHAAA=",
        "Name": "Social",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SQ=="
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



**响应类型**

新的[日历](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)中。

****

<a name="CreateCalendarsClient"> </a>
### <a name="create-a-calendar-client"></a>创建一个日历 （客户端）

创建一个日历。 请参阅有关如何创建事件的示例[创建事件](#CreateEventsClient)。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
Calendar newCal = new Calendar
{
    Name = "Personal"
};

// Add the calendar to the Calendars collection
await client.Me.Calendars.AddCalendarAsync(newCal);

// Get the ID of the calendar
string calendarId = newCal.Id;
```

<!-- ENDSECTION -->

****


<a name="UpdateCalendars"> </a>
## <a name="update-calendars"></a>更新日历

REST API︰[更新日历 (REST)](#UpdateACalendar)

客户端库︰[更新日历 （客户端）](#UpdateCalendarsClient)

<a name="UpdateACalendar"></a>
###<a name="update-a-calendar-rest"></a>更新日历 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

更改日历的名称。 **名称**是[日历](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)的只写属性。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/calendars/{calendar_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|
|_正文参数_|
|名称|string|新日历的名称。|


**示例请求**

```
PATCH https://outlook.office.com/api/beta/me/calendars/AAMkAGE4xLIAAA=
Content-Type: application/json

{
  "Name": "Social events"
}
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLIAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw==\"",
  "Id": "AAMkAGE4xLIAAA=",
  "Name": "Social events",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|
|_正文参数_|
|名称|string|新日历的名称。|


**示例请求**

```
PATCH https://outlook.office.com/api/v2.0/me/calendars/AAMkAGE4xLIAAA=
Content-Type: application/json

{
  "Name": "Social events"
}
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Calendars/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Calendars('AAMkAGE4xLIAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw==\"",
  "Id": "AAMkAGE4xLIAAA=",
  "Name": "Social events",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|
|_正文参数_|
|名称|string|新日历的名称。|

```REST
{
    "method": "PATCH",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars/{calender_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 29
    },
    "parameterDetails": [
        {
            "name": "calender_id",
            "type": "string",
            "description": "The calendar ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA="
        }
    ],
    "requestBody": {
        "Name": "Social events"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Calendars/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/Calendars('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=",
        "Name": "Social events",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Sw=="
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->



**响应类型**

更新的[日历](..\api\complex-types-for-mail-contacts-calendar.md#CalendarResource)。

****

<a name="UpdateCalendarsClient"> </a>
### <a name="update-a-calendar-client"></a>更新日历 （客户端）

更改日历的名称。 **名称**的日历是只写属性。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)，[有的日历 ID](#GetCalendars)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar by ID
ICalendar calendarToUpdate = await client.Me.Calendars[calendarId].ExecuteAsync();
calendarToUpdate.Name = "Family";

// Commit the change
await calendarToUpdate.UpdateAsync();

// Get the updated property
string newCalendarName = calendarToUpdate.Name;
```

<!-- ENDSECTION -->


您可以定义多个更新客户端，发送请求所有次 （批它们） 通过使用以下模式︰
1. 调用`UpdateAsync(true)`为每个您想要更新的实体。 指定`true`注册客户端在本地更新但不将其发布到服务器。
2. 调用`client.Context.SaveChangesAsync()`将本地注册的所有更新。

****

<a name="DeleteCalendars"> </a>
## <a name="delete-calendars"></a>删除日历

删除的日历。

REST API︰[删除日历 (REST)](#DeleteACalendar)

客户端库︰[删除日历 （客户端）](#DeleteCalendarsClient)

<a name="DeleteACalendar"></a>
###<a name="delete-a-calendar-rest"></a>删除日历 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]



```no-highlight
DELETE https://outlook.office.com/api/beta/me/calendars/{calendar_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|


**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/calendars/AAMkAGE4xLIAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]



```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/calendars/{calendar_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|


**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/calendars/AAMkAGE4xLIAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]


```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/calendars/{calendar_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_id|string|该日历 id。|

```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendars/{calender_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendars/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calender_id",
            "type": "string",
            "description": "The calendar ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLIAAA="
        }
    ],
    "statusCode": 204

}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->




****

<a name="DeleteCalendarsClient"> </a>
### <a name="delete-a-calendar-client"></a>删除日历 （客户端）


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)，[有的日历 ID](#GetCalendars)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar by ID
ICalendar calendarToDelete = await client.Me.Calendars[calendarId].ExecuteAsync();
    
// Delete the calendar
await calendarToDelete.DeleteAsync(false);
```

<!-- ENDSECTION -->

****

<a name="GetCalendarGroups"> </a>
## <a name="get-calendar-groups"></a>获取日历组

您可以获取日历组集合或[获取日历组](#GetCalendarGroup)。


**请注意**Outlook.com 支持仅可通过访问默认日历组`../me/calendars`快捷方式。


REST API︰[获取日历组集合 (REST)](#GetCalendarGroupCollection) | [(REST) 一日历组](#GetCalendarGroup)

客户端库︰[获取日历组 （客户端）](#GetCalendarGroupsClient)


****


<a name="GetCalendarGroupCollection"> </a>
###<a name="get-a-calendar-group-collection-rest"></a>获取日历组集合 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

获取邮箱中的日历组。 


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendargroups
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

**示例请求**

```
GET https://outlook.office.com/api/beta/me/calendargroups
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
            "Id": "AAMkAGI2TGuKAAA=",
            "Name": "My Calendars",
            "ClassId": "0006f0b7-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuMAAA=')",
            "Id": "AAMkAGI2TGuMAAA=",
            "Name": "Other Calendars",
            "ClassId": "0006f0b8-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0/A=="
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendargroups
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/calendargroups
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
            "Id": "AAMkAGI2TGuKAAA=",
            "Name": "My Calendars",
            "ClassId": "0006f0b7-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuMAAA=')",
            "Id": "AAMkAGI2TGuMAAA=",
            "Name": "Other Calendars",
            "ClassId": "0006f0b8-0000-0000-c000-000000000046",
            "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0/A=="
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendargroups
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups",
        "value": [
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
                "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
                "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
                "Name": "My Calendars",
                "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
                "ClassId": "0006f0b7-0000-0000-c000-000000000046"
            },
            {
                "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuMAAA=')",
                "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0/A==\"",
                "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuMAAA=",
                "Name": "Other Calendars",
                "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0/A==",
                "ClassId": "0006f0b8-0000-0000-c000-000000000046"
            }
        ]
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


**响应类型**

请求的[日历组](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)集合中。

****


<a name="GetCalendarGroup"> </a>
###<a name="get-a-calendar-group-rest"></a>获取一个日历组 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.read_
- _wl.calendars_
- _wl.contacts\_日历_

获取日历组的 id。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
GET https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|


**示例请求**

```
GET https://outlook.office.com/api/beta/me/calendargroups/AAMkAGI2TGuKAAA=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
    "Id": "AAMkAGI2TGuKAAA=",
    "Name": "My Calendars",
    "ClassId": "0006f0b7-0000-0000-c000-000000000046",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/calendargroups/AAMkAGI2TGuKAAA=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGI2TGuKAAA=')",
    "Id": "AAMkAGI2TGuKAAA=",
    "Name": "My Calendars",
    "ClassId": "0006f0b7-0000-0000-c000-000000000046",
    "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g=="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|


```REST-i
{
    "method": "GET",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups/AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_group_id",
            "type": "string",
            "description": "The calendar group ID.",
            "defaultValue": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA="
        }
    ],
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=')",
        "@odata.etag": "W/\"nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==\"",
        "Id": "AAMkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQBGAAAAAADUuTJK1K9aTpCdqXop_4NaBwCd9nJ-tVysQos2hTfspaWRAAAAAAEGAACd9nJ-tVysQos2hTfspaWRAAADTGuKAAA=",
        "Name": "My Calendars",
        "ChangeKey": "nfZyf7VcrEKLNoU37KWlkQAAA0x0+g==",
        "ClassId": "0006f0b7-0000-0000-c000-000000000046"
    }
}

```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


**响应类型**

请求的[日历组](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)。

****

<a name="GetCalendarGroupsClient"> </a>
### <a name="get-calendar-groups-client"></a>获取日历组 （客户端）

获取用户的日历组。 若要获得其他日历组，作为**CalendarGroups**集合中的索引指定的日历组 ID，或使用**GetById**方法。

示例︰`client.Me.CalendarGroups[calendarGroupId].ExecuteAsync()`


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


**请注意**日历组集合支持**选择**、**排序**，并**执行**查询表达式。

此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IPagedCollection<ICalendarGroup> calendarGroupsResults = await client.Me.CalendarGroups.ExecuteAsync();

// Get the ID of the first calendar group
string groupId = calendarGroupsResults.CurrentPage[0].Id;
```

<!-- ENDSECTION -->

****


<a name="CreateCalendarGroups"> </a>
## <a name="create-calendar-groups"></a>创建日历组

创建一个日历组。 **名称**是一个日历组的只写属性。


**请注意**Outlook.com 支持仅可通过访问默认日历组`../me/calendars`快捷方式。 不能在 Outlook.com 中创建其他日历组。


REST API︰[创建一个日历组 (REST)](#CreateACalendarGroup)

客户端库︰[创建一个日历组 （客户端）](#CreateCalendarGroupsClient)

<a name="CreateACalendarGroup"></a>
###<a name="create-a-calendar-group-rest"></a>创建一个日历组 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_



<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
POST https://outlook.office.com/api/beta/me/calendargroups
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|_正文参数_|
|名称|string|在日历组的名称。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/calendargroups
Content-Type: application/json

{
  "Name": "Birthdays"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0M4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==\"",
  "Id": "AAMkAGE0M4xLGAAA=",
  "Name": "Birthdays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/calendargroups
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|_正文参数_|
|名称|string|在日历组的名称。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/calendargroups
Content-Type: application/json

{
  "Name": "Birthdays"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0M4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==\"",
  "Id": "AAMkAGE0M4xLGAAA=",
  "Name": "Birthdays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/calendargroups
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|_正文参数_|
|名称|string|在日历组的名称。|


```REST
{
    "method": "POST",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups",
    "requestHeaders": {
        "Accept": "application/json",
        "Content-Type": "application/json",
        "Content-Length": 23
    },
    "parameterDetails": [],
    "requestBody": {
        "Name": "Birthdays"
    },
    "statusCode": 201,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
        "Name": "Birthdays",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/Rw==",
        "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
    }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


**响应类型**

新[日历组](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)。


****

<a name="CreateCalendarGroupsClient"> </a>
### <a name="create-a-calendar-group-client"></a>创建一个日历组 （客户端）


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
CalendarGroup newCalendarGroup = new CalendarGroup
{
    Name = "Business"
};

// Add it to the CalendarGroups collection
await client.Me.CalendarGroups.AddCalendarGroupAsync(newCalendarGroup);

// Get the ID of the calendar group
string calendarGroupId = newCalendarGroup.Id;
```

<!-- ENDSECTION -->


****


<a name="UpdateCalendarGroups"> </a>
## <a name="update-calendar-groups"></a>更新日历组

REST API︰[更新日历组 (REST)](#UpdateACalendarGroup)

客户端库︰[更新日历组 （客户端）](#UpdateCalendarGroupsClient)

<a name="UpdateACalendarGroup"></a>
### <a name="update-a-calendar-group-rest"></a>更新日历组 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_

更改日历组的名称。 **名称**是唯一可写[的日历组](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)属性。


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|
|_正文参数_|
|名称|string|更新的日历组的名称。|


**示例请求**

```
PATCH https://outlook.office.com/api/beta/me/calendargroups/AAMkAGE0M4xLGAAA=
Content-Type: application/json

{
  "Name": "Holidays"
}
```

**响应示例**

```
{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0MGM4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==\"",
  "Id": "AAMkAGE0MGM4xLGAAA=",
  "Name": "Holidays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|
|_正文参数_|
|名称|string|更新的日历组的名称。|


**示例请求**

```
PATCH https://outlook.office.com/api/v2.0/me/calendargroups/AAMkAGE0M4xLGAAA=
Content-Type: application/json

{
  "Name": "Holidays"
}
```

**响应示例**

```
{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/CalendarGroups/$entity",
  "@odata.id": "https://https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/CalendarGroups('AAMkAGE0MGM4xLGAAA=')",
  "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==\"",
  "Id": "AAMkAGE0MGM4xLGAAA=",
  "Name": "Holidays",
  "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==",
  "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|
|_正文参数_|
|名称|string|更新的日历组的名称。|


```REST
 {
    "method": "PATCH",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_group_id",
            "type": "string",
            "description": "The calendar group ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA="
        }
    ],
    "requestBody": {
        "Name": "Holidays"
    },
    "statusCode": 200,
    "responseBody": {
        "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/CalendarGroups/$entity",
        "@odata.id": "https://https://outlook.office.com/api/v1.0/Users('alexd@a830edad9050849NDA1.onmicrosoft.com')/CalendarGroups('AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=')",
        "@odata.etag": "W/\"Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==\"",
        "Id": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
        "Name": "Holidays",
        "ChangeKey": "Jj9S59cHB0Wq4jXUzBgDvQAAFeN/SA==",
        "ClassId": "4d969bba-8942-42a0-ae33-c7d4410d1e11"
    }
}
```


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->

**响应类型**

更新的[日历组](..\api\complex-types-for-mail-contacts-calendar.md#CalendarGroupResource)。

****

<a name="UpdateCalendarGroupsClient"> </a>
### <a name="update-a-calendar-group-client"></a>更新日历组 （客户端）

更改日历组的名称。 **名称**是一个日历组的只写属性。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户](..\api\use-outlook-rest-api.md#GetClient)，[有的日历组 ID](#GetCalendarGroups)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar group by ID
ICalendarGroup groupToUpdate = await client.Me.CalendarGroups[groupId].ExecuteAsync();
groupToUpdate.Name = "Contoso";

// Commit the change
await groupToUpdate.UpdateAsync();

// Get the updated property
string newCalendarGroupName = groupToUpdate.Name;
```

<!-- ENDSECTION -->


您可以定义多个更新客户端，发送请求所有次 （批它们） 通过使用以下模式︰
1. 调用`UpdateAsync(true)`为每个您想要更新的实体。 指定`true`注册客户端在本地更新但不将其发布到服务器。
2. 调用`client.Context.SaveChangesAsync()`将本地注册的所有更新。


****


<a name="DeleteCalendarGroups"> </a>
## <a name="delete-calendar-groups"></a>删除日历组

删除日历组。


**请注意**Outlook.com 支持仅可通过访问默认日历组`../me/calendars`快捷方式。 不要删除此日历组。


REST API︰[删除日历组 (REST)](#DeleteACalendarGroup)

客户端库︰[删除日历组 （客户端）](#DeleteCalendarGroupsClient)

<a name="DeleteACalendarGroup"></a>
###<a name="delete-a-calendar-group-rest"></a>删除日历组 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/calendars.readwrite_
- _wl.calendars\_更新_
- _wl.events\_创建_


<!-- ============================================================================================================ -->

<!-- ==================================== Start beta content ==================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]


```no-highlight
DELETE https://outlook.office.com/api/beta/me/calendargroups/{calendar_group_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|


**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/calendargroups/AAMkAGE0MGM4xLGAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End BETA content ====================================================== -->

<!-- ============================================================================================================ -->


<!-- ============================================================================================================ -->

<!-- ==================================== Start v2 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]


```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/calendargroups/{calendar_group_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|

**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/calendargroups/AAMkAGE0MGM4xLGAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v2 content ======================================================== -->

<!-- ============================================================================================================ -->



<!-- ============================================================================================================ -->

<!-- ==================================== Start v1 content ====================================================== -->

<!-- ============================================================================================================ -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|calendar_group_id|string|日历组 id。|


```REST
{
    "method": "DELETE",
    "resourceFormat": "https://outlook.office.com/api/v1.0/me/calendargroups/{calendar_group_id}",
    "requestUrl": "https://outlook.office.com/api/v1.0/me/calendargroups/AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA=",
    "requestHeaders": {
        "Accept": "application/json"
    },
    "parameterDetails": [
        {
            "name": "calendar_group_id",
            "type": "string",
            "description": "The calendar group ID.",
            "defaultValue": "AAMkAGE0MGM1Y2M5LWEzMmUtNGVlNy05MjRlLTk0YmJjYzVkN2I5MABGAAAAAAC_0WfqSjt_SqLtNkuO-bj1BwAmP1Ln1wcHRariNdTMGAO9AAAAAAEGAAAmP1Ln1wcHRariNdTMGAO9AAAV4xLGAAA="
        }
    ],
    "statusCode": 204

}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1sectionhtml)]

<!-- ============================================================================================================ -->

<!-- ==================================== End v1 content ======================================================== -->

<!-- ============================================================================================================ -->


****

<a name="DeleteCalendarGroupsClient"> </a>
### <a name="delete-a-calendar-group-client"></a>删除日历组 （客户端）


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户](..\api\use-outlook-rest-api.md#GetClient)，[有的日历组 ID](#GetCalendarGroups)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
// Get an existing calendar group by ID
ICalendarGroup groupToDelete = await client.Me.CalendarGroups[groupId].ExecuteAsync();

// Delete the group
await groupToDelete.DeleteAsync(); 
```

<!-- ENDSECTION -->

****

<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

无论您是准备开始构建应用程序，或只是想要了解更多，我们有您的要求。


- [开始使用邮件、 日历和联系人 REST Api](http://dev.outlook.com/RestGettingStarted)。
  
- 探讨使用交互式[API 沙盒](http://apisandbox.msdn.microsoft.com/)办公室 REST Api。
    
- 需要示例？ [我们已经有了](..\howto\starter-projects-and-code-samples.md)。
    

或者，了解有关使用 Office 365 的平台︰

- [在 Outlook 开发人员中心上的 outlook REST API，](http://dev.outlook.com/RestGettingStarted/Overview)

- [在 Office 365 的平台上开发的概述](..\howto\platform-development-overview.md)
    
- [Office 365 的应用程序的身份验证和资源授权](..\howto\common-app-authentication-tasks.md)
    
- [手动注册您的应用程序 Azure 的广告，这样它可以访问 Office 365 的 Api](..\howto\add-common-consent-manually.md)
  
- [邮件发送 API 参考](..\api\mail-rest-operations.md)
  
- [联系人 API 参考](..\api\contacts-rest-operations.md)

- [任务 REST API （预览）](..\api\task-rest-operations.md)

- [OneDrive API](https://dev.onedrive.com/)

- [发现服务 REST API 操作参考](..\api\discovery-service-rest-operations.md)

- [资源引用的邮件、 日历、 联系人和任务 REST Api](..\api\complex-types-for-mail-contacts-calendar.md)



[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefilteringhtml)]

