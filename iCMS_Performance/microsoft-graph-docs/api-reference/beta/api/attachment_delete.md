# <a name="delete-attachment"></a>删除附件

从日历事件、 电子邮件或组帖子删除附件。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

* 如果邮件中的附件的访问︰ *Mail.ReadWrite*
* 如果在事件中的附件的访问︰ *Calendars.ReadWrite*
* 如果访问中事件进行分组或公告附件︰ *Group.ReadWrite.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
附件为[事件](../resources/event.md)中的用户或组的默认[日历](../resources/calendar.md)。
```http
DELETE /me/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/events/<id>/attachments/<id>
DELETE /groups/<id>/events/<id>/attachments/<id>

DELETE /me/calendar/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendar/events/<id>/attachments/<id>
DELETE /groups/<id>/calendar/events/<id>/attachments/<id>
```
附件属于[calendarGroup](../resources/calendargroup.md)的用户的默认[日历](../resources/calendar.md)中的[事件](../resources/event.md)。
```http
DELETE /me/calendars/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments/<id>

DELETE /me/calendargroup/calendars/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments/<id>
```
附件属于用户的[calendarGroup](../resources/calendargroup.md)[日历](../resources/calendar.md)中的[事件](../resources/event.md)。
```http
DELETE /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments/<id>
```
用户的邮箱中的[邮件](../resources/message.md)的附件。
```http
DELETE /me/messages/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/messages/<id>/attachments/<id>
```
附件包含在顶部的[消息](../resources/message.md)级别的[mailFolder](../resources/mailfolder.md)用户的邮箱中。
```http
DELETE /me/mailFolders/<id>/messages/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/mailFolders/<id>/messages/<id>/attachments/<id>
```
[MailFolder](../resources/mailfolder.md)用户的邮箱中的子文件夹中包含的[邮件](../resources/message.md)的附件。  下面的示例演示一个嵌套级别的但消息可以位于中子级的子级，等等。
```http
DELETE /me/mailFolders/<id>/childFolders/<id>/.../messages/<id>/attachments/<id>
DELETE /users/<id | userPrincipalName>/mailFolders/<id>/childFolders/<id>/messages/<id>/attachments/<id>
```
[发送](../resources/post.md)[线程](../resources/conversationthread.md)属于一组[对话](../resources/conversation.md)中的附件。
```http
DELETE /groups/<id>/threads/<id>/posts/<id>/attachments/<id>
DELETE /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/attachments/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。


## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "delete_attachment"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/events/<id>/attachments/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete attachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
