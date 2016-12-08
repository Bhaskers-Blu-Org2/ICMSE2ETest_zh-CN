# <a name="privilegedrole-selfactivate"></a>privilegedRole: selfActivate
激活该角色分配给请求者。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ _Directory.AccessAsUser.All_

请求者可以仅调用```selfActivate```分配给他的角色。
 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /privilegedRoles/<id>/selfActivate
```

请注意，``<id>``是目标角色 id。
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|原因|string|可选项。 有关此角色激活的原因的说明。|
|duration|string|可选项。 有效的值可能是```min```（激活最小持续时间） ```default``` （默认激活持续时间的角色），或一个双精度值，以指定小时数是激活。 指定的持续时间不能超过该角色激活角色设置持续时间。 |
|ticketNumber|string|可选项。 用来跟踪此角色激活证号。|
|ticketSystem|string|可选项。 票据系统。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码和[privilegedRoleAssignment](../resources/privilegedroleassignment.md)对象在响应正文中的。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "privilegedrole_selfactivate"
}-->
```http
POST https://graph.microsoft.com/beta/privilegedRoles/<id>/selfActivate
Content-type: application/json
Content-length: 142

{
  "reason": "reason-value",
  "duration": "duration-value",
  "ticketNumber": "ticketNumber-value",
  "ticketSystem": "ticketSystem-value"
}
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
  "description": "privilegedRole: selfActivate",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->