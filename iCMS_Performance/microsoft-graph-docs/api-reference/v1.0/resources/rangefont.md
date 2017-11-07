# <a name="rangefont-resource-type"></a>RangeFont 资源类型

此对象表示的对象的字体属性 （字体名称、 字体大小、 颜色等）。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 RangeFont](../api/rangefont_get.md) | [RangeFont](rangefont.md) |读取属性和关系的 rangeFont 对象。|
|[更新](../api/rangefont_update.md) | [RangeFont](rangefont.md)   |更新 RangeFont 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|bold|布尔|表示字体的加粗的状态。|
|color|string|文本颜色的 HTML 颜色代码表示。 例如 #FF0000 表示红色。|
|italic|布尔|表示字体的倾斜状态。|
|name|字符串|字体名称 （例如"宋体")|
|“大小”|double|字体大小。|
|underline|string|应用于字体的下划线类型。 可能的值为︰ `None`， `Single`， `Double`， `SingleAccountant`， `DoubleAccountant`。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rangeFont"
}-->

```json
{
  "bold": true,
  "color": "string",
  "italic": true,
  "name": "string",
  "size": 1024,
  "underline": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "RangeFont resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->