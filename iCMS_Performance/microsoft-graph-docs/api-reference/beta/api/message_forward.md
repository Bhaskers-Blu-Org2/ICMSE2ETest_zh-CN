# <a name="message-forward"></a>消息︰ 向前

转发邮件、 添加注释或修改任何可更新属性  
在一个**发展**中的所有调用。 邮件保存在已发送邮件文件夹中。

或者，您可以第一个[创建转发邮件草稿](../api/message_createforward.md)包括注释或更新任何消息属性，然后[发送](../api/message_send.md)邮件草稿。

**请注意**

- 注释或**body**属性可以指定`message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 您必须指定`toRecipients`参数或的**toRecipients**属性`message`参数。 如果同时指定或指定既不会返回 HTTP 400 错误的请求错误。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.Send*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/forward
POST /users/<id | userPrincipalName>/messages/<id>/forward
POST /me/mailFolders/<id>/messages/<id>/forward
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/forward
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|批注|String|要包含的注释。 可以为空字符串。|
|toRecipients|[收件人](../resources/recipient.md)集合|收件人列表中。|
|消息|[消息](../resources/message.md)|要更新答复邮件中的任何可写属性。|

## <a name="response"></a>响应
如果成功，此方法返回`202, Accepted`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
下面的示例将**isDeliveryReceiptRequested**属性设置为 true，添加注释并将消息转发。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "message_forward"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAH5JaLAAA=/forward
Content-Type: application/json

{
  "message":{  
    "isDeliveryReceiptRequested": true,
    "toRecipients":[
      {
        "emailAddress": {
          "address":"danas@contoso.onmicrosoft.com",
          "name":"Dana Swope"
        }
      }
     ]
  },
  "comment": "Dana, just want to make sure you get this." 
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: forward",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
