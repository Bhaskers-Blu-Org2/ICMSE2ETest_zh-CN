# <a name="create-attachment"></a>创建附件

使用此 API 可以将[附件](../resources/attachment.md)添加到帖子。 由于目前每个其余请求的总大小限制为 4 MB，这就限制了可以添加到下 4 MB 附件的大小。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

* Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
[发送](../resources/post.md)[线程](../resources/conversationthread.md)属于一组[对话](../resources/conversation.md)中的附件。
```http
POST /groups/<id>/threads/<id>/posts/<id>/attachments
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/attachments
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |

## <a name="request-body"></a>请求正文
在请求正文中，提供[附件](../resources/attachment.md)对象的 JSON 的表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应并在响应正文中的[附件](../resources/attachment.md)对象。

## <a name="example-file-attachment"></a>示例 （附件）

##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_post"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/threads/<id>/posts/<id>/attachments
Content-type: application/json
Content-length: 142

{
  "@odata.type": "#microsoft.graph.fileAttachment",
  "name": "name-value",
  "contentBytes": "contentBytes-value"
}
```

在请求正文中，提供[附件](../resources/attachment.md)对象的 JSON 的表示。

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 162

{
  "lastModifiedDateTime": "datetime-value",
  "name": "name-value",
  "contentType": "contentType-value",
  "size": 99,
  "isInline": true,
  "id": "id-value"
}
```

## <a name="example-item-attachment"></a>示例 （项目附件）

##### <a name="request"></a>请求
<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_post"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/threads/<id>/posts/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": { }
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 162

{
  "lastModifiedDateTime": "datetime-value",
  "name": "name-value",
  "contentType": "contentType-value",
  "size": 99,
  "isInline": true,
  "id": "id-value"
}
```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Attachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
