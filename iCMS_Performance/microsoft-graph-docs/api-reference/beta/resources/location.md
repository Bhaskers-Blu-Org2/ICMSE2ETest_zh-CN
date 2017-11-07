# <a name="location-resource-type"></a>位置的资源类型

表示事件的位置信息。


## <a name="properties"></a>属性
| 属性  | 类型   | 说明                                                     |
|:----------|:-------|:----------------------------------------------------------------|
| address | [physicalAddress](physicalAddress.md) |街道地址的位置。 |
| 坐标 | [outlookGeoCoordinates](outlookGeoCoordinates.md) |地理坐标、 提升和其程度的物理位置的准确性。 |
| 显示名称  | String | 与该位置关联的名称。                       |
| locationEmailAddress | String | 可选的电子邮件地址的位置。              |
| locationUri | String | 可选表示的位置的 URI。|


## <a name="json-representation"></a>JSON 表示形式

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.location"
}-->
```json
{
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "coordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},  
  "displayName": "string",
  "locationEmailAddress": "string",
  "locationUri": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "location resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->