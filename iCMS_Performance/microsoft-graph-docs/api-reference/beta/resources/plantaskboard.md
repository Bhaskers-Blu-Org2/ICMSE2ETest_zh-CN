# <a name="plantaskboard-resource-type"></a>planTaskBoard 资源类型

PlanTaskBoard 资源表示用来呈现一个计划任务板视图正确的信息。 每个[计划](plan.md)将具有三个 planTaskBoard 对象，一样可以有计划的三个任务板视图。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.plantaskboard"
}-->

```json
{
  "id": "string (identifier)",
  "type": "String (identifier)"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|String| 只读的。 计划的 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。 |
|类型|String| 只读的。 用于设置使用此对象来呈现任务板视图的类型。 可能的值为︰ `progress`， `assignedTo`， `bucket`。|

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 planTaskBoard](../api/plantaskboard_get.md) | [planTaskBoard](plantaskboard.md) |读取属性和关系的 planTaskBoard 对象。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "planTaskBoard resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->