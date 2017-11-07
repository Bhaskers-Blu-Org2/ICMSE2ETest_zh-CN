# <a name="get-a-driveitem-resource"></a>获得 driveItem 资源

文件系统路径或唯一的 id 来检索驱动器中 driveItem 的元数据。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/<item-id>
GET /me/drive/root:/<item-path>
GET /groups/<group-id>/drive/items/<item-id>
```

## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头

| 名称          | 值  | 说明                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                |
| 如果没有-匹配 | String | 如果此请求标头将包含并提供 eTag （或 cTag） 匹配当前标记的文件，`HTTP 304 Not Modified`返回的响应。 |


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[项目](../resources/driveitem.md)对象。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。

##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_item"
}-->
```
GET /me/drive/items/{item-id}
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
  "createdBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "createdDateTime": "2016-03-21T20:01:37Z",
  "cTag": "\"c:{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},0\"",
  "eTag": "\"{86EB4C8E-D20D-46B9-AD41-23B8868DDA8A},1\"",
  "file": {  },
  "id": "01NKDM7HMOJTVYMDOSXFDK2QJDXCDI3WUK",
  "lastModifiedBy": {
      "user": {
          "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
          "displayName": "Ryan Gregg"
      }
  },
  "lastModifiedDateTime": "2016-03-21T20:01:37Z",
  "name": "OneDrive Graph API.docx",
  "parentReference": {
      "driveId": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "id": "01NKDM7HN6Y2GOVW7725BZO354PWSELRRZ",
      "path": "/drive/root:"
  },
  "size": 31679,
  "webUrl": "https://contoso-my.sharepoint.com/personal/rgregg_contoso_com/Documents/OneDrive%20Graph%20API.docx"
}
```

## <a name="notes"></a>注释

您可以使用[`expand`](https://dev.onedrive.com/odata/optional-query-parameters.htm#expanding-collections)查询字符串参数来作为检索的项的元数据的同一个调用中包含项的子项。

## <a name="head-requests"></a>HEAD 请求

在大多数情况下，HEAD 请求将行为与 GET 请求相同的方式。 有一些差异︰

1. HEAD 请求将只返回相应的 GET 请求标头。 这是标准做法 HEAD 响应。
2. HEAD 请求将自动提供一个[特殊的文件夹](../resources/specialfolder.md)。
   相反，如果一个特殊的文件夹不存在， `404` ，则会返回错误。

在此示例中，您可以看到，请求驱动器的根目录资源将以响应只是`200 OK`。

## <a name="http-request"></a>HTTP 请求

<!-- {"blockType": "request", "name": "head-root"} -->
```
HEAD /me/drive/root
Accept: application/json
```

## <a name="response"></a>响应

<!-- {"blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true} -->
```
HTTP/1.1 200 OK
Content-Type: application/json
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Get item"
}-->
