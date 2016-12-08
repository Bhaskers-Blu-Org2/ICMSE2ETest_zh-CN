# <a name="group-addfavorite"></a>组︰ addFavorite
将组添加到列表中的当前用户的收藏夹组。 只有 Office 365 组的支持。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/addFavorite
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "group_addfavorite"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/addFavorite
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.none"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group: addFavorite",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->