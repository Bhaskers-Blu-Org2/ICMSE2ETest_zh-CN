# <a name="update-user"></a>更新用户

更新用户对象的属性。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *User.ReadWrite;User.ReadWrite.All;Directory.ReadWrite.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /users/<id | userPrincipalName>
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值|
|:-----------|:------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|aboutMe|String|用户描述自己一个自由形式的文本输入字段。|
|accountEnabled|Boolean| **如此**如果启用了帐户;否则为**假**。 在创建用户时，此属性是必需的。 支持 $filter。    |
|assignedLicenses|[assignedLicense](../resources/assignedlicense.md)集合|分配给该用户的许可证。 不可以为 null。            |
|生日|方法|用户的生日。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|市/县|String|用户所在的城市。 支持 $filter。|
|国家/地区|String|国家/地区用户所在;例如，"美国"或"英国"。 支持 $filter。|
|部门|String|用户的工作部门的名称。 支持 $filter。|
|显示名称|String|显示在通讯簿中的用户的名称。 这通常是名字的用户，中间初始和最后一个名称的组合。 创建用户并在更新过程中不能清除时，该属性是必需的。 $Filter 和 $orderby 的支持。|
|givenName|String|给定名称 （名字） 的用户。 支持 $filter。|
|hiredate|方法|雇佣日期是在用户。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|兴趣爱好|字符串集合|要描述他们的兴趣的用户列表。|
|职务|String|用户的职务。 支持 $filter。|
|mailNickname|String|用户邮件别名。 在创建用户时，必须指定此属性。 支持 $filter。|
|mobilePhone|String|主要的移动电话用户数。|
|mySite|String|用户的个人站点的 URL。|
|办公室|String|在用户的位置业务的办公地点。|
|onPremisesImmutableId|String|此属性用于将 Azure AD 用户对象为内部部署 Active Directory 用户帐户相关联。 在关系图中创建新的用户帐户，如果您使用的联盟的域用户的**范围内**(UPN) 属性时，必须指定此属性。 **重要︰****$** ，并指定此属性时，不能使用**_**字符。 支持 $filter。                            |
|passwordPolicies|String|指定用户的密码策略。 此值是一个可能的值为"DisableStrongPassword"，使较弱的密码比默认策略来指定一个枚举。 此外可以指定"DisablePasswordExpiration"。 可以指定两个在一起;例如:"DisablePasswordExpiration，DisableStrongPassword"。|
|passwordProfile|[PasswordProfile](../resources/passwordprofile.md)|指定用户的密码配置文件。 配置文件包含用户的密码。 在创建用户时，此属性是必需的。 在配置文件中的密码必须满足最低要求为**passwordPolicies**属性指定的。 默认情况下，使用强密码是必需的。|
|pastProjects|字符串集合|若要枚举其过去的项目的用户列表。|
|邮政编码|String|用户的邮政地址的邮政编码。 邮政编码是特定于用户的国家/地区。 在美国，此属性包含邮政编码。|
|preferredLanguage|String|用户的首选的语言。 应遵循 ISO 639-1 代码;如"EN-US"。|
|preferredName|String|用户首选的名称。|
|责任|字符串集合|要枚举其职责的用户列表。|
|学校|字符串集合|枚举它们已参加学校的用户列表。|
|技能|字符串集合|若要枚举其技能的用户列表。|
|状态|String|状态或用户的地址中的省。 支持 $filter。|
|街道地址|String|用户的业务地点的街道地址。|
|姓氏|String|用户的姓 （系列名称或姓氏）。 支持 $filter。|
|usageLocation|String|两个字母的国家代码 (ISO 3166 标准)。 所需的将由于法律要求在国家和地区的服务的可用性检查许可证分配的用户。  例如:"美国"、"JP"和"GB"。 不可以为 null。 支持 $filter。|
|范围内|String|用户主要名称 (UPN) 的用户。 UPN 是基于互联网标准 RFC 822 用户互联网式登录名。 按照惯例，这应映射到用户的电子邮件名称。 常规格式是alias@domain,域必须是现租户的集合的已验证的域中。 在创建用户时，此属性是必需的。 从[组织](../resources/organization.md)的**verifiedDomains**属性可以访问租户的验证的域。 $Filter 和 $orderby 的支持。
|用户类型|String|一个字符串值，可以用于分类目录，例如"成员"和"访客"中的用户类型。 支持 $filter。          |

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的更新的[用户](../resources/user.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_user"
}-->
```http
PATCH https://graph.microsoft.com/beta/me
Content-type: application/json
Content-length: 491

{
  "accountEnabled": true,
  "assignedLicenses": [
    {
      "disabledPlans": [ "bea13e0c-3828-4daa-a392-28af7ff61a0f" ],
      "skuId": "skuId-value"
    }
  ],
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "bea13e0c-3828-4daa-a392-28af7ff61a0f"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "companyName": "companyName-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.user"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 491

{
  "accountEnabled": true,
  "assignedLicenses": [
    {
      "disabledPlans": [ "bea13e0c-3828-4daa-a392-28af7ff61a0f" ],
      "skuId": "skuId-value"
    }
  ],
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "servicePlanId-value"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "companyName": "companyName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update user",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
