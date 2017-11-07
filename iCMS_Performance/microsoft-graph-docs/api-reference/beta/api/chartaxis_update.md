# <a name="update-chartaxis"></a>更新 chartaxis

更新 chartaxis 对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/seriesaxis
PATCH /workbook/worksheets(<id|name>)/charts(<name>)/axes/categoryaxis
```
## <a name="optional-request-headers"></a>可选的请求标头
| 名称       | 说明|
|:-----------|:-----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|majorUnit|对象|表示两个主要刻度线标记之间的时间间隔。 可以设置为数字值或空字符串。  返回的值始终是一个数字。|
|maximum|对象|表示数值轴上的最大值。  可以设置为数字值或空字符串 （用于自动轴值）。  返回的值始终是一个数字。|
|minimum|对象|表示数值轴上的最小值。 可以设置为数字值或空字符串 （用于自动轴值）。  返回的值始终是一个数字。|
|minorUnit|对象|表示两个次要刻度线标记之间的时间间隔。 "可以设置为数字值或空字符串 （用于自动轴值）。 返回的值始终是一个数字。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新后的[ChartAxis](../resources/chartaxis.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_chartaxis"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/axes/valueaxis
Content-type: application/json
Content-length: 64

{
  "majorUnit": {
  },
  "maximum": {
  },
  "minimum": {
  }
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.chartaxis"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 64

{
  "majorUnit": {
  },
  "maximum": {
  },
  "minimum": {
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update chartaxis",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->