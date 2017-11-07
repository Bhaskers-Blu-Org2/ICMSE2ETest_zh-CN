# <a name="worksheetprotection-resource-type"></a>WorksheetProtection 资源类型

表示一个工作表的保护。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 WorksheetProtection](../api/worksheetprotection_get.md) | [WorksheetProtection](worksheetprotection.md) |读取属性和关系的 worksheetProtection 对象。|
|[保护](../api/worksheetprotection_protect.md)|无|保护工作表。 如果工作表处于保护状态，则会引发。|
|[取消](../api/worksheetprotection_unprotect.md)|无|取消工作表保护|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|受保护的|布尔|如果工作表受保护的指示。  只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|选项|[WorksheetProtectionOptions](worksheetprotectionoptions.md)|工作表保护选项。 只读的。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.worksheetProtection"
}-->

```json
{
  "protected": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "WorksheetProtection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->