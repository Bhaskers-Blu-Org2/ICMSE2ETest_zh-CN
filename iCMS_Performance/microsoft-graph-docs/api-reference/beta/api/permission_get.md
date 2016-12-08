# <a name="get-permission"></a>获得权限

检索的属性和关系的权限对象。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/<item-id>/permissions/<id>
GET /me/drive/root:/<item-path>:/permissions/<id>
GET /groups/<group-id>/drive/items/<item-id>/permissions/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。


## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[权限](../resources/permission.md)对象。

## <a name="example"></a>示例

##### <a name="request"></a>请求

下面是示例请求访问根文件夹上的权限。

<!-- {
  "blockType": "request",
  "name": "get_permission"
}-->
```http
GET /me/drive/root/permissions/<id>
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
Content-length: 762

{
  "grantedTo": {
    "user": {
      "displayName": "Ryan Gregg",
      "id": "efee1b77-fb3b-4f65-99d6-274c11914d12"
    }
  },
  "id": "1",
  "roles": [ "write" ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get permission",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Get permission"
}-->
