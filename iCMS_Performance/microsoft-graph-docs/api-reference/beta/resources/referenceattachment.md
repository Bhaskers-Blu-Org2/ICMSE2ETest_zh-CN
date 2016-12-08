# <a name="referenceattachment-resource-type"></a>referenceAttachment 资源类型

链接到文件夹或文件 （例如文本文件或 Word 文档） 在 OneDrive 上的业务云驱动器中，或其他支持的存储位置，附加到的事件、 消息或开机自检。

从[附件](attachment.md)。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 referenceAttachment](../api/referenceattachment_get.md) | [referenceAttachment](referenceattachment.md) |读取属性和关系的 referenceAttachment 对象。|
|[删除](../api/attachment_delete.md) | 无 |删除 referenceAttachment 对象。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|contentType|String|附件的内容类型。 可选项。|
|id|String|附件 id。  只读的。|
|isFolder|Boolean|指定附件是否指向文件夹的链接。 必须设置为 true，如果**sourceUrl**是指向文件夹的链接。 可选项。|
|isInline|Boolean|如果，设置为 true 附件显示为内嵌在正文中嵌入的对象。 可选项。|
|lastModifiedDateTime|方法|日期和上次修改该附件的时间。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 可选项。|
|name|String|表示嵌入的附件的图标下显示的文本。 这不必是实际的文件名。 必需。|
|权限|ReferenceAttachmentPermissions|指定的**提供程序类型**的提供程序的类型附件授予的权限。 Possible values are: `other`, `view`, `edit`, `anonymousView`, `anonymousEdit`, `organizationView`, `organizationEdit`. 可选项。|
|previewUrl|String|适用于仅图像的 URL 以获取预览图像的引用附件。 仅在**sourceUrl**标识的图像文件时，请使用**thumbnailUrl**和**previewUrl** 。 可选项。|
|提供程序类型|ReferenceAttachmentProviders|提供程序支持此 contentType 附件的类型。 可能的值为︰ `other`， `oneDriveBusiness`， `oneDriveConsumer`， `dropbox`。 可选项。|
|size|Int32|以字节为单位的附件的大小。 可选项。|
|sourceUrl|String|若要获取附件内容的 URL。 如果这是一个文件夹的 URL，然后在 Outlook 或 web 上的 Outlook 中正确显示的文件夹设置**isFolder**为 true。 必需。|
|thumbnailUrl|String|适用于仅图像的获取缩略图的图像的 URL 的引用附件。 仅在**sourceUrl**标识的图像文件时，请使用**thumbnailUrl**和**previewUrl** 。 可选项。|



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
  "isFolder": true,
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "permission": "string",
  "previewUrl": "string",
  "providerType": "string",
  "size": 1024,
  "sourceUrl": "string",
  "thumbnailUrl": "string"
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
