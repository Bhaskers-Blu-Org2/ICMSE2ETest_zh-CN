# <a name="message-resource-type"></a>消息资源类型

将邮箱文件夹中的邮件。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "extensions"
  ],
  "@odata.type": "microsoft.graph.message"
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
  "conversationIndex": "binary",
  "createdDateTime": "String (timestamp)",
  "flag": {"@odata.type": "microsoft.graph.followupFlag"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "parentFolderId": "string",
  "receivedDateTime": "String (timestamp)",
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "UnsubscribeData": "string",
  "UnsubscribeEnabled": true,
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
|conversationIndex|二进制|电子邮件属于的对话的索引。|
|createdDateTime|方法|日期和时间创建了的消息。|
|标志|[followUpFlag](followupflag.md)|标志值，它指示状态、 开始日期、 截止日期或完成日期的消息。|
|from|[收件人](recipient.md)|邮箱所有者，并且该邮件的发件人。|
|hasAttachments|Boolean|指示该消息是否包含附件。|
|id|String|（请注意，此值可能会更改，即使移动或改变消息） 的消息的唯一标识符|
|重要性|String| 消息的重要性︰ `Low`， `Normal`， `High`。|
|inferenceClassification|String| 对于用户，根据推导出的相关性和重要性，或显式重写邮件的分类。 可能的值为︰ `focused`， `other`。|
|isDeliveryReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|isDraft|Boolean|指示该消息是否为草稿。 如果它尚未尚未发送，邮件是一个草稿。|
|isRead|Boolean|表示是否已阅读该邮件。|
|isReadReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|lastModifiedDateTime|方法|日期和上次更改该邮件的时间。|
|parentFolderId|String|父 mailFolder 消息的唯一标识符。|
|receivedDateTime|方法|日期和收到邮件的时间。|
|回复|[收件人](recipient.md)集合|在答复时使用的电子邮件地址。|
|发件人|[收件人](recipient.md)|实际用于生成邮件帐户。|
|sentDateTime|方法|日期和发送消息的时间。|
|主题|String|邮件的主题。|
|toRecipients|[收件人](recipient.md)集合|邮件的收件人︰ 收件人。|
|uniqueBody|[itemBody](itembody.md)|是唯一的当前邮件的邮件正文的一部分。|
|UnsubscribeData|String|从列表中取消订阅头分析有效条目。  如果 UnsubscribeEnabled 属性为 true，这是取消订阅列表的标头中的邮件命令的数据。|
|UnsubscribeEnabled|Boolean|指示该消息是否为取消订阅启用。  其 valueTrue 如果取消订阅列表的标头符合 rfc 2369。|
|网页链接|String|要在 Outlook Web App 中打开消息的 URL。<br><br>您可以更改邮件的显示方式的 URL 末尾附加 ispopout 参数。 如果 ispopout 不存在，或如果它被设置为 1，则该消息会显示在弹出窗口中。 如果 ispopout 设置为 0，则浏览器将在 Outlook Web App 审阅窗格中显示邮件。<br><br>如果您登录到您的邮箱通过 Outlook Web App，邮件将会在浏览器中打开。 系统将提示您登录如果使用浏览器您尚未登录。<br><br>在 iFrame 内，可以从访问此 URL。|

**从 Body 属性删除脚本**

消息正文可以是 HTML 或文本。 如果主体是 HTML，默认情况下，将其余部分响应中返回的正文内容之前删除 Body 属性中嵌入任何潜在的不安全 HTML (例如，JavaScript)。
若要获取整个、 原始 HTML 内容，包括以下 HTTP 请求标头︰
```
Prefer: outlook.allow-unsafe-html
```

**人和发件人设置属性**

当正在撰写邮件，在大多数情况下，发，发件人属性表示同一个已登录的用户，除非可以将更新以下方案中所述︰

- 可以更改**从**属性，如果 Exchange 管理员已分配给某些其他用户的邮箱的**SendAs**权利。 管理员可以执行此操作通过在 Azure 管理门户中，选择该邮箱所有者的**邮箱的权限**或使用 Exchange 管理员中心或 Windows PowerShell 添加 ADPermission cmdlet。 然后，您可以以编程方式**从**将属性设置为这些用户拥有该邮箱的**SendAs**权利之一。
- 如果邮箱所有者已委托一个或多个用户能够从该邮箱发送邮件，则可以更改**发件人**属性。 在 Outlook 中，可以委派邮箱所有者。 当代理发送消息代表邮箱所有者时，**发件人**属性设置到代理的帐户，并**从**属性保持作为邮箱所有者。 以编程方式，可以委托有权利对该邮箱的用户设置**发件人**属性。

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|附件|[附件](attachment.md)集合|[FileAttachment](fileattachment.md)和[itemAttachment](itemattachment.md)的邮件附件。|
|扩展|[扩展](extension.md)集合| 只读的。 可以为 null。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)集合| 多值扩展属性定义消息的集合。 只读的。 可以为 null。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md)集合| 单值扩展属性定义消息的集合。 只读的。 可以为 null。|


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取消息](../api/message_get.md) | [消息](message.md) |读取属性和消息对象的关系。|
|[创建附件](../api/message_post_attachments.md) |[附件](attachment.md)| 由过账到的附件集合中创建一个新的附件。|
|[附件列表](../api/message_list_attachments.md) |[附件](attachment.md)集合| 获取附件的对象集合。|
|[更新](../api/message_update.md) | [消息](message.md) |更新消息对象。 |
|[删除](../api/message_delete.md) | 无 |删除消息对象。 |
|[复制](../api/message_copy.md)|[消息](message.md)|将邮件复制到一个文件夹。|
|[createForward](../api/message_createforward.md)|[消息](message.md)|创建转发邮件草稿包括注释或更新都在一个**createForward**调用任何消息属性。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。|
|[createReply](../api/message_createreply.md)|[消息](message.md)|创建包含注释或更新任何消息属性中一个**createReply**调用的所有回复邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。|
|[createReplyAll](../api/message_createreplyall.md)|[消息](message.md)|创建包含注释或更新任何消息属性，都是在一次**createReplyAll**调用全部答复邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。|
|[前进](../api/message_forward.md)|无|转发邮件，添加注释或修改都在**前**一次调用任何可更新属性。 然后在已发送邮件文件夹中保存邮件。|
|[移动](../api/message_move.md)|[消息](message.md)|将邮件移动到文件夹中。 这会在目标文件夹中创建邮件的新副本。|
|[回复](../api/message_reply.md)|无|答复邮件的发件人、 添加注释或修改任何可更新一个**应答**呼叫中的所有属性。 然后在已发送邮件文件夹中保存邮件。|
|[全部答复](../api/message_replyall.md)|无|通过指定注释和所有通过使用**全部答复**方法中修改任何可更新属性的回复，回复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。|
|[发送](../api/message_send.md)|无|将以前创建的邮件草稿。 然后在已发送邮件文件夹中保存邮件。|
|[取消订阅](../api/message_unsubscribe.md)|无|发送邮件使用的数据和取消订阅列表的标头中的第一个邮寄地址命令中指定的地址。|
|[创建 openTypeExtension](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| 创建一个开放类型数据扩展，添加新的或现有的资源实例中的自定义属性。|
|[获得 openTypeExtension](../api/opentypeextension_get.md) |[openTypeExtension](opentypeextension.md)集合| 得到一个**openTypeExtension**对象或对象标识的名称或完全限定的名称。|
|[创建扩展的单值属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[消息](message.md)  |在新的或现有邮件中创建一个或多个单值扩展的属性。   |
|[得到消息的单值扩展属性](../api/singlevaluelegacyextendedproperty_get.md)  | [消息](message.md) | 收到的邮件包含扩展属性，通过使用一个单值`$expand`或`$filter`。 |
|[创建扩展属性的多值](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [消息](message.md) | 在新的或现有邮件中创建一个或多个多值扩展的属性。  |
|[获取与多值扩展属性的消息](../api/multivaluelegacyextendedproperty_get.md)  | [消息](message.md) | 收到的邮件包含多值扩展的属性通过使用`$expand`。 |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->