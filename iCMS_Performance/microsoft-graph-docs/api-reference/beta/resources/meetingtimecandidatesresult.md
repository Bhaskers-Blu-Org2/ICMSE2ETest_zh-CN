# <a name="meetingtimecandidatesresult-resource-type"></a>meetingTimeCandidatesResult 资源类型

一个会议的建议，如果有任何问题，或如果没有的原因。

该[findMeetingTimes](../api/user_findmeetingtimes.md)不会返回任何会议的建议的原因可能如下。

|**emptySuggestionsHint 值**|**原因**|
|:-----|:-----|
| attendeesUnavailable | 所有与会者的可用性已知的但没有足够的与会者均可到达会议可信度阈值，即 50%，默认情况下，对于任何时间段。 此阈值根据与会者的忙/闲状态建议的会议时间段，与会者自由状态与出勤、 未知的状态 50%和繁忙状态 0%100%几率相对应。|
| attendeesUnavailableOrUnknown | 部分或全部与会者具有未知可用性，导致会议信心低于设定的阈值，即默认情况下的 50%。 与会者可行性会变得未知，如果与会者不属于该组织，或获取忙/闲信息时出错。|
| locationsUnavailable | [LocationConstraint](locationconstraint.md)参数的**isRequired**属性指定为必需的且尚未有没有位置在计算的时间段。 |
| organizerUnavailable | **IsOrganizerOptional**参数为 false，并且尚未管理器不可用请求的时间期间。 |
| 未知 | 未返回任何会议的建议的原因是未知的。|

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.meetingTimeCandidatesResult"
}-->

```json
{
  "emptySuggestionsHint": "String",
  "meetingTimeSlots": [{"@odata.type": "microsoft.graph.meetingTimeCandidate"}]
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|emptySuggestionsHint|String|未返回任何会议的建议的原因。 可能的值为︰ `attendeesUnavailable`， `attendeesUnavailableOrUnknown`， `locationsUnavailable`， `organizerUnavailable`，或`unknown`。|
|meetingTimeSlots|[meetingTimeCandidate](meetingTimeCandidate.md)集合|会议建议的数组。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "meetingTimeCandidatesResult resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->