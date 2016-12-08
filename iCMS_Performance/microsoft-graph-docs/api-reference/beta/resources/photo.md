# <a name="photo-resource-type"></a>照片资源类型

**照片**资源提供照片和照相机属性，例如，EXIF 元数据， [driveItem](driveitem.md)。


## <a name="properties"></a>属性
| 属性                | 类型                      | 说明                                                     |
|:------------------------|:--------------------------|:----------------------------------------------------------------|
| **takenDateTime**       | 方法            | 表示的日期和照片的拍摄的时间。 只读的。               |
| **cameraMake**          | String                    | 相机制造商。 只读的。                                            |
| **cameraModel**         | String                    | 相机模型。 只读的。                                                   |
| **fNumber**             | Double                    | 从照相机 F-stop 值。 只读的。                               |
| **exposureDenominator** | Int32                     | 从相机曝光时间分数分母。 只读的。 |
| **exposureNumerator**   | Int32                     | 从相机曝光时间分数的分子。 只读的。   |
| **focalLength**         | Double                    | 从照相机的焦距。 只读的。                               |
| **iso**                 | Int32                     | 从相机的 ISO 值。 只读的。                                  |

## <a name="json-representation"></a>JSON 表示形式

<!-- {
  "blockType": "resource",
  "optionalProperties": [  ],
  "@odata.type": "microsoft.graph.photo"
}-->
```json
{
  "cameraMake": "string",
  "cameraModel": "string",
  "exposureDenominator": 1024,
  "exposureNumerator": 1024,
  "fNumber": 1024,
  "focalLength": 1024,
  "iso": 1024,
  "takenDateTime": "String (timestamp)"
}
```

## <a name="remarks"></a>备注
业务和 SharePoint OneDrive 仅返回的**takenDateTime**属性。


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "photo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
