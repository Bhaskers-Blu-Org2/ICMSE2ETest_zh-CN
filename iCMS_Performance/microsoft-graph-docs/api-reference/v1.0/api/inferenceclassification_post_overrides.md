# <a name="create-inferenceclassificationoverride"></a>创建 inferenceClassificationOverride

创建发件人标识 SMTP 地址重写。 未来从消息的 SMTP 地址将一直归在重写中指定。

**请注意**

- 如果已存在具有相同 STMP 地址重写，然后重写**classifyAs**和**名称**字段将更新与提供的值。
- 重写对邮箱支持的最大数目为 1000，基于唯一发件人的 SMTP 地址。
- POST 操作支持一次创建一个重写。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/inferenceClassification/overrides
POST /users/<id>/inferenceClassification/overrides
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文，提供[inferenceClassificationOverride](../resources/inferenceclassificationoverride.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[inferenceClassificationOverride](../resources/inferenceclassificationoverride.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_inferenceclassificationoverride_from_inferenceclassification"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/inferenceClassification/overrides
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Fanny Downs",
    "address": "fannyd@adatum.onmicrosoft.com"
  }
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.inferenceClassificationOverride"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Fanny Downs",
    "address": "fannyd@adatum.onmicrosoft.com"
  },
  "id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create inferenceClassificationOverride",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->