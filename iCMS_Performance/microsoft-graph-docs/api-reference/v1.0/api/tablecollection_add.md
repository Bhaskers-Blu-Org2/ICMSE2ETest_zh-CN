# <a name="tablecollection-add"></a>TableCollection︰ 添加

创建一个新表。 区域的源地址确定将在其下添加表的工作表。 如果无法将该表添加 （例如，因为地址无效，或与另一个表，表将与重叠），则将引发错误。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/tables/add
POST /workbook/worksheets(<id|name>)/tables/add

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|address|string|地址或名称的 range 对象，该对象表示的数据源。 如果该地址不包含工作表名称，则使用当前活动工作表。|
|hasHeaders|布尔|布尔值，该值指示是否正在导入的数据具有列标志。 如果源中不包含页眉 （即，大于。 当此属性设置为 false），Excel 将自动生成一行向下移动数据的标题。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码和[表](../resources/table.md)对象在响应正文中的。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "tablecollection_add"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/tables/add
Content-type: application/json
Content-length: 54

{
  "address": "address-value",
  "hasHeaders": true
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.table"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 109

{
  "id": 99,
  "name": "name-value",
  "showHeaders": true,
  "showTotals": true,
  "style": "style-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableCollection: add",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->