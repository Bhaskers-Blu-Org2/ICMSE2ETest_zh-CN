# <a name="worksheet-resource-type"></a>工作表中的资源类型

Excel 工作表时单元格组成的网格。 它可以包含数据、 表格、 图表等。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取工作表](../api/worksheet_get.md) | [工作表](worksheet.md) |读取属性和关系的工作表对象。|
|[创建图表](../api/worksheet_post_charts.md) |[图表](chart.md)| 由过账到图表集合中创建新图表。|
|[列表的图表](../api/worksheet_list_charts.md) |[图表](chart.md)集合| 获取图表对象集合。|
|[创建表](../api/worksheet_post_tables.md) |[表](table.md)| 由过账到 tables 集合中创建新表。|
|[列表中的表](../api/worksheet_list_tables.md) |[表](table.md)集合| 获取表的对象集合。|
|[更新](../api/worksheet_update.md) | [工作表](worksheet.md)   |更新工作表对象。 |
|[单元格](../api/worksheet_cell.md)|[范围](range.md)|获取包含行号和列标上基于单个单元格的 range 对象。 该单元格可以超出其父范围的界限，只要是在表中的网格内的保持。|
|[范围](../api/worksheet_range.md)|[范围](range.md)|获取指定的地址或名称的 range 对象。|
|[Usedrange](../api/worksheet_usedrange.md)|[范围](range.md)|使用的范围包括任何值的单元格的最小范围或格式分配给他们。 如果工作表为空，此函数将返回左上角的单元格。|
|[删除](../api/worksheet_delete.md)|无|从工作簿中删除工作表。|
|[列表](../api/worksheet_list.md) | [工作表](worksheet.md)集合 |获取工作表对象集合。 |
|[添加](../api/worksheetcollection_add.md)|[工作表](worksheet.md)|向工作簿添加新工作表。 将在现有工作表的末尾添加工作表。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|string|返回一个值，用于唯一标识给定工作簿中的工作表。 即使在工作表被重命名或移动的标识符的值保持不变。 只读的。|
|name|string|工作表的显示名称。|
|position|int|工作簿中工作表的位置从零开始。|
|visibility|string|工作表的可见性。 可能的值为︰ `Visible`， `Hidden`， `VeryHidden`。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|charts|[图表](chart.md)集合|返回图表工作表的一部分的集合。 只读的。|
|保护|[WorksheetProtection](worksheetprotection.md)|返回表工作表的保护的对象。 只读的。|
|tables|[表](table.md)集合|工作表的一部分的表的集合。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.worksheet"
}-->

```json
{
  "id": "string",
  "name": "string",
  "position": 1024,
  "visibility": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Worksheet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->