# <a name="get-resource"></a>获取资源

检索文件或图像[资源](../resources/resource.md)对象的二进制数据。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰  
Notes.Read、 Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite、 Notes.Read.All 或 Notes.ReadWrite.All
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/resources/<id>/content
GET /users/<id | userPrincipalName>/notes/resources/<id>/content
GET /groups/<id>/notes/resources/<id>/content
```

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的图像或文件的二进制数据。

注意︰ 图像不会直接在浏览器中呈现，因为它们需要检索它们，像其余的页内容的授权。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_resource"
}-->
```http
GET https://graph.microsoft.com/beta/me/notes/resources/<id>/content
```
##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "stream"
} -->
```http
HTTP/1.1 200 OK

...binary data...
```
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.resource"
} -->

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
