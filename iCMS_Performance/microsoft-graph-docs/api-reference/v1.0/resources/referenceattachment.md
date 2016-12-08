# <a name="referenceattachment-resource-type"></a>referenceAttachment 资源类型

链接到的文件 （例如文本文件或 Word 文档） 在 OneDrive 业务云驱动器或其他受支持的存储位置，附加到的事件、 消息或开机自检。

从[附件](attachment.md)。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 referenceAttachment](../api/referenceattachment_get.md) | [referenceAttachment](referenceattachment.md) |读取属性和关系的 referenceAttachment 对象。|
|[删除](../api/attachment_delete.md) | 无 |删除 referenceAttachment 对象。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|contentType|String|附件的内容类型。|
|id|String|附件 id。  只读的。|
|isInline|Boolean|如果，设置为 true 附件显示为内嵌在正文中嵌入的对象。|
|lastModifiedDateTime|方法|日期和上次修改该附件的时间。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|name|String|表示嵌入的附件的图标下显示的文本。 这不必是实际的文件名。|
|size|Int32|以字节为单位的附件的大小。|


## <a name="relationships"></a>Relationships
无



## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.referenceAttachment"
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
  "description": "referenceAttachment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
