# <a name="chart-image"></a>图表︰ 图像

通过缩放图表以适合指定的尺寸为 base64 编码的图像呈现图表。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/worksheets(<id|name>)/charts(<name>)/Image(width=0,height=0,fittingMode='fit')

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|height|number|可选项。 生成的图像所需的高度。|
|width|number|可选项。 生成的图像所需的宽度。|
|fittingMode|string|可选项。 该方法用于缩放到指定为指定的尺寸图 （如果设置高度和宽度）。"  可能的值为︰ `Fit`， `FitAndCenter`， `Fill`。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码和 base 64 图像响应正文中的字符串。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- { "blockType": "ignored" } -->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<id>/workbook/worksheets(<id|name>)/charts(<name>)/Image(width=0,height=0,fittingMode='fit')
Content-type: application/json
Content-length: 77

{
  "height": {
  },
  "width": {
  },
  "fittingMode": "fittingMode-value"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 3

{
"value" : "base-64 chart image string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Chart: Image",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->