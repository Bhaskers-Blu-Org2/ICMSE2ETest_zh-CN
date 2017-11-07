# <a name="recurrencerange-resource-type"></a>recurrenceRange 资源类型

事件的持续时间。

## <a name="properties"></a>属性

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|结束日期|日期|该系列的结束日期。|
|numberOfOccurrences|Int32|多少次重复事件。|
|recurrenceTimeZone|String |**开始日期**和**结束日期**属性的时区。 | 
|开始日期|日期|该系列的开始日期。|
|类型|String|定期范围︰ 结束日期 = 0，NoEnd = 1，编号 = 2。 可能的值为︰ `EndDate`， `NoEnd`， `Numbered`。||


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.recurrencerange"
}-->

```json
{
  "endDate": "String (timestamp)",
  "numberOfOccurrences": 1024,
  "recurrenceTimeZone": "string",
  "startDate": "String (timestamp)",
  "type": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "recurrenceRange resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
