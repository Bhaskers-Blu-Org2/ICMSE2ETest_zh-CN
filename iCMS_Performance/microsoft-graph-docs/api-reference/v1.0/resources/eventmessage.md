# <a name="eventmessage-resource-type"></a>eventMessage 资源类型

一条消息，表示会议请求，会议取消的消息、 会议接受消息、 会议暂定接受消息，或拒绝消息的会议。

EventMessage 通常在其中为结果创建会议或者活动的组织者或与会者响应会议请求到达时的收件箱文件夹中找到。 事件消息作用则作用于邮件中，存在一些细微的差别，如下表中所述的方式相同。


## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 eventMessage](../api/eventmessage_get.md) | [eventMessage](eventmessage.md) |读取属性和关系的 eventMessage 对象。|
|[附件列表](../api/message_list_attachments.md) |[附件](attachment.md)集合| 获取附件的对象集合。|
|[更新](../api/eventmessage_update.md) | [eventMessage](eventmessage.md)  |更新 eventMessage 对象。 |
|[删除](../api/message_delete.md) | 无 |删除 eventMessage 对象。 |
|[复制](../api/message_copy.md)|[消息](message.md)|将邮件复制到一个文件夹。|
|[createForward](../api/message_createforward.md)|[消息](message.md)|创建转发邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。|
|[createReply](../api/message_createreply.md)|[消息](message.md)|创建答复邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。|
|[createReplyAll](../api/message_createreplyall.md)|[消息](message.md)|创建全部答复邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。|
|[前进](../api/message_forward.md)|无|转发邮件。 然后在已发送邮件文件夹中保存邮件。|
|[移动](../api/message_move.md)|[消息](message.md)|将邮件移动到文件夹中。 这会在目标文件夹中创建邮件的新副本。|
|[回复](../api/message_reply.md)|无|答复邮件的发件人。 然后在已发送邮件文件夹中保存邮件。|
|[全部答复](../api/message_replyall.md)|无|答复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。|
|[发送](../api/message_send.md)|无|将以前创建的邮件草稿。 然后在已发送邮件文件夹中保存邮件。|
|[创建数据扩展插件](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| 创建一个开放类型数据扩展，添加新的或现有的资源实例中的自定义属性。|
|[获取数据扩展插件](../api/opentypeextension_get.md) |[openTypeExtension](opentypeextension.md)集合| 得到一个**openTypeExtension**对象或对象标识的名称或完全限定的名称。|


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
|from|[收件人](recipient.md)|邮箱所有者，并且该邮件的发件人。|
|hasAttachments|Boolean|指示该消息是否包含附件。|
|id|String||
|重要性|String| 消息的重要性︰ `Low`， `Normal`， `High`。|
|internetMessageId |String |由[RFC2822](http://www.ietf.org/rfc/rfc2822.txt)指定格式的消息 ID。 |
|isDeliveryReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|isDraft|Boolean|指示该消息是否为草稿。 如果它尚未尚未发送，邮件是一个草稿。|
|isRead|Boolean|表示是否已阅读该邮件。|
|isReadReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|lastModifiedDateTime|方法|日期和上次更改该邮件的时间。|
|meetingMessageType|String| 事件消息的类型︰ `None`， `MeetingRequest`， `MeetingCancelled`， `MeetingAccepted`， `MeetingTenativelyAccepted`， `MeetingDeclined`。|
|parentFolderId|String|父 mailFolder 消息的唯一标识符。|
|receivedDateTime|方法|日期和收到邮件的时间。|
|回复|[收件人](recipient.md)集合|在答复时使用的电子邮件地址。|
|发件人|[收件人](recipient.md)|实际用于生成邮件帐户。|
|sentDateTime|方法|日期和发送消息的时间。|
|主题|String|邮件的主题。|
|toRecipients|[收件人](recipient.md)集合|邮件的收件人︰ 收件人。|
|uniqueBody|[itemBody](itembody.md)|是唯一的当前邮件的邮件正文的一部分。|
|网页链接|String|要在 Outlook Web App 中打开消息的 URL。<br><br>您可以更改邮件的显示方式的 URL 末尾附加 ispopout 参数。 如果 ispopout 不存在，或如果它被设置为 1，则该消息会显示在弹出窗口中。 如果 ispopout 设置为 0，则浏览器将在 Outlook Web App 审阅窗格中显示邮件。<br><br>如果您登录到您的邮箱通过 Outlook Web App，邮件将会在浏览器中打开。 系统将提示您登录如果使用浏览器您尚未登录。<br><br>在 iFrame 内，可以从访问此 URL。|


## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|附件|[附件](attachment.md)集合| 只读的。 可以为 null。|
|事件|[事件](event.md)| 事件消息相关联的事件。 与会者或空间资源的前提是日历助理被设置为自动更新与会议请求事件消息到达时事件的日历。 导航属性。  只读的。|
|扩展|[扩展](extension.md)集合|开放式类型数据扩展插件定义联系人的集合。 只读的。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源  

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "event"
  ],
  "@odata.type": "microsoft.graph.eventmessage"
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
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "internetMessageId": "String",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "meetingMessageType": "String",
  "parentFolderId": "string",
  "receivedDateTime": "String (timestamp)",
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "eventMessage resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
