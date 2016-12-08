# <a name="taskboardtaskformat-resource-type"></a>taskBoardTaskFormat 资源类型

TaskBoardTaskFormat 资源表示用来呈现正确地在任务板视图的任务的信息。 每个[任务](task.md)将有如三个 taskBoardTaskFormat 对象可以有三个任务板视图中的任务。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.taskboardtaskformat"
}-->

```json
{
  "id": "string (identifier)",
  "orderHint": "string",
  "type": "String (identifier)"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|String| 只读的。 任务 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。 |
|orderHint|String| 用来在任务板视图中的垂直设置任务的相对顺序。 考虑三个任务的顺序︰ `'O'`， `'P'`， `'Q'`。 若要移动`'P'`设置为垂直的顶部，其`'orderHint'`为小于的`'O'`。 比较是序号字符串比较。|
|类型|String| 只读的。 用于设置使用此对象来呈现该任务的任务板视图的类型。 可能的值为︰ `progress`， `assignedTo`， `bucket`。 |

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 taskBoardTaskFormat](../api/taskboardtaskformat_get.md) | [taskBoardTaskFormat](taskboardtaskformat.md) |读取属性和关系的 taskBoardTaskFormat 对象。|
|[更新 taskBoardTaskFormat](../api/taskboardtaskformat_update.md) | 无  |更新 taskBoardTaskFormat 对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "taskBoardTaskFormat resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->