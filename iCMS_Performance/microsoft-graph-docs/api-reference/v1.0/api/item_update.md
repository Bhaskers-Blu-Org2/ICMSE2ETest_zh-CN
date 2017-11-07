# <a name="update-a-driveitem-metadata"></a>更新 driveItem 元数据

更新按 ID 或路径 driveItem 的元数据。

您可以使用更新将项目移动到另一个上级，通过更新项的**parentReference**属性。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/drive/items/{item-id}
PATCH /me/drive/root:/{item-path}
PATCH /groups/<id>/drive/items/<item-id>
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                                         |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                           |
| 如果匹配      | String | 如果此请求标头将包含并提供 eTag （或 cTag） 不匹配的文件夹中，当前的 eTag`412 Precondition Failed`返回的响应。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供应更新的属性的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能您的应用程序不应包括尚未更改的属性。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[项](../resources/driveitem.md)对象在响应正文中。

## <a name="example"></a>示例
本示例重命名该文件，并将说明添加到 driveItem。

<!-- {
  "blockType": "request",
  "name": "update_item"
}-->
```http
PATCH /me/drive/items/<item-id>
Content-type: application/json

{
    "name": "new-file-name.docx",
  "description": "Adding a description to this file",
}
```

## <a name="response"></a>响应
这里是响应的示例。 为了提高可读性，此响应将被截断。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
    "name": "new-file-name.docx",
  "description": "Adding a description to this file",
    "file": { }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Update item"
}-->
