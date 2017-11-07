# <a name="move-an-item"></a>移动项目

更新按 ID 或路径项的父文件夹。 若要移动项，您可以更新其 parentReference 属性。

也可以通过更新的目标父 id **parentInfo.id**或**parentInfo.path**属性，到另一个文件夹中移动项目。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求

```http
PATCH /me/drive/items/{item-id}
PATCH /me/drive/root:/{item-path}
PATCH /groups/<id>/drive/<item-id>
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                                         |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                           |
| 如果匹配      | String | 如果此请求标头将包含并提供 eTag （或 cTag） 不匹配的文件夹中，当前的 eTag`412 Precondition Failed`返回的响应。 |


## <a name="request-body"></a>请求正文
在请求正文，提供**parentReference**属性的新值。
不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

**注意︰**将项目移动到根目录下的 OneDrive 时不能使用`"id:" "root"`的语法。 既需要使用的根文件夹中的真实 ID，或者使用`{"path": "/drive/root"}`为父引用。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[项](../resources/driveitem.md)对象在响应正文中。

## <a name="example"></a>示例
本示例将一个文件夹移到新的父路径。

<!-- {
  "blockType": "request",
  "name": "update_item"
}-->
```http
PATCH /drive/items/{item-id}
Content-type: application/json

{
    "name": "new-item-name",
    "parentReference" : {"path": "/drive/root:/Documents"}
}
```

## <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "0123456789abc",
    "name": "BFolder",
    "folder": { "childCount": 3 }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Move item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
