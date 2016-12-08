# <a name="download-the-contents-of-a-driveitem"></a>下载 driveItem 的内容

下载 driveItem 的内容。 可以下载仅 driveItem 具有的**文件**属性。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/items/{item-id}/content
GET /me/drive/root:/{item-path and filename}:/content
GET /groups/<id>/drive/items/<item-id>/content
```

## <a name="request-headers"></a>请求标头

| 名称          | 值  | 说明                                                                                                                                              |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 授权 | string | 持有者<token>。 必需。                                                                                                                                |
| 如果没有-匹配 | String | 如果此请求标头将包含并提供 eTag （或 cTag） 匹配当前标记的文件，`HTTP 304 Not Modified`返回的响应。 |
| Range         | 区域  | 在响应中返回的字节范围。                                                                                                                 |


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。


<!-- { "blockType": "request", "name": "driveitem-download-contents" } -->
```http
GET /me/drive/items/{item-id}/content
```

##### <a name="response"></a>响应
返回`302 Found`响应重定向到文件的预身份验证的下载 URL。 这是同一个 URL 可通过`@content.downloadUrl`的项的属性。

下载您的应用程序将需要按照该文件的内容`Location`在响应中的标头。

预身份验证的下载 Url 短的一段时间 （几分钟后） 才有效，而不需要`Authorization`邮件头以下载。

<!-- { "blockType": "response", "@odata.type": "stream" } -->
```http
HTTP/1.1 302 Found
Location: https://b0mpua-by3301.files.1drv.com/y23vmagahszhxzlcvhasdhasghasodfi
```

## <a name="range-downloads"></a>范围的下载

若要下载部分的项目范围，请在[RFC 2616](https://www.ietf.org/rfc/rfc2616.txt)中指定使用范围 HTTP 标头。 请注意，必须在接收后的 HTTP 请求追加 Range 标头`302 Found`。

<!-- { "blockType": "request", "name": "driveitem-get-partial-content" } -->
```http
GET https://b0mpua-by3301.files.1drv.com/y23vmag
Range: bytes=0-1023
```

这将返回`HTTP 206 Partial Content`字节的请求范围内的响应文件中。 如果无法生成范围 Range 标头可能会忽略和`HTTP 200`将返回的响应文件的完整内容。

<!-- { "blockType": "response", "@odata.type": "stream" } -->
```http
HTTP/1.1 206 Partial Content
Content-Range: bytes 0-1023/2048

<first 1024 bytes of file>
```

## <a name="notes"></a>注释  

当通过请求其 /content 下载项的内容属性，必须提供身份验证头中，以便授予访问下载。 正常情况下将返回响应`302`重定向到文件，可以从下载的 URL。 此 URL 预身份验证，并且不需要身份验证头。


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Download item",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Download file"
}-->
