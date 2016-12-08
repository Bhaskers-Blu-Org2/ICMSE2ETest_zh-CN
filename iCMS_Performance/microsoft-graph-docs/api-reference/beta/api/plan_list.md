# <a name="list-plans"></a>列表计划

检索计划 * 对象的列表。

* 注意该筛选器时需要此方法。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.Read.All Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /plans
```
## <a name="optional-query-parameters"></a>可选的查询参数
|名称|值|说明|
|:---------------|:--------|:-------|
|$filter|字符串|只筛选基于`owner`支持属性。 |

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）" |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和响应正文中的[计划](../resources/plan.md)对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/plans?$filter=owner eq'400723e1-102b-43aa-aba9-f35524827084'
```
##### <a name="response"></a>响应
这里是响应的示例。 
<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 153

{
  "value": [
    {
      "createdBy": "createdBy-value",
      "owner": "owner-value",
      "title": "title-value",
      "id": "id-value"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List plans",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
