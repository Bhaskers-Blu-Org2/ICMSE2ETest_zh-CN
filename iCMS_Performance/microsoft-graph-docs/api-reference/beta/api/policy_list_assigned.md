# <a name="list-policies-assigned-to-application-or-service-principal"></a>分配给应用程序或服务主体列表策略

检索分配给应用程序或服务主体的[策略](../resources/policy.md)对象。

### <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /applications/<id>/policies
```

> 注意︰ 在申请中的"id"是应用程序或服务主体，不是"应用程序标识"属性的"id"属性。

### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

### <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

### <a name="response"></a>响应
如果成功，此方法返回`200, OK`在响应正文中的响应代码和[策略](../resources/policy.md)对象。 如果不成功，`4xx`与特定的详细信息，则返回错误。

### <a name="example"></a>示例
下面的示例检索分配给应用程序的策略。

##### <a name="request"></a>请求
下面是示例请求。

```http
GET https://graph.microsoft.com/beta/applications/<id>/policies
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 200 OK
Cache-Control: private
Content-Type: application/json

{
    "value":[
        {
            "@odata.type":"#microsoft.graph.policy",
            "id":"id-value",
            "alternativeIdentifier":null,
            "definition":["policy-definition"],
            "displayName":"name-value",
            "isOrganizationDefault":boolean-value,
            "keyCredentials":[key-credentials],
            "type":"type-value"
        }
    ]
}
```
