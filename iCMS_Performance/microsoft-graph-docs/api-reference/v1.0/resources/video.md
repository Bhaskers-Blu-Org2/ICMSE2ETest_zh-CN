# <a name="video-resource-type"></a>视频资源类型

**视频**资源指出一项视频媒体文件，并提供有关视频的详细信息。

## <a name="properties"></a>属性

| 属性 | 类型  | 说明                               |
|:---------|:------|:------------------------------------------|
| 比特率  | Int32 | 以位 / 秒的视频比特率。 |
| duration | Int64 | 以毫秒为单位的文件的持续时间。     |
| height   | Int32 | 视频中，以像素为单位的高度。           |
| width    | Int32 | 视频中，以像素为单位的宽度。            |



## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.video"
}-->

```json
{
  "bitrate": 1024,
  "duration": 1024,
  "height": 1024,
  "width": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "video resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
