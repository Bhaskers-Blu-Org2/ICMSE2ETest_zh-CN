# <a name="oauth2permission-resource-type"></a>oAuth2Permission 资源类型

表示一个 OAuth 2.0 委派的权限范围。 指定的 OAuth 2.0 版可能请求委派的权限范围 （通过[应用程序](application.md)对象的**requiredResourceAccess**集合） 的客户端应用程序调用资源应用程序时。 **AppRoles**属性和[应用程序](application.md)实体的[servicePrincipal](serviceprincipal.md)实体是**oAuth2Permission**的集合。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.oAuth2Permission"
}-->

```json
{
  "adminConsentDescription": "string",
  "adminConsentDisplayName": "string",
  "id": "guid",
  "isEnabled": true,
  "origin": "string",
  "type": "string",
  "userConsentDescription": "string",
  "userConsentDisplayName": "string",
  "value": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|adminConsentDescription|String|权限管理员同意的情况下，应用程序分配经验中显示的帮助文本。|
|adminConsentDisplayName|String|权限管理员同意的情况下，应用程序分配经验中出现的显示名称。|
|id|Guid|唯一的作用域权限中的 oauth2Permissions 集的标识符。|
|启用|Boolean|当创建或更新权限时，此属性必须设置为**true** （这是默认值）。 若要删除权限，此属性必须首先设置为**false**。  此时，在后续调用中，可能会删除权限。|
|类型|String|指定是否此范围的权限可以同意由最终用户，或者是否必须要同意由公司管理员组织范围内的权限。  可能的值为"用户"或"管理员"。|
|userConsentDescription|String|权限帮助文本显示在最终用户同意的情况下体验中。|
|userConsentDisplayName|String|显示名称将显示在最终用户同意的情况下体验的权限。|
|value|String|OAuth 2.0 访问令牌中预见资源应用程序的范围内声明的值。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "oAuth2Permission resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
