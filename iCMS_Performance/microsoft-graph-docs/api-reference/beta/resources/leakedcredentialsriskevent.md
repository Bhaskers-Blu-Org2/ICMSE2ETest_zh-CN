# <a name="leakedcredentialsriskevent-resource-type"></a>leakedCredentialsRiskEvent 资源类型

检测到[Azure 活动目录标识保护](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection/)帐户凭据已被检测到处于放任状态的风险事件。 [Azure AD 身份保护文档](https://azure.microsoft.com/en-us/documentation/articles/active-directory-identityprotection-risk-events-types/)中找不到有关风险事件的完整信息。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 leakedCredentialsRiskEvent](../api/leakedcredentialsriskevent_get.md) | [leakedCredentialsRiskEvent](leakedcredentialsriskevent.md) |读取属性和关系的 leakedCredentialsRiskEvent 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|closedDateTime|方法| 日期和时间已关闭的风险事件|
|createdDateTime|方法| 日期和风险事件的创建时间。 这始终是大于或等于本身的风险事件的日期时间。 这是正确的属性时要使用的筛选器查询风险事件。|
|id|string| 只读的|
|riskEventDateTime|方法| 当风险事件发生的时间与日期|
|riskEventStatus|string| Possible values are: `active`, `remediated`, `dismissedAsFixed`, `dismissedAsFalsePositive`, `dismissedAsIgnore`, `loginBlocked`, `closedMfaAuto`, `closedMultipleReasons`.|
|riskLevel|string| 可能的值为︰ `low`， `medium`， `high`。|
|riskEventType|string| 风险的类型|
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
  "@odata.type": "microsoft.graph.leakedCredentialsRiskEvent"
}-->

```json
{
  "closedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "riskEventDateTime": "String (timestamp)",
  "riskEventStatus": "string",
  "riskLevel": "string",
  "riskType": "string",
  "userDisplayName": "string",
  "userId": "string",
  "userPrincipalName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "leakedCredentialsRiskEvent resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->