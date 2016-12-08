# <a name="chartcollection-add"></a>ChartCollection︰ 添加

创建新的图表。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/worksheets(<id|name>)/charts

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|类型|string|表示图表的类型。  Possible values are: `ColumnClustered`, `ColumnStacked`, `ColumnStacked100`, `BarClustered`, `BarStacked`, `BarStacked100`, `LineStacked`, `LineStacked100`, `LineMarkers`, `LineMarkersStacked`, `LineMarkersStacked100`, `PieOfPie`, `etc.`.|
|源数据|string|对应于源数据的范围对象。|
|seriesBy|string|可选项。 指定的方法列或行用作在图表上的数据系列。  可能的值为︰ `Auto`， `Columns`， `Rows`。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应并在响应正文中的[图表](../resources/chart.md)对象。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "chartcollection_add"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts
Content-type: application/json
Content-length: 94

{
  "type": "type-value",
  "sourceData": "sourceData-value",
  "seriesBy": "seriesBy-value"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chart"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 52

{
  "id": "id-value",
  "height": 99,
  "left": 99
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ChartCollection: add",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->