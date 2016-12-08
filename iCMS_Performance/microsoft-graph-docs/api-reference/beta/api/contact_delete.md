# <a name="delete-contact"></a>删除联系人

删除联系人。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Contacts.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
[请联系](../resources/contact.md)来自用户的默认值[contactFolder](../resources/contactfolder.md)。
```http
DELETE /me/contacts/<id>
DELETE /users/<id | userPrincipalName>/contacts/<id>
```
[请联系](../resources/contact.md)来自用户的前级[contactFolder](../resources/contactfolder.md)。
```http
DELETE /me/contactFolders/<id>/contacts/<id>
DELETE /users/<id | userPrincipalName>/contactFolders/<id>/contacts/<id>
```
[联系](../resources/contact.md) [contactFolder](../resources/mailfolder.md)子文件夹中。  下面的示例演示一个嵌套级别的但联系人可以位于中子级的子级，等等。
```http
DELETE /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
DELETE /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。


## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "delete_contact"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/contacts/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->