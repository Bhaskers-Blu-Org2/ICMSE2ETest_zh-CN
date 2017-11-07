# <a name="range-resource-type"></a>区域资源类型

范围表示一组一个或多个相邻单元格的单元格、 行、 列，块单元格等。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取范围](../api/range_get.md) | [范围](range.md) |读取属性和关系的 range 对象。|
|[更新](../api/range_update.md) | [范围](range.md)   |更新范围对象。 |
|[Boundingrect](../api/range_boundingrect.md)|[范围](range.md)|获取最小的 range 对象，该对象包含给定的范围。 例如，"B2:C5"和"D10:E15"GetBoundingRect 是"B2:E16"。|
|[单元格](../api/range_cell.md)|[范围](range.md)|获取包含行号和列标上基于单个单元格的 range 对象。 该单元格可以超出其父范围的界限，只要是在表中的网格内的保持。 返回单元格的位置相对于该区域左上角单元格。|
|[列](../api/range_column.md)|[范围](range.md)|获取区域中包含的列。|
|[Entirecolumn](../api/range_entirecolumn.md)|[范围](range.md)|获取一个对象，表示区域的整个列。|
|[Entirerow](../api/range_entirerow.md)|[范围](range.md)|获取一个对象，表示区域的整行。|
|[交集](../api/range_intersection.md)|[范围](range.md)|获取表示指定范围的矩形交集的 range 对象。|
|[Lastcell](../api/range_lastcell.md)|[范围](range.md)|获取范围内的最后一个单元格。 例如，"B2:D5"的最后一个单元是"D5"。|
|[Lastcolumn](../api/range_lastcolumn.md)|[范围](range.md)|获取此范围的最后一列。 例如，"B2:D5"的最后一列是"D2:D5"。|
|[Lastrow](../api/range_lastrow.md)|[范围](range.md)|获取范围中的最后一行。 例如，"B2:D5"的最后一行是"B5:D5"。|
|[Offsetrange](../api/range_offsetrange.md)|[范围](range.md)|获取对象，该对象表示来自指定范围的偏移量范围。 返回的文本区域的尺寸将与该范围匹配。 如果表中的网格的边界之外强制生成的范围，则将引发异常。|
|[一行](../api/range_row.md)|[范围](range.md)|获取区域中包含的行。|
|[Usedrange](../api/range_usedrange.md)|[范围](range.md)|返回给定范围内对象的使用的范围。|
|[清除](../api/range_clear.md)|无|明确范围值、 格式、 填充、 边框等。|
|[删除](../api/range_delete.md)|无|删除与该范围关联的单元格。|
|[插入](../api/range_insert.md)|[范围](range.md)|代替这一范围，在工作表中插入单元格区域，并将其他单元格以腾出空间。 返回新的 Range 对象，该对象在现在的空白。|
|[合并](../api/range_merge.md)|无|将单元格区域合并到工作表中的一个区域。|
|[取消合并](../api/range_unmerge.md)|无|为单个单元格取消合并单元格区域。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|address|string|表示以 A1 样式范围引用。 地址值将包含工作表引用 (如工作表 Sheet1 ！A1: B4)。 只读的。|
|addressLocal|string|表示用户的语言中的指定范围的单元格区域引用。 只读的。|
|cellCount|int|区域中的单元格数目。 只读的。|
|列数|int|表示范围中的列的总数。 只读的。|
|隐藏列|布尔|表示如果当前范围中的所有列都隐藏的。|
|列索引|int|表示范围中的第一个单元格的列号。 零开始编制索引。 只读的。|
|formulas|字符串并从中获取一个对象。|表示以 A1 样式表示法表示的公式。|
|formulasLocal|字符串并从中获取一个对象。|代表公式以 A1 样式表示法，以用户的语言和数字格式的区域设置。  例如，英语"= SUM (A1，1.5)"的公式将变为"= SUMME(A1;1.5)"在德语中。|
|formulasR1C1|字符串并从中获取一个对象。|表示以 R1C1 样式表示法表示的公式。|
|hidden|布尔|表示如果所有单元格的当前区域处于隐藏状态。 只读的。|
|numberFormat|字符串并从中获取一个对象。|表示 Excel 的给定单元格的数字格式代码。|
|行计数|int|返回区域中的行的总数。 只读的。|
|rowHidden|布尔|表示如果当前范围内的所有行都被都隐藏。|
|rowIndex|int|返回区域中的第一个单元格的行号。 零开始编制索引。 只读的。|
|text|字符串并从中获取一个对象。|指定范围中的文本值。 该文本值将不取决于单元格的宽度。 发生在 Excel 用户界面中 # 符号替换不会影响由 API 返回的文本值。 只读的。|
|值|string|表示每个单元格的数据的类型。 Possible values are: `Unknown`, `Empty`, `String`, `Integer`, `Double`, `Boolean`, `Error`. 只读的。|
|values|字符串并从中获取一个对象。|表示指定范围的原始值。 返回的数据可能是类型字符串、 数字或布尔值。 包含错误的单元格将返回的错误字符串。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|格式|[RangeFormat](rangeformat.md)|返回一个格式对象，封装该范围的字体、 填充、 边框、 对齐和其他属性。 只读的。|
|排序|[RangeSort](rangesort.md)|包含当前范围的工作表。 只读的。|
|worksheet|[工作表](worksheet.md)|包含当前范围的工作表。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.range"
}-->

```json
{
  "address": "string",
  "addressLocal": "string",
  "cellCount": 1024,
  "columnCount": 1024,
  "columnHidden": true,
  "columnIndex": 1024,
  "formulas": "json",
  "formulasLocal": "json",
  "formulasR1C1": "json",
  "hidden": true,
  "numberFormat": "json",
  "rowCount": 1024,
  "rowHidden": true,
  "rowIndex": 1024,
  "text": "json",
  "valueTypes": "string",
  "values": "json"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Range resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->