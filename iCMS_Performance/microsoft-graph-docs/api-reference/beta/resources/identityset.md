# <a name="identityset-resource-type"></a>identitySet 资源类型

**IdentitySet**类型是[标识](identity.md)对象的键控的集合。 它用来表示各种事件的一个项目，例如_创建_或_上次修改者_关联的标识一组。

## <a name="properties"></a>属性

| 属性    | 类型                    | 说明                                           |
|:------------|:------------------------|:------------------------------------------------------|
| application | [标识](identity.md) | 表示应用程序标识资源。 |
| 设备      | [标识](identity.md) | 表示设备标识资源。      |
| user        | [标识](identity.md) | 表示用户的标识资源。          |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "user", "device", "application" ],
  "@odata.type": "microsoft.graph.identitySet"
}-->

```json
{
  "application": {"@odata.type": "microsoft.graph.identity"},
  "device": {"@odata.type": "microsoft.graph.identity"},
  "user": {"@odata.type": "microsoft.graph.identity"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "identitySet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
