# <a name="list-overrides"></a>列表会覆盖

获取用户设置始终将来自特定发件人的邮件分类以特定的方式重写。

每个替代与发件人的 SMTP 地址相对应。 最初，用户没有任何重写。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Mail.Read*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/inferenceClassification/overrides
GET /users/<id>/inferenceClassification/overrides
```

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[inferenceClassificationOverride](../resources/inferenceclassificationoverride.md)对象的集合。
如果用户没有设置任何重写，则返回一个空集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_overrides"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/inferenceClassification/overrides
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.inferenceClassificationOverride",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "classifyAs": "focused",
      "senderEmailAddress": {
        "name": "Fanny Downs",
        "address": "fannyd@adatum.onmicrosoft.com"
      },
      "id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9"
    },
    {
      "classifyAs": "other",
      "senderEmailAddress": {
        "name": "Randi Welch",
        "address": "randiw@adatum.onmicrosoft.com"
      },
      "id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r"
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List overrides",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->