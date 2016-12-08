# <a name="remove-acceptedsender"></a>删除 acceptedSender

从 acceptedSenders 列表中删除用户或组。 
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
DELETE /groups/<id>/acceptedSenders/$ref?$id=<id>

```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。


## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
以下是几个请求的示例。
<!-- {
  "blockType": "request",
  "name": "create_directoryobject_from_group"
}-->
```http
DELETE https://graph.microsoft.com/beta/groups/<id>/acceptedSenders/$ref?$id="users/<id>"

DELETE https://graph.microsoft.com/beta/groups/<id>/acceptedSenders/$ref?$id="groups/<id>"
```

##### <a name="response"></a>响应
这里是响应的示例。 
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create acceptedSender",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->