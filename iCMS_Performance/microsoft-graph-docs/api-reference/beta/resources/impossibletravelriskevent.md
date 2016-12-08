# <a name="impossibletravelriskevent-resource-type"></a>impossibleTravelRiskEvent 资源类型

检测到[Azure 活动目录标识保护](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection/)其中从典型用户的位置发生的两个帐户登录，将不可能在登录之间的持续时间中的位置之间移动的风险事件。 [Azure AD 身份保护文档](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection-risk-events-types/)中找不到有关风险事件的完整信息。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 impossibleTravelRiskEvent](../api/impossibletravelriskevent_get.md) | [impossibleTravelRiskEvent](impossibletravelriskevent.md) |读取属性和关系的 impossibleTravelRiskEvent 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|closedDateTime|方法| 日期和时间已关闭的风险事件|
|createdDateTime|方法| 日期和风险事件的创建时间。 这始终是大于或等于本身的风险事件的日期时间。 这是正确的属性时要使用的筛选器查询风险事件。|
|deviceInformation|string| 有关设备的信息|
|id|string| 只读的|
|ip 地址|string| 第二个登录的 IP 地址|
|isAtypicalLocation|布尔| 如果某个位置是典型的用户|
|位置|string| 挂接到 IP 地址的第二个签入的位置|
|previousIPAddress|string| 第一个登录的 IP 地址|
|previousLocation|string| 挂接到第一个登录的 IP 地址的位置|
|previousSigninDateTime|方法| 日期和时间的第一号|
|riskEventDateTime|方法| 日期和时间的第二个签入|
|riskEventStatus|string| Possible values are: `active`, `remediated`, `dismissedAsFixed`, `dismissedAsFalsePositive`, `dismissedAsIgnore`, `loginBlocked`, `closedMfaAuto`, `closedMultipleReasons`.|
|riskLevel|string| 可能的值为︰ `low`， `medium`， `high`。|
|riskEventType|string| 风险的类型|
|用户代理|string| 浏览器的用户代理字符串|
|userDisplayName|string| 自负的用户的名称|
|用户 Id|string| 自负的用户 id|
|范围内|string| 自负的用户的用户主体名称|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|impactedUser|[用户](user.md)| 只读的。 可以为 null。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.impossibleTravelRiskEvent"
}-->

```json
{
  "closedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "deviceInformation": "string",
  "id": "string (identifier)",
  "ipAddress": "string",
  "isAtypicalLocation": true,
  "location": "string",
  "previousIPAddress": "string",
  "previousLocation": "string",
  "previousSigninDateTime": "String (timestamp)",
  "riskEventDateTime": "String (timestamp)",
  "riskEventStatus": "string",
  "riskLevel": "string",
  "riskType": "string",
  "userAgent": "string",
  "userDisplayName": "string",
  "userId": "string",
  "userPrincipalName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "impossibleTravelRiskEvent resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->