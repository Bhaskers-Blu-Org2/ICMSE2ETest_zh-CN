# <a name="get-calendar"></a>获取日历

检索的属性和关系的日历对象。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.Read*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
用户或组的默认[日历](../resources/calendar.md)。
```http
GET /me/calendar
GET /users/<id | userPrincipalName>/calendar
GET /groups/<id>/calendar
```
[日历](../resources/calendar.md)的用户的默认值[calendarGroup](../resources/calendargroup.md)。
```http
GET /me/calendars/<id>
GET /users/<id | userPrincipalName>/calendars/<id>

GET /me/calendarGroup/calendars/<id>
GET /users/<id | userPrincipalName>/calendarGroup/calendars/<id>
```
在特定的[calendarGroup](../resources/calendargroup.md)的用户的[日历](../resources/calendar.md)。
```http
GET /me/calendarGroups/<id>/calendars/<id>
GET /users/<id | userPrincipalName>/calendarGroups/<id>/calendars/<id>
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
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[日历](../resources/calendar.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_calendar"
}-->
```http
GET https://graph.microsoft.com/beta/me/calendar
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.calendar"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 98

{
  "name": "name-value",
  "color": {
  },
  "changeKey": "changeKey-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get calendar",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
