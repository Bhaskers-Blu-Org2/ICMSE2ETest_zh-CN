# <a name="plan-resource-type"></a>计划资源类型

计划资源表示 Office 365 中的计划。 一个计划可以归[组](group.md)和包含[任务](task.md)的集合。 它还可以有一套[桶](bucket.md)。 每个计划对象有一个[详细信息](plandetails.md)对象，它包含有关该计划的详细信息。 有关组、 计划和任务之间的关系的[概述](tasks_overview.md)，请参阅。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "assignedToTaskBoard",
    "bucketTaskBoard",
    "buckets",
    "details",
    "progressTaskBoard",
    "tasks"
  ],
  "@odata.type": "microsoft.graph.plan"
}-->

```json
{
  "createdBy": "string",
  "id": "string (identifier)",
  "owner": "string",
  "title": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|创建者|String|只读的。 用户 id 所创建的计划。|
|id|String| 只读的。 计划的 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。 |
|所有者|String|[组](group.md)`id`通过该计划所拥有。 可以将此字段设置之前，必须存在有效的组。 一旦进行了设置，这可以只更新所有者。|
|title|字符串| 必需。 该计划的标题。 这通常是设置计划所属的组的名称。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|assignedToTaskBoard|[planTaskBoard](plantaskboard.md)| 只读的。 用于在分配给按分组正确呈现任务板视图。|
|bucketTaskBoard|[planTaskBoard](plantaskboard.md)| 只读的。 用于呈现在任务板视图中正确的存储桶。|
|存储桶|[地址散列表元](bucket.md)集合| 只读的。 可以为 null。 计划中的存储桶的集合。 |
|详细信息|[planDetails](plandetails.md)| 只读的。 有关该计划的其他详细信息。 |
|progressTaskBoard|[planTaskBoard](plantaskboard.md)| 只读的。 用来正确呈现任务板视图分组后进行的。|
|任务|[任务](task.md)集合| 只读的。 可以为 null。 计划中的任务的集合。 |

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取计划](../api/plan_get.md) | [计划](plan.md) |读取属性和关系的计划对象。|
|[列表存储桶](../api/plan_list_buckets.md) |[地址散列表元](bucket.md)集合| 获取存储桶对象集合。|
|[列表中的任务](../api/plan_list_tasks.md) |[任务](task.md)集合| 获取任务对象集合。 |
|[创建计划](../api/plan_post_plans.md) | [计划](plan.md) | 创建新的计划。 |
|[更新计划](../api/plan_update.md) | 无    |更新计划对象。 |
|[删除计划](../api/plan_delete.md) | 无 |删除计划对象。 |
|[列表计划](../api/plan_list.md) | [计划](plan.md)集合 | 获取计划对象集合。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "plan resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->