# <a name="list-children-of-a-driveitem"></a>DriveItem 的列表子

文件夹属性的项目包含子项目。 此 API 列表内容的**driveItem 的**`children`使用根 driveItem、 driveItem ID 或路径的集合。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
```http
GET /me/drive/root/children
GET /me/drive/items/{item-id}/children
GET /me/drive/root:/{item-path}:/children
```

## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 载体 {标记}。 必需。                                                                                                                                |
| 如果没有-匹配 | String | 如果此请求标头将包含并提供 eTag （或 cTag） 匹配当前标记的文件，`HTTP 304 Not Modified`返回的响应。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。

##### <a name="request"></a>请求
下面是示例请求返回根目录中已登录的用户 OneDrive driveItems。

<!-- {
  "blockType": "request",
  "name": "get_children"
}-->
```http
GET /me/drive/root/children
```

## <a name="response"></a>响应

这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {"name": "myfile.jpg", "size": 2048, "file": {} },
    {"name": "Documents", "folder": { "childCount": 4} },
    {"name": "Photos", "folder": { "childCount": 203} },
    {"name": "my sheet(1).xlsx", "size": 197 }
  ],
  "@odata.nextLink": "https://..."
}
```

**注意︰**如果超出了集合的默认页面大小 （200 项），**@odata.nextLink**属性返回响应指出更多的项目可用，并提供项目的第二页的请求 URL 中。

您可以控制通过[可选的查询字符串参数](https://dev.onedrive.com/odata/optional-query-parameters.htm)的页面大小。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List the children of an item.",
  "keywords": "list,children,collection",
  "section": "documentation",
  "tocPath": "OneDrive/DriveItem/List children"
} -->
