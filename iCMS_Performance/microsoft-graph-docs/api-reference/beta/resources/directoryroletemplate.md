# <a name="directoryroletemplate-resource-type"></a>directoryRoleTemplate 资源类型

表示目录角色模板。 目录角色模板指定目录角色 ([directoryRole](directoryrole.md)) 的属性值。 没有为每个可能会在一个租户中激活目录角色关联的目录角色模板对象。 若要读取目录角色或更新它的成员，它必须首先激活在租户。 默认情况下，只有公司管理员目录角色被激活。 要激活其他可用的目录角色发送 POST 请求到`/directoryRoles`请求的**roleTemplateId**参数中指定的目录角色模板目录角色基于 id 的终结点。 在此请求成功完成，您就可以开始读取和目录角色分配成员。 **注意**︰ 目录角色模板公开用户目录角色。 用户目录角色是隐式的不是对目录客户端可见。 由基础结构情况下，租户的每个用户分配到此角色。 已激活该角色。 不要使用此模板。


## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 directoryRoleTemplate](../api/directoryroletemplate_get.md) | [directoryRoleTemplate](directoryroletemplate.md) |读取属性和关系的 directoryRoleTemplate 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|description|字符串|要设置目录角色的说明。 只读的。|
|显示名称|String|若要设置目录角色显示名称。 只读的。 |
|id|String|模板的唯一标识符。 从[directoryObject](directoryobject.md)继承。 POST 请求中的**roleTemplateId**属性激活租户在[directoryRole](directoryrole.md)指定目录角色模板的**id** 。 键，不可以为 null。 只读的。|

## <a name="relationships"></a>Relationships
无



## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.directoryRoleTemplate"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directoryRoleTemplate resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
