# <a name="update-inferenceclassificationoverride"></a>更新 inferenceclassificationoverride

更改为指定重写**classifyAs**字段。 

修补程序不能用于更改[inferenceClassificationOverride](../resources/inferenceClassificationOverride.md)实例中的任何其他字段。 

如果重写用于发件人和发件人改变他/她的显示名称，可用于[发布](inferenceclassification_post_overrides.md)强制更新现有的重写中字段的名称。

如果重写用于发件人和发件人改变他/她的 SMTP 地址，[删除](inferenceclassificationoverride_delete.md)现有重写和[创建](inferenceclassification_post_overrides.md)一个新新的 SMTP 地址是"更新"重写此发件人的唯一办法。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Mail.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /me/inferenceClassification/overrides/<id>
PATCH /users/<id>/inferenceClassification/overrides/<id>
```

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文，提供**classifyAs**的新值。 为了获得最佳性能不应包括现有未更改的值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|classifyAs|string| 指定如何将传入消息从特定发件人应始终归为。 可能的值为︰ `focused`， `other`。|


## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[inferenceClassificationOverride](../resources/inferenceclassificationoverride.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面的示例更改 SMTP 地址重写randiw@adatum.onmicrosoft.com从`other`到`focused`。

<!-- {
  "blockType": "request",
  "name": "update_inferenceclassificationoverride"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/inferenceClassification/overrides/<id>
Content-type: application/json

{
  "classifyAs": "focused"
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
HTTP/1.1 200 OK
Content-type: application/json

{
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Randi Welch",
    "address": "randiw@adatum.onmicrosoft.com"
  },
  "id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update inferenceclassificationoverride",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->