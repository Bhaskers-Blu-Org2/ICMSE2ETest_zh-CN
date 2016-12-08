# <a name="update-chartdatalabels"></a>更新 chartdatalabels

更新 chartdatalabels 对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/datalabels
```
## <a name="optional-request-headers"></a>可选的请求标头
| 名称       | 说明|
|:-----------|:-----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|position|string|DataLabelPosition 值，该值表示数据标签的位置。 Possible values are: `None`, `Center`, `InsideEnd`, `InsideBase`, `OutsideEnd`, `Left`, `Right`, `Top`, `Bottom`, `BestFit`, `Callout`.|
|Separator|string|表示用于图表中数据标签的分隔符字符串。|
|showBubbleSize|布尔|布尔值，表示如果数据标签的气泡大小是可见的或不。|
|showCategoryName|布尔|布尔值，表示如果数据标签的类别名称，或不是可见的。|
|showLegendKey|布尔|布尔值，表示如果数据标签图例项标示是可见的或不。|
|showPercentage|布尔|布尔值，表示如果数据标签的百分比是可见的或不。|
|showSeriesName|布尔|布尔值，表示如果数据标签的系列名称，或不是可见的。|
|showValue|布尔|布尔值，表示如果数据标签的值可见。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新后的[ChartDataLabels](../resources/chartdatalabels.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_chartdatalabels"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/datalabels
Content-type: application/json
Content-length: 134

{
  "position": "position-value",
  "showValue": true,
  "showSeriesName": true,
  "showCategoryName": true,
  "showLegendKey": true
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chartDataLabels"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 134

{
  "position": "position-value",
  "showValue": true,
  "showSeriesName": true,
  "showCategoryName": true,
  "showLegendKey": true
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update chartdatalabels",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->