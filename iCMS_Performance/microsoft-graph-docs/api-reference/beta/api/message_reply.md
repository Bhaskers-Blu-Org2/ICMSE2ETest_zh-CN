# <a name="message-reply"></a>消息︰ 答复

答复邮件的发件人、 添加注释或修改任何可更新一个**应答**呼叫中的所有属性。 然后在已发送邮件文件夹中保存邮件。

或者，您可以第一个[创建答复邮件草稿](../api/message_createreply.md)包括注释或更新任何消息属性，然后[发送](../api/message_send.md)答复。

**请注意**

- 注释或**body**属性可以指定`message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果**回复**属性指定在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822))，应该在**回复**并不**从**属性中的检索收件人发送给收件人的答复。 


## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.Send*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/reply
POST /users/<id | userPrincipalName>/messages/<id>/reply
POST /me/mailFolders/<id>/messages/<id>/reply
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/reply
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
|消息|[消息](../resources/message.md)|要更新答复邮件中的任何可写属性。|

## <a name="response"></a>响应
如果成功，此方法返回`202, Accepted`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
下面的示例包含一个注释，添加一位收件人答复邮件。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "message_reply"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/reply
Content-Type: application/json

{
  "message":{  
    "toRecipients":[
      {
        "emailAddress": {
          "address":"fannyd@contoso.onmicrosoft.com",
          "name":"Fanny Downs"
        }
      },
      {
        "emailAddress":{
          "address":"randiw@contoso.onmicrosoft.com",
          "name":"Randi Welch"
        }
      }
     ]
  },
  "comment": "Fanny, Randi, would you name the group please?" 
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 201 Created
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: reply",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
