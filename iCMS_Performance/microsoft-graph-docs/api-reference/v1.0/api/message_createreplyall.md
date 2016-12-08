# <a name="message-createreplyall"></a>邮件︰ createReplyAll

创建全部答复邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/createReplyAll
POST /users/<id | userPrincipalName>/messages/<id>/createReplyAll
POST /me/mailFolders/<id>/messages/<id>/createReplyAll
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/createReplyAll
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文

## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[消息](../resources/message.md)对象在响应正文中的。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "message_createreplyall"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/createReplyAll
Content-type: application/json
Content-length: 248

{
  "comment": "comment-value"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 248

{
  "receivedDateTime": "datetime-value",
  "sentDateTime": "datetime-value",
  "hasAttachments": true,
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "bodyPreview": "bodyPreview-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: createReplyAll",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
