# <a name="create-page"></a>创建页

指定的节中创建一个新[页](../resources/page.md)。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰   
Notes.Create、 Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite 或 Notes.ReadWrite.All 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/sections/<id>/pages
POST /users/<id | userPrincipalName>/notes/sections/<id>/pages
POST /groups/<id>/notes/sections/<id>/pages
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |
| 内容类型 | string | `text/html`或`application/xhtml+xml`的 HTML 内容，包括有关的多部分请求所需的"演示文稿"部分。 多部分请求使用`multipart/form-data; boundary=your-boundary`内容类型。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供页面 HTML 内容。

正文可以包含 HTML 直接放在请求正文中，或者它可以包含多部分邮件格式，如示例中所示。 如果要发送二进制数据，则必须发送一个多部分的请求。

## <a name="response"></a>响应
如果成功，此方法返回`201 Created`响应代码和新的[page](../resources/page.md)对象在响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。

<!-- { "blockType": "ignored" } -->
```http
POST https://graph.microsoft.com/beta/me/notes/sections/<id>/pages
Content-length: 312
Content-type: multipart/form-data; boundary=MyPartBoundary198374

--MyPartBoundary198374
Content-Disposition:form-data; name="Presentation"
Content-Type:text/html

<!DOCTYPE html>
<html>
  <head>
    <title>A page with <i>rendered</i> images and an <b>attached</b> file</title>
    <meta name="created" content="2015-07-22T09:00:00-08:00" />
  </head>
  <body>
    <p>Here's an image from an online source:</p>
    <img src="http://..." alt="an image on the page" width="500" />
    <p>Here's an image uploaded as binary data:</p>
    <img src="name:imageBlock1" alt="an image on the page" width="300" />
    <p>Here's a file attachment:</p>
    <object data-attachment="FileName.pdf" data="name:fileBlock1" type="application/pdf" />
  </body>
</html>

--MyPartBoundary198374
Content-Disposition:form-data; name="imageBlock1"
Content-Type:image/jpeg

... binary image data ...

--MyPartBoundary198374
Content-Disposition:form-data; name="fileBlock1"
Content-Type:application/pdf

... binary file data ...

--MyPartBoundary198374--
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 此处所示的响应对象将被截断为简洁起见。 从实际调用将返回的所有属性。
<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 312

{
  "title": "title-value",
  "createdByAppId": "createdByAppId-value",
  "links": {
    "oneNoteClientUrl": {
      "href": "href-value"
    },
    "oneNoteWebUrl": {
      "href": "href-value"
    }
  },
  "contentUrl": "contentUrl-value",
  "content": "content-value",
  "lastModifiedTime": "datetime-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Page",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->