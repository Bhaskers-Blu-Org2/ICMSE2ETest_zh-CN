# <a name="thumbnailset-resource-type"></a>thumbnailSet 资源类型

**ThumbnailSet**类型为[缩略图](thumbnail.md)对象的键控的集合。 它用来表示一套与 OneDrive 上的单个文件的缩略图。


## <a name="methods"></a>方法

| 方法                                         | 返回类型                     | 说明                                               |
|:-----------------------------------------------|:--------------------------------|:----------------------------------------------------------|
| [获得 thumbnailSet](../api/thumbnailset_get.md) | [thumbnailSet](thumbnailset.md) | 读取属性和关系的 thumbnailSet 对象。 |

## <a name="properties"></a>属性

| 属性 | 类型                      | 说明                                                                       |
|:---------|:--------------------------|:----------------------------------------------------------------------------------|
| id       | String                    | 在项目 id。 只读的。                                                |
| 大    | [缩略图](thumbnail.md) | 1920 x 1920 缩放后的缩略图。                                                     |
| 中等深浅   | [缩略图](thumbnail.md) | 176 x 176 缩放后的缩略图。                                                       |
| 小    | [缩略图](thumbnail.md) | 一个 48x48 裁剪缩略图。                                                        |
| 来源   | [缩略图](thumbnail.md) | 自定义缩略图图像或原始图像用来生成其他缩略图。 |


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "source"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.thumbnailSet"
}-->

```json
{
  "id": "string (identifier)",
  "large": {"@odata.type": "microsoft.graph.thumbnail"},
  "medium": {"@odata.type": "microsoft.graph.thumbnail"},
  "small": {"@odata.type": "microsoft.graph.thumbnail"},
  "source": {"@odata.type": "microsoft.graph.thumbnail"}
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "thumbnailSet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
