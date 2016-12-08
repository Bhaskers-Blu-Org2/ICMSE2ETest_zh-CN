# <a name="plandetails-resource-type"></a>planDetails 资源类型

PlanDetails 资源表示计划有关的附加信息。 [计划](plan.md)中的每个对象都有一个详细信息的对象。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.plandetails"
}-->

```json
{
  "category0Description": "string",
  "category1Description": "string",
  "category2Description": "string",
  "category3Description": "string",
  "category4Description": "string",
  "category5Description": "string",
  "id": "string (identifier)",
  "sharedWith": {"@odata.type": "microsoft.graph.userIdCollection"}
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|category0Description|String| 可应用于任务的说明的类别 （或标签）。 |
|category1Description|String| 可应用于任务的说明的类别 （或标签）。 |
|category2Description|String| 可应用于任务的说明的类别 （或标签）。 |
|category3Description|String| 可应用于任务的说明的类别 （或标签）。 |
|category4Description|String| 可应用于任务的说明的类别 （或标签）。 |
|category5Description|String| 可应用于任务的说明的类别 （或标签）。 |
|id|String| 只读的。 计划的 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。|
|sharedWith|[userIdCollection](useridcollection.md)| 此计划与共享的用户 id 的列表。 如果您将充分利用 Office 365 组，使用组 API 管理组成员共享[组的](group.md)计划。 但不是必需为其访问组拥有的计划，还可以向此集合添加组的现有成员。 |

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 planDetails](../api/plandetails_get.md) | [planDetails](plandetails.md) |读取属性和关系的 planDetails 对象。|
|[更新 planDetails](../api/plandetails_update.md) | 无  |更新 planDetails 对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "planDetails resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->