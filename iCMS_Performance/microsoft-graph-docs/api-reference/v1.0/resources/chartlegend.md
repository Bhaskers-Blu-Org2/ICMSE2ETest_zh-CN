# <a name="chartlegend-resource-type"></a>ChartLegend 资源类型

代表图表中的图例。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartLegend](../api/chartlegend_get.md) | [ChartLegend](chartlegend.md) |读取属性和关系的 chartLegend 对象。|
|[更新](../api/chartlegend_update.md) | [ChartLegend](chartlegend.md) |更新 ChartLegend 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|重叠|布尔|图表图例与图表的主体中应是否重叠的布尔值。|
|position|string|代表图表上图例的位置。 Possible values are: `Top`, `Bottom`, `Left`, `Right`, `Corner`, `Custom`.|
|visible|布尔|一个布尔值表示 ChartLegend 对象的可见性。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartLegendFormat](chartlegendformat.md)|代表图表图例中，其中包括填色和字体格式的格式。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartLegend"
}-->

```json
{
  "overlay": true,
  "position": "string",
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartLegend resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->