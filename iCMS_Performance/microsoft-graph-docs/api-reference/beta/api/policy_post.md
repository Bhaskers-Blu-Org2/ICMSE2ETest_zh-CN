# <a name="create-policy"></a>创建策略

通过指定显示名称、 策略类型和策略说明创建新的[策略](../resources/policy.md)对象。

>注意︰ 将在存储之前验证策略的详细信息。 如果它未通过验证，400 错误的请求将返回。

### <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.AccessAsUser.All*
### <a name="http-request"></a>HTTP 请求

```http
POST /policies
```
### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | 应用程序/json  | 正文中的实体数据的性质。 必需。 |

### <a name="request-body"></a>请求正文
在请求正文中，提供[策略](../resources/policy.md)对象的 JSON 的表示。

下表显示当您在创建策略时所需的属性。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|定义|String|[策略](../resources/policy.md)对象的字符串版本。|
|显示名称|String|自定义策略的名称。|
|类型|String|指定的策略的类型。 目前必须是"TokenLifetimePolicy"|

### <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[策略](../resources/policy.md)对象。 如果不成功，`4xx`与特定的详细信息，则返回错误。  

### <a name="example"></a>示例
下面的示例创建新的令牌生存期策略。 请注意，该字符串定义参数已转义双引号。

##### <a name="request"></a>请求
下面是示例请求。

```http
POST https://graph.microsoft.com/beta/policies
Content-Type: application/json

{
  "displayName":"CustomTokenLifetimePolicy",
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\"}}"],
  "type":"TokenLifetimePolicy"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#policies/$entity",
  "id":"id-value",
  "alternativeIdentifier":null,
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\"}}"],
  "displayName":"name-value",
  "isOrganizationDefault":false,
  "keyCredentials",
  "type":"TokenLifetimePolicy"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "message: createReply",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
