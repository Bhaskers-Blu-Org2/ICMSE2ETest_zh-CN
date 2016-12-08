# <a name="update-page"></a>更新页

更新的 OneNote 页的内容。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰   
Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite 或 Notes.ReadWrite.All 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/notes/pages/<id>/content
PATCH /users/<id | userPrincipalName>/notes/pages/<id>/content
PATCH /groups/<id>/notes/pages/<id>/content
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |
| 内容类型 | string | `application/json` |

## <a name="request-body"></a>请求正文
在请求正文，提供[patchContentCommand](../resources/patchcontentcommand.md)对象表示页面的更改数组。 有关详细信息和示例，请参阅<a href="https://msdn.microsoft.com/office/office365/howto/onenote-update-page">更新 OneNote 页</a>。

## <a name="response"></a>响应
如果成功，此方法返回`204 No Content`响应代码。  为修补程序请求返回 JSON 数据。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_page"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/notes/pages/<id>/content
Content-type: application/json
Content-length: 312

[
   {
    'target':'#para-id',
    'action':'insert',
    'position':'before',
    'content':'<img src="image-url-or-part-name" alt="image-alt-text" />'
  }, 
  {
    'target':'#list-id',
    'action':'append',
    'content':'<li>new-page-content</li>'
  }
]
```
##### <a name="response"></a>响应
这里是响应的示例。 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.page"
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
