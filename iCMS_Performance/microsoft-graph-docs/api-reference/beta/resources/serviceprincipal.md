# <a name="serviceprincipal-resource-type"></a>servicePrincipal 资源类型

表示目录中应用程序的一个实例。 从[directoryObject](directoryobject.md)继承。


### <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "appRoleAssignedTo",
    "appRoleAssignments",
    "createdObjects",
    "createdOnBehalfOf",
    "memberOf",
    "oauth2PermissionGrants",
    "ownedObjects",
    "owners"
  ],
  "@odata.type": "microsoft.graph.serviceprincipal"
}-->

```json
{
  "accountEnabled": true,
  "addIns": [{"@odata.type": "microsoft.graph.addIn"}],
  "appDisplayName": "string",
  "appId": "string",
  "appOwnerOrganizationId": "guid",
  "appRoleAssignmentRequired": true,
  "appRoles": [{"@odata.type": "microsoft.graph.appRole"}],
  "displayName": "string",
  "errorUrl": "string",
  "homepage": "string",
  "id": "string (identifier)",
  "keyCredentials": [{"@odata.type": "microsoft.graph.keyCredential"}],
  "logoutUrl": "string",
  "oauth2Permissions": [{"@odata.type": "microsoft.graph.oAuth2Permission"}],
  "passwordCredentials": [{"@odata.type": "microsoft.graph.passwordCredential"}],
  "preferredTokenSigningKeyThumbprint": "string",
  "publisherName": "string",
  "replyUrls": ["string"],
  "samlMetadataUrl": "string",
  "servicePrincipalNames": ["string"],
  "tags": ["string"]
}

```
### <a name="properties"></a>属性
| 属性     | 类型 |说明|
|:---------------|:--------|:----------|
|accountEnabled|Boolean| **如此**如果启用服务主体帐户;否则为**假**。            |
|appDisplayName|String|由关联的应用程序显示名称。|
|应用程序标识|String|对于关联的应用程序 （及其**应用程序标识**属性） 的唯一标识符。|
|appRoleAssignmentRequired|Boolean|指定用户或组对**appRoleAssignment**都要求之前 Azure 的广告会对应用程序发出用户的访问令牌。 不可以为 null。 |
|appRoles|[appRole](approle.md)集合|应用程序角色关联的应用程序公开。 详细信息请参阅[应用程序](application.md)实体上的**appRoles**属性定义。 不可以为 null。 |
|显示名称|String|服务主体为显示名称。|
|errorUrl|String|            |
|主页|String|指向关联的应用程序的主页的 URL。|
|keyCredentials|[keyCredential](keycredential.md)集合|凭据与主体服务相关联的集合。 不可以为 null。            |
|logoutUrl|String|            |
|oauth2Permissions|[oAuth2Permission](oauth2permission.md)集合|OAuth 2.0 权限关联的应用程序公开。 详细信息请参阅[应用程序](application.md)实体上的**oauth2Permissions**属性定义。 不可以为 null。            |
|id|String|服务主体的的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键。 不可以为 null。 只读的。|
|passwordCredentials|[passwordCredential](passwordcredential.md)集合|服务主体与相关联的密码凭据集合。 不可以为 null。 |
|preferredTokenSigningKeyThumbprint|String|保留为仅供内部使用。 不要写或否则依赖于此属性。 可能会在将来版本中删除。 |
|publisherName|String|在其中指定关联的应用程序组织显示名称。|
|replyUrls|字符串集合|用户令牌发送给以登录关联的应用程序或重定向 Uri 的 OAuth 2.0 授权码，并访问令牌发送给关联应用程序的 Url。 不可以为 null。 |
|samlMetadataUrl|String| |
|servicePrincipalNames|字符串集合|标识相关联的应用程序 Uri。 有关详细信息，请参阅[应用程序对象和服务主体对象](https://msdn.microsoft.com/en-us/library/azure/dn132633.aspx)。**Any**运算符，则需要为多值属性的筛选器表达式。  不可以为 null。 |
|标记|字符串集合| 不可以为 null。 |

### <a name="relationships"></a>Relationships
| 关系 | 类型 |说明|
|:---------------|:--------|:----------|
|appRoleAssignedTo|[appRoleAssignment](approleassignment.md)|承担者 （用户、 组和服务主体） 分配给此服务主体。 只读的。|
|appRoleAssignments|[appRoleAssignment](approleassignment.md)集合|服务主体分配给应用程序。 只读的。 可以为 null。|
|createdObjects|[directoryObject](directoryobject.md)集合|此服务主要由创建的目录对象。 只读的。 可以为 null。|
|memberOf|[directoryObject](directoryobject.md)集合|此服务主要是的成员的角色。 HTTP 方法︰ 获取只读的。 可以为 null。|
|oauth2PermissionGrants|[oAuth2PermissionGrant](oauth2permissiongrant.md)集合|与此服务主体相关联的用户模拟授予。 只读的。 可以为 null。|
|ownedObjects|[directoryObject](directoryobject.md)集合|此服务主要由拥有的目录对象。 只读的。 可以为 null。|
|所有者|[directoryObject](directoryobject.md)集合|将此服务主体的所有者的目录对象。 所有者是一套非管理员用户有权修改此对象。 只读的。 可以为 null。|
|策略|[策略](policy.md)集合|分配给此服务主体的策略。|

### <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 servicePrincipal](../api/serviceprincipal_get.md) | [servicePrincipal](serviceprincipal.md) |读取属性和关系的 servicePrincipal 对象。|
|[创建 appRoleAssignment](../api/serviceprincipal_post_approleassignments.md) |[appRoleAssignment](approleassignment.md)| 由过账到 appRoleAssignments 集合中创建新的 appRoleAssignment。|
|[列表 appRoleAssignments](../api/serviceprincipal_list_approleassignments.md) |[appRoleAssignment](approleassignment.md)集合| 获得 appRoleAssignment 对象集合。|
|[创建 createdObject](../api/serviceprincipal_post_createdobjects.md) |[directoryObject](directoryobject.md)| 由过账到 createdObjects 集合中创建新的 createdObject。|
|[列表 createdObjects](../api/serviceprincipal_list_createdobjects.md) |[directoryObject](directoryobject.md)集合| 获得 createdObject 对象集合。|
|[创建 memberOf](../api/serviceprincipal_post_memberof.md) |[directoryObject](directoryobject.md)| 创建新的 memberOf 由过账到 memberOf 集合。|
|[列表 memberOf](../api/serviceprincipal_list_memberof.md) |[directoryObject](directoryobject.md)集合| 获取 memberOf 对象集合。|
|[列表分配策略](../api/policy_list_assigned.md)| [策略](policy.md)集合| 获取分配给此对象的所有策略。|
|[创建 oAuth2PermissionGrant](../api/serviceprincipal_post_oauth2permissiongrants.md) |[oAuth2PermissionGrant](oauth2permissiongrant.md)| 由过账到 oauth2PermissionGrants 集合中创建新的 oAuth2PermissionGrant。|
|[列表 oauth2PermissionGrants](../api/serviceprincipal_list_oauth2permissiongrants.md) |[oAuth2PermissionGrant](oauth2permissiongrant.md)集合| 获得 oAuth2PermissionGrant 对象集合。|
|[创建 ownedObject](../api/serviceprincipal_post_ownedobjects.md) |[directoryObject](directoryobject.md)| 由过账到 ownedObjects 集合中创建新的 ownedObject。|
|[列表 ownedObjects](../api/serviceprincipal_list_ownedobjects.md) |[directoryObject](directoryobject.md)集合| 获得 ownedObject 对象集合。|
|[创建所有者](../api/serviceprincipal_post_owners.md) |[directoryObject](directoryobject.md)| 由过账到所有者集合中创建一个新的所有者。|
|[列出所有者](../api/serviceprincipal_list_owners.md) |[directoryObject](directoryobject.md)集合| 获取所有者对象集合。|
|[更新](../api/serviceprincipal_update.md) | [servicePrincipal](serviceprincipal.md)  |更新 servicePrincipal 对象。 |
|[删除](../api/serviceprincipal_delete.md) | 无 |删除 servicePrincipal 对象。 |
|[checkMemberGroups](../api/serviceprincipal_checkmembergroups.md)|字符串集合||
|[getMemberGroups](../api/serviceprincipal_getmembergroups.md)|字符串集合||
|[getMemberObjects](../api/serviceprincipal_getmemberobjects.md)|字符串集合||

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "servicePrincipal resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
