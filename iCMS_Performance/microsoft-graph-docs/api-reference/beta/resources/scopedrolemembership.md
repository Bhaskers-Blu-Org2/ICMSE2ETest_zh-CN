# <a name="scopedrolemembership-resource-type"></a>scopedRoleMembership 资源类型

指定了作用域的角色成员资格描述目录角色，进一步将作用于管理单元 (AU) 的用户的成员资格。  这提供了一种机制来允许租户级公司 adminsistrator 以委派管理权限给用户以管理用户和组的组织的一个子集 （AU 所定义的子集）。 

## <a name="methods"></a>方法
不支持对此资源的直接查询。  请参阅[管理单元](administrativeunit.md)主题以查看有关如何查询范围角色成员资格，以及添加和移除范围角色成员资格信息。 

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|administrativeUnitId|string|目录角色的作用范围的管理单位的唯一标识符|
|id|string| 唯一标识符的作用域角色成员资格。 只读的。|
|roleId|string| 为目录角色中的成员的唯一标识符。|
|roleMemberInfo|[identityInfo](identityinfo.md)| 角色成员身份信息，表示此范围角色成员的用户。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.scopedrolemembership"
}-->

```json
{
  "administrativeUnitId": "string",
  "id": "string (identifier)",
  "roleId": "string",
  "roleMemberInfo": {"@odata.type": "microsoft.graph.identityInfo"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "scopedRoleMembership resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->