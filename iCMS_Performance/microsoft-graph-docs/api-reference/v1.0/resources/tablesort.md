# <a name="tablesort-resource-type"></a>单列排序资源类型

管理表对象的排序操作。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取单列排序](../api/tablesort_get.md) | [单列排序](tablesort.md) |读取属性和关系的单列排序对象。|
|[应用](../api/tablesort_apply.md)|无|执行排序操作。|
|[清除](../api/tablesort_clear.md)|无|清除表上的当前排序。 尽管这不能修改表的排序，它会清除标题按钮的状态。|
|[重新应用](../api/tablesort_reapply.md)|无|对表重新应用当前的排序参数。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|matchCase|布尔|表示是否大小写受影响表的最后一次排序。 只读的。|
|方法|string|表示中文字符排序上次用来对表进行排序的方法。 可能的值为︰ `PinYin`， `StrokeCount`。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|字段|[排序字段](sortfield.md)|表示当前使用最后一次对表进行排序的条件。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tableSort"
}-->

```json
{
  "matchCase": true,
  "method": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableSort resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->