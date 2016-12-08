# <a name="outlookgeocoordinates-resource-type"></a>outlookGeoCoordinates 资源类型

地理坐标、 提升和其程度的物理位置的准确性。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.outlookGeoCoordinates"
}-->

```json
{
  "accuracy": 1024,
  "altitude": 1024,
  "altitudeAccuracy": 1024,
  "latitude": 1024,
  "longitude": 1024
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|准确性|double|纬度和经度的准确性。 举一个例子，准确性可以度量在米，例如纬度和经度是精确到 50 米。|
|海拔|double|海拔高度的位置。|
|altitudeAccuracy|double|海拔高度的精确性。|
|纬度|double|位置的纬度。|
|经度|double|位置的经度。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "outlookGeoCoordinates resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->