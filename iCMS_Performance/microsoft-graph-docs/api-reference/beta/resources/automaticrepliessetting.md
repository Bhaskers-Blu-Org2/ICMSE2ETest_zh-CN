# <a name="automaticrepliessetting-resource-type"></a>automaticRepliesSetting 资源类型

自动通知发件人接收的电子邮件，一封来自已登录的用户的配置设置。 例如，电子邮件自动答复通知中已登录的用户将无法响应。 


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|externalAudience|String| 观众向已登录的用户的组织外部**状态**是否会收到**ExternalReplyMessage**，套`AlwaysEnabled`或`Scheduled`。 可能的值为︰ `none`， `contactsOnly`， `all`。|
|externalReplyMessage|string|自动回复将发送到指定的外部目标群体，如果**状态**是`AlwaysEnabled`或`Scheduled`。|
|internalReplyMessage|string|自动答复发送给观众向已登录的用户的组织，内部**状态**是`AlwaysEnabled`或`Scheduled`。 |
|scheduledEndDateTime|[dateTimeTimeZone](datetimetimezone.md)|日期和时间自动答复设置结束，如果**状态**设置为`Scheduled`。 |
|scheduledStartDateTime|[dateTimeTimeZone](datetimetimezone.md)|日期和时间自动答复设置开始，如果**状态**设置为`Scheduled`。|
|status|String|自动答复的配置状态。 可能的值为︰ `disabled`， `alwaysEnabled`， `scheduled`。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.automaticRepliesSetting"
}-->

```json
{
  "externalAudience": "String",
  "externalReplyMessage": "string",
  "internalReplyMessage": "string",
  "scheduledEndDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "scheduledStartDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "automaticRepliesSetting resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->