# <a name="taskdetails-resource-type"></a>taskDetails 资源类型

TaskDetails 资源表示有关任务的附加信息。 [任务](task.md)的每个对象都有一个详细信息的对象。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.taskdetails"
}-->

```json
{
  "checklist": {"@odata.type": "microsoft.graph.checklistItemCollection"},
  "completedBy": "string",
  "description": "string",
  "id": "string (identifier)",
  "previewType": "String",
  "references": {"@odata.type": "microsoft.graph.externalReferenceCollection"}
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|核对清单|[checklistItemCollection](checklistitemcollection.md)| 在该任务的核对清单项的集合。|
|completedBy|String| 按其完成任务的用户 id。 |
|description|字符串| 任务的描述。 |
|id|String| 只读的。 任务 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。|
|previewType|String| 这将设置在任务显示的预览的类型。 可能的值为︰ `automatic`， `noPreview`， `checklist`， `description`， `reference`。|
|引用|[externalReferenceCollection](externalreferencecollection.md)| 在该任务上的引用的集合。 |

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 taskDetails](../api/taskdetails_get.md) | [taskDetails](taskdetails.md) |读取属性和关系的 taskDetails 对象。|
|[更新 taskDetails](../api/taskdetails_update.md) | 无|更新 taskDetails 对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "taskDetails resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->