# <a name="rangeborder-resource-type"></a>RangeBorder 资源类型

代表对象的边框。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 RangeBorder](../api/rangeborder_get.md) | [RangeBorder](rangeborder.md) |读取属性和关系的 rangeBorder 对象。|
|[更新](../api/rangeborder_update.md) | [RangeBorder](rangeborder.md) |更新 RangeBorder 对象。 |
|[列表](../api/rangeborder_list.md) | [RangeBorder](rangeborder.md)集合 |获得 rangeBorder 对象集合。 |
|[Itemat](../api/rangebordercollection_itemat.md)|[RangeBorder](rangeborder.md)|获取一个 border 对象，该对象使用的索引|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|color|string|表示颜色的边框线，#RRGGBB 的窗体 (例如"FFA500") 或已命名的 HTML 颜色 （如"橙色"） 作为 HTML 颜色代码。|
|id|string|表示边框标识符。 Possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. 只读的。|
|sideIndex|string|常量值，该值指示指定侧边框。 Possible values are: `EdgeTop`, `EdgeBottom`, `EdgeLeft`, `EdgeRight`, `InsideVertical`, `InsideHorizontal`, `DiagonalDown`, `DiagonalUp`. 只读的。|
|style|string|一个指定线条样式的边框的线条样式的常量。 Possible values are: `None`, `Continuous`, `Dash`, `DashDot`, `DashDotDot`, `Dot`, `Double`, `SlantDashDot`.|
|weight|string|指定区域周围的边框的粗细。 可能的值为︰ `Hairline`， `Thin`， `Medium`， `Thick`。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeBorder"
}-->

```json
{
  "color": "string",
  "id": "string",
  "sideIndex": "string",
  "style": "string",
  "weight": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "RangeBorder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->