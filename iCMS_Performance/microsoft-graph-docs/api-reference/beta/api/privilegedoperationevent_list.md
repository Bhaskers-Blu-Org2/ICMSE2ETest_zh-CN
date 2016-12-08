# <a name="list-privilegedoperationevents"></a>列表 privilegedOperationEvents

检索列表的[privilegedOperationEvent](../resources/privilegedoperationevent.md)对象，表示由特权身份管理角色操作生成审核事件。 有关审核事件的详细信息，请参阅[privilegedOperationEvent](../resources/privilegedoperationevent.md)。 要筛选查询结果，请使用标准的 OData``$filter``表达式。


## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ _Directory.AccessAsUser.All_

请求程序需要具有下列角色之一︰_特权角色管理员_、_全局管理员_、_安全管理员_、 或_安全读取器_。

 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /privilegedOperationEvents
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<code>|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和响应正文中的[privilegedOperationEvent](../resources/privilegedoperationevent.md)对象的集合。
## <a name="example"></a>示例
##### <a name="request-1"></a>申请 1
下面是示例请求。
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/privilegedOperationEvents
```
##### <a name="response-1"></a>响应 1
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedOperationEvent",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 227

{
  "value": [
    {
      "id": "id-value",
      "userId": "userId-value",
      "userName": "userName-value",
      "userMail": "userMail-value",
      "roleId": "roleId-value",
      "roleName": "roleName-value"
    }
  ]
}
```

##### <a name="request-2"></a>请求 2
下面是一个示例使用 $filter 来获得审核事件具有请求的``requestType``为``Elevate``。
<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/privilegedOperationEvents?$filter=requestType eq 'Elevate'
```
##### <a name="response-2"></a>2 响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.privilegedOperationEvent",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 547

{
    "value": [
        {
            "id": "201605110001636551",
            "userId": "0f693614-c255-4cf5-92fa-74e770c656d8",
            "userName": "admin",
            "userMail": "admin@contoso.onmicrosoft.com",
            "roleId": "558dba2d-e536-4349-a983-dd73ec2be1f7",
            "roleName": "Security Administrator",
            "expirationDateTime": "2016-05-11T19:31:14.1157385Z",
            "creationDateTime": "2016-05-11T18:31:14.5013728Z",
            "requestorId": "0f693614-c255-4cf5-92fa-74e770c656d8",
            "requestorName": "admin",
            "tenantId": "ffffae8b-cc96-4325-9bd1-dc82594b0b40",
            "requestType": "Elevate",
            "additionalInformation": "elevate me"
        },
        {
            "id": "201605190001743860",
            "userId": "0f693614-c255-4cf5-92fa-74e770c656d8",
            "userName": "admin",
            "userMail": "admin@contoso.onmicrosoft.com",
            "roleId": "558dba2d-e536-4349-a983-dd73ec2be1f7",
            "roleName": "Security Administrator",
            "expirationDateTime": "2016-05-19T17:52:58.6019279Z",
            "creationDateTime": "2016-05-19T16:52:58.9475243Z",
            "requestorId": "ffff3614-c255-4cf5-92fa-74e770c656d8",
            "requestorName": "admin",
            "tenantId": "ffffae8b-cc96-4325-9bd1-dc82594b0b40",
            "requestType": "Elevate",
            "additionalInformation": "elevate me"
        }
    ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List privilegedOperationEvents",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->