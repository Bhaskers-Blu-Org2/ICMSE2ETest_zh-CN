# <a name="image-resource-type"></a>图像资源类型

**图像**资源出现在这些项表示位图或图像上。


## <a name="properties"></a>属性

| 属性   | 类型  | 说明                                |
|:-----------|:------|:-------------------------------------------|
| **高度** | Int32 | 以像素为单位的图像的高度。 只读的。 |
| **宽度**  | Int32 | 图像，以像素为单位的宽度。 只读的。  |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.image"
}-->

```json
{
  "height": 1024,
  "width": 1024
}

```

## <a name="remarks"></a>备注

在业务的 OneDrive，在项上，预期是基于文件扩展名的图像时，将返回该资源。 此资源业务的 OneDrive 返回任何属性。


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "image resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
