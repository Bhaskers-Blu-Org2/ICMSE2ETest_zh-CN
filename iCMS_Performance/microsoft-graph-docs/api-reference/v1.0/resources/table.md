# <a name="table-resource-type"></a>资源类型一个表

表示一个 Excel 表。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取表](../api/table_get.md) | [表](table.md) |读取属性和关系的表对象。|
|[创建 TableColumn](../api/table_post_columns.md) |[TableColumn](tablecolumn.md)| 由过账到列集合中创建新的 TableColumn。|
|[列表列](../api/table_list_columns.md) |[TableColumn](tablecolumn.md)集合| 获得 TableColumn 对象集合。|
|[创建 TableRow](../api/table_post_rows.md) |[TableRow](tablerow.md)| 由过账到行集合中创建新的 TableRow。|
|[列表行数](../api/table_list_rows.md) |[TableRow](tablerow.md)集合| 获得 TableRow 对象集合。|
|[更新](../api/table_update.md) | [表](table.md)   |更新表对象。 |
|[Databodyrange](../api/table_databodyrange.md)|[范围](range.md)|获取关联的表的数据体的范围对象。|
|[Headerrowrange](../api/table_headerrowrange.md)|[范围](range.md)|获取关联的表的标题行的 range 对象。|
|[范围](../api/table_range.md)|[范围](range.md)|获取整个表与相关的 range 对象。|
|[Totalrowrange](../api/table_totalrowrange.md)|[范围](range.md)|获取与表中的汇总行的 range 对象。|
|[Clearfilters](../api/table_clearfilters.md)|无|清除当前的表上应用的所有筛选器。|
|[Converttorange](../api/table_converttorange.md)|[范围](range.md)|将表转换为普通单元格区域。 所有数据将被都保留。|
|[删除](../api/table_delete.md)|无|删除表。|
|[Reapplyfilters](../api/table_reapplyfilters.md)|无|重新应用当前表中的所有筛选器。|
|[列表](../api/table_list.md) | [表](table.md)集合 |获取表的对象集合。 |
|[添加](../api/tablecollection_add.md)|[表](table.md)|创建一个新表。 区域的源地址确定将在其下添加表的工作表。 如果无法将该表添加 （例如，因为地址无效，或与另一个表，表将与重叠），则将引发错误。|



## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|int|返回一个值，用于唯一标识给定工作簿中的表。 即使表被重命名标识符的值保持不变。 只读的。|
|name|string|表的名称。|
|showHeaders|布尔|表示标题行是否可见。 可以设置此值以显示或删除标题行。|
|showTotals|布尔|指示是否显示汇总行。 可以设置此值以显示或删除汇总行。|
|style|string|常量的值，该值表示表格样式。 可能的值为︰ TableStyleLight1-TableStyleLight21，TableStyleMedium1-TableStyleMedium28，TableStyleStyleDark1 至 TableStyleStyleDark11。 也可以指定自定义用户定义的样式的工作簿中存在。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|columns|[TableColumn](tablecolumn.md)集合|表示表中的所有列的集合。 只读的。|
|rows|[TableRow](tablerow.md)集合|表示表中的所有行的集合。 只读的。|
|排序|[单列排序](tablesort.md)|表示对表进行排序。 只读的。|
|worksheet|[工作表](worksheet.md)|包含当前表的工作表。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.table"
}-->

```json
{
  "id": 1024,
  "name": "string",
  "showHeaders": true,
  "showTotals": true,
  "style": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Table resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->