# <a name="passwordprofile-resource-type"></a>passwordProfile 资源类型

包含与特定用户关联的密码配置文件。 [用户](user.md)实体的**passwordProfile**属性是一个**passwordProfile**对象。


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|forceChangePasswordNextSignIn|Boolean| **如此**如果用户必须更改密码在下次登录时;其他**假**。 |
|password|String|用户的密码。 在创建用户时，此属性是必需的。 可以更新，但将要求用户在下次登录时更改密码。 密码必须满足用户的**passwordPolicies**属性指定的最小要求。 默认情况下，使用强密码是必需的。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.passwordprofile"
}-->

```json
{
  "forceChangePasswordNextSignIn": true,
  "password": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "passwordProfile resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->