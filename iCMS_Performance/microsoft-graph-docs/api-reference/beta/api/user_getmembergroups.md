# <a name="user-getmembergroups"></a>用户︰ getMemberGroups
返回所有组成员的用户。 检查是可传递的与不同的阅读[memberOf](../api/user_list_memberof.md)导航属性，它返回该用户是直接成员的组。

此功能支持 Office 365 和其他类型的组设置 Azure 的广告。 组每个请求可以返回的最大数目为 2046 个。 注意︰ Office 365 组不能包含组。 因此在 Office 365 组中的成员身份始终是直接的。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *User.Read;User.ReadWrite;User.Read.All;User.ReadWrite.All;Directory.Read.All;Directory.ReadWrite.All;Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /users/<id | userPrincipalName>/getMemberGroups
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|securityEnabledOnly|Boolean|应返回**true**指定只有安全组用户是的成员;**false**指定应返回所有组成员的用户。 注意︰ 此函数只能调用对用户如果该参数为**true**。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应并在响应正文中包含用户所在的组的 Id 的字符串集合。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "user_getmembergroups"
}-->
```http
POST https://graph.microsoft.com/beta/me/getMemberGroups
Content-type: application/json
Content-length: 33

{
  "securityEnabledOnly": true
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "string",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 39

{
  "value": [
    "string-value"
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user: getMemberGroups",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
