# <a name="search-for-an-item"></a>搜索项目

搜索查询匹配的项的项的层次结构。 您可以搜索和/或筛选结果以查找您的应用程序的项目正在寻找。

搜索从指定 URL 和该项的所有子项中的项返回匹配的结果。 筛选适用上的项的集合返回，使用搜索或只是直接子级使用集合可以是任一所有子级。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```
GET /me/drive/root/search(q='vacation')
GET /me/drive/items/{item-id}/search(q='vacation')
GET /me/drive/root:/{item-path}:/search(q='vacation')
```

## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

#### <a name="function-parameters"></a>函数参数

| 名称 | 值  | 说明                                                                                                                          |
|:-----|:-------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `q`  | string | 用来搜索项目的查询文本。 可能跨多个域，包括文件名、 元数据和文件内容相匹配的值。 |

## <a name="example"></a>示例
这里是如何调用此 API 的示例。

##### <a name="request"></a>请求

下面是一个示例搜索登录的用户的 OneDrive 请求的
<!-- {
  "blockType": "request",
  "name": "item_search"
}-->
```http
GET /me/drive/root/search(q='{search-query}')
```

##### <a name="response"></a>响应
此方法返回一个对象，包含与搜索条件匹配的[driveItems](../resources/driveitem.md)的数组。 如果未不找到任何项目，则返回一个空数组。

如果有太多的匹配项将分页响应和一个**@odata.nextLink**属性将包含下一步的结果页的 URL。 您可以使用`top`查询参数来指定页中的项的数目。

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
      {
        "id": "0123456789abc!123",
        "name": "Vacation photos",
        "folder": {},
        "searchResult": { "onClickTelemetryUrl": "https://bing.com/0123456789abc!123" }
      },
      {
        "id": "0123456789abc!456",
        "name": "Summer Vacation Rentals.docx",
        "file": {},
        "searchResult": { "onClickTelemetryUrl": "https://bing.com/0123456789abc!456" }
      }
    ],
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/drive/root/search(query='vacation')&skipToken=1asdlnjnkj1nalkm!asd"
}
```

## <a name="remarks"></a>备注

**注意︰**在业务和 SharePoint OneDrive，搜索不会返回以下属性︰

* `parentReference`


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item: search",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Items/Search items"
}-->
