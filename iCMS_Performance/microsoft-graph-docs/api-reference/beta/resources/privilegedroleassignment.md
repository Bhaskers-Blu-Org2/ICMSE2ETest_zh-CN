# <a name="privilegedroleassignment-resource-type"></a>privilegedRoleAssignment 资源类型

表示特定用户的特权的角色分配。 


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[列表 privilegedRoleAssignment 集合](../api/privilegedroleassignment_list.md) | [privilegedRoleAssignment](privilegedroleassignment.md)集合|得到的 privilegedRoleAssignment 对象的集合。|
|[获得 privilegedRoleAssignment](../api/privilegedroleassignment_get.md) | [privilegedRoleAssignment](privilegedroleassignment.md) |读取属性和关系的 privilegedRoleAssignment 对象。|
|[创建工作分配](../api/privilegedroleassignment_post_privilegedroleassignments.md) |[privilegedRoleAssignment](privilegedroleassignment.md)| 由过账到分配集合中创建新的分配。|
|[删除](../api/privilegedroleassignment_delete.md) | 无 |删除 privilegedRoleAssignment 对象。 |
|[makePermanent](../api/privilegedroleassignment_makepermanent.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|请为永久角色分配。|
|[makeEligible](../api/privilegedroleassignment_makeeligible.md)|[privilegedRoleAssignment](privilegedroleassignment.md)|请为符合角色分配。|
|[我](../api/privilegedroleassignment_my.md)|[privilegedRoleAssignment](privilegedroleassignment.md)集合|获取当前用户的特权的角色分配。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|expirationDateTime|方法|UTC 日期时间将过期临时特权的角色分配。 为永久角色分配的值为 null。|
|id|string| 特权的角色分配的唯一标识符。 只读的。 它是以 userId_roleId，其中用户 Id 是 Azure AD 用户 id 的 GUID 字符串，roleId 是 Azure 管理员角色 id 的 GUID 字符串格式。|
|isElevated|布尔|**如此**如果角色分配处于激活状态。 **假**如果角色分配处于停用状态。|
|resultMessage|string|由服务设置的结果消息。|
|roleId|string|角色标识符。 在 GUID 字符串格式。|
|用户 Id|string|用户标识符。 在 GUID 字符串格式。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|roleInfo|[privilegedRole](privilegedrole.md)| 只读的。 可以为 null。 关联的角色的信息。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleAssignment"
}-->

```json
{
  "expirationDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "isElevated": true,
  "resultMessage": "string",
  "roleId": "string",
  "userId": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleAssignment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->