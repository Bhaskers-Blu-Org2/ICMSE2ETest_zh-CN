# <a name="create-a-new-folder-driveitem"></a>创建新的文件夹 driveItem

使用此 API 的驱动器中创建一个新文件夹。 您的应用程序可以创建文件夹根目录中的一个驱动器，文件夹属性，现有 driveItem 下或在 OneDrive 的[**approot**文件夹中](https://dev.onedrive.com/misc/appfolder.htm)

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/drive/root/children
POST /me/drive/items/<id>/children
POST /me/drives/<id>/root/children
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
在请求正文，提供[driveItem](../resources/driveitem.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[项目](../resources/driveitem.md)对象。

## <a name="example"></a>示例

##### <a name="request"></a>请求

下面是示例请求用户的 OneDrive 的根目录中创建一个新文件夹。

<!-- {
  "blockType": "request",
  "name": "create_item_from_item"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/root/children
Content-Type: application/json

{
  "folder": { },
  "name": "Graph Project Files"
}
```
在请求正文中，提供[项目](../resources/driveitem.md)对象的 JSON 表示。

##### <a name="response"></a>响应
这里是响应的示例。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "createdBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "createdDateTime": "2016-03-21T20:01:37Z",
  "cTag": "\"c:{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},0\"",
  "eTag": "\"{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},1\"",
  "folder": {
      "childCount": 0
  },
  "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
  "lastModifiedBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "lastModifiedDateTime": "2016-03-21T20:01:37Z",
  "name": "Graph Project Files",
  "parentReference": {
      "driveId": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "id": "01NKDM7HN6Y2GOVW7725BZO354PWSELRRZ",
      "path": "/drive/root:"
  },
  "size": 0,
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/Graph%20Project%20Files"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create children",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Create folder"
}-->
