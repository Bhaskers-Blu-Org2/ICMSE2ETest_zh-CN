# <a name="list-available-drives"></a>列表中可用的驱动器

检索用户或 Office 365 组可用的驱动器对象的列表。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/drives
GET /groups/<id>/drives
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和响应正文中的[驱动器](../resources/drive.md)对象的集合。

## <a name="example"></a>示例

##### <a name="request"></a>请求
下面是示例请求的用户的驱动器。

<!-- {
  "blockType": "request",
  "name": "get_drives"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/drives
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.drive",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 579

{
  "value": [
    {
      "id": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
      "driveType": "business",    
      "owner": {
          "user": {
              "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
              "displayName": "Ryan Gregg"
          }
      },
      "quota": {
          "deleted": 256938,
          "remaining": 1099447353539,
          "state": "normal",
          "total": 1099511627776
      }
    }
  ]
}
```

## <a name="remarks"></a>备注

大多数用户将只有一个 OneDrive。 Office 365 组可能具有多个驱动器可用。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List drives",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/List Drives"
}-->
