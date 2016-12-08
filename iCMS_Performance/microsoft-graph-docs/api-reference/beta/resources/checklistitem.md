# <a name="checklistitem-resource-type"></a>checklistItem 资源类型

ChecklistItem 资源表示任务的检查表中的项。 任务清单是由[checklistItemCollection](checklistitemcollection.md)表示。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.checklistitem"
}-->

```json
{
  "isChecked": true,
  "lastModifiedBy": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "orderHint": "string",
  "title": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|isChecked|Boolean| 值是`true`如果选中该项，则和`false`否则为。 |
|lastModifiedBy|String| 只读的。 这最后一次修改的用户 id。 |
|lastModifiedDateTime|方法| 只读的。 日期和时间的这最后一次修改。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|orderHint|String| 用来核对清单中设置项目的相对顺序。 考虑三项顺序为︰ `'O'`， `'P'`， `'Q'`。 移动`'P'`设置为检查表的顶部，其`'orderHint'`为小于的`'O'`。 比较是序号字符串比较。 |
|title|字符串| 该项目的标题。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "checklistItem resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->