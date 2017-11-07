# <a name="delete-policy"></a>删除策略

删除[策略](../resources/policy.md)。

### <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.AccessAsUser.All*

### <a name="http-request"></a>HTTP 请求

```http
DELETE /policies/<id>
```
### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

### <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

### <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 如果不成功。.

### <a name="example"></a>示例
下面的示例删除一个策略。

##### <a name="request"></a>请求
下面是示例请求。

```http
DELETE https://graph.microsoft.com/beta/policies/<id>
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 204 No Content
```
