# <a name="copy-a-driveitem-to-a-new-location"></a>将 driveItem 复制到新位置

创建一份[driveItem](../resources/driveitem.md) （包括任何子级），一个新的父级下或使用新名称。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```
POST /me/drive/items/<id>/copy
POST /me/drive/root:/<path>:/copy
POST /groups/<id>/drive/items/<id>/copy
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                                                         |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。


| 名称            | 值                                          | 说明                                                                                                 |
|:----------------|:-----------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| parentReference | [ItemReference](../resources/itemreference.md) | 可选项。 对将在中创建该副本的父项的引用。                                         |
| name            | string                                         | 可选项。 新的副本的名称。 如果不提供该，相同的名称将用作原始。    |

**注意︰**_ParentReference_应包括任何一个`id`或`path`但不是能同时存在。 如果两者都包括在内，他们需要为引用相同的项或将发生错误。

## <a name="example"></a>示例

<!-- { "blockType": "request", "name": "copy-item", "scopes": "files.readwrite" } -->
```http
POST /me/drive/items/{item-id}/copy
Content-Type: application/json

{
  "parentReference": {
    "path": "/drive/root:/Documents"
  },
  "name": "foobar.txt"
}
```

## <a name="response"></a>响应

返回有关如何监视该副本时接受请求进度的详细信息。

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 202 Accepted
```

## <a name="remarks"></a>备注

以异步方式完成复制。 API 的响应只会指示复制操作已被接受或拒绝，说由于目标文件名已在使用中。 但是，没有办法知道当复制操作已完成。

<!-- {
  "type": "#page.annotation",
  "description": "Create a copy of an existing item.",
  "keywords": "copy existing item",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Copy"
} -->
