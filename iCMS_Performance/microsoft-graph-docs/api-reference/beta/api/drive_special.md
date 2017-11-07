# <a name="get-a-special-folder-by-name"></a>按名称获取特殊文件夹

使用特殊集合可以按名称访问特殊文件夹。

特殊文件夹提供简单可访问 OneDrive 中的已知文件夹，而无需查找按 （这将需要本地化） 的路径，该文件夹的别名或引用的文件夹 id。 如果特殊文件夹被重命名或移动到驱动器中的其他位置，将继续这种语法来查找该文件夹。

第一次应用程序试图写入，如果不存在自动创建特殊文件夹。 如果用户删除了一个，都会重新创建它时再次写入。

**注意︰** 如果您拥有只读权限，请求不存在的特殊文件夹，您将收到`403 Forbidden`错误。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/special/<name>
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
如果成功，此方法返回`200 OK`响应代码和一个[driveItem](../resources/driveitem.md)对象在响应正文中的。

## <a name="example"></a>示例

##### <a name="request"></a>请求
下面是示例请求的用户的驱动器。

<!-- {
  "blockType": "request",
  "name": "get_drive_special"
}-->
```http
GET https://graph.microsoft.com/beta/me/drive/special/<name>
```

##### <a name="response"></a>响应
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
  "folder": { },
  "id": "s!lkjqwlkj124912049an",
  "name": "Photos",
  "specialFolder": { "name": "photos" },
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/Photos",
}
```

## <a name="example-head-requests-for-special-folders"></a>对于特殊文件夹的示例 HEAD 请求

如果您需要通过使用 GET 请求不存在的特殊文件夹，将为您自动创建特殊文件夹。 您可以测试的特殊文件夹是否存在使用 HEAD 请求。 如果该文件夹不存在，将返回 HEAD 请求`404`响应。

##### <a name="request-folder-does-not-exist"></a>请求 （文件夹不存在）

<!-- { "blockType": "request", "name": "head-does-not-create-special-folder" } -->
```
HEAD /drive/special/{special-folder-name}
```

##### <a name="response"></a>响应
<!-- {"blockType": "response"} -->
```
HTTP/1.1 404 Not Found
```

##### <a name="request-folder-does-exist"></a>请求 （存在文件夹）

另一方面，当该文件夹已存在发送同一请求将返回`200 OK`响应。

<!-- { "blockType": "request", "name": "head-existing-special-folder", "scopes": "files.read" } -->
```
HEAD /drive/special/{special-folder-name}
```

##### <a name="response"></a>响应

<!-- {"blockType": "response", "isEmpty": true } -->
```
HTTP/1.1 200 OK
```

## <a name="remarks"></a>备注

若要请求特殊文件夹的子级，则可以请求`children`集合或使用展开子集合的[扩展](http://graph.microsoft.io/docs/overview/query_parameters)选项。


<!-- {
  "type": "#page.annotation",
  "description": "List drives",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Get special folder"
}-->
