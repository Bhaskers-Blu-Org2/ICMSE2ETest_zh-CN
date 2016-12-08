# <a name="update-serviceprincipal"></a>更新 serviceprincipal

更新 serviceprincipal 对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /servicePrincipals/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|accountEnabled|Boolean|                **如此**如果启用服务主体帐户;否则为**假**。            |
|appDisplayName|String|由关联的应用程序显示名称。|
|应用程序标识|String|对于关联的应用程序 （及其**应用程序标识**属性） 的唯一标识符。|
|appRoleAssignmentRequired|Boolean|指定用户或组对**appRoleAssignment**都要求之前 Azure 的广告会对应用程序发出用户的访问令牌。                            **备注**︰ 需要 1.5 版或更高版本时，不可以为 null。            |
|appRoles|appRole|应用程序角色关联的应用程序公开。 详细信息请参阅**appRoles**属性定义对应用程序实体**说明**︰ 需要 1.5 版或更高版本时，不可以为 null。            |
|显示名称|String|服务主体为显示名称。|
|errorUrl|String|            |
|主页|String|指向关联的应用程序的主页的 URL。|
|keyCredentials|keyCredential|凭据与主体服务相关联的集合。                            **备注**︰ 不可以为 null。            |
|logoutUrl|String|            |
|oauth2Permissions|oAuth2Permission|OAuth 2.0 权限关联的应用程序公开。 详细信息请参阅应用程序实体上的**oauth2Permissions**属性定义。                            **备注**︰ 需要 1.5 版或更高版本时，不可以为 null。            |
|passwordCredentials|passwordCredential|服务主体与相关联的密码凭据集合。                            **备注**︰ 不可以为 null。            |
|preferredTokenSigningKeyThumbprint|String|保留为仅供内部使用。 不要写或否则依赖于此属性。 可能会在将来版本中删除。                            **备注**︰ 要求版本 1.5 或更高版本。            |
|publisherName|String|在其中指定关联的应用程序组织显示名称。|
|replyUrls|String|用户令牌发送给以登录关联的应用程序或重定向 Uri 的 OAuth 2.0 授权码，并访问令牌发送给关联应用程序的 Url。                            **备注**︰ 不可以为 null。            |
|samlMetadataUrl|String|            |
|servicePrincipalNames|String|标识相关联的应用程序 Uri。 有关详细信息，请参阅[应用程序对象和服务主体对象](https://msdn.microsoft.com/en-us/library/azure/dn132633.aspx)。                            **备注**︰ 不可以为 null， **any**运算符是所必需的筛选器表达式的多值属性;有关详细信息，请参阅[支持查询、 筛选和分页选项](https://msdn.microsoft.com/library/azure/dn727074.aspx)。            |
|标记|String|                                        **备注**︰ 不可以为 null。            |

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[servicePrincipal](../resources/serviceprincipal.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_serviceprincipal"
}-->
```http
PATCH https://graph.microsoft.com/beta/servicePrincipals/<id>
Content-type: application/json
Content-length: 391

{
  "accountEnabled": true,
  "addIns": [
    {
      "id": "id-value",
      "type": "type-value",
      "properties": [
        {
          "key": "key-value",
          "value": "value-value"
        }
      ]
    }
  ],
  "appDisplayName": "appDisplayName-value",
  "appId": "appId-value",
  "appOwnerOrganizationId": "appOwnerOrganizationId-value",
  "appRoleAssignmentRequired": true
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.serviceprincipal"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 391

{
  "accountEnabled": true,
  "addIns": [
    {
      "id": "id-value",
      "type": "type-value",
      "properties": [
        {
          "key": "key-value",
          "value": "value-value"
        }
      ]
    }
  ],
  "appDisplayName": "appDisplayName-value",
  "appId": "appId-value",
  "appOwnerOrganizationId": "appOwnerOrganizationId-value",
  "appRoleAssignmentRequired": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update serviceprincipal",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
