# <a name="calendargroup-resource-type"></a>calendarGroup 资源类型

一组的日历。

**请注意**Outlook.com 支持仅可通过访问默认日历组。./ 我/日历快捷方式。 无法删除该日历组。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[列表中的日历组](../api/user_list_calendargroups.md) |[日历](calendar.md)的集合| 获取用户的日历组。|
|[创建日历组](../api/user_post_calendargroups.md) |[日历](calendar.md)| 创建一个新日历组。|
|[获取日历组](../api/calendargroup_get.md) | [calendarGroup](calendargroup.md) |读取属性和关系的日历组对象。|
|[更新](../api/calendargroup_update.md) | [calendarGroup](calendargroup.md) |更新 calendarGroup 对象。 |
|[删除](../api/calendargroup_delete.md) | 无 |删除 calendarGroup 对象。 |
|[列表中的日历](../api/calendargroup_list_calendars.md) |[日历](calendar.md)的集合| 列表中的日历组的日历。|
|[创建日历](../api/calendargroup_post_calendars.md) |[日历](calendar.md)| 在一个日历组中创建新日历。|


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|name|String|组的名称。|
|更改密钥|String|标识的版本的日历组。 每次更改日历组，那么也将更改。 这样，可以将更改应用于该对象的正确版本的 Exchange。 只读的。|
|classId|Guid|类标识符。 只读的。|
|id|String|组的唯一标识符。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|日历|[日历](calendar.md)的集合|在日历组日历。 导航属性。 只读的。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "calendars"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.calendarGroup"
}-->

```json
{
  "changeKey": "string",
  "classId": "guid",
  "id": "string (identifier)",
  "name": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "calendarGroup resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
