# <a name="task-resource-type"></a>任务资源类型

任务资源表示 Office 365 中的任务。 一项任务包含在[计划](plan.md)中，可以在计划中分配给[存储桶](bucket.md)。 任务的每个对象都有一个[详细信息](taskdetails.md)对象，它可以包含有关任务的详细信息。 有关组、 计划和任务之间的关系的[概述](tasks_overview.md)，请参阅。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "assignedToTaskBoardFormat",
    "bucketTaskBoardFormat",
    "details",
    "progressTaskBoardFormat"
  ],
  "@odata.type": "microsoft.graph.task"
}-->

```json
{
  "appliedCategories": {"@odata.type": "microsoft.graph.appliedCategoriesCollection"},
  "assignedBy": "string",
  "assignedDateTime": "String (timestamp)",
  "assignedTo": "string",
  "assigneePriority": "string",
  "bucketId": "string",
  "completedDateTime": "String (timestamp)",
  "conversationThreadId": "string",
  "createdBy": "string",
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "hasDescription": true,
  "id": "string (identifier)",
  "orderHint": "string",
  "percentComplete": 1024,
  "planId": "string",
  "previewType": "String",
  "startDateTime": "String (timestamp)",
  "title": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|appliedCategories|[appliedCategoriesCollection](appliedcategoriescollection.md)|已应用任务类别。 请参阅可能的值为 appliedCategoriesCollection。 |
|assignedBy|String|只读的。 按其任务分配的用户 id。|
|assignedDateTime|方法|只读的。 日期和时间的分配任务。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|分配给|String|向其分配任务的用户 id。 |
|assigneePriority|String|用于设置分配给用户在列表视图中的任务的相对优先顺序。 考虑三个任务的优先级顺序︰ `'A'`， `'B'`， `'C'`。 移动`'B'`在最上面，设置其`assignneePriority`为小于的`'A'`。 比较是序号字符串比较。 |
|bucketId|String|此任务所属的桶 id。 桶需处于计划中的任务。|
|completedDateTime|方法|只读的。 日期和时间的`'percentComplete'`的任务设置为`'100'`。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|conversationThreadId|String|在该任务上对话的线程 id。 这是在组中创建会话线程对象的 id。 |
|创建者|String|只读的。 创建任务的用户 id。 |
|createdDateTime|方法|只读的。 日期和时间在其中创建该任务。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|dueDateTime|方法|日期和时间的任务的截止日期。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|hasDescription|Boolean|只读的。 值是`true`如果该任务的详细信息对象具有非空的说明和`false`否则为。|
|id|String|只读的。 任务 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。 |
|orderHint|String|用于在列表视图中设置任务的相对顺序。 考虑三个任务的顺序︰ `'X'`， `'Y'`， `'Z'`。 移动`'Y'`在最上面，设置其`orderHint`为小于的`'X'`。 比较是序号字符串比较。|
|完成百分比|Int32|任务完成的百分比。 当设置为`100`，会认为任务已完成。 |
|planId|String|计划任务所属的 id。 一旦进行了设置，这不能更新。 |
|previewType|String| 只读的。 这将设置在任务显示的预览的类型。 可能的值为︰ `automatic`， `noPreview`， `checklist`， `description`， `reference`。|
|开始日期时间|方法|日期和时间启动任务。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|title|字符串|必需。 任务的标题。 |

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|assignedToTaskBoardFormat|[taskBoardTaskFormat](taskboardtaskformat.md)| 只读的。 用于呈现正确中按分配给分组任务板视图的任务。 |
|bucketTaskBoardFormat|[taskBoardTaskFormat](taskboardtaskformat.md)| 只读的。 用于呈现正确中按桶分组任务板视图的任务。|
|详细信息|[taskDetails](taskdetails.md)| 只读的。 有关任务的其他详细信息。 包含`description`， `references`，`checklist`等。 |
|progressTaskBoardFormat|[taskBoardTaskFormat](taskboardtaskformat.md)| 只读的。 用于呈现的任务在任务板视图分组后进行的。 |

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取任务](../api/task_get.md) | [任务](task.md) |读取属性和 task 对象的关系。|
|[创建任务](../api/task_post_tasks.md) | [任务](task.md) | 创建一个新任务。 |
|[更新任务](../api/task_update.md) | 无    |更新任务对象。 |
|[删除任务](../api/task_delete.md) | 无 |删除任务的对象。 |
|[列表中的任务](../api/task_list.md) | [任务](task.md)集合 | 获取任务对象集合。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "task resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->