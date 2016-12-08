# <a name="approle-resource-type"></a>appRole 资源类型

表示应用程序角色可能由客户端应用程序调用另一个应用程序请求的或可能用于分配给用户或组指定的应用程序角色的应用程序。 **AppRoles**属性和[应用程序](application.md)实体的[servicePrincipal](serviceprincipal.md)实体是**appRole**的集合。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.approle"
}-->

```json
{
  "allowedMemberTypes": ["string"],
  "description": "string",
  "displayName": "string",
  "id": "guid",
  "isEnabled": true,
  "origin": "string",
  "value": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|allowedMemberTypes|字符串集合|设置"应用程序"，或者对二者同时指定此应用程序的角色定义可以被设置为"用户"，或其他应用程序 （即访问此应用程序在后台程序服务情况下） 分配给用户和组。|
|description|字符串|权限帮助管理应用程序分配中出现的文本，并同意体验。|
|显示名称|String|权限管理员同意的情况下，应用程序分配经验中出现的显示名称。|
|id|Guid|**AppRoles**集合内的角色的唯一标识符。|
|启用|Boolean|当创建或更新角色定义，这必须设置为**true** （这是默认值）。 若要删除角色，这必须首先被设置为**false**。  此时，在后续调用中，可能会删除此角色。|
|value|String|指定在身份验证和访问令牌中的预见，该应用程序角色声明的值。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "appRole resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->