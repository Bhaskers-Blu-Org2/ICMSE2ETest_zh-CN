# <a name="geocoordinates-resource-type"></a>geoCoordinates 资源类型

地理坐标和提升的一个位置。

此资源组地理位置相关的数据上 OneDrive 到一个单一的结构。 它出现在**位置**属性中的项目资源相关联的地理位置上。


## <a name="properties"></a>属性

| 属性  | 类型   | 说明                                                    |
|:----------|:-------|:---------------------------------------------------------------|
| 海拔  | Double | 海拔高度 （高） 中项的海平面英尺。 |
| 纬度  | Double | 在十进制中，物料的纬度。                        |
| 经度 | Double | 在十进制中，物料的经度。                       |

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.geoCoordinates"
}-->

```json
{
  "altitude": 1024.13,
  "latitude": 26.13246,
  "longitude": 24.34616
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "geoCoordinates resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
