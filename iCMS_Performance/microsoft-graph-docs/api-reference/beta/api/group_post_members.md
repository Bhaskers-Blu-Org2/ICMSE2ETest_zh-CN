# <a name="add-member"></a>添加成员

使用此 API 可以将成员添加到 Office 365 组、 安全组或已启用邮件的安全组的**成员**导航属性。 您可以添加用户或其他组。 重要提示︰ 您可以向 Office 365 组中添加仅用户。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Group.ReadWrite.All*或*Directory.ReadWrite.All*或*Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/members/$ref
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供要添加[directoryObject](../resources/directoryobject.md)、[用户](../resources/user.md)或[组](../resources/group.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_directoryobject_from_group"
}-->
```http
POST https://graph.microsoft.com/beta/groups/<id>/members/$ref
Content-type: application/json
Content-length: 30

{
  "@odata.id": "https://graph.microsoft.com/beta/directoryObjects/<id>"
}
```
在请求正文中，提供的 JSON 表示`id`您想要添加的[directoryObject](../resources/directoryobject.md)、[用户](../resources/user.md)或[组](../resources/group.md)的对象。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directoryObject"
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create member",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->