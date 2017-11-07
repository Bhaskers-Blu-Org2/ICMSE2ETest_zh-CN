# <a name="list-members"></a>列表成员

使用此 API 来获取成员一个管理单元的列表 （用户和组）。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.Read.All*或*Directory.ReadWrite.All*或*Directory.AccessAsUser.All*。

## <a name="http-request"></a>HTTP 请求

```http
GET /administrativeUnits/<id>/members
GET /administrativeUnits/<id>/members/$ref
```
## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的[用户](../resources/user.md)和/或[组](../resources/group.md)对象的集合。  相反，如果将`$ref`在请求结束时，响应将包含一套`@odata.id`的成员每 Url 链接。

## <a name="examples"></a>示例
##### <a name="list-member-objects"></a>列表成员对象
以下请求将列出的管理单元，并返回一个集合，用户和/或组的成员。

```http
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members
```

这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
 
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "value":[
    {
      "@odata.type":"#microsoft.graph.user",
      "id":"492c5308-59fd-4740-9c83-4b3db07a6d70"
      "accountEnabled":true,
      "businessPhones":[],
      "companyName":null,
      "displayName":"Demo User"
    },
    {
      "@odata.type":"#microsoft.graph.group",
      "id":"07eaa5c7-c9b6-45cf-8ff7-3147d5122caa",
      "description":"This group is the best ever",
      "displayName":"Awesome group"
    }
  ]
}
```

##### <a name="list-member-references"></a>列表中成员的引用
以下请求将列出该管理单元，返回的集合的成员参照`@odata.id`对成员的引用。
```
GET https://graph.microsoft.com/beta/administrativeUnits/<id>/members/$ref
```
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
 
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 100

{
  "value":[
    {
      "@odata.id": "https://graph.microsoft.com/beta/directoryObjects/492c5308-59fd-4740-9c83-4b3db07a6d70"
    },
    {
      "@odata.id": "https://graph.microsoft.com/beta/directoryObjects/07eaa5c7-c9b6-45cf-8ff7-3147d5122caa"
    }
  ]
}
```
