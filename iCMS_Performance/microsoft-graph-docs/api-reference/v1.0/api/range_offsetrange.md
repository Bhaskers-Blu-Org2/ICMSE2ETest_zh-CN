# <a name="range-offsetrange"></a>范围︰ OffsetRange

获取对象，该对象表示来自指定范围的偏移量范围。 返回的文本区域的尺寸将与该范围匹配。 如果表中的网格的边界之外强制生成的范围，则将引发异常。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/names(<name>)/range/OffsetRange
POST /workbook/worksheets(<id|name>)/range(<address>)/OffsetRange
POST /workbook/tables(<id|name>)/columns(<id|name>)/range/OffsetRange

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|rowOffset|number|行数 （正数、 负数或 0） 范围的偏移量。 正值表示向下偏移，负值表示向上偏移。|
|columnOffset|number|列数 （正数、 负数或 0） 范围的偏移量。 正值表示向右偏移，负值表示向左偏移。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应并在响应正文中的[Range](../resources/range.md)对象。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "range_offsetrange"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/<id>/workbook/names(<name>)/range/OffsetRange
Content-type: application/json
Content-length: 49

{
  "rowOffset": {
  },
  "columnOffset": {
  }
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
  "description": "Range: OffsetRange",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->