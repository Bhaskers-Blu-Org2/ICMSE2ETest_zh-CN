# <a name="worksheetprotectionoptions-resource-type"></a>WorksheetProtectionOptions 资源类型

代表工作表保护选项。

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|allowAutoFilter|布尔|表示工作表保护选项允许使用自动筛选功能。|
|allowDeleteColumns|布尔|表示工作表保护选项允许删除的列。|
|allowDeleteRows|布尔|表示工作表保护选项允许删除的行。|
|allowFormatCells|布尔|表示工作表保护选项允许设置单元格格式。|
|allowFormatColumns|布尔|表示允许设置列格式的工作表保护选项。|
|allowFormatRows|布尔|表示工作表保护选项允许格式的行。|
|allowInsertColumns|布尔|表示工作表保护选项允许插入列。|
|allowInsertHyperlinks|布尔|表示允许插入超链接的工作表保护选项。|
|allowInsertRows|布尔|表示工作表保护选项允许插入行。|
|allowPivotTables|布尔|表示允许使用数据透视表功能的工作表保护选项。|
|allowSort|布尔|表示工作表保护选项允许使用排序功能。|


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.worksheetProtectionOptions"
}-->

```json
{
  "allowAutoFilter": true,
  "allowDeleteColumns": true,
  "allowDeleteRows": true,
  "allowFormatCells": true,
  "allowFormatColumns": true,
  "allowFormatRows": true,
  "allowInsertColumns": true,
  "allowInsertHyperlinks": true,
  "allowInsertRows": true,
  "allowPivotTables": true,
  "allowSort": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "WorksheetProtectionOptions resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->