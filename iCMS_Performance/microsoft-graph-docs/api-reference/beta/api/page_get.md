# <a name="get-page"></a>获取页

检索的属性和关系的[page](../resources/page.md)对象。

**获取页面内容**

您可以使用页面的`content`端点获取 HTML 页的内容︰

```
GET /me/notes/pages/<id>/content[?includeIDs=true]
```

`includeIDs=true`查询选项用于[更新的网页](../api/page_update.md)。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰  
Notes.Read、 Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite、 Notes.Read.All 或 Notes.ReadWrite.All
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/pages/<id>
GET /users/<id | userPrincipalName>/notes/pages/<id>
GET /groups/<id>/notes/pages/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持`select`和`expand` [OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

展开默认响应`parentSection`，并选择该节的`id`， `name`，和`self`属性。 有效`expand`的值的页面是`parentNotebook`， `parentSection`。

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |
| 接受 | string | `application/json` |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[页](../resources/page.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
 <!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/me/notes/pages/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 此处所示的响应对象将被截断为简洁起见。 从实际调用将返回的所有属性。
 <!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 312

{
  "title": "title-value",
  "createdByAppId": "createdByAppId-value",
  "links": {
    "oneNoteClientUrl": {
      "href": "href-value"
    },
    "oneNoteWebUrl": {
      "href": "href-value"
    }
  },
  "contentUrl": "contentUrl-value",
  "content": "content-value",
  "lastModifiedTime": "datetime-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->