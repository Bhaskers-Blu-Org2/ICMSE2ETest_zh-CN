# <a name="create-bucket"></a>创建存储桶

使用此 API 来创建新的存储桶。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /buckets

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）" |

## <a name="request-body"></a>请求正文
在请求正文中，提供[地址散列表元](../resources/bucket.md)对象的 JSON 的表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[桶](../resources/bucket.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_bucket_from_buckets"
}-->
```http
POST https://graph.microsoft.com/beta/buckets
Content-type: application/json
Content-length: 88

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value"
}
```
在请求正文中，提供[地址散列表元](../resources/bucket.md)对象的 JSON 的表示。
##### <a name="response"></a>响应
这里是响应的示例。 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.bucket"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 108

{
  "name": "name-value",
  "planId": "planId-value",
  "orderHint": "orderHint-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create bucket",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->