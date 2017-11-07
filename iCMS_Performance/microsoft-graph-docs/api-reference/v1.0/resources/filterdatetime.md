# <a name="filterdatetime-resource-type"></a>FilterDatetime 资源类型

代表如何筛选日期筛选值时。

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|date|string|ISO8601 格式用于筛选数据中的日期。|
|特定|string|如何具体日期应该用于保留数据。 例如，如果 specifity 设置为"月"的日期是 2005年-04-02，则筛选操作将在 2009 年 4 月的月保留具有一个日期的所有行。 Possible values are: `Year`, `Monday`, `Day`, `Hour`, `Minute`, `Second`.|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.filterDateTime"
}-->

```json
{
  "date": "string",
  "specificity": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "FilterDatetime resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->