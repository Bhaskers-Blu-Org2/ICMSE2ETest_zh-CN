# <a name="chartdatalabels-resource-type"></a>ChartDataLabels 资源类型

表示图表上的点上的所有数据标签的集合。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartDataLabels](../api/chartdatalabels_get.md) | [ChartDataLabels](chartdatalabels.md) |读取属性和关系的 chartDataLabels 对象。|
|[更新](../api/chartdatalabels_update.md) | [ChartDataLabels](chartdatalabels.md) |更新 ChartDataLabels 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|position|string|DataLabelPosition 值，该值表示数据标签的位置。 Possible values are: `None`, `Center`, `InsideEnd`, `InsideBase`, `OutsideEnd`, `Left`, `Right`, `Top`, `Bottom`, `BestFit`, `Callout`.|
|Separator|string|表示用于图表中数据标签的分隔符字符串。|
|showBubbleSize|布尔|布尔值，表示如果数据标签的气泡大小是可见的或不。|
|showCategoryName|布尔|布尔值，表示如果数据标签的类别名称，或不是可见的。|
|showLegendKey|布尔|布尔值，表示如果数据标签图例项标示是可见的或不。|
|showPercentage|布尔|布尔值，表示如果数据标签的百分比是可见的或不。|
|showSeriesName|布尔|布尔值，表示如果数据标签的系列名称，或不是可见的。|
|showValue|布尔|布尔值，表示如果数据标签的值可见。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartDataLabelFormat](chartdatalabelformat.md)|代表图表数据标签，其中包括填充和格式的字体格式。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartDataLabels"
}-->

```json
{
  "position": "string",
  "separator": "string",
  "showBubbleSize": true,
  "showCategoryName": true,
  "showLegendKey": true,
  "showPercentage": true,
  "showSeriesName": true,
  "showValue": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartDataLabels resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->