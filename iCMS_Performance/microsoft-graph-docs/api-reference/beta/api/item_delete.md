# <a name="delete-an-item"></a>删除项

通过使用其 ID 或路径中删除项目。 请注意，删除项目使用此方法将项目移到回收站中，而不是永久删除它们。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```
DELETE /me/drive/items/{item-id}
DELETE /me/drive/root:/{item-path}
DELETE /groups/<id>/drive/items/<item-id>
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                                                         |
| 如果匹配      | String | 如果此请求标头将包括提供 eTag （或 cTag） 与当前标记的项目，不匹配`412 Precondition Failed`返回的响应并不会删除该项目。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="example"></a>示例

这里是如何调用此 API 的示例。

<!-- {
  "blockType": "request",
  "name": "delete-item"
}-->
```
DELETE /me/drive/items/{item-id}
```

## <a name="response"></a>响应

如果成功，此调用将返回`204 No Content`响应，表示该资源已被删除，没有返回。

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Delete item"
}-->
