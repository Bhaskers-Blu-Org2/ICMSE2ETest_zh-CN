# <a name="create-thread"></a>创建线程

指定会话中创建一个新线程。

将创建一个线程和公告指定。 使用[回复线程](conversationthread_reply.md)进一步发布到该线程。 或者，如果您收到的发布 ID，您还可以[回复](post_reply.md)到该张贴内容在该线程中。

注意︰ 您还可以[启动一个新的会话，方法是首先创建一个线程](group_post_threads.md)。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Group.ReadWrite.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/conversations/<id>/threads
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文，提供[ConversationThread](../resources/conversationthread.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[ConversationThread](../resources/conversationthread.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_conversationthread_from_conversation"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/conversations/<id>/threads
Content-type: application/json

{
  "topic": "topic-value",
  "posts": [{
      "body": {
        "contentType": "html",
        "content": "this is body content"
      }
  }]
}
```
在请求正文，提供[conversationThread](../resources/conversationthread.md)对象的 JSON 表示。
##### <a name="response"></a>响应

如果成功，此方法返回`201, Created`响应代码和`id`在响应正文中的新线程。
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversationThread"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 346

{
  "id": "thread-id-value"
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
