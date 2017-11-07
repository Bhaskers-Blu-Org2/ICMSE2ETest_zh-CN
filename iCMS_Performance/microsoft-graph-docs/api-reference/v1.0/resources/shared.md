# <a name="shared-resource-type"></a>共享的资源类型

表示，已与其他人共享项目。 包括有关如何共享项目信息。

## <a name="properties"></a>属性

| 属性 | 类型                          | 说明                                                                                        |
|:---------|:------------------------------|:---------------------------------------------------------------------------------------------------|
| 所有者    | [IdentitySet](identityset.md) | 共享项目的所有者的身份。 只读的。                                           |
| scope    | String                        | 指示如何共享该项的范围︰ `anonymous`， `organization`，或`users`。 只读的。 |

## <a name="scope-values"></a>范围值

| 值        | 说明                                                                           |
|:-------------|:--------------------------------------------------------------------------------------|
| 公用       | 通过使用适用于任何人与链接的链接共享项。               |
| 组织 | 通过使用链接适用于所有者的组织中的任何人共享项。 |
| 用户        | 与特定的用户共享项目。                                          |

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.shared"
}-->
```json
{
  "owner": {"@odata.type": "microsoft.graph.identitySet"},
  "scope": "public | organization | users"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "shared resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
