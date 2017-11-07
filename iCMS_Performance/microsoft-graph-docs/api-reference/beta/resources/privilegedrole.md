# <a name="privilegedrole-resource-type"></a>privilegedRole 资源类型

表示一个 Azure AD 管理员角色，诸如︰**全局管理员、 记帐管理员、 服务管理员、 用户管理员、 管理员密码**等。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[PrivilegedRole 对象列表](../api/privilegedrole_list.md) | [privilegedRole](privilegedrole.md)集合|获取 privilegedRole 的集合。|
|[获得 privilegedRole](../api/privilegedrole_get.md) | [privilegedRole](privilegedrole.md) |读取属性和关系的 privilegedRole 对象。|
|[列表中的工作分配](../api/privilegedrole_list_assignments.md) |[privilegedRoleAssignment](privilegedroleassignment.md)集合| 获取此角色分配对象集合。|
|[selfActivate](../api/privilegedrole_selfactivate.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|激活指定的角色。|
|[selfDeactivate](../api/privilegedrole_selfdeactivate.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|停用分配的角色。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|string|管理员角色的唯一标识符。 它是一个 GUID 的字符串和从 Azure 广告为给定角色的角色模板 id 的值相同。 只读的。|
|name|string|角色名称。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|工作分配|[privilegedRoleAssignment](privilegedroleassignment.md)集合| 此角色的分配。 只读的。 可以为 null。|
|设置|[privilegedRoleSettings](privilegedrolesettings.md)| 此角色的设置。 只读的。 可以为 null。|
|摘要|[privilegedRoleSummary](privilegedrolesummary.md)| 此角色的摘要信息。 只读的。 可以为 null。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRole"
}-->

```json
{
  "id": "string (identifier)",
  "name": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRole resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->