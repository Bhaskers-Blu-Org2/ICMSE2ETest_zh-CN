# <a name="itemattachment-resource-type"></a>itemAttachment 资源类型

联系人、 事件或附加到另一个事件、 消息或发布的消息。  

从[附件](attachment.md)。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 itemAttachment](../api/itemattachment_get.md) | [itemAttachment](itemattachment.md) |读取属性和关系的 itemAttachment 对象。|
|[删除](../api/attachment_delete.md) | 无 |删除 itemAttachment 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|contentType|String|附件的内容类型。|
|id|String| 附件 id。|
|isInline|Boolean|设置为 true，如果附件是内联的如在项目正文中嵌入图像。|
|lastModifiedDateTime|方法|最后一次和附件的修改日期。|
|name|String|附件的显示名称。|
|size|Int32|以字节为单位的附件的大小。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|项目|[OutlookItem](outlookitem.md)|附加的消息或事件。 导航属性。|

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "item"
  ],
  "@odata.type": "microsoft.graph.itemAttachment"
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
  "description": "itemAttachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
