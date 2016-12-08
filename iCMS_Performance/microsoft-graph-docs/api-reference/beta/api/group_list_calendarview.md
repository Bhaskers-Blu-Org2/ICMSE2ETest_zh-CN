# <a name="list-calendarview"></a>日历视图列表

检索事件对象的列表。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Group.Read.All*或*Group.ReadWrite.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```
## <a name="query-parameters"></a>查询参数

在请求 URL 中，将以下必需的查询参数提供值。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|开始日期时间|String|开始日期和时间的 ISO 8601 格式表示的时间范围。 例如，"2015年-11-08T19:00:00.0000000"。|
|endDateTime|String|结束日期和时间的 ISO 8601 格式表示的时间范围。 例如，"2015年-11-08T20:00:00.0000000"。|

此方法还支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 更喜欢 | string | <Time zone>. 可选，UTC 假定如果不存在。|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和[事件](../resources/event.md)响应正文中的对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_calendarview"
}-->
```http
GET https://graph.microsoft.com/beta/groups/<id>/calendarView
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
  "description": "List calendarView",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
