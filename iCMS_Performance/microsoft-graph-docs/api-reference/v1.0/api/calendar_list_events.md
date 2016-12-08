# <a name="list-events"></a>事件列表

检索日历中的事件的列表。  该列表包含单个实例会议和系列的主控形状。

获取扩展的事件实例，您可以[获得日历视图](calendar_list_calendarview.md)，或[获得的事件实例](event_list_instances.md)。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.Read*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
用户或组的默认[日历](../resources/calendar.md)。
```http
GET /me/calendar/events
GET /users/<id | userPrincipalName>/calendar/events
GET /groups/<id>/calendar/events
```
[日历](../resources/calendar.md)的用户的默认值[calendarGroup](../resources/calendargroup.md)。
```http
GET /me/calendars/<id>/events
GET /users/<id | userPrincipalName>/calendars/<id>/events

GET /me/calendarGroup/calendars/<id>/events
GET /users/<id | userPrincipalName>/calendarGroup/calendars/<id>/events
```
在特定的[calendarGroup](../resources/calendargroup.md)的用户的[日历](../resources/calendar.md)。
```http
GET /me/calendarGroups/<id>/calendars/<id>/events
GET /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>/events
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 更喜欢  | outlook.timezone="Eastern 标准时间"。 可选项。 使用此选项来指定时区的时间响应中的开始和结束时间。 如果未指定，以 UTC 返回响应。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和[事件](../resources/event.md)响应正文中的对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_events"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/calendar/events
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.event",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 354

{
  "value": [
    {
      "originalStartTimeZone": "originalStartTimeZone-value",
      "originalEndTimeZone": "originalEndTimeZone-value",
      "responseStatus": {
        "response": "",
        "time": "datetime-value"
      },
      "iCalUId": "iCalUId-value",
      "reminderMinutesBeforeStart": 99,
      "isReminderOn": true
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List events",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
