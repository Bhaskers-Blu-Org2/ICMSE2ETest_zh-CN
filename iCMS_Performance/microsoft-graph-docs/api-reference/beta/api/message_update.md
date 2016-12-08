# <a name="update-message"></a>更新邮件

更新消息对象的属性。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/messages/<id>
PATCH /users/<id | userPrincipalName>/messages/<id>
PATCH /me/mailFolders/<id>/messages/<id>
PATCH /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |
## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。 写/可更新属性

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|bccRecipients|Recipient|邮件的密件抄送收件人。 可更新仅当 IsDraft = true。|
|类别|字符串集合|与消息关联的类别。|
|ccRecipients|收件人的集合|邮件的抄送收件人。 可更新仅当 IsDraft = true。|
|from|Recipient|邮箱所有者，并且该邮件的发件人。 可更新仅当 IsDraft = true。|
|重要性|String|消息的重要性。 可能的值为︰ `Low`， `Normal`， `High`。|
|inferenceClassification | String | 对于用户，根据推导出的相关性和重要性，或显式重写邮件的分类。 可能的值为︰`focused`或`other`。 |
|internetMessageId |String |由[RFC2822](http://www.ietf.org/rfc/rfc2822.txt)指定格式的消息 ID。 可更新仅当 IsDraft = true。|
|isRead|Boolean|表示是否已阅读该邮件。|
|回复|收件人的集合|在答复时使用的电子邮件地址。 可更新仅当 IsDraft = true。|
|发件人|Recipient|实际用于生成邮件帐户。 可更新仅当 IsDraft = true。|
|toRecipients|收件人的集合|邮件的收件人。 可更新仅当 IsDraft = true。|
|body|ItemBody|邮件的正文。 可更新仅当 IsDraft = true。|
|isDeliveryReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|isReadReceiptRequested|Boolean|指示是否已读的回执请求的邮件。|
|主题|String|邮件的主题。 可更新仅当 IsDraft = true。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的更新的[消息](../resources/message.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_message"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/messages/<id>
Content-type: application/json
Content-length: 248

{
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "inferenceClassification": "other"
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
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 248

{
  "receivedDateTime": "datetime-value",
  "sentDateTime": "datetime-value",
  "hasAttachments": true,
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "bodyPreview": "bodyPreview-value",
  "inferenceClassification": "other"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update message",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
