# <a name="privilegedrole-selfdeactivate"></a>privilegedRole: selfDeactivate

停用分配给请求方的角色。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ _Directory.AccessAsUser.All_

请求者可以仅调用```selfDeactivate```分配给他的角色。 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /privilegedRoles/<id>/selfDeactivate
```

请注意，``<id>``是目标角色 id。
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码和[privilegedRoleAssignment](../resources/privilegedroleassignment.md)对象在响应正文中的。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "privilegedrole_selfdeactivate"
}-->
```http
POST https://graph.microsoft.com/beta/privilegedRoles/<id>/selfDeactivate
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedRoleAssignment"
} -->
```http
HTTP/1.1 200 OK
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
  "description": "privilegedRole: selfDeactivate",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->