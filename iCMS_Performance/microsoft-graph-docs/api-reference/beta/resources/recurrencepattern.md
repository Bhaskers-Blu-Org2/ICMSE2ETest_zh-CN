# <a name="recurrencepattern-resource-type"></a>recurrencePattern 资源类型

事件的频率。


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|dayOfMonth|Int32|事件发生在个月天。|
|daysOfWeek|字符串集合|事件发生在一周中的天的集合。 Possible values are: `Sunday`, `Monday`, `Tuesday`, `Wednesday`, `Thursday`, `Friday`, `Saturday`.|
|firstDayOfWeek|String|重复周期的开始的一周中的某一天。 Possible values are: `Sunday`, `Monday`, `Tuesday`, `Wednesday`, `Thursday`, `Friday`, `Saturday`.|
|index|String|每周定期进行的索引。: `First`， `Second`， `Third`， `Fourth`， `Last`。|
|时间间隔|Int32|单位的给定定期类型的两次发生之间。|
|月份|Int32|事件发生在个月。  这是从 1 到 12 之间的数字。|
|类型|String|定期模式类型︰ `Daily`， `Weekly`， `AbsoluteMonthly`， `RelativeMonthly`， `AbsoluteYearly`， `RelativeYearly`。|

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.recurrencepattern"
}-->

```json
{
  "dayOfMonth": 1024,
  "daysOfWeek": ["String"],
  "firstDayOfWeek": "String",
  "index": "String",
  "interval": 1024,
  "month": 1024,
  "type": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "recurrencePattern resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->