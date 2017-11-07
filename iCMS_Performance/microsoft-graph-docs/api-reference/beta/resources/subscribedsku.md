# <a name="subscribedsku-resource-type"></a>subscribedSku 资源类型

只读取的操作都支持订阅的 Sku。创建、 更新和删除不受支持。 不支持查询筛选器表达式。 从[directoryObject](directoryobject.md)继承。


## <a name="methods"></a>方法
| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 subscribedSku](../api/subscribedsku_get.md) | [subscribedSku](subscribedsku.md) |读取属性和关系的 subscribedSku 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|capabilityStatus|String||
|consumedUnits|Int32||
|id|String| 键。 只读的。|
|prepaidUnits|[licenseUnitsDetail](licenseunitsdetail.md)||
|servicePlans|[servicePlanInfo](serviceplaninfo.md)集合||
|skuId|Guid||
|skuPartNumber|String||
|格值|String||

## <a name="relationships"></a>Relationships
无

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.subscribedSku"
}-->

```json
{
  "appliesTo": "string",
  "capabilityStatus": "string",
  "consumedUnits": 1024,
  "id": "string (identifier)",
  "prepaidUnits": {"@odata.type": "microsoft.graph.licenseUnitsDetail"},
  "servicePlans": [{"@odata.type": "microsoft.graph.servicePlanInfo"}],
  "skuId": "guid",
  "skuPartNumber": "string"
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "subscribedSku resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
