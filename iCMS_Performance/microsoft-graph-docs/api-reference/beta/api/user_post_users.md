# <a name="create-user"></a>创建用户

使用此 API 来创建一个新用户。
请求正文包含要创建的用户。 至少必须指定所需的用户属性。 您可以选择指定任何其他可写属性。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /users
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json  |

## <a name="request-body"></a>请求正文
在请求正文中，提供[用户](../resources/user.md)对象的 JSON 的表示。

下表显示当您创建用户时所需的属性。

| 参数 | 类型 | 说明|
|:---------------|:--------|:----------|
|accountEnabled |布尔 |如果启用了帐户;否则为则返回 false。|
|显示名称 |string |要显示在通讯簿中的用户的名称。|
|onPremisesImmutableId |string |只需创建一个新用户帐户，如果您使用的联盟的域用户的范围内 (UPN) 属性时，指定。|
|mailNickname |string |用户邮件别名。|
|passwordProfile|[PasswordProfile](../resources/passwordprofile.md) |用户的密码配置文件。|
|范围内 |string |用户主要名称 (someuser@contoso.com)。|

## <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[用户](../resources/user.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_user_from_users"
}-->
```http
POST https://graph.microsoft.com/beta/users
Content-type: application/json
Content-length: 551

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
在请求正文中，提供[用户](../resources/user.md)对象的 JSON 的表示。
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
Content-length: 551

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

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create User",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
