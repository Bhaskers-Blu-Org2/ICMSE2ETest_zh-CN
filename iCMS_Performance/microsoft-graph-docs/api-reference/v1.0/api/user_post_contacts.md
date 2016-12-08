# <a name="create-contact"></a>创建联系人

将联系人添加到根的联系人文件夹或另一个联系人文件夹的联系人终结点。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Contacts.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/contacts
POST /users/<id | userPrincipalName>/contacts
POST /me/contactFolders/<contactFolderId>/contacts
POST /users/<id | userPrincipalName>/contactFolders/<contactFolderId>/contacts
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，提供[联系人](../resources/contact.md)对象的 JSON 的表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应并在响应正文中的[联系人](../resources/contact.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_contact_from_user"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/contacts
Content-type: application/json

{
  "givenName": "Pavel",
  "surname": "Bansky",
  "emailAddresses": [
    {
      "address": "pavelb@fabrikam.onmicrosoft.com",
      "name": "Pavel Bansky"
    }
  ],
  "businessPhones": [
    "+1 732 555 0102"
  ]
}
```
在请求正文中，提供 JSON 对象的表示形式[，请与联系](../resources/contact.md)。

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.contact"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "id-value",
  "createdDateTime": "2015-11-09T02:14:32Z",
  "lastModifiedDateTime": "2015-11-09T02:14:32Z",
   "displayName": "Pavel Bansky"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
