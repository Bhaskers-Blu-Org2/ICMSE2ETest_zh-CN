# <a name="onenoteidentity-resource-type"></a>oneNoteIdentity 资源类型

**即将推出的支持**

该 OneNoteIdentity 类型表示的_用户_的标识。

在将来，这种类型将合并使用[标识](identity.md)


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.onenoteidentity"
}-->

```json
{
  "displayName": "string",
  "id": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|显示名称|string|此身份信息的显示名称。|
|id|string|标识的的唯一标识符。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "oneNoteIdentity resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
