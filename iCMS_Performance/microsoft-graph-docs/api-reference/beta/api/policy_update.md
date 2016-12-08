# <a name="update-policy"></a>更新策略

更新中既有[策略](../resources/policy.md)的属性。

### <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP 请求

```http
PATCH /policies/<id>
```
### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | 应用程序/json  | 正文中的实体数据的性质。 必需。 |

### <a name="request-body"></a>请求正文
在请求正文中，提供了一个 JSON 对象需要更新的参数。 下表显示了可能的参数。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|定义|String|[策略](../resources/policy.md)对象的 stringified 的版本。|
|显示名称|String|自定义策略的名称。|
|isOrganizationDefault|Boolean|指定默认情况下是否应用此策略。|
|类型|String|指定的策略的类型。 目前必须是"TokenLifetimePolicy"|

### <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 如果不成功，`4xx`与特定的详细信息，则返回错误。

### <a name="example"></a>示例
下面的示例更新的令牌的生存期策略的定义，并将其设置为默认组织。

##### <a name="request"></a>请求
下面是示例请求。

```http
PATCH https://graph.microsoft.com/beta/policies/<id>
Content-Type: application/json
{
    "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\",\"MaxInactiveTime\":\"20:00:00\",}}"],
    "isOrganizationDefault":true
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 204 No Content
```
