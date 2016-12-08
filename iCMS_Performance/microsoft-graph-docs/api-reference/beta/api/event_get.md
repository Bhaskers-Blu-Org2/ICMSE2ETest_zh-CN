# <a name="get-event"></a>获取事件

获取属性和指定的[事件](../resources/event.md)对象的关系。

对于所有 GET 操作返回的事件，您可以使用`Prefer: outlook.timezone`标头，指定时区的事件开始和结束时间在响应中。 

例如，以下`Prefer: outlook.timezone`标头设置开始和结束时间为美国东部标准时间响应中。
```http
Prefer: outlook.timezone="Eastern Standard Time"
```

如果该事件在不同的时区中创建的开始和结束时间将被调整为时间区域中，指定`Prefer`头。 请参阅此[列表](../resources/datetimetimezone.md)以供支持的次区域的名称。 如果`Prefer: outlook.timezone`不指定标头，开始和结束时间以返回 UTC。

可用于**OriginalStartTimeZone**和**OriginalEndTimeZone**属性**事件**资源上找出创建事件时所使用的时区。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.Read*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>
GET /users/<id | userPrincipalName>/events/<id>
GET /groups/<id>/events/<id>

GET /me/calendar/events/<id>
GET /users/<id | userPrincipalName>/calendar/events/<id>
GET /groups/<id>/calendar/events/<id>

GET /me/calendars/<id>/events/<id>
GET /users/<id | userPrincipalName>/calendars/<id>/events/<id>

GET /me/calendargroup/calendars/<id>/events/<id>
GET /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>

GET /me/calendargroups/<id>/calendars/<id>/events/<id>
GET /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 喜欢︰ | outlook.timezone | 在响应中的事件默认时区。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[事件](../resources/event.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_event"
}-->
```http
GET https://graph.microsoft.com/beta/me/events/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.event"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 285

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "iCalUId": "iCalUId-value",
  "reminderMinutesBeforeStart": 99,
  "isReminderOn": true,
  "start": {
    "dateTime": "datetime-value",
    "timeZone": "timezone-value"
  },
  "end": {
    "dateTime": "datetime-value",
    "timeZone": "timezone-value"
  },        
  "location": {
    "displayName": "displayName-value"
  },
  "organizer": {
    "emailAddress": {
      "address": "address-value",
      "name": "name-value"
    }
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get event",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
