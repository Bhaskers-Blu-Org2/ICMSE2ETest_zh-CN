# <a name="nameditem-resource-type"></a>NamedItem 资源类型

代表单元格区域或值的定义的名称。 名称可以是基元 （如下面的类型中所示） 命名的对象、 范围对象，对区域的引用。 此对象可用于获取与名称相关联的 range 对象。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 NamedItem](../api/nameditem_get.md) | [NamedItem](nameditem.md) |读取属性和关系的 namedItem 对象。|
|[更新](../api/nameditem_update.md) | [NamedItem](nameditem.md)   |更新 NamedItem 对象。 |
|[范围](../api/nameditem_range.md)|[范围](range.md)|返回 range 对象，该对象与该名称相关联。 如果已命名的项的类型不是一系列，则引发异常。|
|[列表](../api/nameditem_list.md) | [NamedItem](nameditem.md)集合 |获得 namedItem 对象集合。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|name|string|对象的名称。 只读的。|
|类型|string|表示什么类型的引用名称相关联。 可能的值为︰ `String`， `Integer`， `Double`， `Boolean`， `Range`。 只读的。|
|value|object|表示到定义名称的公式引用。 例如 = Sheet14 ！ $B$ 2: $H 美元 12 = 4.75，等等。只读的。|
|visible|布尔|指定对象是否可见。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.namedItem"
}-->

```json
{
  "name": "string",
  "type": "string",
  "value": {"@odata.type": "microsoft.graph.range"},
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "NamedItem resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->