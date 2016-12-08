# <a name="azure-ad-privileged-identity-management"></a>Azure AD 特权身份管理

这是由[特权身份管理](https://azure.microsoft.com/en-us/documentation/articles/active-directory-privileged-identity-management-configure/)服务提供的方法的列表。

OData 之上构建服务。 若要筛选的查询结果，请使用标准的 OData``$filter``在 Uri 中的表达式。

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[列表 privilegedOperationEvent](../api/privilegedoperationevent_list.md) | [privilegedOperationEvent](privilegedoperationevent.md)集合 |获得 privilegedOperationEvent 对象集合。 |
|[获得 privilegedRole](../api/privilegedrole_get.md) |[privilegedRole](privilegedrole.md)| 得到一个 privilegedRole 对象。|
|[列表 privilegedRole](../api/privilegedrole_list.md) | [privilegedRole](privilegedrole.md)集合 |获得 privilegedRole 对象集合。 |
|[角色分配](../api/privilegedrole_list_assignments.md) | [privilegedRoleAssignment](privilegedroleassignment.md)集合 |获得 privilegedRoleAssignment 集合的特定角色。 每个 privilegedRoleAssignment 表示给用户角色分配。|
|[selfActivate](../api/privilegedrole_selfactivate.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |激活该角色分配给请求者。|
|[selfDeactivate](../api/privilegedrole_selfdeactivate.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |停用分配给请求方的角色。|
|[创建 privilegedRoleAssignment](../api/privilegedroleassignment_post_privilegedroleassignments.md) |[privilegedRoleAssignment](privilegedroleassignment.md)| 由过账到 privilegedRoleAssignments 集合中创建新的 privilegedRoleAssignment (角色分配)。|
|[列表 privilegedRoleAssignment](../api/privilegedroleassignment_list.md) | [privilegedRoleAssignment](privilegedroleassignment.md)集合 |获得 privilegedRoleAssignment 对象集合。 该集合包含组织的所有角色分派。 每个 privilegedRoleAssignment 表示给用户角色分配。 |
|[获得 privilegedRoleAssignment](../api/privilegedroleassignment_get.md) | [privilegedRoleAssignment](privilegedroleassignment.md)|获取具有指定的作业 id 的 privilegedRoleAssignment 对象。 |
|[删除 privilegedRoleAssignment](../api/privilegedroleassignment_delete.md) | 无。 |删除 privilegedRoleAssignment 对象。 |
|[makePermanent](../api/privilegedroleassignment_makepermanent.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |请为永久角色分配。 |
|[makeEligible](../api/privilegedroleassignment_makeeligible.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |请为符合角色分配。 |
|[我](../api/privilegedroleassignment_my.md) | [privilegedRoleAssignment](privilegedroleassignment.md)集合|获取请求者的角色分配。 |
|[获得 privilegedRoleSettings](../api/privilegedrolesettings_get.md) | [privilegedRoleSettings](../resources/privilegedrolesettings.md)|检索 privilegedRoleSettings 对象的属性。 |
|[获得 privilegedRoleSummary](../api/privilegedrolesummary_get.md) | [privilegedRoleSummary](../resources/privilegedrolesummary.md)|检索的 privilegedRoleSummary 对象。 |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Service root",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
