# <a name="update-application"></a>更新应用程序

更新应用程序对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /applications/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|应用程序标识|String|应用程序的唯一标识符。|
|appRoles|appRole|应用程序可以将声明的应用程序角色的集合。 可以将这些角色分配给用户、 组或服务主体。                              **备注**︰ 要求版本 1.5，不可以为 null。|
|availableToOtherOrganizations|Boolean|                **如此**如果与其他承租人; 共享应用程序否则为**假**。|
|显示名称|String|应用程序显示名称。|
|errorUrl|String|                              |
|groupMembershipClaims|String|在用户或应用程序期望的 OAuth 2.0 访问令牌配置颁发的"组"声明一个位掩码。 位掩码值︰ 0︰ 无 1︰ 安全组和 Azure 的广告角色，2︰ 预留，并且 4︰ 保留。 将位掩码设置为 7 可使所有安全组、 通讯组和 Azure 的广告目录角色的成员的已登录的用户。                              **备注**︰ 需要 1.5 版。|
|主页|String|即到 URL™ s 主页。|
|identifierUris|String|标识应用程序的 Uri。 有关详细信息，请参阅[应用程序对象和服务主体对象](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-objects/)。                              **说明︰**不可以为 null， **any**运算符是所必需的筛选器表达式的多值属性;有关详细信息，请参阅[支持查询、 筛选和分页选项](https://msdn.microsoft.com/library/azure/dn727074.aspx)。|
|keyCredentials|keyCredential|与应用程序相关联的密钥凭据集合**备注︰**不可以为 null|
|knownClientApplications|Guid|客户端应用程序依赖于此资源的应用程序。 同意任何已知的客户端应用程序将导致资源应用程序通过组合的同意对话 （显示客户端和资源所需的 OAuth 权限范围） 的默许。                              **备注**︰ 要求版本 1.5，不可以为 null。|
|logoutUrl|String|                              |
|mainLogo|Stream|应用程序主标志。                              **说明︰**不可以为 null|
|oauth2AllowImplicitFlow|Boolean|指定此 web 应用程序是否可以请求 OAuth2.0 隐式流标记。 默认值为**false**。                              **备注**︰ 要求版本 1.5，不可以为 null。|
|oauth2AllowUrlPathMatching|Boolean|指定是否，作为 OAuth 2.0 令牌请求的一部分，Azure 广告允许的应用程序的**replyUrls**针对重定向 URI 路径匹配。 默认值为**false**。                              **备注**︰ 要求版本 1.5，不可以为 null。|
|oauth2Permissions|oAuth2Permission|向客户端应用程序公开的 web 应用程序 API （资源） 的 OAuth 2.0 权限范围的集合。 这些权限范围可能会期间同意授予客户端应用程序。                              **备注**︰ 要求版本 1.5，不可以为 null。|
|oauth2RequirePostResponse|Boolean||
|passwordCredentials|passwordCredential|与应用程序相关联的密码凭据集合。                              **说明︰**不可以为 null|
|publicClient|Boolean|指定此应用程序是否是公共客户端 （如运行在移动设备上安装的应用程序）。  默认值为**false**。|
|replyUrls|String|指定用户标记为符号，被发送到的 Url 或重定向 Uri 的 OAuth 2.0 授权码和访问令牌被发送到。                              **说明︰**不可以为 null|
|requiredResourceAccess|requiredResourceAccess|指定此应用程序需要访问和 OAuth 权限范围和应用程序角色，则需要在每个这些资源组的资源。 预先配置的所需的资源访问驱动器的同意的情况下体验。                              **备注**︰ 要求版本 1.5，不可以为 null。|
|samlMetadataUrl|String|对 SAML 元数据应用程序的 URL。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[应用程序](../resources/application.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_application"
}-->
```http
PATCH https://graph.microsoft.com/beta/applications/<id>
Content-type: application/json
Content-length: 636

{
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
  "appId": "appId-value",
  "appRoles": [
    {
      "allowedMemberTypes": [
        "allowedMemberTypes-value"
      ],
      "description": "description-value",
      "displayName": "displayName-value",
      "id": "id-value",
      "isEnabled": true,
      "origin": "origin-value",
      "value": "value-value"
    }
  ],
  "availableToOtherOrganizations": true,
  "displayName": "displayName-value",
  "errorUrl": "errorUrl-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.application"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 636

{
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
  "appId": "appId-value",
  "appRoles": [
    {
      "allowedMemberTypes": [
        "allowedMemberTypes-value"
      ],
      "description": "description-value",
      "displayName": "displayName-value",
      "id": "id-value",
      "isEnabled": true,
      "origin": "origin-value",
      "value": "value-value"
    }
  ],
  "availableToOtherOrganizations": true,
  "displayName": "displayName-value",
  "errorUrl": "errorUrl-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update application",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->