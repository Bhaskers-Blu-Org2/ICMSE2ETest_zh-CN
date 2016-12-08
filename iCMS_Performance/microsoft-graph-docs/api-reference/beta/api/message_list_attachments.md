# <a name="list-attachments"></a>附件列表

检索附加到邮件中的[附件](../resources/attachment.md)对象的列表。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.Read* 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
用户的邮箱中的[邮件](../resources/message.md)的附件。
```http
GET /me/messages/<id>/attachments
GET /users/<id | userPrincipalName>/messages/<id>/attachments
```
附件包含在顶部的[消息](../resources/message.md)级别的[mailFolder](../resources/mailfolder.md)用户的邮箱中。
```http
GET /me/mailFolders/<id>/messages/<id>/attachments
GET /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/attachments
```
[MailFolder](../resources/mailfolder.md)用户的邮箱中的子文件夹中包含的[邮件](../resources/message.md)的附件。  下面的示例演示一个嵌套级别的但消息可以位于中子级的子级，等等。
```http
GET /me/mailFolders/<id>/childFolders/<id>/.../messages/<id>/attachments/<id>
GET /users/<id | userPrincipalName>/mailFolders/<id>/childFolders/<id>/messages/<id>/attachments/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

特别是，您可以使用 $展开查询参数，包括所有与其余的消息属性的内联邮件附件。 例如︰

```
GET https://graph.microsoft.com/beta/me/messages/<id>?$expand=attachments
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[附件](../resources/attachment.md)对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_attachments"
}-->
```http
GET https://graph.microsoft.com/beta/me/messages/<id>/attachments
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 215

{
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
      "contentType": "contentType-value",
      "contentLocation": "contentLocation-value",
      "contentBytes": "contentBytes-value",
      "contentId": "null",
      "lastModifiedDateTime": "datetime-value",
      "id": "id-value",
      "isInline": false,
      "isContactPhoto": false,
      "name": "name-value",
      "size": 99
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List attachments",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->