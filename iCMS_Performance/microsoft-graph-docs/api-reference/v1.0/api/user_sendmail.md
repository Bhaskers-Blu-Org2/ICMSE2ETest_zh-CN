# <a name="user-sendmail"></a>用户︰ sendMail

发送请求主体动态中指定的消息。 您可以选择保存在已发送邮件文件夹中的邮件。

相同的**sendMail**操作调用中，可以包含[文件附件](../resources/fileattachment.md)。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.Send*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /users/<id | userPrincipalName>/sendMail
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|Message|[消息](../resources/message.md)|要发送的消息。 必需。|
|SaveToSentItems|Boolean|指示是否将邮件保存在已发送邮件中。 可选项。 默认值为 true。|

## <a name="response"></a>响应
如果成功，此方法返回`202, Accepted`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "user_sendmail"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/sendMail
Content-type: application/json
Content-length: 1944

{
  "Message": {
    "receivedDateTime": "datetime-value",
    "sentDateTime": "datetime-value",
    "hasAttachments": true,
    "subject": "subject-value",
    "body": {
      "contentType": "",
      "content": "content-value"
    },
    "bodyPreview": "bodyPreview-value",
    "importance": {
    },
    "parentFolderId": "parentFolderId-value",
    "sender": {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    },
    "from": {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    },
    "toRecipients": [
      {
        "emailAddress": {
          "name": "name-value",
          "address": "address-value"
        }
      }
    ],
    "ccRecipients": [
      {
        "emailAddress": {
          "name": "name-value",
          "address": "address-value"
        }
      }
    ],
    "bccRecipients": [
      {
        "emailAddress": {
          "name": "name-value",
          "address": "address-value"
        }
      }
    ],
    "replyTo": [
      {
        "emailAddress": {
          "name": "name-value",
          "address": "address-value"
        }
      }
    ],
    "conversationId": "conversationId-value",
    "uniqueBody": {
      "contentType": "",
      "content": "content-value"
    },
    "isDeliveryReceiptRequested": true,
    "isReadReceiptRequested": true,
    "isRead": true,
    "isDraft": true,
    "webLink": "webLink-value",
    "createdDateTime": "datetime-value",
    "lastModifiedDateTime": "datetime-value",
    "changeKey": "changeKey-value",
    "categories": [
      "categories-value"
    ],
    "id": "id-value",
    "attachments": [
      {
        "@odata.type": "#microsoft.graph.fileAttachment",
        "name": "menu.txt",
        "contentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "SaveToSentItems": true
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
  "description": "user: sendMail",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
