# <a name="get-group"></a>获取组

获取控件的一些属性和组对象的关系。

默认情况下不返回以下属性︰
* AccessType
* 电子邮件地址
* AllowExternalSenders
* AutoSubscribeNewMembers
* IsSubscribedByMail
* IsFavorite
* UnseenCount

可以使用查询参数**$select**以获得特定的组中，除**IsFavorite**之外的一个或多个属性的值。


## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Group.Read.All*或*Group.ReadWrite.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[组](../resources/group.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_group"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/groups/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。

注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.group"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: xxx

{
  "id": "id-value",
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "onPremisesLastSyncDateTime": "onPremisesLastSyncDateTime-value",
  "onPremisesSecurityIdentifier": "onPremisesSecurityIdentifier-value",
  "onPremisesSyncEnabled": true,
  "proxyAddresses": [
    "proxyAddresses-value"
   ],
   "securityEnabled": true,
   "visibility": "visibility-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
