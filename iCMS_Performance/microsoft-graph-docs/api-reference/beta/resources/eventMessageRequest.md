# <a name="eventmessagerequest-resource-type"></a>eventMessageRequest 资源类型

对象表示一个会议请求消息。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "event",
    "extensions",
    "previousLocation",
    "previousStartDateTime",
    "previousEndDateTime"
  ],
  "@odata.type": "microsoft.graph.eventmessagerequest"
}-->

```json
{
  "bccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "string",
  "categories": ["string"],
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "changeKey": "string",
  "conversationId": "string",
  "createdDateTime": "String (timestamp)",
  "endDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isOutOfDate": "Boolean",
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "meetingMessageType": "microsoft.graph.meetingMessageType",
  "parentFolderId": "string",
  "previousEndDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "previousLocation": {"@odata.type": "microsoft.graph.location"},
  "previousStartDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "receivedDateTime": "String (timestamp)",
  "recurrence": {"@odata.type": "microsoft.graph.patternedrecurrence"},
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "startDateTime": {"@odata.type": "microsoft.graph.datetimetimezone"},
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "type": "string",
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|bccRecipients|[收件人](recipient.md)集合|邮件的密件抄送︰ 收件人。|
|body|[itemBody](itembody.md)|邮件的正文。|
|bodyPreview|String|邮件正文前 255 个字符。|
|类别|字符串集合|与消息关联的类别。|
|ccRecipients|[收件人](recipient.md)集合|电子邮件抄送邮件的收件人。|
|更改密钥|String|消息的版本。|
|转换 Id|String|电子邮件所属的会话的 ID。|
|createdDateTime|方法|日期和时间创建了的消息。|
|endDateTime|[DateTimeTimeZone](datetimetimezone.md)|请求的会议的结束时间。|
|from|[收件人](recipient.md)|邮箱所有者，并且该邮件的发件人。|
|hasAttachments|Boolean|指示该消息是否包含附件。|
|id|String|只读的。|
|重要性|String| 消息的重要性︰ `Low`， `Normal`， `High`。|
|inferenceClassification|String| 可能的值为︰ `Focused`， `Other`。|
|isDeliveryReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|isDraft|Boolean|指示该消息是否为草稿。 如果它尚未尚未发送，邮件是一个草稿。|
|isOutOfDate|Boolean|指示是否此会议请求已过期由较新的请求。|
|isRead|Boolean|表示是否已阅读该邮件。|
|isReadReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|lastModifiedDateTime|方法|日期和上次更改该邮件的时间。|
|位置|[位置](location.md)|请求的会议地点。|
|meetingMessageType|String| 事件消息的类型︰ `None`， `MeetingRequest`， `MeetingCancelled`， `MeetingAccepted`， `MeetingTenativelyAccepted`， `MeetingDeclined`。|
|parentFolderId|String|父 mailFolder 消息的唯一标识符。|
|previousEndDateTime|[DateTimeTimeZone](datetimetimezone.md)|以前的请求的会议的结束时间。|
|previousLocation|[位置](location.md)|请求的会议的前一位置。|
|previousStartDateTime|[DateTimeTimeZone](datetimetimezone.md)|以前的请求的会议的开始时间。|
|receivedDateTime|方法|日期和收到邮件的时间。|
|重复周期|[PatternedRecurrence](patternedrecurrence.md)|会议请求的定期模式。|
|回复|[收件人](recipient.md)集合|在答复时使用的电子邮件地址。|
|发件人|[收件人](recipient.md)|实际用于生成邮件帐户。|
|sentDateTime|方法|日期和发送消息的时间。|
|开始日期时间|[DateTimeTimeZone](datetimetimezone.md)|会议请求的开始时间。|
|主题|String|邮件的主题。|
|toRecipients|[收件人](recipient.md)集合|邮件的收件人︰ 收件人。|
|类型|String|请求的会议类型︰ `singleInstance`， `occurence`， `exception`， `seriesMaster`。|
|uniqueBody|[itemBody](itembody.md)|是唯一的当前邮件的邮件正文的一部分。|
|网页链接|String|要在 Outlook Web App 中打开消息的 URL。<br><br>您可以更改邮件的显示方式的 URL 末尾附加 ispopout 参数。 如果 ispopout 不存在，或如果它被设置为 1，则该消息会显示在弹出窗口中。 如果 ispopout 设置为 0，则浏览器将在 Outlook Web App 审阅窗格中显示邮件。<br><br>如果您登录到您的邮箱通过 Outlook Web App，邮件将会在浏览器中打开。 系统将提示您登录如果使用浏览器您尚未登录。<br><br>在 iFrame 内，可以从访问此 URL。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|附件|[附件](attachment.md)集合| 只读的。 可以为 null。|
|事件|[事件](event.md)| 事件消息相关联的事件。 与会者或空间资源的前提是日历助理被设置为自动更新与会议请求事件消息到达时事件的日历。 导航属性。  只读的。|
|扩展|[扩展](extension.md)集合| 只读的。 可以为 null。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 eventMessage](../api/eventmessage_get.md) | [eventMessage](eventmessage.md) |读取属性和关系的 eventMessage 对象。|
|[创建附件](../api/eventmessage_post_attachments.md) |[附件](attachment.md)| 由过账到的附件集合中创建一个新的附件。|
|[附件列表](../api/eventmessage_list_attachments.md) |[附件](attachment.md)集合| 获取附件的对象集合。|
|[扩展列表](../api/eventmessage_list_extensions.md) |[扩展](extension.md)集合| 获取扩展对象集合。|
|[更新](../api/eventmessage_update.md) | [eventMessage](eventmessage.md)  |更新 eventMessage 对象。 |
|[删除](../api/eventmessage_delete.md) | 无 |删除 eventMessage 对象。 |
|[复制](../api/message_copy.md)|[消息](message.md)||
|[createForward](../api/message_createforward.md)|[消息](message.md)||
|[createReply](../api/message_createreply.md)|[消息](message.md)||
|[createReplyAll](../api/message_createreplyall.md)|[消息](message.md)||
|[前进](../api/message_forward.md)|无|将邮件转发。 然后在已发送邮件文件夹中保存邮件。|
|[移动](../api/message_move.md)|[消息](message.md)|将邮件移动到 mailFolder。|
|[回复](../api/message_reply.md)|无|向邮件的发件人的回复。 然后在已发送邮件文件夹中保存邮件。|
|[全部答复](../api/message_replyall.md)|无|答复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。|
|[发送](../api/message_send.md)|无|将以前创建的邮件草稿。 然后在已发送邮件文件夹中保存邮件。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "eventMessageRequest resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->