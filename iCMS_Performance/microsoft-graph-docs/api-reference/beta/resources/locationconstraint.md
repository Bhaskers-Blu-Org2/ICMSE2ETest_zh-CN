# <a name="locationconstraint-resource-type"></a>locationConstraint 资源类型

客户端位置的会议可通过所列的条件。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.locationconstraint"
}-->

```json
{
  "isRequired": true,
  "locations": [{"@odata.type": "microsoft.graph.location"}],
  "suggestLocation": true
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|isRequired|Boolean|客户端请求服务响应中包括会议的会议地点。|
|位置|[位置](location.md)的集合|客户端请求的会议的一个或多个位置。|
|suggestLocation|Boolean|客户端请求服务或多个会议地点提出建议。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "locationConstraint resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->