# <a name="update-task"></a>更新任务

更新任务对象的属性。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /tasks/<id>

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）"|
| 如果匹配 | string | 应设置对象的 ETag 值 |
| 更喜欢 | string | 值应该设置为"返回 = 表示"以便在响应中返回更新后的对象。 这被建议，以便客户端可以获得新的 ETag 值的更新后的对象而无需进行更多的获取 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|appliedCategories|[appliedCategoriesCollection](../resources/appliedcategoriescollection.md)|已应用任务类别。 请参阅可能的值为 appliedCategoriesCollection。 |
|分配给|String|向其分配任务的用户 id。|
|assigneePriority|String|用于设置分配给用户在列表视图中的任务的相对优先顺序。 考虑三个任务的优先级顺序︰ `'A'`， `'B'`， `'C'`。 移动`'B'`在最上面，设置其`assignneePriority`为小于的`'A'`。 比较是序号字符串比较。|
|bucketId|String|此任务所属的桶 id。 桶需处于计划中的任务。|
|conversationThreadId|String|在该任务上对话的线程 id。 这是在组中创建会话线程对象的 id。|
|dueDateTime|方法|日期和时间的任务的截止日期。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|orderHint|String|用于在列表视图中设置任务的相对顺序。 考虑三个任务的顺序︰ `'X'`， `'Y'`， `'Z'`。 移动`'Y'`在最上面，设置其`orderHint`为小于的`'X'`。 比较是序号字符串比较。|
|完成百分比|Int32|任务完成的百分比。 当设置为`100`，会认为任务已完成。|
|开始日期时间|方法|日期和时间启动任务。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|title|字符串|任务的标题。|

## <a name="response"></a>响应
如果成功，此方法返回`204 No Content`响应代码。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_task"
}-->
```http
PATCH https://graph.microsoft.com/beta/tasks/<id>
Content-type: application/json
Content-length: 663
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "assignedTo": "assignedTo-value",
  "bucketId": "bucketId-value",
  "title": "title-value",
  "orderHint": "orderHint-value",
  "assigneePriority": "assigneePriority-value",
  "percentComplete": 99,
  "startDateTime": "datetime-value",
  "dueDateTime": "datetime-value",
  "previewType": "previewType-value",
  "appliedCategories": {
  },
  "conversationThreadId": "conversationThreadId-value",
}
```
##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.task"
} -->
```http
HTTP/1.1 204 No Content
```
若要获取已更新的对象，请使用`Prefer`头。 请参阅上面的请求标头。
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update task",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->