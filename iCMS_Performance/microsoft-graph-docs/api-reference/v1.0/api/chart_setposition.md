# <a name="chart-setposition"></a>图表︰ setPosition

相对于工作表上的单元格的位置的图表。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/worksheets(<id|name>)/charts(<name>)/setPosition

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|startCell|string|起始单元格。 这是图表将移动到的位置。 起始单元格为左上角或右上角单元格，具体取决于用户的从右到左显示设置。|
|endCell|string|可选项。 结尾的单元格。 如果指定，将设置图表的宽度和高度，此单元格/范围完全覆盖。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "chart_setposition"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/setPosition
Content-type: application/json
Content-length: 66

{
  "startCell": "startCell-value",
  "endCell": "endCell-value"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.none"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Chart: setPosition",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->