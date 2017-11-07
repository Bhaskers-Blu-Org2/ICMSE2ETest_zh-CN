# <a name="timeconstraint-resource-type"></a>timeConstraint 资源类型

指定性质的活动的时间段。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.timeconstraint"
}-->

```json
{
  "activityDomain": "String",
  "timeslots": [{"@odata.type": "microsoft.graph.timeSlot"}]
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|activityDomain|String|可选的活动性质。 可能的值为︰ `unknown`， `work`， `personal`。 [FindMeetingTimes](../api/user_findmeetingtimes.md)目前始终假定值是`work`过程，并返回任何会议建议仅组织者或与会者的工作时间。|
|时间段|[时间段](timeslot.md)集合|时间段的数组。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "timeConstraint resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->