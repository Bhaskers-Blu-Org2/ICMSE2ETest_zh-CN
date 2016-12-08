# <a name="chartaxistitle-resource-type"></a>ChartAxisTitle 资源类型

代表图表坐标轴的标题。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartAxisTitle](../api/chartaxistitle_get.md) | [ChartAxisTitle](chartaxistitle.md) |读取属性和关系的 chartAxisTitle 对象。|
|[更新](../api/chartaxistitle_update.md) | [ChartAxisTitle](chartaxistitle.md)    |更新 ChartAxisTitle 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|text|string|代表的坐标轴标题。|
|visible|布尔|一个布尔值，指定坐标轴标题的可见性。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartAxisTitleFormat](chartaxistitleformat.md)|代表图表坐标轴标题的格式。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartAxisTitle"
}-->

```json
{
  "text": "string",
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartAxisTitle resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->