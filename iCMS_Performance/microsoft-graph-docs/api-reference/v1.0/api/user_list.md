# <a name="list-users"></a>用户列表

检索用户对象的列表。

> 注意︰ 列出用户返回一组默认的属性唯一 （*businessPhones、 显示名称、 givenName、 id、 职务、 邮件、 mobilePhone、 办公室、 preferredLanguage、 姓、 范围内*）。 使用`$select`来获得[用户](../resources/user.md)对象的属性和关系。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *User.ReadBasic.All;User.Read.All;User.ReadWrite.All;Directory.Read.All;Directory.ReadWrite.All;Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /users
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。
## <a name="request-headers"></a>请求标头
| 页眉       | 值|
|:-----------|:------|
| 授权  | 持有者<token>。 必需。  |
| 接受  | 应用程序/json|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[用户](../resources/user.md)对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_users"
}-->
```http
GET https://graph.microsoft.com/v1.0/users
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.user",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 608

{
  "value": [
    {
      "businessPhones": [
        "businessPhones-value"
      ],
      "displayName": "displayName-value",
      "givenName": "givenName-value",
      "jobTitle": "jobTitle-value",
      "mail": "mail-value",
      "mobilePhone": "mobilePhone-value",
      "officeLocation": "officeLocation-value",
      "preferredLanguage": "preferredLanguage-value",
      "surname": "surname-value",
      "userPrincipalName": "userPrincipalName-value",
      "id": "id-value"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List users",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
