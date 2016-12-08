# <a name="update-organization"></a>更新组织

更新的属性的当前经过身份验证的组织。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /organization

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|assignedPlans|AssignedPlan|与租户相关的服务计划的集合。                            **备注**︰ 不可以为 null。            |
|市/县|String|            |
|companyLastDirSyncTime|方法|在租户最后一次与后端目录同步的日期和时间。|
|国家/地区|String|            |
|countryLetterCode|String|            |
|deletionTimestamp|方法||
|dirSyncEnabled|Boolean|**如此**如果此对象同步从本地目录中。**假**如果此对象最初从内部目录同步，但不会再同步;**null**如果该对象已永远不会从内部目录 （默认值） 进行同步。|
|显示名称|String|对于组织显示名称。|
|marketingNotificationEmails|String|                                        **备注**︰ 不可以为 null。            |
|对象类型|String|一个字符串，标识对象类型。 承租人的值始终为"公司"。 从[directoryObject](../resources/directoryobject.md)继承。|
|邮政编码|String|            |
|preferredLanguage|String|            |
|provisionedPlans|ProvisionedPlan|                                        **备注**︰ 不可以为 null。            |
|provisioningErrors|ProvisioningError|                                        **备注**︰ 不可以为 null。            |
|securityComplianceNotificationMails|String||
|securityComplianceNotificationPhones|String||
|状态|String|            |
|街道|String|            |
|technicalNotificationMails|String|                                        **备注**︰ 不可以为 null。            |
|telephoneNumber|String|            |
|verifiedDomains|VerifiedDomain|与该组织相关联的域的集合。                            **备注**︰ 不可以为 null。            |

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的更新后的[组织](../resources/organization.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_organization"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/organization
Content-type: application/json
Content-length: 411

{
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
  "country": "country-value",
  "countryLetterCode": "countryLetterCode-value",
  "displayName": "displayName-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.organization"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 411

{
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
  "country": "country-value",
  "countryLetterCode": "countryLetterCode-value",
  "displayName": "displayName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update organization",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
