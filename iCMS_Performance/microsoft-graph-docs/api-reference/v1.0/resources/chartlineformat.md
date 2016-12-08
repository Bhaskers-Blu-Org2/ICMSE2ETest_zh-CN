# <a name="chartlineformat-resource-type"></a>ChartLineFormat 资源类型

Enapsulates 的直线元素的格式设置选项。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 ChartLineFormat](../api/chartlineformat_get.md) | [ChartLineFormat](chartlineformat.md) |读取属性和关系的 chartLineFormat 对象。|
|[更新](../api/chartlineformat_update.md) | [ChartLineFormat](chartlineformat.md) |更新 ChartLineFormat 对象。 |
|[清除](../api/chartlineformat_clear.md)|无|清除图表元素的格式。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|color|string|代表图表中的线条的颜色的 HTML 颜色代码。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.chartLineFormat"
}-->

```json
{
  "color": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartLineFormat resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->