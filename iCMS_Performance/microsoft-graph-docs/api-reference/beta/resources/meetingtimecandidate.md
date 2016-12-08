# <a name="meetingtimecandidate-resource-type"></a>meetingTimeCandidate 资源类型

会议建议，其中包括会议时间、 出勤可能性、 单个可用性和可用的会议位置等信息。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.meetingTimeCandidate"
}-->

```json
{
  "attendeeAvailability": [{"@odata.type": "microsoft.graph.attendeeAvailability"}],
  "confidence": 1024,
  "locations": [{"@odata.type": "microsoft.graph.location"}],
  "meetingTimeSlot": {"@odata.type": "microsoft.graph.timeSlot"},
  "organizerAvailability": "String",
  "suggestionHint": "String"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|attendeeAvailability|[attendeeAvailability](attendeeavailability.md)集合|一个数组，其中显示为此会议建议每个与会者的可用性状态。|
|信心|Double|代表所有与会者参加 likelhood 的百分比。|
|位置|[位置](location.md)的集合|一个数组，指定的名称和为此会议建议每个会议地点的地理位置。|
|meetingTimeSlot|[时间段](timeslot.md)|建议会议的一个时间段。|
|organizerAvailability|String| 会议组织者为此会议建议的可用性。 Possible values are: `free`, `tentative`, `busy`, `oof`, `workingElsewhere`, `unknown`.|
|suggestionHint|String|描述建议的会议时间。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "meetingTimeCandidate resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->