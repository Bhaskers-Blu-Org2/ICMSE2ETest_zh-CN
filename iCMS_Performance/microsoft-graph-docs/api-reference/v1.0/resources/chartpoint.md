# <a name="chartpoint-resource-type"></a>ChartPoint 资源类型

代表图表中系列的点。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartPoint](../api/chartpoint_get.md) | [ChartPoint](chartpoint.md) |读取属性和关系的 chartPoint 对象。|
|[列表](../api/chartpoint_list.md) | [ChartPoint](chartpoint.md)集合 |获得 chartPoint 对象集合。 |
|[Itemat](../api/chartpointscollection_itemat.md)|[ChartPoint](chartpoint.md)|检索基于它在序列中位置的点。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|value|object|返回图表点的值。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartPointFormat](chartpointformat.md)|封装格式属性图表点。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartPoint"
}-->

```json
{
  "value": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartPoint resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->