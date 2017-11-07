# <a name="notesoperationerror-resource-type"></a>notesOperationError 资源类型

从 OneNote 操作失败时出错。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.notesoperationerror"
}-->

```json
{
  "code": "string",
  "message": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|code|string|错误代码。|
|消息|string|错误消息中。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notesOperationError resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->