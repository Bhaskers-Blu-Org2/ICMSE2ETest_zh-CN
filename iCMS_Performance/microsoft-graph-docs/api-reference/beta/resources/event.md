# <a name="event-resource-type"></a>事件资源类型

在日历中的事件。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "attachments",
    "calendar",
    "extensions",
    "instances"
  ],
  "@odata.type": "microsoft.graph.event"
}-->

```json
{
  "attendees": [{"@odata.type": "microsoft.graph.attendee"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "string",
  "categories": ["string"],
  "changeKey": "string",
  "createdDateTime": "String (timestamp)",
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "hasAttachments": true,
  "iCalUId": "string",
  "id": "string (identifier)",
  "importance": "String",
  "isAllDay": true,
  "isCancelled": true,
  "isOrganizer": true,
  "isReminderOn": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "organizer": {"@odata.type": "microsoft.graph.recipient"},
  "originalEndTimeZone": "string",
  "originalStart": "String (timestamp)",
  "originalStartTimeZone": "string",
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "reminderMinutesBeforeStart": 1024,
  "responseRequested": true,
  "responseStatus": {"@odata.type": "microsoft.graph.responseStatus"},
  "sensitivity": "String",
  "seriesMasterId": "string",
  "showAs": "String",
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "subject": "string",
  "type": "String",
  "webLink": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|与会者|[与会者](attendee.md)集合|与会者的事件的集合。|
|body|[ItemBody](itembody.md)|与该事件相关联的消息正文。|
|bodyPreview|String|与该事件相关联的消息预览。|
|类别|字符串集合|与该事件关联的类别。|
|更改密钥|String|标识事件对象的版本。 每次更改事件时，那么也将更改。 这样，可以将更改应用于该对象的正确版本的 Exchange。|
|createdDateTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|结束|[DateTimeTimeZone](datetimetimezone.md)|日期和事件结束的时间。|
|hasAttachments|Boolean|设置为 true，如果该事件包含附件。|
|iCalUId|String|由间共享的事件的所有实例使用不同的日历的唯一标识符。|
|id|String| 只读的。|
|重要性|String|该事件的重要性︰ 低 = 0，普通 = 1、 高 = 2。 可能的值为︰ `Low`， `Normal`， `High`。|
|isAllDay|Boolean|设置为 true，如果事件持续一整天。|
|isCancelled|Boolean|设置为 true，如果该事件已被取消。|
|isOrganizer|Boolean|如果，设置为 true 的消息发件人也是组织者。|
|isReminderOn|Boolean|如果，设置为 true 设置警报以提醒用户的事件。|
|lastModifiedDateTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|位置|[位置](location.md)|事件的位置。|
|OnlineMeetingUrl|String|联机会议的 URL。|
|组织者|[收件人](recipient.md)|该事件的组织者。|
|originalEndTimeZone|String|创建事件时设置结束时间区域。|
|originalStart|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|originalStartTimeZone|String|事件的创建时设置的开始时间区域。|
|重复周期|[PatternedRecurrence](patternedrecurrence.md)|事件的定期模式。|
|reminderMinutesBeforeStart|Int32|在该事件之前的分钟数开始提醒警报发生的时间。|
|responseRequested|Boolean|设置为 true，如果发件人希望接到响应事件被接受或拒绝时。|
|responseStatus|[ResponseStatus](responsestatus.md)|指示在响应事件消息中发送的响应的类型。|
|区分大小写|String| 可能的值为︰ `Normal`， `Personal`， `Private`， `Confidential`。|
|seriesMasterId|String|分配给项目的类别。|
|showAs|String|要显示的状态︰ 免费 = 0，暂定 = 1，忙 = 2，Oof = 3，WorkingElsewhere = 4，未知 =-1。 Possible values are: `Free`, `Tentative`, `Busy`, `Oof`, `WorkingElsewhere`, `Unknown`.|
|start|[DateTimeTimeZone](datetimetimezone.md)|事件的开始时间。|
|主题|String|事件的主题行的文本。|
|类型|String|事件类型︰ SingleInstance = 0，发生 = 1，异常 = 2，SeriesMaster = 3。 可能的值为︰ `SingleInstance`， `Occurrence`， `Exception`， `SeriesMaster`。|
|网页链接|String|要在 Outlook Web App 中打开事件的 URL。<br/><br/>如果您登录到您的邮箱通过 Outlook Web App，事件将会在浏览器中打开。 系统将提示您登录如果使用浏览器您尚未登录。<br/><br/>在 iFrame 内，可以从访问此 URL。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|附件|[附件](attachment.md)集合|[FileAttachment](fileattachment.md)、 [ItemAttachment](itemattachment.md)和[referenceAttachment](referenceAttachment.md)附件的事件的集合。 导航属性。 只读的。 可以为 null。|
|calendar|[日历](calendar.md)|包含事件的日历。 导航属性。 只读的。|
|扩展|[扩展](extension.md)集合|开放式类型数据扩展插件定义的事件的集合。 只读的。 可以为 null。|
|实例|[事件](event.md)集合|事件的实例。 导航属性。 只读的。 可以为 null。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)集合| 为此事件定义多值扩展属性的集合。 只读的。 可以为 null。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md)集合| 为此事件定义的单值扩展属性的集合。 只读的。 可以为 null。|


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[事件列表](../api/user_list_events.md)|[事件](event.md)集合 |检索用户的邮箱中的[事件](../resources/event.md)对象的列表。 该列表包含单个实例会议和系列的主控形状。|
|[获取事件](../api/event_get.md) | [事件](event.md) |读取属性和事件对象的关系。|
|[更新](../api/event_update.md) | [事件](event.md)   |更新事件的对象。 |
|[删除](../api/event_delete.md) | 无 |删除事件对象。 |
|[取消](../api/event_cancel.md) | 无 | 从组织者向所有与会者发送取消消息并取消指定的会议。 | 
|[接受](../api/event_accept.md)|无|接受指定的事件。|
|[tentativelyAccept](../api/event_tentativelyaccept.md)|无|暂定接受指定的事件。|
|[拒绝](../api/event_decline.md)|无|拒绝邀请到指定的事件。|
|[dismissReminder](../api/event_dismissreminder.md)|无|关闭指定的事件的提醒。|
|[snoozeReminder](../api/event_snoozereminder.md)|无|暂停指定事件的提醒。|
|[列表实例](../api/event_list_instances.md) |[事件](event.md)集合| 获取一个事件对象集合。|
|[附件列表](../api/event_list_attachments.md) |[附件](attachment.md)集合| 获取附件的对象集合。|
|[创建附件](../api/event_post_attachments.md) |[附件](attachment.md)| 由过账到的附件集合中创建一个新的附件。|
|[创建数据扩展插件](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| 创建一个开放类型数据扩展，添加新的或现有的资源实例中的自定义属性。|
|[获取数据扩展插件](../api/opentypeextension_get.md) |[openTypeExtension](opentypeextension.md)集合| 得到一个**openTypeExtension**对象或对象标识的名称或完全限定的名称。|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
