# <a name="user-reminderview"></a>用户︰ reminderView
返回的列表中指定的开始时间和结束时间的日历提醒。 

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.Read;Calendars.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /users/<id | userPrincipalName>/reminderView(startDateTime=startDateTime-value,endDateTime=endDateTime-value)
```

## <a name="function-parameters"></a>函数参数
在请求 URL 中，将以下函数参数提供值。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|开始日期时间|String|开始日期和事件的提醒设置的时间。 例如，在 ISO 8601 格式表示的值"2015年-11-08T19:00:00.0000000"。|
|endDateTime|String|结束日期和事件的提醒设置的时间。 例如，在 ISO 8601 格式表示的值"2015年-11-08T20:00:00.0000000"。|


## <a name="request-headers"></a>请求标头
| 页眉       | 值|
|:-----------|:------|
| 授权  | 持有者<token>。 必需。  |
| 更喜欢 | < 时区 >。 可选，UTC 假定如果不存在。| 

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`在响应正文中的响应代码和[提醒](../resources/reminder.md)集合的对象。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "user_reminderview"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/reminderView(startDateTime=startDateTime-value,endDateTime=endDateTime-value)
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.reminder",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 673

{
  "value": [
    {
      "eventId": "eventId-value",
      "eventStartTime": {
        "dateTime": "dateTime-value",
        "timeZone": "timeZone-value"
      },
      "eventEndTime": {
        "dateTime": "dateTime-value",
        "timeZone": "timeZone-value"
      },
      "changeKey": "changeKey-value",
      "eventSubject": "eventSubject-value",
      "eventLocation": {
        "displayName": "displayName-value",
        "address": {
          "street": "street-value",
          "city": "city-value",
          "state": "state-value",
          "countryOrRegion": "countryOrRegion-value",
          "postalCode": "postalCode-value"
        }
      }
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user: reminderView",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
