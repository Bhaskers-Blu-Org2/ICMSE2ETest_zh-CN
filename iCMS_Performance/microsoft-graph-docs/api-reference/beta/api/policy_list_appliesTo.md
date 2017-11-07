# <a name="list-applications-and-service-principals-with-specific-policy-assigned"></a>列出应用程序和服务主体与特定的策略分配

检索与指定的策略分配的[应用程序](../resources/application.md)和[服务的主要](../resources/serviceprincipal.md)对象。

### <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP 请求
```http
GET /policies/<id>/appliesTo
```

### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

### <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

### <a name="response"></a>响应
如果成功，此方法返回`200, OK`在响应正文中的响应代码和[应用程序](../resources/application.md)以及[主要的服务](../resources/serviceprincipal.md)对象。 如果不成功，`4xx`与特定的详细信息，则返回错误。

### <a name="example"></a>示例
下面的示例检索与特定的策略分配的应用程序和服务主体。

##### <a name="request"></a>请求
下面是示例请求。

```http
GET https://graph.microsoft.com/beta/policies/<id>/appliesTo
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value":[
        {
            "@odata.type"="#microsoft.graph.application",
            "appId":"appId-value",
            "displayName":"displayName-value",
            "errorUrl":"errorUrl-value",
            "groupMembershipClaims":"groupMembershipClaims-value",
            "homepage":"homepage-value",
            "id":"id-value",
            "keyCredentials":[key-credentials],
            "logoutUrl":"logoutUrl-value",
            "replyUrls":["replyUrls-value"]
        }
    ]
}
```
