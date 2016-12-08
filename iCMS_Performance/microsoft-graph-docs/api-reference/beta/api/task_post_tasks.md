# <a name="create-task"></a>创建任务

使用此 API 来创建一个新任务。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /tasks

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）"|

## <a name="request-body"></a>请求正文
在请求正文中，提供[任务](../resources/task.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[任务](../resources/task.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_task_from_tasks"
}-->
```http
POST https://graph.microsoft.com/beta/tasks
Content-type: application/json
Content-length: 192

{
  "assignedTo": "assignedTo-value",
  "planId": "planId-value",
  "bucketId": "bucketId-value",
  "title": "title-value",
  "orderHint": "orderHint-value"
}
```
在请求正文中，提供[任务](../resources/task.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.task"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 663

{
  "@odata.etag": "W/\"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn\"",
  "createdBy": "createdBy-value",
  "assignedTo": "assignedTo-value",
  "planId": "planId-value",
  "bucketId": "bucketId-value",
  "title": "title-value",
  "orderHint": "orderHint-value",
  "assigneePriority": "assigneePriority-value",
  "percentComplete": 99,
  "startDateTime": "datetime-value",
  "assignedDateTime": "datetime-value",
  "createdDateTime": "datetime-value",
  "assignedBy": "assignedBy-value",
  "dueDateTime": "datetime-value",
  "hasDescription": true,
  "previewType": "previewType-value",
  "completedDateTime": "datetime-value",
  "appliedCategories": {
  },
  "conversationThreadId": "conversationThreadId-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create task",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
