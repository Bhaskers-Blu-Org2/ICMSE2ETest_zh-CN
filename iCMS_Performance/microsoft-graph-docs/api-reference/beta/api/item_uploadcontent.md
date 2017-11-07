# <a name="upload-or-replace-the-contents-of-a-driveitem"></a>上载或替换内容的 driveItem

简单上载 API 允许您提供一个新的文件的内容或更新一个 API 调用中的现有文件的内容。 此方法仅支持文件的大小为 4 MB。

若要上载大文件请参阅[上载大文件上载会话](item_createUploadSession.md)。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PUT /me/drive/items/{parent-id}:/{filename}:/content
PUT /me/drive/root:/{parent-path}/{filename}:/content
PUT /me/drive/items/{parent-id}/children/{filename}/content
PUT /groups/<id>/drive/items/<parent-id>/children/<filename>/content
```

## <a name="request-body"></a>请求正文
请求正文的内容应该要上载的文件的二进制流。

## <a name="response"></a>响应
如果成功，则此方法会返回一个[driveItem](../resources/driveitem.md)对象响应正文为新创建的文件中。

## <a name="example"></a>示例
此示例中路径已登录的用户 OneDrive 上载的文件。

<!-- {
  "blockType": "request",
  "name": "upload_item"
}-->
```http
PUT /me/drive/root:/{item-path}:/content
Content-type: text/plain

The contents of the file goes here.
```

## <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0123456789abc",
  "name": "myfile.jpg",
  "size": 10191,
  "file": { }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Upload item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
