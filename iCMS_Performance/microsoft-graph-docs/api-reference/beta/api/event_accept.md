# <a name="event-accept"></a>事件︰ 接受

接受指定的事件。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/accept
POST /users/<id | userPrincipalName>/events/<id>/accept
POST /groups/<id>/events/<id>/accept

POST /me/calendar/events/<id>/accept
POST /users/<id | userPrincipalName>/calendar/events/<id>/accept
POST /groups/<id>/calendar/events/<id>/accept

POST /me/calendars/<id>/events/<id>/accept
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/accept

POST /me/calendargroup/calendars/<id>/events/<id>/accept
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/accept

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/accept
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/accept
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|批注|String|在响应中包含的文本。 可选项。|
|sendResponse|Boolean|`true`如果响应将发送给组织者;否则为`false`。 可选项。 默认值是`true`。|

## <a name="response"></a>响应
如果成功，此方法返回`202, Accepted`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "event_accept"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/accept
Content-type: application/json
Content-length: 56

{
  "comment": "comment-value",
  "sendResponse": true
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event: accept",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
