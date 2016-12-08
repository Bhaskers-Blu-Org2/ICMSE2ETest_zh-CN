# <a name="get-photo"></a>获取照片

获取指定的[profilePhoto](../resources/profilephoto.md)或其元数据 （**profilePhoto**属性）。

获取操作首先寻找网上交换，该用户的邮箱中的指定照片，如果有，不能再看起来在 Azure 活动目录 (AAD)。

支持的 Exchange Online 上的高清晰度照片的大小如下所示:"48 x 48"、 'x64 的 64'、"96 96 倍"、"x 120 120"、"240 x 240"、"360 x 360，432 x 432'、 '504 x 504' 和 ' 648 x 648。 如果它们存储在 AAD，可以任意尺寸的照片。

可以获得的最大可用的照片中，元数据，或指定要获取的元数据，该照片的大小的大小。
如果您请求的大小不是可用的您仍然可以较小的用户具有上载并使其可用。
例如，如果用户上载照片这是 504 x 504 像素，则所有但 648 x 648 大小的照片可供下载。
如果没有指定的大小，在用户的邮箱或 AAD，1 x 1 的大小则返回元数据的其余部分。

## <a name="prerequisites"></a>先决条件
以下**范围**之一需要执行此 API，以便︰

*   包括已登录的用户- *User.ReadBasic.All; 组织中任何用户的个人资料照片User.Read.All;User.ReadWrite.All*
*   特别是已登录的用户的- *User.Read，User.ReadWrite; 个人资料照片User.ReadBasic.All;User.Read.All;User.ReadWrite.All*
* 个人资料照片**组**的 - *Group.Read.All;Group.ReadWrite.All*
* 照片的**联系** - *Contacts.Read;Contacts.ReadWrite*

## <a name="http-request-to-get-the-photo"></a>HTTP 请求以获取照片
<!-- { "blockType": "ignored" } -->
```http
GET /me/photo/$value
GET /users/<id | userPrincipalName>/photo/$value
GET /groups/<id>/photo/$value
GET /me/contacts/<id>/photo/$value
GET /users/<id | userPrincipalName>/contacts/<id>/photo/$value
GET /me/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
GET /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo/$value
```
## <a name="http-request-to-get-the-metadata-of-the-photo"></a>HTTP 请求获取照片的元数据
<!-- { "blockType": "ignored" } -->
```http
GET /me/photo
GET /users/<id | userPrincipalName>/photo
GET /groups/<id>/photo
GET /me/contacts/<id>/photo
GET /users/<id | userPrincipalName>/contacts/<id>/photo
GET /me/contactfolders/<contactFolderId>/contacts/<id>/photo
GET /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photo
```

## <a name="http-request-to-get-the-metadata-for-a-specific-photo-size"></a>HTTP 请求获取元数据的特定照片大小
<!-- { "blockType": "ignored" } -->
```http
GET /me/photos/<size>
GET /users/<id | userPrincipalName>/photos/<size>
GET /groups/<id>/photos/<size>
GET /me/contacts/<id>/photos/<size>
GET /users/<id | userPrincipalName>/contacts/<id>/photos/<size>
GET /me/contactfolders/<contactFolderId>/contacts/<id>/photos/<size>
GET /users/<id | userPrincipalName>/contactfolders/<contactFolderId>/contacts/<id>/photos/<size>
```

## <a name="parameters"></a>参数

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|size  |String  |照片大小。 |

## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者\<标记\>。 必需。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response-for-getting-the-photo"></a>响应中获取照片
如果成功，此方法返回`200 OK`请求的照片的响应代码和二进制数据。  如果没有照片存在，该操作返回`404 Not Found`。
## <a name="response-for-getting-the-metadata-of-the-photo"></a>响应中获取的元数据的照片
如果成功，此方法返回`200 OK`响应代码和[profilePhoto](../resources/profilePhoto.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request-1"></a>申请 1
此请求获取已登录的用户，在最大可用大小的照片。

<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/beta/me/photo/$value
Content-Type: image/jpg
```

##### <a name="response-1"></a>响应 1
包含二进制数据的请求的照片。 HTTP 响应代码为 200。

##### <a name="request-2"></a>请求 2
此请求已登录的用户获取 48x48 照片。

<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/beta/me/photos/48x48/$value
Content-Type: image/jpg
```

##### <a name="response-2"></a>2 响应
包含请求 48x48 照片的二进制数据。 HTTP 响应代码为 200。

##### <a name="request-3"></a>请求 3
此请求获取的元数据中的已登录的用户的用户照片。

<!-- {
  "blockType": "ignored"
}-->
```http
GET https://graph.microsoft.com/beta/me/photo
```

##### <a name="response-3"></a>3 响应
以下的响应数据显示照片的元数据。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。

<!-- {
  "blockType": "ignored"
}-->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/photo/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/jpeg",
    "@odata.mediaEtag": "\"BA09D118\"",
    "id": "240X240",
    "width": 240,
    "height": 240
}
```

以下的响应数据显示响应的内容时未已经为用户上载照片。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。

<!-- {
  "blockType": "ignored"
}-->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/photo/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4')/photo",
    "@odata.mediaContentType": "image/gif",
    "@odata.mediaEtag": "",
    "id": "1X1",
    "width": 1,
    "height": 1
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get photo",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
