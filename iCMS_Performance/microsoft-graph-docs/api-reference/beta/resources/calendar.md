# <a name="calendar-resource-type"></a>日历的资源类型

这是一个用于事件的日历。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[列表中的日历](../api/user_list_calendars.md)|[日历](calendar.md)的集合|获取所有用户的日历或默认实例或其他特定日历组中的日历。|
|[创建日历](../api/user_post_calendars.md) |[日历](calendar.md)| 默认日历组或指定的日历组中创建新日历。|
|[获取日历](../api/calendar_get.md) | [日历](calendar.md) |读取属性和关系的日历对象。|
|[更新](../api/calendar_update.md) | [日历](calendar.md)  |更新日历对象。 |
|[删除](../api/calendar_delete.md) | 无 |删除日历对象。 |
|[日历视图列表](../api/calendar_list_calendarview.md) |[事件](event.md)集合| 在定义的时间范围，从用户的主日历的日历视图中获取事件、 异常和事件的单个实例`(../me/calendarview)`或从指定的日历。|
|[事件列表](../api/calendar_list_events.md) |[事件](event.md)集合| 检索日历中的事件的列表。  该列表包含单个实例会议和系列的主控形状。|
|[创建事件](../api/calendar_post_events.md) |[事件](event.md)| 默认或指定的日历中创建新的事件。|
|[创建扩展的单值属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[日历](calendar.md)  |在新的或现有的日历中创建一个或多个单值扩展的属性。   |
|[获取与单值扩展属性的日历](../api/singlevaluelegacyextendedproperty_get.md)  | [日历](calendar.md) | 获取包含扩展属性，通过使用一个单值的日历`$expand`或`$filter`。 |
|[创建扩展属性的多值](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [日历](calendar.md) | 在新的或现有的日历中创建一个或多个多值扩展的属性。  |
|[获取扩展的多值属性的日历](../api/multivaluelegacyextendedproperty_get.md)  | [日历](calendar.md) | 获取包含多值扩展的属性通过使用日历`$expand`。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|更改密钥|String|标识该日历对象的版本。 每次更改日历，那么也将更改。 这样，可以将更改应用于该对象的正确版本的 Exchange。 只读的。|
|color|String|指定要区分从用户界面中的其他日历的日历的颜色主题。 属性值是︰ LightBlue = 0，LightGreen = 1，LightOrange = 2，LightGray = 3，LightYellow = 4，LightTeal = 5，LightPink = 6，LightBrown = 7，LightRed = 8，MaxColor = 9，自动 = 1|
|id|String|组的唯一标识符。 只读的。|
|isDefaultCalendar|Boolean|如果此属性为 true 的日历在用户的默认日历，假的其他方面。|
|name|String|日历名称。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|日历视图|[事件](event.md)集合|日历的日历视图中。 导航属性。 只读的。|
|事件|[事件](event.md)集合|在日历中的事件。 导航属性。 只读的。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)集合| 多值为日历定义的扩展属性的集合。 只读的。 可以为 null。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md)集合| 单值为日历定义的扩展属性的集合。 只读的。 可以为 null。|

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "calendarView",
    "events"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.calendar"
}-->

```json
{
  "changeKey": "string",
  "color": "String",
  "id": "string (identifier)",
  "isDefaultCalendar": "boolean",
  "name": "string"
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "calendar resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
