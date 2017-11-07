# <a name="list-trendingaround"></a>列表 trendingAround

计算出的洞察力，以返回用户围绕趋势分析的项的列表。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Sites.Read.All*

## <a name="http-request"></a>HTTP 请求
```http
GET /me/trendingAround
GET /users/<id | userPrincipalName>/trendingAround
GET /drive/root/createdByUser/trendingAround
GET /drive/root/lastModifiedByUser/trendingAround
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头
| 页眉         | 值                      |
|:---------------|:---------------------------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型   | 应用程序/json           |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法将在响应正文中返回 200 OK 响应代码和[driveItem](../resources/driveItem.md)对象的集合。

## <a name="example"></a>示例
##### <a name="request"></a>请求
```http
GET https://graph.microsoft.com/beta/me/trendingAround
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 226

{
  "id": "id-value",
  "name": "name-value",
  "DateTimeCreated": "DateTimeCreated-value",
  "DateTimeLastModified": "DateTimeLastModified-value",
  "webUrl": "webUrl-value",
}
```