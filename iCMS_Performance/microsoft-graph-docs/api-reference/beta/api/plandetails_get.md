# <a name="get-plandetails"></a>获得 planDetails

检索的属性和关系的 plandetails 对象。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.Read.All Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /plans/<id>/details

```
## <a name="optional-query-parameters"></a>可选的查询参数
无

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）" |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和[planDetails](../resources/plandetails.md)对象在响应正文中的。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_plandetails"
}-->
```http
GET https://graph.microsoft.com/beta/plans/<id>/details
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plandetails"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 381

{
  "sharedWith": {
  },
  "category0Description": "category0Description-value",
  "category1Description": "category1Description-value",
  "category2Description": "category2Description-value",
  "category3Description": "category3Description-value",
  "category4Description": "category4Description-value",
  "category5Description": "category5Description-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get planDetails",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->