# <a name="create-thread"></a>创建线程

通过首先创建一个线程启动一个新的会话。 

在组中创建新会话、 会话线程和开机自检。 使用[回复线程](conversationthread_reply.md)或[答复张贴内容](post_reply.md)进一步发布到该线程。

注意︰ 您还可以[启动一个新线程在当前对话中](conversation_post_threads.md)。 

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/threads
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，提供包含[发布](../resources/post.md)的[conversationThread](../resources/conversationthread.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[conversationThread](../resources/conversationthread.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_conversationthread_from_group"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/threads
Content-type: application/json

{
  "topic": "New Conversation Thread Topic",
  "posts": [{
    "body": {
      "contentType": "html",
      "content": "this is body content"
    },
    "newParticipants": [{
      "emailAddress": {
        "name": "Alex Darrow",
        "address": "alexd@contoso.com"
      }
    }]
  }]
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversationThread"
} -->
```http
HTTP/1.1 201 OK
Content-type: application/json
Content-length: 419

{
  "toRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ],
  "topic": "topic-value",
  "hasAttachments": true,
  "lastDeliveredDateTime": "datetime-value",
  "uniqueSenders": [
    "uniqueSenders-value"
  ],
  "ccRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create thread",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
