# <a name="resourceaccess-resource-type"></a>resourceAccess 资源类型

指定 OAuth 2.0 权限范围或应用程序要求应用程序角色。 [RequiredResourceAccess](requiredResourceAccess.md)类型的**resourceAccess**属性是集合的**ResourceAccess**。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.resourceAccess"
}-->

```json
{
  "id": "guid",
  "type": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|Guid|一个资源应用程序公开的[oAuth2Permission](oauth2permission.md)或[appRole](approle.md)实例的唯一标识符。|
|类型|String|指定的**id**属性是否引用[oAuth2Permission](oauth2permission.md)或[appRole](approle.md)。 可能的值为"范围"或"角色"。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "resourceAccess resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
