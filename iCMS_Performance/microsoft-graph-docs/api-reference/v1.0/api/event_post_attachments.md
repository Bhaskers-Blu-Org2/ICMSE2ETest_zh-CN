# <a name="create-attachment"></a>创建附件

使用此 API 可以将[附件](../resources/attachment.md)添加到事件。 由于目前每个其余请求的总大小限制为 4 MB，这就限制了可以添加到下 4 MB 附件的大小。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
附件为[事件](../resources/event.md)中的用户或组的默认[日历](../resources/calendar.md)。
```http
POST /me/events/<id>/attachments
POST /users/<id | userPrincipalName>/events/<id>/attachments
POST /groups/<id>/events/<id>/attachments

POST /me/calendar/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendar/events/<id>/attachments
POST /groups/<id>/calendar/events/<id>/attachments
```
附件属于[calendarGroup](../resources/calendargroup.md)的用户的默认[日历](../resources/calendar.md)中的[事件](../resources/event.md)。
```http
POST /me/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments

POST /me/calendargroup/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments
```
附件属于用户的[calendarGroup](../resources/calendargroup.md)[日历](../resources/calendar.md)中的[事件](../resources/event.md)。
```http
POST /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments
POST /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |
| 内容类型 | string  | 正文中的实体数据的性质。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供[附件](../resources/attachment.md)对象的 JSON 的表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应并在响应正文中的[附件](../resources/attachment.md)对象。

## <a name="example-file-attachment"></a>示例 （附件）

##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_file_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages/<id>/attachments
Content-type: application/json
Content-length: 142

{
  "@odata.type": "#microsoft.graph.fileAttachment",
  "name": "name-value",
  "contentBytes": "contentBytes-value"
}
```

在请求正文中，提供[附件](../resources/attachment.md)对象的 JSON 的表示。

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```

## <a name="example-item-attachment"></a>示例 （项目附件）

##### <a name="request"></a>请求

下面是示例请求。

<!-- {
  "blockType": "request",
  "name": "create_item_attachment_from_event"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/events/<id>/attachments
Content-type: application/json
Content-length: 100

{
  "@odata.type": "#microsoft.graph.itemAttachment",
  "name": "name-value",
  "item": {}
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Attachment",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
