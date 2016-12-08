# <a name="create-an-item-in-a-collection"></a>在集合中创建项目

使用此 API 集合中创建新项。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /drive/root/children
POST /drive/items/<id>/children
POST /drives/<id>/root/children

```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
在请求正文中，提供[项目](../resources/driveitem.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[项目](../resources/driveitem.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_item_from_item"
}-->
```http
POST https://graph.microsoft.com/v1.0/drive/root
Content-Type: application/json

{
  "name": "test-folder",
  "folder": { }
}
```

##### <a name="response"></a>响应
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
  "createdBy": {
    "application": {
      "displayName": "displayName-value",
      "id": "id-value"
    },
    "user": {
      "displayName": "displayName-value",
      "id": "id-value"
    }
  },
  "createdDateTime": "datetime-value",
  "cTag": "cTag-value",
  "eTag": "eTag-value",
  "id": "id-value",
  "lastModifiedBy": {
    "application": {
      "displayName": "displayName-value",
      "id": "id-value"
    },
    "user": {
      "displayName": "displayName-value",
      "id": "id-value"
    }
  },
  "lastModifiedDateTime": "datetime-value",
  "name": "name-value",
  "parentReference": {
    "driveId": "driveId-value",
    "id": "id-value",
    "path": "path-value"
  },
  "size": 0,
  "folder": {
    "childCount": 0
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create children",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
