# <a name="update-permission"></a>更新权限

更新现有权限对象的属性。 只有角色属性可以进行修改。

## <a name="prerequisites"></a>先决条件

以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```http
PATCH /me/drive/root/permissions/<id>
PATCH /me/drive/items/<id>/permissions/<id>
PATCH /groups/<group-id>/drive/items/<item-id>/permissions/<id>
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                                                                       |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                                                         |
| 如果匹配      | string | 如果此请求标头将包括提供 eTag （或 cTag） 与当前标记的项目，不匹配`412 Precondition Failed`返回的响应并不会删除该项目。 |


## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   | 说明                   |
|:-------------|:-------|:------------------------------|
| **角色**    | String | 权限类型的数组。 |


## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[权限](../resources/permission.md)对象在响应正文中。

## <a name="example"></a>示例

##### <a name="request"></a>请求

下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_permission"
}-->
```http
PATCH /me/drive/items/<item-id>/permissions/<id>
Content-type: application/json

{
  "roles": [ "read" ]
}
```
##### <a name="response"></a>响应

这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "grantedTo": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12"
    }
  },
  "id": "1",
  "roles": [ "read" ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update permission",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Update permission"
}-->
