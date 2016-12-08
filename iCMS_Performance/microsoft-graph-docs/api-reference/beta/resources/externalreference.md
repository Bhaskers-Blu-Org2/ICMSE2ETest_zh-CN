# <a name="externalreference-resource-type"></a>externalReference 资源类型

ExternalReference 资源表示的元数据的引用 （如 URL 文件附件）。 它是[externalReferenceCollection](externalreferencecollection.md)中的属性-值对的值。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.externalReference"
}-->

```json
{
  "alias": "string",
  "lastModifiedBy": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "previewPriority": "string",
  "type": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|别名|String| 描述引用别名。 |
|lastModifiedBy|String| 只读的。 这最后一次修改的用户 id。 |
|lastModifiedDateTime|方法| 只读的。 日期和时间的这最后一次修改。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|previewPriority|String| 用来为任务预览设置该引用将显示在其中的相对优先顺序。 |
|类型|String| 用于描述该引用的类型。 类型包括︰ `PowerPoint`， `Word`， `Excel`， `Other`。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "externalReference resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->