# <a name="attachment-resource-type"></a>附件资源类型

文件、 项目 （联系人、 事件或消息） 或链接到文件，附加到的[事件](../resources/event.md)、[消息](../resources/message.md)，或[发布](../resources/post.md)。 DateTime  
对应的[fileAttachment](../resources/fileattachment.md)、 [itemAttachment](../resources/itemattachment.md)和[referenceAttachment](../resources/referenceattachment.md)资源都来自**附件**资源。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获取附件](../api/attachment_get.md) | [附件](attachment.md) |读取属性和关系的附件对象。|
|[将附件添加到事件](../api/event_post_attachments.md) | [附件](attachment.md) |项，添加一个文件，文件或链接附件事件。|
|[将附件添加到邮件](../api/message_post_attachments.md) | [附件](attachment.md) |项，添加文件，或链接到邮件中的附件。|
|[将附件添加到帖子](../api/post_post_attachments.md) | [附件](attachment.md) |项，添加文件，或链接到张贴内容的附件。|
|[列表中的附件的事件](../api/event_list_attachments.md) | [附件](attachment.md)集合 | 获取事件的附件的列表。 |
|[列表中的附件的邮件](../api/message_list_attachments.md) | [附件](attachment.md)集合 | 获取消息的附件的列表。 |
|[列表中的附件的公告](../api/post_list_attachments.md) | [附件](attachment.md)集合 | 获取列表的附件的公告。 |
|[删除](../api/attachment_delete.md) | 无 |删除的附件对象。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|contentType|String|MIME 类型。|
|id|String| 只读的。|
|isInline|Boolean|`true`如果附件是内嵌附件;否则为`false`。|
|lastModifiedDateTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|name|String|附件的显示名称。 这不必是实际的文件名。|
|size|Int32|长度 （以字节为单位的附件）。|

## <a name="relationships"></a>Relationships
无

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.attachment"
}-->

```json
{
  "contentType": "string",
  "id": "string (identifier)",
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "size": 1024
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "attachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
