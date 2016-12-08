# <a name="list-permissions-on-a-driveitem"></a>在 driveItem 上的列表权限

列表项的有效权限。

无法在列表项目或单个项扩展权限。 您必须直接访问权限的属性。

## <a name="access-to-permissions"></a>访问权限

权限集合包括潜在的敏感信息，并为每个调用方可能没有。

* 该项目的所有者，则将返回所有权限。 这包括共同所有者。
* 对于非所有者呼叫者，返回仅应用到调用方的权限。
* 包含机密信息的权限属性 (例如`shareId`， `webUrl`) 为能够创建权限的调用方，才会返回。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/root/permissions
GET /me/drive/items/<id>/permissions
GET /groups/<id>/drive/items/<id>/permissions
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                     |
|:--------------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                       |
| 如果没有-匹配 | string | 如果此请求标头将包含并提供 etag 匹配项，当前的 etag`HTTP 304 Not Modified`返回的响应。 |


## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[权限](../resources/permission.md)对象的集合。

有效权限的项可以有两个来源︰ 或者直接在上设置项目本身或该从继承权限项的祖先。

如果该权限继承，或者不是通过检查**inheritedFrom**属性，调用方可以区分。 此属性是[**itemReference**](../resources/itemreference.md)的资源引用该权限继承中的祖先。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_permissions"
}-->
```http
GET /me/drive/items/<id>/permissions
```


##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "1",
      "roles": ["write"],
      "link": {
        "webUrl": "https://onedrive.live.com/redir?resid=5D33DD65C6932946!70859&authkey=!AL7N1QAfSWcjNU8&ithint=folder%2cgif",
        "type": "edit"
      }
    },
    {
      "id": "2",
      "roles": ["write"],
      "grantedTo": {
        "user": {
          "id": "5D33DD65C6932946",
          "displayName": "John Doe"
        }
      },
      "inheritedFrom": {
        "driveId": "1234567890ABD",
        "id": "1234567890ABC!123",
        "path": "/drive/root:/Documents" }
    },
    {
      "id": "3",
      "roles": ["write"],
      "link": {
        "webUrl": "https://onedrive.live.com/redir?resid=5D33DD65C6932946!70859&authkey=!AL7N1QAfSWcjNU8&ithint=folder%2cgif",
        "type": "edit",
        "application": {
          "id": "12345",
          "displayName": "TimeTravelPlus"
        }
      }
    }
  ]
}
```

**注意︰**为清楚起见，响应对象将被截断。 从实际调用将返回所有的默认属性。

检索单个权限资源的更多详细信息，请参阅[获取权限](permission_get.md)。


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List permissions",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/List permissions"
}-->
