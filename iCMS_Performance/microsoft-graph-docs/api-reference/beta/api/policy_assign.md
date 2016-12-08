# <a name="assign-policy"></a>分配策略

将一个[策略](../resources/policy.md)分配给某个应用程序或服务主体。

>注︰ 目前，策略分配仅适用于令牌的生存期策略。 [策略](../resources/policy.md)描述了这种类型的策略。

### <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP 请求

```http
POST /applications/<id>/policies/$ref
POST /serviceprincipals/<id>/policies/$ref
```

> 注意︰ 在申请中的"id"是应用程序或服务主体，不是"应用程序标识"属性的"id"属性。

### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | 应用程序/json  | 正文中的实体数据的性质。 必需。 |

### <a name="request-body"></a>请求正文
在请求正文中，提供要添加的策略对象的 JSON 表示。

### <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 如果不成功，`4xx`与特定的详细信息，则返回错误。

### <a name="example"></a>示例
下面的示例将一个策略分配给应用程序。

##### <a name="request"></a>请求
下面是示例请求。

```http
POST /applications/<id>/policies/$ref
Content-type: application/json
{
    "@odata.id":"https://graph.microsoft.com/beta/policies/<policyid>"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 204 No Content
```
