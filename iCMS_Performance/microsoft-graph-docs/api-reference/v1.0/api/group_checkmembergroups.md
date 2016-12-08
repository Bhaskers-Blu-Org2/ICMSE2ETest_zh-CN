# <a name="group-checkmembergroups"></a>组︰ checkMemberGroups
检查指定的组列表中的成员资格。 从列表中返回指定的组的直接或可传递成员身份的组。 

最大为每个请求的 20 组，您可以检查。 此功能支持 Office 365 和其他类型的组设置 Azure 的广告。 注意︰ Office 365 组不能包含组。 因此在 Office 365 组中的成员身份始终是直接的。 

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups/<id>/checkMemberGroups
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|groupIds|String|组 id 的数组|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应并在响应正文中的字符串集合对象。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "group_checkmembergroups"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/<id>/checkMemberGroups
Content-type: application/json
Content-length: 44

{
  "groupIds": [
    "groupIds-value"
  ]
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "string",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 39

{
  "value": [
    "string-value"
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group: checkMemberGroups",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
