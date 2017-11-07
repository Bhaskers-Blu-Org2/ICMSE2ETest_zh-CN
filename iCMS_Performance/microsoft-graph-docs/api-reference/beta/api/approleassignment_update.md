# <a name="update-approleassignment"></a>更新 approleassignment

更新 approleassignment 对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /users/<id | userPrincipalName>/appRoleAssignments/<id>
PATCH /servicePrincipals/<id>/appRoleAssignedTo
PATCH /groups/<id>/appRoleAssignments/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|creationTimestamp|方法|授予创建时的时间。|
|id|Guid|已分配给该主体角色 id。  此角色必须声明通过其**appRoles**属性在目标资源应用程序**资源 Id** 。 其中资源没有声明任何权限，必须指定一个默认 id (零 GUID)。                            **备注**︰ 不可以为 null。            |
|principalDisplayName|String|被授予访问权的主体显示名称。|
|principalId|Guid|唯一标识符 (**objectId**) 被授予访问权限的主体。                            **说明**︰ 所需。            |
|principalType|String|主体的类型。  这可以是"用户"、"组"或"ServicePrincipal"。|
|resourceDisplayName|String|对其进行分配的资源显示名称。|
|资源 Id|Guid|唯一标识符 (**objectId**) 目标资源 （服务主体） 对其进行分配。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[appRoleAssignment](../resources/approleassignment.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_approleassignment"
}-->
```http
PATCH https://graph.microsoft.com/beta/appRoleAssignments/<id>
Content-type: application/json
Content-length: 233

{
  "creationTimestamp": "datetime-value",
  "principalDisplayName": "principalDisplayName-value",
  "principalId": "principalId-value",
  "principalType": "principalType-value",
  "resourceDisplayName": "resourceDisplayName-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.approleassignment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 253

{
  "creationTimestamp": "datetime-value",
  "id": "id-value",
  "principalDisplayName": "principalDisplayName-value",
  "principalId": "principalId-value",
  "principalType": "principalType-value",
  "resourceDisplayName": "resourceDisplayName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update approleassignment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->