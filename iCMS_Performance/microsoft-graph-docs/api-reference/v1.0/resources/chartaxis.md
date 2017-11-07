# <a name="chartaxis-resource-type"></a>ChartAxis 资源类型

代表图表中的单个坐标轴。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartAxis](../api/chartaxis_get.md) | [ChartAxis](chartaxis.md) |读取属性和关系的 chartAxis 对象。|
|[更新](../api/chartaxis_update.md) | [ChartAxis](chartaxis.md)   |更新 ChartAxis 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|majorUnit|对象|表示两个主要刻度线标记之间的时间间隔。 可以设置为数字值或空字符串。  返回的值始终是一个数字。|
|maximum|对象|表示数值轴上的最大值。  可以设置为数字值或空字符串 （用于自动轴值）。  返回的值始终是一个数字。|
|minimum|对象|表示数值轴上的最小值。 可以设置为数字值或空字符串 （用于自动轴值）。  返回的值始终是一个数字。|
|minorUnit|对象|表示两个次要刻度线标记之间的时间间隔。 "可以设置为数字值或空字符串 （用于自动轴值）。 返回的值始终是一个数字。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartAxisFormat](chartaxisformat.md)|代表图表对象，其中包括线条和字体格式的格式。 只读的。|
|majorGridlines|[ChartGridlines](chartgridlines.md)|返回一个表示指定坐标轴的主要网格线网格线对象。 只读的。|
|同时|[ChartGridlines](chartgridlines.md)|返回一个表示指定坐标轴的次要网格线网格线对象。 只读的。|
|title|[ChartAxisTitle](chartaxistitle.md)|代表的坐标轴标题。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartaxis"
}-->

```json
{
  "majorUnit": "string",
  "maximum": "string",
  "minimum": "string",
  "minorUnit": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartAxis resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->