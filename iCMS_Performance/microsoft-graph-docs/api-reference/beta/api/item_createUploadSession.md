# <a name="upload-large-files-with-an-upload-session"></a>上载大文件上载会话

创建上载会话以允许您的应用程序上载超过最大文件大小的文件。
在上载会话允许您的应用程序上载 sequental API 请求，这样，如果在上载过程中断开连接时可以继续在传输的文件的范围。

若要上载使用上载会话的文件，有两个步骤︰

1. [创建上载会话](#create-an-upload-session)
2. [在上载会话到上载字节](#upload-bytes-to-the-upload-session)

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="create-an-upload-session"></a>创建上载会话

要开始大文件上传，您的应用程序首先必须请求新的上载会话。
这将创建一个临时存储位置直到上载完成文件将保存的文件的字节数。
一旦已上载的文件的最后一个字节在上载会话完成，最终的文件出现在目标文件夹中。

### <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/drive/root:/{path-to-item}:/createUploadSession
POST /me/drive/items/{parent-item-id}:/{filename}:/createUploadSession
```

### <a name="request-body"></a>请求正文
没有请求正文是必需的。 但是，您可以指定请求正文提供有关正在上载的文件的其他数据。

例如，如果该文件名已被控制的行为，可以指定冲突行为属性请求的正文中。

```json
{
    "item": {
        "@microsoft.graph.conflictBehavior": "rename"
    }
}
```

### <a name="optional-request-headers"></a>可选的请求标头

| 名称       | 值 | 说明                                                                                                                                                            |
|:-----------|:------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *如果匹配* | etag  | 如果此请求标头将包含并提供 eTag （或 cTag） 不匹配的项目，当前的 etag `412 Precondition Failed` errr 响应则返回。 |


### <a name="response"></a>响应
对此请求的响应将提供新创建[uploadSession](../resources/uploadsession.md)，其中包括用于上传文件的部分的 URL 的详细信息。 

### <a name="example"></a>示例

<!-- {
  "blockType": "request",
  "name": "driveItem_createUploadSession"
}-->
```http
POST /me/drive/root:/{item-path}:/createUploadSession
```

### <a name="response"></a>响应
这里是响应的示例。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.uploadSession"
} -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "uploadUrl": "https://tenant-my.sharepoint.com/alkjl1kjklna",
  "expirationDateTime": "2020-08-24T10:58:00Z",
  "nextExpectedRanges": ["0-"]
}
```

## <a name="upload-bytes-to-the-upload-session"></a>在上载会话到上载字节

若要上载的文件或文件的某一部分，您的应用程序时，可使一个 PUT 请求对**createUploadSession**响应中收到的**uploadUrl**值。
您可以上载整个文件，或将文件拆分为若干段，只要在任何给定的请求的最大字节数是少于 60 MiB。
必须按顺序 sequentally 上载文件的片段。
上传无序的片段将导致错误。

**注意︰**如果您的应用程序将一个文件拆分成多个段，**必须**每个片段的大小是 320 KiB 的倍数。 使用由 320 不均匀除片断大小会导致提交某些文件的错误。

### <a name="example"></a>示例

本示例为上载前 26 个字节的 128 字节的文件。
**内容长度**标头指定当前请求的大小。
**内容范围**标头指示表示此请求的总体文件中的字节范围。
可以上载的文件的第一个片段之前，必须知道文件的总长度。

<!-- { "blockType": "request", "name": "upload-fragment-piece", "scopes": "files.readwrite" } -->
```
PUT https://tenant-my.sharepoint.com/alkjl1kjklna
Content-Length: 26
Content-Range: bytes 0-25/128

<bytes 0-25 of the file>
```

**重要︰**您的应用程序必须确保**内容范围**标头中指定的总文件大小都相同的所有请求。
如果一段声明不同的文件大小，则请求将失败。

### <a name="response"></a>响应
<!-- { "blockType": "response", "@odata.type": "microsoft.graph.uploadSession", "truncated": true } -->
```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "expirationDateTime": "2015-01-29T09:21:55.523Z",
  "nextExpectedRanges": ["26-"]
}
```

您的应用程序可以使用**nextExpectedRanges**值来确定从何处着手下一步的片段。
您可能看到指定的多个区域，指示服务器尚未收到文件的各个部分。 如果您需要恢复已中断的传输，并且您的客户端不能确定服务的状态，这很有用。

您应首先确定片段大小根据下面的最佳做法。 不要假定该**nextExpectedRanges**将返回上载碎片适当大小的 reanges。 **NextExpectedRanges**属性指示的文件尚未收到的范围并不的图案应该上载文件的方式。

**注释︰**

* `nextExpectedRanges`属性始终不会列出所有丢失的区域。
* 成功的片段写入，它将返回下一个范围从 （如启动 "523-"）。
* 在失败时的客户端发送已收到服务器的片段，服务器将响应`HTTP 416 Requested Range Not Satisfiable`。 
  您可以[上载状态请求](#resuming-an-in-progress-upload)以获取更详细的缺失的范围列表。


## <a name="completing-a-file"></a>完成一个文件

服务器接收到一个文件的最后片段时将响应时使用`HTTP 201 Created`或`HTTP 200 OK`。
响应正文，还将包括为**driveItem**表示已完成的文件设置的默认属性。

<!-- { "blockType": "request", "name": "upload-fragment-final", "scopes": "files.readwrite" } -->
```
PUT https://tenant-my.sharepoint.com/alkjl1kjklna
Content-Length: 21
Content-Range: bytes 101-127/128

<final bytes of the file>
```

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.driveItem", "truncated": true } -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "912310013A123",
  "name": "largefile.vhd",
  "size": 128,
  "file": { }
}
```
**注意︰**项的响应被截断为文档清晰。

## <a name="cancel-an-upload-session"></a>取消在上载会话

若要取消上载会话到上载 URL 发送删除请求。
这清理临时文件按住以前上载的数据。
这应在方案中止上载是位置，例如，如果用户取消转移。

临时文件和其随附的上载会话自动清理**expirationDateTime**过后。

### <a name="example"></a>示例

删除请求将 immedately 终止上载会话，并删除任何以前上载的字节数。

<!-- { "blockType": "request", "name": "upload-fragment-cancel", "scopes": "files.readwrite" } -->
```http
DELETE https://tenant-my.sharepoint.com/alkjl1kjklna
```

### <a name="response"></a>响应

<!-- { "blockType": "response" } -->
```http
HTTP/1.1 204 No Content
```

## <a name="resuming-an-in-progress-upload"></a>恢复正在进行上载

如果上载请求已断开连接或请求完成之前发生了故障，将忽略该请求中的所有字节。
如果您的应用程序和服务之间的连接断开，这可能发生。
如果发生这种情况，您的应用程序仍可以继续从以前已完成的片段文件传输。

若要查找以前已接收的字节范围，您的应用程序可以请求上载会话的状态。

### <a name="example"></a>示例
通过发送一个 GET 请求的查询的上载状态`uploadUrl`。

<!-- { "blockType": "request", "name": "upload-fragment-resume", "scopes": "files.readwrite" } -->
```
GET https://tenant-my.sharepoint.com/alkjl1kjklna
```

服务器将响应缺少需要上载的字节范围，并在上载会话过期时间的列表。

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.uploadSession", "truncated": true } -->
```http
HTTP/1.1 200 OK

{
  "expirationDateTime": "2015-01-29T09:21:55.523Z",
  "nextExpectedRanges": ["12345-"]
}
```

### <a name="upload-remaining-data"></a>将剩余的数据上载
现在，您的应用程序知道从哪里开始上的传，[传到上载会话](#upload-bytes-to-the-upload-session)中的步骤继续上载。


## <a name="best-practices"></a>最佳做法

* 恢复或重试上载由连接中断或包括任何 5xx 错误引起的失败︰
  * `500 Internal Server Error`
  * `502 Bad Gateway`
  * `503 Service Unavailable`
  * `504 Gateway Timeout`
* 如果恢复或重试上载请求时返回任何 5xx 服务器错误，请使用指数后退战略。
* 对于其它错误，不应使用指数后退战略而进行的重试次数的限制。
* 处理`404 Not Found`进行可恢复上载由开始整个上载时的错误。
* 使用可恢复的文件大于 10 的 MiB 文件的传输 (10 \* 1024年\*1024 字节)。
* 为稳定高速的连接 10 个 MiB 片断大小是最佳的。 
  对于速度较慢或不可靠的连接可能会更好的结果，从较小的片段。 
  建议使用的片段大小为 5-10 MiB。
* 使用片段大小的倍数的 320 KiB (320 \* 1024 字节)。 
  不能使用片段大小的倍数的 320 KiB 可能会导致失败后的最后一个片段被上载大文件的传输。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Upload item",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
