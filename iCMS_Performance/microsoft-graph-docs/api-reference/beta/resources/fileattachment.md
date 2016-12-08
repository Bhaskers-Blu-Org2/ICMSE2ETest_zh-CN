# <a name="fileattachment-resource-type"></a>fileAttachment 资源类型

附加到事件、 消息或公告 （如文本文件或 Word 文档） 的文件。 **ContentBytes**属性包含 base64 编码文件的内容。  

在创建一个文件附件时，在请求正文中包括以下︰
* `"@odata.type": "#microsoft.graph.fileAttachment"`
* 必需的属性**名称**和**contentBytes**。

从[附件](attachment.md)。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 fileAttachment](../api/fileattachment_get.md) | [fileAttachment](fileattachment.md) |读取属性和关系的 fileAttachment 对象。|
|[删除](../api/attachment_delete.md) | 无 |删除 fileAttachment 对象。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|contentBytes|二进制|二进制文件的内容。|
|contentId|String|对 Exchange 存储中的附件的 ID。|
|contentLocation|String|对应于附件的内容所在位置的统一资源标识符 (URI)。|
|contentType|String|附件的内容类型。|
|id|String|附件 id。|
|isInline|Boolean|设置为 true，如果这是内嵌附件。|
|lastModifiedDateTime|方法|日期和上次修改该附件的时间。|
|name|String|表示文本表示嵌入的附件的图标下显示的名称。这不必是实际的文件名。|
|size|Int32|以字节为单位的附件的大小。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.fileAttachment"
}-->

```json
{
  "contentBytes": "binary",
  "contentId": "string",
  "contentLocation": "string",
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
  "description": "fileAttachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
