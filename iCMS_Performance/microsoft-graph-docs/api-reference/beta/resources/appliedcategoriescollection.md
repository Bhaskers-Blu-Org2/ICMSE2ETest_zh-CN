# <a name="appliedcategoriescollection-resource-type"></a>appliedCategoriesCollection 资源类型

AppliedCategoriesCollection * 资源表示已应用于任务的类别 （或标签） 的集合。 它是[task](task.md)对象的一部分。
最多可以有 6 应用于任务的类别。 类别名称，例如`category0`，`category1`等均[计划详细信息](plandetails.md)对象的一部分。 

* 请注意，这是开放类型。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.appliedCategoriesCollection"
}-->

```json
{
  "String-value": true
}
```

示例： 

```json
{
  "category0": true,
  "category3": true,
  "category5": true
}
```

## <a name="properties"></a>属性
开放类型的属性可以由客户端定义。 在这种情况下，客户端必须提供了`category0`， `category1`， `category3`，`category4`和/或`category5`作为属性的值在`true`布尔值的相应类别应用任务时。 上面显示了示例。 当他们不适用时，通过将其值设置为自动删除属性`false`boolean 类型的值。 

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "appliedCategoriesCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->