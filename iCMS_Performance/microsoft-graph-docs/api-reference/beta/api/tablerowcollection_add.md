# <a name="tablerowcollection-add"></a>TableRowCollection︰ 添加

向表中添加一个新行。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/tables(<id|name>)/rows/add
POST /workbook/worksheets(<id|name>)/tables(<id|name>)/rows/add

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|index|number|可选项。 指定新行的相对位置。 如果为 null，增加反应结束时。 任何行下面插入行向下移动。 零开始编制索引。|
|values|（布尔值或字符串或数字）|可选项。 未格式化表格行中的值的二维数组。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码和[TableRow](../resources/tablerow.md)对象在响应正文中的。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "tablerowcollection_add"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/tables(<id|name>)/rows/add
Content-type: application/json
Content-length: 51

{
  "index": {
  },
  "values": [
    {
    }
  ]
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.tableRow"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 45

{
  "index": 99,
  "values": "values-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableRowCollection: add",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->