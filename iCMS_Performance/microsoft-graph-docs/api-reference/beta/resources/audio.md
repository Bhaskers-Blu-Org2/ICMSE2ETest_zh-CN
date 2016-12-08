# <a name="audio-resource-type"></a>音频资源类型

**音频**资源分组到一个单一的结构与音频相关的数据，在一个项目上。

## <a name="properties"></a>属性

| 属性          | 类型    | 说明                                                          |
|:------------------|:--------|:---------------------------------------------------------------------|
| 唱片集             | string  | 此音频文件的唱集的标题。                          |
| albumArtist       | string  | 音频文件上专辑命名为艺术家。                    |
| 艺术家            | string  | 音频文件表演艺术家。                            |
| 比特率           | string  | 比特率以 kbps 为单位表示。                                           |
| 作曲者         | string  | 音频文件的编辑器的名称。                          |
| 版权         | string  | 音频文件的版权信息。                            |
| 光盘              | number  | 此音频文件来自的磁盘的数量。                    |
| discCount         | number  | 此相册中的磁盘的总数。                             |
| duration          | number  | 音频文件，以毫秒为单位的持续时间                |
| 流派             | string  | 此音频文件 genre。                                        |
| hasDrm            | 布尔 | 如果文件受数字版权管理保护的指示。   |
| isVariableBitrate | 布尔 | 指示是否用可变比特率编码的文件。            |
| title             | string  | 音频文件的标题。                                         |
| 跟踪             | number  | 此音频文件原始光盘上的轨道数。    |
| trackCount        | number  | 此音频文件原始光盘上的曲目的总数。 |
| 年份              | number  | 一年录制的音频文件。                                |

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.audio"
}-->
```json
{
  "album": "string",
  "albumArtist": "string",
  "artist": "string",
  "bitrate": 1024,
  "composers": "string",
  "copyright": "string",
  "disc": 1024,
  "discCount": 1024,
  "duration": 1024,
  "genre": "string",
  "hasDrm": true,
  "isVariableBitrate": true,
  "title": "string",
  "track": 1024,
  "trackCount": 1024,
  "year": 1024
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "audio resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->