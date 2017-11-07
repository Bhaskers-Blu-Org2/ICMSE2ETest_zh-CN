# <a name="update-bucket"></a>更新存储桶

更新地址散列表元对象的属性。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /buckets/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）" |
| 如果匹配 | string | 应设置对象的 ETag 值 |
| 更喜欢 | string | 值应该设置为"返回 = 表示"以便在响应中返回更新后的对象。 这被建议，以便客户端可以获得新的 ETag 值的更新后的对象而无需进行更多的获取 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|name|String|存储桶的名称。|
|orderHint|String|用于任务板视图中设置存储桶的相对顺序。 考虑三个存储桶的顺序︰ `'E'`， `'F'`， `'G'`。 以`'F'`第一个桶，设置其`'orderHint'`为小于的`'x'`。 比较是序号字符串比较。|
|planId|String|桶属于计划 id。|

## <a name="response"></a>响应
如果成功，此方法返回`204 No Content`响应代码。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_bucket"
}-->
```http
PATCH https://graph.microsoft.com/beta/buckets/<id>
Content-type: application/json
Content-length: 108
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value",
  "id": "id-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.bucket"
} -->
```http
HTTP/1.1 204 No Content
```
若要获取已更新的对象，请使用`Prefer`头。 请参阅上面的请求标头。
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update bucket",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->