# <a name="application-resource-type"></a>应用程序资源类型

表示应用程序。 Outsources 对 Azure AD 身份验证的任何应用程序必须在目录中进行注册。 这涉及到有关您的应用程序，包括有位置，将答复发送身份验证之后，URI 来标识您的应用程序，以及其他的 URL 的 URL 告诉 Azure 的广告。  有关详细信息，请参阅[基础知识的注册 Azure 广告中的应用程序](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-scenarios/#basics-of-registering-an-application-in-azure-ad)。 从[directoryObject](directoryObject.md)继承。


### <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "createdOnBehalfOf",
    "extensionProperties",
    "owners"
  ],
  "@odata.type": "microsoft.graph.application"
}-->

```json
{
  "addIns": [{"@odata.type": "microsoft.graph.addIn"}],
  "appId": "string",
  "appRoles": [{"@odata.type": "microsoft.graph.approle"}],
  "availableToOtherOrganizations": true,
  "displayName": "string",
  "errorUrl": "string",
  "groupMembershipClaims": "string",
  "homepage": "string",
  "id": "string (identifier)",
  "identifierUris": ["string"],
  "keyCredentials": [{"@odata.type": "microsoft.graph.keyCredential"}],
  "knownClientApplications": ["guid"],
  "logoutUrl": "string",
  "mainLogo": "stream",
  "oauth2AllowImplicitFlow": true,
  "oauth2AllowUrlPathMatching": true,
  "oauth2Permissions": [{"@odata.type": "microsoft.graph.oAuth2Permission"}],
  "oauth2RequirePostResponse": true,
  "passwordCredentials": [{"@odata.type": "microsoft.graph.passwordCredential"}],
  "publicClient": true,
  "recordConsentConditions": "string",
  "replyUrls": ["string"],
  "requiredResourceAccess": [{"@odata.type": "microsoft.graph.requiredResourceAccess"}],
  "samlMetadataUrl": "string"
}

```
### <a name="properties"></a>属性
| 属性     | 类型 |说明|
|:---------------|:--------|:----------|
|应用程序标识|String|应用程序的唯一标识符。|
|appRoles|[appRole](approle.md)集合|应用程序可以将声明的应用程序角色的集合。 可以将这些角色分配给用户、 组或服务主体。 不可以为 null。|
|availableToOtherOrganizations|Boolean| **如此**如果与其他承租人; 共享应用程序否则为**假**。|
|显示名称|String|应用程序显示名称。|
|errorUrl|String|                              |
|groupMembershipClaims|String|在用户或应用程序期望的 OAuth 2.0 访问令牌配置颁发的"组"声明一个位掩码。 位掩码值︰ 0︰ 无 1︰ 安全组和 Azure 的广告角色，2︰ 预留，并且 4︰ 保留。 将位掩码设置为 7 可使所有安全组、 通讯组和 Azure 的广告目录角色的成员的已登录的用户。 |
|主页|String|指向应用程序的主页的 URL。|
|identifierUris|字符串集合|标识应用程序的 Uri。 有关详细信息，请参阅[应用程序对象和服务主体对象](https://azure.microsoft.com/en-us/documentation/articles/active-directory-application-objects/)。 **Any**运算符，则需要为多值属性的筛选器表达式。 不可以为 null。 |
|keyCredentials|[keyCredential](keycredential.md)集合|凭据不与应用程序相关联的集合为空。|
|knownClientApplications|Guid 集合|客户端应用程序依赖于此资源的应用程序。 同意任何已知的客户端应用程序将导致资源应用程序通过组合的同意对话 （显示客户端和资源所需的 OAuth 权限范围） 的默许。 不可以为 null。|
|logoutUrl|String|                              |
|mainLogo|Stream|应用程序主标志。 不可为空|
|oauth2AllowImplicitFlow|Boolean|指定此 web 应用程序是否可以请求 OAuth2.0 隐式流标记。 默认值为**false**。 不可以为 null。|
|oauth2AllowUrlPathMatching|Boolean|指定是否，作为 OAuth 2.0 令牌请求的一部分，Azure 广告允许的应用程序的**replyUrls**针对重定向 URI 路径匹配。 默认值为**false**。 不可以为 null。|
|oauth2Permissions|[oAuth2Permission](oauth2permission.md)集合|向客户端应用程序公开的 web 应用程序 API （资源） 的 OAuth 2.0 权限范围的集合。 这些权限范围可能会期间同意授予客户端应用程序。 不可以为 null。|
|oauth2RequirePostResponse|Boolean||
|id|String|应用程序的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键。 不可以为 null。 只读的。|
|passwordCredentials|[passwordCredential](passwordcredential.md)集合|与应用程序相关联的密码凭据集合。 不可以为 null。|
|publicClient|Boolean|指定此应用程序是否是公共客户端 （如运行在移动设备上安装的应用程序）。  默认值为**false**。|
|replyUrls|字符串集合|指定用户标记为符号，被发送到的 Url 或重定向 Uri 的 OAuth 2.0 授权码和访问令牌被发送到。 不可以为 null。|
|requiredResourceAccess|[requiredResourceAccess](requiredresourceaccess.md)集合|指定此应用程序需要访问和 OAuth 权限范围和应用程序角色，则需要在每个这些资源组的资源。 预先配置的所需的资源访问驱动器的同意的情况下体验。 不可以为 null。|
|samlMetadataUrl|String|对 SAML 元数据应用程序的 URL。|

### <a name="relationships"></a>Relationships
| 关系 | 类型 |说明|
|:---------------|:--------|:----------|
|createdOnBehalfOf|[directoryObject](directoryobject.md)| 只读的。|
|extensionProperties|[extensionProperty](extensionproperty.md)集合|与应用程序关联的扩展属性。 只读的。 可以为 null。|
|所有者|[directoryObject](directoryobject.md)集合|目录是应用程序的所有者的对象。 所有者是一套非管理员用户有权修改此对象。 要求 2013年-11-08 版或更高版本。  只读的。 可以为 null。|
|策略|[策略](policy.md)集合|分配给此应用程序的策略。|

### <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获取应用程序](../api/application_get.md) | [应用程序](application.md) |读取属性和应用程序对象的关系。|
|[创建 extensionProperty](../api/application_post_extensionproperties.md) |[extensionProperty](extensionproperty.md)| 由过账到 extensionProperties 集合中创建新的 extensionProperty。|
|[列表 extensionProperties](../api/application_list_extensionproperties.md) |[extensionProperty](extensionproperty.md)集合| 获得 extensionProperty 对象集合。|
|[列表分配策略](../api/policy_list_assigned.md)| [策略](policy.md)集合| 获取分配给此对象的所有策略。|
|[创建所有者](../api/application_post_owners.md) |[directoryObject](directoryobject.md)| 由过账到所有者集合中创建一个新的所有者。|
|[列出所有者](../api/application_list_owners.md) |[directoryObject](directoryobject.md)集合| 获取所有者对象集合。|
|[更新](../api/application_update.md) | [应用程序](application.md) |更新应用程序对象。 |
|[删除](../api/application_delete.md) | 无 |删除应用程序对象。 |
|[还原](../api/application_restore.md)|[应用程序](application.md)|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "application resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
