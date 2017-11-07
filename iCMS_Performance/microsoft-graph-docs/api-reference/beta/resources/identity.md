# <a name="identity-resource-type"></a>标识资源类型

**标识**资源表示_参与者_的标识。 例如，参与者可以是用户、 设备或应用程序。

## <a name="properties"></a>属性

| 属性    | 类型   | 说明                                                                                                                                                                                                                                                                                                           |
|:------------|:-------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 显示名称 | String | 此身份信息的显示名称。 请注意，这不总是可能或最新的可用。 例如，如果用户更改了其显示名称，API 可能会在将来的响应中，显示新值，但与该用户关联的项不会显示为已更改时使用[查找更改](../api/item_delta.md) |
| id          | String | 标识的的唯一标识符。                                                                                                                                                                                                                                                                                   |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.identity"
}-->

```json
{
  "displayName": "string",
  "id": "string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "identity resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
