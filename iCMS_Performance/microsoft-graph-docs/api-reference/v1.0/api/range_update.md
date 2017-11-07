# <a name="update-range"></a>更新范围

更新区域对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /workbook/names(<name>)/range
PATCH /workbook/worksheets(<id|name>)/range(address=<range-address>)
PATCH /workbook/tables(<id|name>)/columns(<id|name>)/range
```
## <a name="optional-request-headers"></a>可选的请求标头
| 名称       | 说明|
|:-----------|:-----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|隐藏列|布尔|表示如果当前范围中的所有列都隐藏的。|
|formulas|字符串并从中获取一个对象。|表示以 A1 样式表示法表示的公式。|
|formulasLocal|字符串并从中获取一个对象。|代表公式以 A1 样式表示法，以用户的语言和数字格式的区域设置。  例如，英语"= SUM (A1，1.5)"的公式将变为"= SUMME(A1;1.5)"在德语中。|
|formulasR1C1|字符串并从中获取一个对象。|表示以 R1C1 样式表示法表示的公式。|
|numberFormat|字符串并从中获取一个对象。|表示 Excel 的给定单元格的数字格式代码。|
|rowHidden|布尔|表示如果当前范围内的所有行都被都隐藏。|
|values|字符串并从中获取一个对象。|表示指定范围的原始值。 返回的数据可能是类型字符串、 数字或布尔值。 包含错误的单元格将返回的错误字符串。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的响应正文中的[Range](../resources/range.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。 更新范围-值、 数字格式和公式。 `null`输入是指示要忽略该特定输入的单元格的 API。 值、 数字格式和公式可以独立更新或相同的 API 调用中组合在一起。 

<!-- {
  "blockType": "request",
  "name": "update_range"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/worksheets('sheet1')/range(address='A1:B2')
Content-type: application/json
Content-length: 169

{
"values" : [["Hello", "100"],["1/1/2016", null]],
"formula" : [[null, null], [null, "=B1*2"]],
"numberFormat" : [[null,null], ["m-ddd", null]]
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.range"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 169

{
  "address": "address-value",
  "addressLocal": "addressLocal-value",
  "cellCount": 99,
  "columnCount": 99,
  "columnIndex": 99,
  "valueTypes": "valueTypes-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update range",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
