# <a name="message-replyall"></a>消息︰ 全部答复

通过指定注释和所有通过使用**全部答复**方法中修改任何可更新属性的回复，回复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。

或者，您可以第一个[创建全部答复邮件草稿](../api/message_createreplyall.md)包括注释或更新任何消息属性，然后[发送](../api/message_send.md)答复。

**请注意**

- 注释或**body**属性可以指定`message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果**回复**属性指定在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822))，应该发送给收件人的答复  
**回复**和**toRecipients**属性，并不在**从**和**toRecipients**属性中的收件人。 


## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.Send*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /users/me/messages/<id>/replyAll
POST /users/<id | userPrincipalName>/messages/<id>/replyAll
POST /me/mailFolders/<id>/messages/<id>/replyAll
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/replyAll
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
下面的示例包含一个注释，并添加全部答复邮件的附件。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "message_replyall"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/replyAll
Content-Type: application/json

{
    "message":{
      "attachments": [ 
        { 
          "@odata.type": "#microsoft.graph.fileAttachment", 
          "name": "guidelines.txt", 
          "contentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "comment": "Please take a look at the attached guidelines before you decide on the name." 
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
  "description": "message: replyAll",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
