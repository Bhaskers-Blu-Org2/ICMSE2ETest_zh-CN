# <a name="privilegedrolesettings-resource-type"></a>privilegedRoleSettings 资源类型

代表特权角色的设置。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 privilegedRoleSettings](../api/privilegedrolesettings_get.md) | [privilegedRoleSettings](privilegedrolesettings.md) |读取属性和关系的 privilegedRoleSettings 对象。|
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|elevationDuration|duration|当激活该角色的持续时间。|
|id|string| 角色设置的唯一标识符。 只读的。|
|isMfaOnElevationConfigurable|布尔|**如此**如果 mfaOnElevation 是可配置的。 **假**如果是不可配置的 mfaOnElevation。|
|lastGlobalAdmin|布尔|仅用于内部。|
|maxElavationDuration|duration|激活角色的的最大持续时间。|
|mfaOnElevation|布尔|**如此**如果 MFA 需要激活该角色。 **假**如果 MFA 无需激活角色。|
|minElevationDuration|duration|最小持续时间的激活作用。|
|notificationToUserOnElevation|布尔|**如此**如果角色激活时向最终用户发送通知。 **假**如果角色被激活时不发送通知。|
|ticketingInfoOnElevation|布尔|**如此**如果票证发放要求信息何时激活角色。 **假**如果票证信息不需要激活该角色。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleSettings"
}-->

```json
{
  "elevationDuration": "String (timestamp)",
  "id": "string (identifier)",
  "isMfaOnElevationConfigurable": true,
  "lastGlobalAdmin": true,
  "maxElavationDuration": "String (timestamp)",
  "mfaOnElevation": true,
  "minElevationDuration": "String (timestamp)",
  "notificationToUserOnElevation": true,
  "ticketingInfoOnElevation": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleSettings resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->