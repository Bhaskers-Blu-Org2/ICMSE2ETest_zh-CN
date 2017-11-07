# <a name="resource-resource-type"></a>资源的资源类型

包含图像或其他文件资源在 OneNote 页上。 

您可以获得资源的二进制数据，但不是支持获取的资源对象或资源集合的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.resource"
}-->

获取对资源的请求，通过发送获取特定资源的二进制数据`content`终结点︰

```
GET ../notes/resources/<id>/content
```

文件的资源时可以使用下列请求的页面的 HTML 内容，则会返回 URI:

```
GET ../notes/pages/<id>/content
```

在页面的 HTML 中，`img`标记包含终结点中的原始图像资源`data-fullres-src`特性和优化的映像中`src`属性︰
```
<img 
    src="image-resource-url"  
    data-src-type="media-type"
    data-fullres-src="image-resource-url"  
    data-fullres-src-type="media-type" ... />
```

`object`标签 （它表示如 PDF，DOCX 和 PNG 文件） 包括文件资源中的终结点`data`属性︰

```
<object
    data="file-resource-url"
    data-attachment="file-name.file-type" 
    type="media-type" ... />
```

## <a name="properties"></a>属性
无。

## <a name="relationships"></a>Relationships
无。


## <a name="methods"></a>方法
| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取资源的二进制数据](../api/resource_get.md) | Stream |检索文件或图像资源的二进制数据。|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "resource resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->