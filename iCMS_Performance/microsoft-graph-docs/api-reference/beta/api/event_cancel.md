# <a name="event-cancel"></a>事件︰ 取消

此操作允许会议发送取消邮件和取消事件的组织者。 

此操作将事件移至已删除邮件文件夹。 组织者还可以取消定期会议的实例通过提供事件的事件 id。 与会者调用此操作获取错误 （HTTP 400 错误的请求），并显示以下错误消息︰

"不能完成您的请求。 您需要被组织者取消会议。

在于**取消**供只有组织者，并允许取消有关与会者发送自定义信息管理器，则此操作不同于[删除](event_delete.md)。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/events/<id>/cancel
POST /users/<id | userPrincipalName>/events/<id>/cancel
POST /groups/<id>/events/<id>/cancel

POST /me/calendar/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendar/events/<id>/cancel
POST /groups/<id>/calendar/events/<id>/cancel

POST /me/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/cancel

POST /me/calendargroup/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/cancel

POST /me/calendargroups/<id>/calendars/<id>/events/<id>/cancel
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/cancel
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
|批注|String|向所有与会者发送取消通知有关的注释。 可选项。|

## <a name="response"></a>响应
如果成功，此方法返回`202, Accepted`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "event_cancel"
}-->
```http
POST https://graph.microsoft.com/beta/me/events/<id>/cancel
Content-type: application/json

{
  "Comment": "Cancelling for this week due to all hands"
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "event: cancel",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
