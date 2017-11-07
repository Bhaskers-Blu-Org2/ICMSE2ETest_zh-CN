# <a name="update-profilephoto"></a>更新 profilephoto

更新已登录的**用户**，或者指定的**组**或**联系人**的照片。 由于目前每个其余请求的总大小限制为 4 MB，这就限制了可以添加到下 4 MB 的照片的大小。

您可以使用修补程序也将放在 1.0 版中此操作。

## <a name="prerequisites"></a>先决条件
以下**范围**之一需要执行此 API，以便︰

- 已登录的**用户**的个人资料照片 - *User.ReadWrite*
- 个人资料照片**组**的 - *Group.ReadWrite.All*
- 照片的**联系** - *Contacts.ReadWrite*

## <a name="http-request-to-update-the-photo"></a>HTTP 请求来更新照片
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/photo/$value
PATCH /users/<id | userPrincipalName>/photo/$value
PATCH /groups/<id>/photo/$value
PATCH /me/contacts/<id>/photo/$value
PATCH /users/<id | userPrincipalName>/contacts/<id>/photo/$value
PATCH /me/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
PATCH /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo/$value

PUT /me/photo/$value
PUT /users/<id | userPrincipalName>/photo/$value
PUT /groups/<id>/photo/$value
PUT /me/contacts/<id>/photo/$value
PUT /users/<id | userPrincipalName>/contacts/<id>/photo/$value
PUT /me/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
PUT /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 图像/jpeg。 必需。  |

## <a name="request-body"></a>请求正文
在请求正文中，包括在请求正文中的照片的二进制数据。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_profilephoto"
}-->
```http
PUT https://graph.microsoft.com/v1.0/me/photo/$value
Content-type: image/jpeg

Binary data for the image

```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.profilePhoto"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update profilephoto",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
