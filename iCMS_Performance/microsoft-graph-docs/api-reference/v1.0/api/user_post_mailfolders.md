# <a name="create-mailfolder"></a>创建 MailFolder

使用此 API 来创建新的邮件文件夹。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /users/<id | userPrincipalName>/mailFolders
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。 **显示名称**是[MailFolder](../resources/mailfolder.md)对象的只写属性。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|parentFolderId|String|父文件夹的文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|显示名称|String|新文件夹的显示名称。|

## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[MailFolder](../resources/mailfolder.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_mailfolder_from_user"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/mailFolders
Content-type: application/json
Content-length: 159

{
  "displayName": "displayName-value",
  "parentFolderId": "parentFolderId-value"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.mailFolder"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 179

{
  "displayName": "displayName-value",
  "parentFolderId": "parentFolderId-value",
  "childFolderCount": 99,
  "unreadItemCount": 99,
  "totalItemCount": 99,
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create MailFolder",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
