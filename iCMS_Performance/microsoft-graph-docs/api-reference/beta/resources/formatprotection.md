# <a name="formatprotection-resource-type"></a>FormatProtection 资源类型

表示格式保护的 range 对象。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 FormatProtection](../api/formatprotection_get.md) | [FormatProtection](formatprotection.md) |读取属性和关系的 formatProtection 对象。|
|[更新](../api/formatprotection_update.md) | [FormatProtection](formatprotection.md)  |更新 FormatProtection 对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|formulaHidden|布尔|指示是否 Excel 隐藏区域中的单元格的公式。 Null 值表示的整个区域不具有统一公式隐藏的设置。|
|锁定|布尔|指示是否 Excel 锁定的对象中的单元格。 Null 值表示的整个区域不具有统一的锁定设置。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.formatProtection"
}-->

```json
{
  "formulaHidden": true,
  "locked": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "FormatProtection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->