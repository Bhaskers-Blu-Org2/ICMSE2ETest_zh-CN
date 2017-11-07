# <a name="update-event"></a>更新事件

更新事件对象的属性。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/events/<id>
PATCH /users/<id | userPrincipalName>/events/<id>
PATCH /groups/<id>/events/<id>

PATCH /me/calendar/events/<id>
PATCH /users/<id | userPrincipalName>/calendar/events/<id>
PATCH /groups/<id>/calendar/events/<id>

PATCH /me/calendars/<id>/events/<id>
PATCH /users/<id | userPrincipalName>/calendars/<id>/events/<id>

PATCH /me/calendargroup/calendars/<id>/events/<id>
PATCH /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>

PATCH /me/calendargroups/<id>/calendars/<id>/events/<id>
PATCH /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|与会者|[与会者](../resources/attendee.md)|与会者的事件的集合。|
|body|[ItemBody](../resources/itembody.md)|与该事件相关联的消息正文。|
|类别|String|与该事件关联的类别。|
|结束|[DateTimeTimeZone](../resources/datetimetimezone.md)|日期和事件结束的时间。<br/><br/>默认情况下，结束时间为 utc。 可以在 EndTimeZone 中指定可选的时区、 表达的结束时间在该时区，和包括与 utc 之间的时间偏移量。 请注意，是否您使用 EndTimeZone，您必须指定一个值为 StartTimeZone 也。<br/><br/>本示例指定于 2015 年 2 月 25 日，在太平洋标准时间下午 9:34:"2015年-02-25T21:34:00-08:00"。 |
|重要性|String|该事件的重要性︰ 低 = 0，普通 = 1、 高 = 2。 可能的值为︰ `Low`， `Normal`， `High`。|
|isAllDay|Boolean|设置为 true，如果事件持续一整天。|
|isReminderOn|Boolean|如果，设置为 true 设置警报以提醒用户的事件。|
|位置|[位置](../resources/location.md)|事件的位置。|
|重复周期|[PatternedRecurrence](../resources/patternedrecurrence.md)|事件定期 patern。|
|reminderMinutesBeforeStart|Int32|在该事件之前的分钟数开始提醒警报发生的时间。|
|responseRequested|Boolean|设置为 true，如果发件人希望接到响应事件被接受或拒绝时。|
|区分大小写|String| 可能的值为︰ `Normal`， `Personal`， `Private`， `Confidential`。|
|showAs|String|要显示的状态︰ 免费 = 0，暂定 = 1，忙 = 2，Oof = 3，WorkingElsewhere = 4，未知 =-1。 Possible values are: `Free`, `Tentative`, `Busy`, `Oof`, `WorkingElsewhere`, `Unknown`.|
|start|[DateTimeTimeZone](../resources/datetimetimezone.md)|事件的开始时间。 <br/><br/>默认情况下，开始时间为 utc。 可以在 StartTimeZone 中指定可选的时区、 表达的开始时间在该时区，和包括与 utc 之间的时间偏移量。 请注意，是否您使用 StartTimeZone，您必须指定一个值为 EndTimeZone 也。<br/><br/>本示例指定于 2015 年 2 月 25 日，在太平洋标准时间下午 7:34:"2015年-02-25T19:34:00-08:00"。  |
|主题|String|事件的主题行的文本。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[事件](../resources/event.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_event"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/events/<id>
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
  "isReminderOn": true
}
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
  "isReminderOn": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update event",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
