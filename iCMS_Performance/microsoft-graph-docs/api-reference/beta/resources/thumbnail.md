# <a name="thumbnail-resource-type"></a>缩略图的资源类型

**缩略图**资源类型表示为图像、 视频、 文档或任何文件或上具有的图形化表示的 OneDrive 文件夹缩略图。

## <a name="properties"></a>属性

| 属性 | 类型   | 说明                                  |
|:---------|:-------|:---------------------------------------------|
| height   | Int32  | 在缩略图，以像素为单位的高度。      |
| url      | String | 用于提取缩略图的内容的 URL。 |
| width    | Int32  | 在缩略图，以像素为单位的宽度。       |


## <a name="relationships"></a>Relationships

| 名称    | 类型   | 说明         |
|:--------|:-------|:--------------------|
| 内容 | Stream | 内容的流。 |


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": ["content", "height", "width"],
  "@odata.type": "microsoft.graph.thumbnail"
}-->

```json
{
  "url": "string",
  "height": 1024,
  "width": 1024,
  "content": "stream"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "thumbnail resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
