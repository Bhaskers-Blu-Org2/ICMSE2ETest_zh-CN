# <a name="get-a-member"></a>获取成员

使用此 API 来获取特定的成员 （用户或组） 在一个管理单元。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.Read.All*或*Directory.ReadWrite.All*或*Directory.AccessAsUser.All*。

## <a name="http-request"></a>HTTP 请求

```http
GET /administrativeUnits/<id>/members/<id>
```
## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[用户](../resources/user.md)或[组](../resources/group.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。

```http
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members/<id>
```

##### <a name="response"></a>响应
这里是一种响应。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "@odata.type":"#microsoft.graph.user",
  "id":"492c5308-59fd-4740-9c83-4b3db07a6d70"
  "accountEnabled":true,
  "businessPhones":[],
  "companyName":null,
  "displayName":"Demo User"
}
```