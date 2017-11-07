# <a name="attendeebase-resource-type"></a>attendeeBase 资源类型

与会者的类型。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.attendeeBase"
}-->

```json
{
  "type": "String"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|类型|String| 与会者的类型。 可能的值为︰ `Required`， `Optional`， `Resource`。 当前如果与会者是个人， [findMeetingTimes](../api/user_findmeetingtimes.md)始终认为此人是的`Required`类型。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "attendeeBase resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->