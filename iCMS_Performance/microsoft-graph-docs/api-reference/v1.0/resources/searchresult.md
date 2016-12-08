# <a name="searchresult-resource-type"></a>searchResult 资源类型

**SearchResult**资源指示物料比对搜索的响应。



## <a name="properties"></a>属性

| 属性            | 类型   | 说明                                                                                                                                                                         |
|:--------------------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| onClickTelemetryUrl | String | 用于记录遥测信息回调 URL。 如果此项目以改善结果的质量与用户交互，应用程序应发出时获取此 URL。 |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
  "onClickTelemtryUrl"
  ],
  "@odata.type": "microsoft.graph.searchResult"
}-->

```json
{
  "onClickTelemetryUrl": "url"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "searchResult resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
