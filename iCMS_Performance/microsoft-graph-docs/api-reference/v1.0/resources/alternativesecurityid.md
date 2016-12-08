# <a name="alternativesecurityid-resource-type"></a>alternativeSecurityId 资源类型

包含与设备相关的可选的安全 ID。 [设备](device.md)实体的**alternativeSecurityIds**属性是集合的**alternativeSecurityId**。

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|identityProvider|String|            |
|Key|二进制|            |
|类型|Int32|            |


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.alternativeSecurityId"
}-->

```json
{
  "identityProvider": "string",
  "key": "binary",
  "type": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "alternativeSecurityId resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
