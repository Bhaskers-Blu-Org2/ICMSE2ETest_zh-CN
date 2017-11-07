# <a name="oauth2permissiongrant-resource-type"></a>oAuth2PermissionGrant 资源类型

表示用户或管理员同意过程的一部分 （由服务主体） 的应用程序被授予 OAuth 2.0 委派权限范围。 


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.oAuth2Permissiongrant"
}-->

```json
{
  "clientId": "string",
  "consentType": "string",
  "expiryTime": "String (timestamp)",
  "id": "string (identifier)",
  "principalId": "string",
  "resourceId": "string",
  "scope": "string",
  "startTime": "String (timestamp)"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|客户机 Id|String||
|consentType|String||
|expiryTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|对象 Id|String| 只读的。|
|principalId|String||
|资源 Id|String||
|scope|String||
|开始时间|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 oAuth2PermissionGrant](../api/oauth2permissiongrant_get.md) | [oAuth2PermissionGrant](oauth2permissiongrant.md) |读取属性和关系的 oAuth2PermissionGrant 对象。|
|[更新](../api/oauth2permissiongrant_update.md) | [oAuth2PermissionGrant](oauth2permissiongrant.md)   |更新 oAuth2PermissionGrant 对象。 |
|[删除](../api/oauth2permissiongrant_delete.md) | 无 |删除 oAuth2PermissionGrant 对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "oAuth2PermissionGrant resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->