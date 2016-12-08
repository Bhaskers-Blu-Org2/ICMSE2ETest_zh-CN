# <a name="post-resource-type"></a>发布资源类型

表示单个 Post 项[converstaionThread](conversationthread.md)实体内。

何时创建新公告您︰

- [答复现有的张贴内容](../api/post_reply.md) 
- [答复现有的线程](../api/conversationthread_reply.md) 
- [在新对话窗口中创建线程](../api/group_post_threads.md)
- [创建一个新的会话](../api/group_post_conversations.md)
 

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "extensions",
    "inReplyTo"
  ],
  "@odata.type": "microsoft.graph.post"
}-->

```json
{
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "categories": ["string"],
  "changeKey": "string",
  "conversationId": "string",
  "conversationThreadId": "string",
  "createdDateTime": "String (timestamp)",
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "newParticipants": [{"@odata.type": "microsoft.graph.recipient"}],
  "receivedDateTime": "String (timestamp)",
  "sender": {"@odata.type": "microsoft.graph.recipient"}
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|body|[itemBody](itembody.md)|公告的内容。 这是默认属性。 此属性可能为 null。|
|类别|字符串集合|与公告关联的类别。|
|更改密钥|String|标识的张贴内容的版本。 每次更改后，更改密钥也将更改。 这样，可以将更改应用于该对象的正确版本的 Exchange。|
|转换 Id|String|对话的唯一 ID。 只读的。|
|conversationThreadId|String|会话线程的唯一 ID。 只读的。|
|createdDateTime|方法|指定当创建张贴内容。 方法类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|from|[收件人](recipient.md)|在代理方案中使用。 指示用户代表另一个用户邮件投递。 这是默认属性。|
|hasAttachments|Boolean|指示开机自检是否具有至少一个附件。 这是默认属性。|
|id|String| 只读的。|
|lastModifiedDateTime|方法|指定上次修改公告。 方法类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|newParticipants|[收件人](recipient.md)集合|作为这篇文章的一部分添加到线程的对话参与者。|
|receivedDateTime|方法|指定收到开机自检时。 方法类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|发件人|[收件人](recipient.md)|包含发件人的地址。 发件人的值假定时未指定发件人需要身份验证的用户，在这种情况中的地址。 这是默认属性。|


## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|附件|[附件](attachment.md)集合|开机自检的[fileAttachment](fileattachment.md)、 [itemAttachment](itemattachment.md)和[referenceAttachment](referenceAttachment.md)附件的集合。 只读的。 可以为 null。|
|扩展|[扩展](extension.md)集合|开放式类型数据扩展为发布定义的集合。 只读的。 可以为 null。|
|inReplyTo|[发布](post.md)|在[conversationThread](conversationthread.md)答复此帖子早开机自检。 只读的。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)集合| 多值定义为张贴内容的扩展属性的集合。 只读的。 可以为 null。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md)集合| 单值定义为张贴内容的扩展属性的集合。 只读的。 可以为 null。|


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[公告列表](../api/conversationthread_list_posts.md) | [发布](post.md) |获取指定线程的公告。 |
|[获取开机自检](../api/post_get.md) | [发布](post.md) |指定线程中获取的属性和关系的帖子。|
|[回复](../api/post_reply.md)|无|答复张贴内容，并添加新的发布到指定的线程组对话中。|
|[前进](../api/post_forward.md)|无|将帖子转发给收件人。|
|[附件列表](../api/post_list_attachments.md) |[附件](attachment.md)集合| 获取附加到发送的附件对象的列表。|
|[创建附件](../api/post_post_attachments.md) |[附件](attachment.md)| 将附件添加到帖子。 |
|[创建数据扩展插件](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| 创建一个开放类型数据扩展，添加新的或现有的资源实例中的自定义属性。|
|[获取数据扩展插件](../api/opentypeextension_get.md) |[openTypeExtension](opentypeextension.md)集合| 得到一个**openTypeExtension**对象或对象标识的名称或完全限定的名称。|
|[创建扩展的单值属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[发布](post.md)  |在新的或现有的文章创建一个或多个单值扩展的属性。   |
|[与单值扩展属性获取开机自检](../api/singlevaluelegacyextendedproperty_get.md)  | [发布](post.md) | 获取包含扩展属性，通过使用一个单值的帖子`$expand`或`$filter`。 |
|[创建扩展属性的多值](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [发布](post.md) | 在新的或现有的文章创建一个或多个多值扩展的属性。  |
|[带有扩展属性的多值获取开机自检](../api/multivaluelegacyextendedproperty_get.md)  | [发布](post.md) | 获取包含多值扩展的属性通过开机自检`$expand`。 |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "post resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->