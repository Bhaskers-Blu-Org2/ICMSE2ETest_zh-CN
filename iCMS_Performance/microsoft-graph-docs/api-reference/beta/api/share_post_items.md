# <a name="create-item"></a>创建项目

使用此 API 来创建一个新项。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /shares/<id>/items

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供[项目](../resources/driveitem.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[项目](../resources/driveitem.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_driveitem_from_share"
}-->
```http
POST https://graph.microsoft.com/beta/shares/<id>/items
Content-type: application/json
Content-length: 504

{
  "driveItem": {
    "content": "content-value",
    "createdBy": {
      "application": {
        "displayName": "displayName-value",
        "id": "id-value"
      },
      "device": {
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
    "description": "description-value",
    "eTag": "eTag-value"
  }
}
```
在请求正文，提供[driveItem](../resources/driveitem.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 504

{
  "driveItem": {
    "content": "content-value",
    "createdBy": {
      "application": {
        "displayName": "displayName-value",
        "id": "id-value"
      },
      "device": {
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
    "description": "description-value",
    "eTag": "eTag-value"
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
