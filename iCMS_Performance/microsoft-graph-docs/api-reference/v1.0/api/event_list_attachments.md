# <a name="list-attachments"></a>附件列表

检索附加到事件的[附件](../resources/attachment.md)对象的列表。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Calendars.Read* 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
附件为[事件](../resources/event.md)中的用户或组的默认[日历](../resources/calendar.md)。
```http
GET /me/events/<id>/attachments
GET /users/<id | userPrincipalName>/events/<id>/attachments
GET /groups/<id>/events/<id>/attachments

GET /me/calendar/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendar/events/<id>/attachments
GET /groups/<id>/calendar/events/<id>/attachments
```
附件属于[calendarGroup](../resources/calendargroup.md)的用户的默认[日历](../resources/calendar.md)中的[事件](../resources/event.md)。
```http
GET /me/calendars/<id>/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendars/<id>/events/<id>/attachments

GET /me/calendargroup/calendars/<id>/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendargroup/calendars/<id>/events/<id>/attachments
```
附件属于用户的[calendarGroup](../resources/calendargroup.md)[日历](../resources/calendar.md)中的[事件](../resources/event.md)。
```http
GET /me/calendargroups/<id>/calendars/<id>/events/<id>/attachments
GET /users/<id | userPrincipalName>/calendargroups/<id>/calendars/<id>/events/<id>/attachments
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
如果成功，此方法返回`200 OK`响应并在响应正文中的[附件](../resources/attachment.md)对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_attachments"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/events/<id>/attachments
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.attachment",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 215

{
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
      "contentType": "contentType-value",
      "contentLocation": "contentLocation-value",
      "contentBytes": "contentBytes-value",
      "contentId": "null",
      "lastModifiedDateTime": "datetime-value",
      "id": "id-value",
      "isInline": false,
      "isContactPhoto": false,
      "name": "name-value",
      "size": 99
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List attachments",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->