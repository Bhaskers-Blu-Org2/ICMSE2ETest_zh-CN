# <a name="rangeformat-resource-type"></a>RangeFormat 资源类型

设置对象格式封装该范围的字体、 填充、 边框、 对齐和其他属性。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 RangeFormat](../api/rangeformat_get.md) | [RangeFormat](rangeformat.md) |读取属性和关系的 rangeFormat 对象。|
|[创建 RangeBorder](../api/rangeformat_post_borders.md) |[RangeBorder](rangeborder.md)| 由过账到边框集合中创建新的 RangeBorder。|
|[列表的边框](../api/rangeformat_list_borders.md) |[RangeBorder](rangeborder.md)集合| 获得 RangeBorder 对象集合。|
|[更新](../api/rangeformat_update.md) | [RangeFormat](rangeformat.md) |更新 RangeFormat 对象。 |
|[Autofitcolumns](../api/rangeformat_autofitcolumns.md)|无|更改当前区域，以达到最佳匹配，根据列中的当前数据列的宽度。|
|[Autofitrows](../api/rangeformat_autofitrows.md)|无|更改当前范围以实现最佳拟合，根据当前数据列中的行的高度。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|列宽|double|获取或设置范围内的所有列的宽度。 如果列宽不是统一的则将返回 null。|
|horizontalAlignment|string|代表指定对象的水平对齐方式。 Possible values are: `General`, `Left`, `Center`, `Right`, `Fill`, `Justify`, `CenterAcrossSelection`, `Distributed`.|
|rowHeight|double|获取或设置区域中所有行的高度。 如果将行高不统一将返回 null。|
|verticalAlignment|string|代表指定对象的垂直对齐方式。 可能的值为︰ `Top`， `Center`， `Bottom`， `Justify`， `Distributed`。|
|文字环绕|布尔|指示是否 Excel 会将文本包装对象中。 Null 值表示的整个区域不具有统一换行设置|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|Borders|[RangeBorder](rangeborder.md)集合|应用于所选的整个区域的边框对象集合的只读的。|
|填充。|[RangeFill](rangefill.md)|返回在整个范围内定义的填充对象。 只读的。|
|font|[RangeFont](rangefont.md)|返回 font 对象，该对象上选定的总体范围定义只读的。|
|保护|[FormatProtection](formatprotection.md)|返回某一范围的格式保护对象。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeFormat"
}-->

```json
{
  "columnWidth": 1024,
  "horizontalAlignment": "string",
  "rowHeight": 1024,
  "verticalAlignment": "string",
  "wrapText": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "RangeFormat resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->