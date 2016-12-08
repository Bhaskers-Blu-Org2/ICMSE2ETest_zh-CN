# <a name="charttitle-resource-type"></a>ChartTitle 资源类型

表示图表的图表标题对象。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartTitle](../api/charttitle_get.md) | [ChartTitle](charttitle.md) |读取属性和关系的 chartTitle 对象。|
|[更新](../api/charttitle_update.md) | [ChartTitle](charttitle.md)    |更新 ChartTitle 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|重叠|布尔|布尔值，表示如果图表标题将覆盖图表或不。|
|text|string|代表图表的标题文本。|
|visible|布尔|一个布尔值表示图表标题对象的可见性。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[ChartTitleFormat](charttitleformat.md)|代表图表标题，其中包括填色和字体格式的格式。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartTitle"
}-->

```json
{
  "overlay": true,
  "text": "string",
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartTitle resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->