# <a name="list-recently-used-files"></a>最近使用的文件列表

列出登录用户最近使用的项的一组。 此列表包括在用户的驱动器中的项目以及他们有权从其他驱动器的物品。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```
GET /me/drive/recent
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                                                         |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="example"></a>示例

<!-- { "blockType": "request", "name": "drive-recent", "scopes": "files.read" } -->
```http
GET /me/drive/recent
```

## <a name="response"></a>响应

此方法返回包含的项与已登录的用户共享的[driveItem 资源](../resources/driveitem.md)的集合。


<!-- { "blockType": "response", "@odata.type": "microsoft.graph.driveItem", "isCollection": true, "truncated": true } -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "1312abc!1231",
      "remoteItem":
      {
        "id": "1991210caf!192",
        "name": "March Proposal.docx",
        "file": { },
        "size": 19121,
        "parentReference": {
          "driveId": "1991210caf",
          "id": "1991210caf!104"
        }
      }
    },
    {
      "id": "1312def!9943",
      "name": "Vacation.jpg",
      "file": { },
      "size": 37810,
      "parentReference": {
        "driveId": "1312def",
        "id": "1312def!123"
      }
    }
  ]
}
```

## <a name="remarks"></a>备注

从**近期**的操作返回某些 driveItems 将包括**remoteItem**方面，这表明它们是在其他驱动器上的项目。 若要访问原始的 driveItem 对象，您需要进行使用**remoteItem**以下面的格式中提供的信息的请求︰

<!-- {"blockType": "ignored"} -->
```http
GET /drives/<remoteItem.driveId>/items/<id>
```

<!-- {
  "type": "#page.annotation",
  "description": "Retrieve a list of files shared with the signed-in user.",
  "keywords": "sharedWithMe onedrive shared files",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Shared with me"
} -->
