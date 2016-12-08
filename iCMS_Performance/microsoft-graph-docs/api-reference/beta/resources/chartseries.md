# <a name="chartseries-resource-type"></a>ChartSeries 资源类型

代表图表中的系列。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartSeries](../api/chartseries_get.md) | [ChartSeries](chartseries.md) |读取属性和关系的 chartSeries 对象。|
|[创建 ChartPoints](../api/chartseries_post_points.md) |[ChartPoints](chartpoint.md)| 由过账到点集合中创建新的 ChartPoints。|
|[列表点](../api/chartseries_list_points.md) |[ChartPoints](chartpoint.md)集合| 获得 ChartPoints 对象集合。|
|[更新](../api/chartseries_update.md) | [ChartSeries](chartseries.md) |更新 ChartSeries 对象。 |
|[列表](../api/chartseries_list.md) | [ChartSeries](chartseries.md)集合 |获得 chartSeries 对象集合。 |
|[Itemat](../api/chartseriescollection_itemat.md)|[ChartSeries](chartseries.md)|检索集合中的位置对基于一系列|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|name|string|代表图表中数据系列的名称。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartSeriesFormat](chartseriesformat.md)|代表图表系列，其中包括填充和线条格式的格式。 只读的。|
|点|[ChartPoints](chartpoint.md)集合|表示数据系列中所有点的集合。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartSeries"
}-->

```json
{
  "name": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartSeries resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->