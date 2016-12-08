# <a name="create-privilegedroleassignment"></a>创建 privilegedRoleAssignment

使用此 API 来创建新的[privilegedRoleAssignment](../resources/privilegedroleassignment.md)。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ _Directory.AccessAsUser.All_

请求程序需要有_特权角色管理员_角色。 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /privilegedRoleAssignments
```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文，提供[privilegedRoleAssignment](../resources/privilegedroleassignment.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[privilegedRoleAssignment](../resources/privilegedroleassignment.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_privilegedroleassignment_from_privilegedroleassignments"
}-->
```http
POST https://graph.microsoft.com/beta/privilegedRoleAssignments
Content-type: application/json
Content-length: 164

{
  "userId": "userId-value",
  "roleId": "roleId-value"
}
```
在请求正文，提供[privilegedRoleAssignment](../resources/privilegedroleassignment.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedRoleAssignment"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 184

{
  "id": "id-value",
  "userId": "userId-value",
  "roleId": "roleId-value",
  "isElevated": true,
  "expirationDateTime": "datetime-value",
  "resultMessage": "resultMessage-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create privilegedRoleAssignment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->