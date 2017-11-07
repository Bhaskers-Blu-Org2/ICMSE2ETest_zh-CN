# <a name="useridcollection-resource-type"></a>userIdCollection 资源类型

UserIdCollection * 资源表示的一个[计划](plan.md)与共享的用户 id 的列表。 如果您将充分利用 Office 365 组，使用组 API 管理组成员共享[组的](group.md)计划。 但不是必需为其访问组拥有的计划，还可以向此集合添加组的现有成员。

* 请注意，这是开放类型。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.userIdCollection"
}-->
```json
{
  "String-value": true
}
```

示例
```json
{
  "400723e1-102b-43aa-aba9-f35524827084": true, // property name is user id
  "f117339e-c914-4a9c-9b66-1c062b027556": true,
  "e886d105-23b9-47e2-bde1-757e75ee4a28": true
}

```### Properties
Properties of an Open Type can be defined by the client. In this case, the client should provide user ids as properties with their values being the `true` boolean. When user ids are no longer shared with, properties are automatically removed by setting their values to the `false` boolean.

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "userIdCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->