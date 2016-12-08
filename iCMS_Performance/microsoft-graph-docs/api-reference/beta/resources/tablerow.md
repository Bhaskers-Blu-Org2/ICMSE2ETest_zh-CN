# <a name="tablerow-resource-type"></a>TableRow 资源类型

表示表中的行。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 TableRow](../api/tablerow_get.md) | [TableRow](tablerow.md) |读取属性和关系的 tableRow 对象。|
|[更新](../api/tablerow_update.md) | [TableRow](tablerow.md)  |更新 TableRow 对象。 |
|[范围](../api/tablerow_range.md)|[范围](range.md)|返回与整行的 range 对象。|
|[删除](../api/tablerow_delete.md)|无|从表格中删除行。|
|[列表](../api/tablerow_list.md) | [TableRow](tablerow.md)集合 |获得 tableRow 对象集合。 |
|[Itemat](../api/tablerowcollection_itemat.md)|[TableRow](tablerow.md)|获取行根据其在集合中的位置。|
|[添加](../api/tablerowcollection_add.md)|[TableRow](tablerow.md)|向表中添加一个新行。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|index|int|返回表的行集中的行的索引号。 零开始编制索引。 只读的。|
|values|字符串并从中获取一个对象。|表示指定范围的原始值。 返回的数据可能是类型字符串、 数字或布尔值。 包含错误的单元格将返回的错误字符串。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tableRow"
}-->

```json
{
  "index": 1024,
  "values": "json"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableRow resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->