# <a name="passwordcredential-resource-type"></a>passwordCredential 资源类型

包含与应用程序或服务主体相关联的密码凭据。 **PasswordCredentials**属性和[应用程序](application.md)实体的[servicePrincipal](serviceprincipal.md)实体是**passwordCredential**的集合。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.passwordCredential"
}-->

```json
{
  "customKeyIdentifier": "binary",
  "endDate": "String (timestamp)",
  "keyId": "guid",
  "startDate": "String (timestamp)",
  "value": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|customKeyIdentifier|二进制|            |
|结束日期|方法|过期日期和时间的密码。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|密钥 id 为|Guid|            |
|开始日期|方法|日期和密码生效的时间。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|value|String|            |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "passwordCredential resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
