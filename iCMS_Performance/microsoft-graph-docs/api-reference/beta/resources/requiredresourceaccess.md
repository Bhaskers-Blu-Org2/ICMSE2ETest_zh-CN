# <a name="requiredresourceaccess-resource-type"></a>requiredResourceAccess 资源类型

指定 OAuth 2.0 权限范围和下指定应用程序需要访问的资源的应用程序角色的集。 指定的 OAuth 2.0 权限范围可能请求的客户端应用程序 （通过**requiredResourceAccess**集合中） 时调用资源应用程序。 [应用程序](application.md)实体的**requiredResourceAccess**属性是集合的**ReqiredResourceAccess**。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.requiredResourceAccess"
}-->

```json
{
  "resourceAccess": [{"@odata.type": "microsoft.graph.resourceAccess"}],
  "resourceAppId": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|resourceAccess|[ResourceAccess](resourceaccess.md)集合|OAuth2.0 权限范围和应用程序需要从指定的资源的应用程序角色的列表。|
|resourceAppId|String|应用程序需要访问的资源的唯一标识符。  这应该是等于上目标资源应用程序声明**应用程序标识**。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "requiredResourceAccess resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
