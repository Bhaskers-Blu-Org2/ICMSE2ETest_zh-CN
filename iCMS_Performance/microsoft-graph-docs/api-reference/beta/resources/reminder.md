# <a name="reminder-resource-type"></a>提醒的资源类型



## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|更改密钥|String|标识的版本提醒。 每次更改提醒，**那么**也将更改。 这样，可以将更改应用于该对象的正确版本的 Exchange。|
|eventEndTime|[DateTimeTimeZone](datetimetimezone.md)|日期、 时间和时区，事件结束。|
|eventId|String|事件的唯一 ID。 只读属性。|
|eventLocation|[位置](location.md)|事件的位置。|
|eventStartTime|[DateTimeTimeZone](datetimetimezone.md)|日期、 时间和时区的事件开始。|
|eventSubject|String|事件的主题行的文本。|
|eventWebLink|String|要在 web 上的 Outlook 中打开事件的 URL。<br/><br/>如果您登录到您的邮箱在 web 上的 Outlook 通过，将会在浏览器中打开事件。 系统将提示您登录如果使用浏览器您尚未登录。<br/><br/>在 iFrame 内，可以从访问此 URL。|
|reminderFireTime|[DateTimeTimeZone](datetimetimezone.md)|日期、 时间和时区设置提醒发生。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.reminder"
}-->

```json
{
  "changeKey": "string",
  "eventEndTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "eventId": "string",
  "eventLocation": {"@odata.type": "microsoft.graph.location"},
  "eventStartTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "eventSubject": "string",
  "eventWebLink": "string",
  "reminderFireTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "reminder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->