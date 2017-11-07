# <a name="list-thumbnails-for-driveitem"></a>DriveItem 的列表缩略图

检索一组 thumbnailSet [driveItem 对象](../resources/driveitem.md)的资源。

驱动器中的项可以由零个或多个[thumbnailSet](../resources/thumbnailset.md)对象来表示。 每个**thumbnailSet**可以有一个或多个[**缩略图**](../resources/thumbnail.md)对象，这些对象表示的项的图像。 例如， **thumbnailSet**可能包含**缩略图**的对象，如常见的包括`small`， `medium`，或`large`。

有许多方法可以在 OneDrive 上使用缩略图。
下面是最常见的︰

* 枚举可用项的缩略图
* 检索单个项目缩略图
* 检索内容的缩略图
* 检索在单个请求中的多个项的缩略图
* 检索自定义缩略图的大小
* 将上载项的自定义缩略图
* 确定是否上传自定义缩略图存在


## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite


## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/root:/{item-path}:/thumbnails
GET /me/drive/items/{item-id}/thumbnails
GET /groups/<id>/drive/items/<item-id>/thumbnails
```
## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |

## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和响应正文中的[thumbnailSet](../resources/thumbnailset.md)对象的集合。

## <a name="example"></a>示例

##### <a name="request"></a>请求

下面是示例请求。

<!-- {
  "blockType": "request",
  "name": "get_thumbnails"
}-->
```http
GET /me/drive/items/<item-id>/thumbnails
```


##### <a name="response"></a>响应
这里是响应的示例。

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.thumbnailSet",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "id": "0",
      "small": { "height": 64, "width": 96, "url": "https://sn3302files..."},
      "medium": { "height": 117, "width": 176, "url": "https://sn3302files..."},
      "large": { "height": 533, "width": 800, "url": "https://sn3302files..."}
    }
  ]
}
```

## <a name="retrieve-a-single-thumbnail"></a>检索单个缩略图

通过解决其直接请求中检索单个缩略图和大小的元数据。

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "request", "name": "get-one-thumbnail" } -->
```http
GET /me/drive/items/<item-id>/thumbnails/<thumb-id>/<size>
```

## <a name="path-parameters"></a>路径参数

| 名称         | 类型   | 说明                                                                         |
|:-------------|:-------|:------------------------------------------------------------------------------------|
| **项 id**  | string | 项目引用的唯一标识符。                                      |
| **拇指 id** | number | 缩略图通常为 0 到 4 的索引。                                            |
| **大小**     | string | 请求的缩略图大小。 这必须是一个列出的标准大小。 |


<!-- { "blockType": "response", "@odata.type": "microsoft.graph.thumbnail" } -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "width": 100,
  "height": 100,
  "url": "http://onedrive.com/asd123a/asdjlkasjdkasdjlk.jpg"
}
```

## <a name="retrieve-thumbnail-content"></a>检索内容的缩略图

通过请求**的内容**缩略图的属性，可以直接检索内容的缩略图。

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "request", "name":"get-thumbnail-content" } -->
```http
GET /me/drive/items/<item-id>/thumbnails/<thumb-id>/<size>/content
```

## <a name="response"></a>响应

该服务与重定向响应该缩略图的 URL。

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 302 Found
Location: https://b0mpua-by3301.files.1drv.com/y23vmagahszhxzlcvhasdhasghasodfi
```

缩略图的 Url 是缓存安全。 该 URL 将更改，如果需要生成新的缩略图的方式更改该项。

## <a name="size-values"></a>大小值

下表定义了可能的缩略图大小。 虽然可以请求任何任意的缩略图大小，定义的值有可能存在，并且能迅速返回值︰

| 名称           | 解决方法  | 长宽比 | 说明                                                          |
|:---------------|:------------|:-------------|:---------------------------------------------------------------------|
| `small`        | 最长 96  | 源语言     | 小的、 高度压缩的缩略图裁剪成方形的长宽比。 |
| `medium`       | 最长 176 | 源语言     | 裁剪到标准项目的 OneDrive web 视图大小。         |
| `large`        | 最长的 800 | 源语言     | 缩略图带有调整到 800 像素的长边。               |


## <a name="remarks"></a>备注

**请注意**在业务和 SharePoint OneDrive:

* 这些调用用于展开缩略图集合将不起作用︰`GET /drive/root:/{item-path}?expand=children(expand=thumbnails)`
  `GET /drive/items/{item-id}/children?expand=thumbnails`


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get metadata and content for thumbnails of multiple sizes for OneDrive items.",
  "keywords": "thumbnail,content,download,sizes",
  "section": "documentation",
  "tocPath": "OneDrive/Item/List thumbnails"
} -->
