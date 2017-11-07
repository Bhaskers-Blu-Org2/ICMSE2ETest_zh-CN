# <a name="sortfield-resource-type"></a>排序字段资源类型

表示在排序操作中的条件。

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|升序|布尔|表示是否排序升序的方式完成。|
|color|string|代表颜色，字体或单元格颜色排序是否是目标的条件。|
|dataOption|string|表示此字段的其他排序选项。 可能的值为︰ `Normal`， `TextAsNumber`。|
|Key|int|表示列 （或多个行，具体取决于排序方向） 上的条件。 从第一列 （或行），表示为一个偏移量。|
|sortOn|string|表示此条件的排序类型。 可能的值为︰ `Value`， `CellColor`， `FontColor`， `Icon`。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|图标|[图标](icon.md)|表示的是目标的条件，如果该单元格图标进行排序是的图标。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.sortField"
}-->

```json
{
  "ascending": true,
  "color": "string",
  "dataOption": "string",
  "key": 1024,
  "sortOn": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "SortField resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->