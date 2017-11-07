# <a name="message-createreply"></a>邮件︰ createReply

创建包含注释或更新任何消息属性中一个**createReply**调用的所有回复邮件的草稿。 然后可以[更新](../api/message_update.md)或[发送](../api/message_send.md)草稿。

**请注意**

- 注释或**body**属性可以指定`message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果**回复**指定在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822))，应该**从**中发送到收件人的**回复**，并不是收件人的答复。 

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/createReply
POST /users/<id | userPrincipalName>/messages/<id>/createReply
POST /me/mailFolders/<id>/messages/<id>/createReply
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/createReply
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
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[消息](../resources/message.md)对象。

## <a name="example"></a>示例
下面的示例创建答复草稿，在请求正文中添加注释和收件人。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "message_createreply"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createReply
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
  "comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
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
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages/$entity",
  "@odata.id": "https://graph.microsoft.com/beta/users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "id": "AAMkADA1MTAAAH5JKoAAA=",
  "subject": "RE: Let's start a group",
  "Body": {
    "contentType": "HTML",
    "content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "sender": {
    "emailAddress": {
      "name": "Admin",
      "address": "admin@contoso.onmicrosoft.com"
    }
  },
  "from": null,
  "toRecipients": [
    {
      "emailAddress": {
        "name": "Fanny Downs",
        "address": "fannyd@contoso.onmicrosoft.com"
      }
    },
    {
      "emailAddress": {
        "name": "Randi Welch",
        "address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: createReply",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
