# <a name="create-attachment"></a>创建附件

使用此 API 可以将[附件](../resources/attachment.md)添加到邮件中。 

您可以添加现有邮件的附件，由过账到其附件集合，也可以添加到正在[创建和发送即时](../api/user_sendmail.md)消息附件。

由于目前每个其余请求的总大小限制为 4 MB，这就限制了可以添加到下 4 MB 附件的大小。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
用户的邮箱中的[邮件](../resources/message.md)的附件。
```http
POST /me/messages/<id>/attachments
POST /users/<id | userPrincipalName>/messages/<id>/attachments
```
附件包含在顶部的[消息](../resources/message.md)级别的[mailFolder](../resources/mailfolder.md)用户的邮箱中。
```http
POST /me/mailFolders/<id>/messages/<id>/attachments
POST /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/attachments
```
[MailFolder](../resources/mailfolder.md)用户的邮箱中的子文件夹中包含的[邮件](../resources/message.md)的附件。  下面的示例演示一个嵌套级别的但消息可以位于中子级的子级，等等。
```http
POST /me/mailFolders/<id>/childFolders/<id>/.../messages/<id>/attachments/<id>
POST /users/<id | userPrincipalName>/mailFolders/<id>/childFolders/<id>/messages/<id>/attachments/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供[附件](../resources/attachment.md)对象的 JSON 的表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应并在响应正文中的[附件](../resources/attachment.md)对象。

## <a name="example-file-attachment"></a>示例 （附件）

##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_message"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/attachments
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
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```

## <a name="example-item-attachment"></a>示例 （项目附件）

##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_message"
}-->

```
POST https://graph.microsoft.com/v1.0/me/events/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": "message or event entity"
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
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
