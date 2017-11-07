# <a name="identityinfo-resource-type"></a>identityInfo 资源类型

表示范围角色的成员的用户。

## <a name="methods"></a>方法

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|显示名称|string|显示用户的名称。|
|id|string|用户的唯一标识符。|
|范围内|string|用户的用户主体名称。|

## <a name="relationships"></a>Relationships
无

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.identityInfo"
}-->

```json
{
  "displayName": "string",
  "id": "string",
  "userPrincipalName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "identityInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->