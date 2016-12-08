# <a name="tablecolumn-resource-type"></a>TableColumn 资源类型

表示表中的列。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 TableColumn](../api/tablecolumn_get.md) | [TableColumn](tablecolumn.md) |读取属性和关系的 tableColumn 对象。|
|[更新](../api/tablecolumn_update.md) | [TableColumn](tablecolumn.md) |更新 TableColumn 对象。 |
|[Databodyrange](../api/tablecolumn_databodyrange.md)|[范围](range.md)|获取关联的列的数据体的范围对象。|
|[Headerrowrange](../api/tablecolumn_headerrowrange.md)|[范围](range.md)|获取列的标头行相关联的范围对象。|
|[范围](../api/tablecolumn_range.md)|[范围](range.md)|获取相关联的整列的范围对象。|
|[Totalrowrange](../api/tablecolumn_totalrowrange.md)|[范围](range.md)|获取关联的列的总计行的 range 对象。|
|[删除](../api/tablecolumn_delete.md)|无|从表中删除列。|
|[列表](../api/tablecolumn_list.md) | [TableColumn](tablecolumn.md)集合 |获得 tableColumn 对象集合。 |
|[Itemat](../api/tablecolumncollection_itemat.md)|[TableColumn](tablecolumn.md)|获取根据其位置在集合中的列。|
|[添加](../api/tablecolumncollection_add.md)|[TableColumn](tablecolumn.md)|向表中添加一个新列。|


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|int|返回的唯一键，在表中的列的标识号。 只读的。|
|index|int|返回表格列集合中的列的索引号。 零开始编制索引。 只读的。|
|name|string|返回表中的列的名称。 只读的。|
|values|字符串并从中获取一个对象。|表示指定范围的原始值。 返回的数据可能是类型字符串、 数字或布尔值。 包含错误的单元格将返回的错误字符串。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|filter|[筛选器](filter.md)|检索应用于列的筛选器。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.tableColumn"
}-->

```json
{
  "id": 1024,
  "index": 1024,
  "name": "string",
  "values": "json"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableColumn resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->