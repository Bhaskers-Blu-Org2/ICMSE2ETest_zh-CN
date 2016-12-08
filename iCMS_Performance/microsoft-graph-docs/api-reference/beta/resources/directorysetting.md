# <a name="directorysetting-resource-type"></a>directorySetting 资源类型

可以创建基于可用[directorySettingTemplates](directorySettingTemplate.md)，并从其预设的默认值更改为目录设置。 这些设置可以控制实体或功能的行为，同时在租户范围级别或特定实体级别。 在这两个租户范围和特定实体级别定义了相同的设置，特定实体级别设置可能退出从租户范围设置。  例如，租户范围的设置可能会允许通过现有组的成员，被邀请的客人，但某个特定组设置可能退出以及不允许通过组成员被邀请的客人。 当前定义的系统设置只是控制办公室组行为。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[创建设置](../api/directorysetting_post_settings.md) | [directorySetting](directorysetting.md) |创建一个基于 directorySettingTemplate 的设置对象。 POST 请求必须提供 settingValues 模板中定义的所有设置。|
|[获取设置](../api/directorysetting_get.md) | [directorySetting](directorysetting.md) |阅读特定设置对象的属性。|
|[列表设置](../api/directorysetting_list.md) | [directorySetting](directorysetting.md)集合 |列出的所有设置对象的属性。|
|[更新设置](../api/directorysetting_update.md) | [directorySetting](directorysetting.md)  |更新设置对象。 只有 settingValues 可以在更新中进行更改。|
|[删除设置](../api/directorysetting_delete.md) | 无 |删除设置对象。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|显示名称|string|此组的设置，来自关联的模板的显示名称。 只读的。|
|id|string| 有关这些设置的唯一标识符。 只读的。|
|模板 Id|string| 用来创建此组的设置的模板的唯一标识符。 只读的。|
|values|[settingValue](settingvalue.md)集合| 名称/值对的集合。 必须包含并设置模板中定义的所有设置。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.directorySetting"
}-->

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "templateId": "string",
  "values": [{"@odata.type": "microsoft.graph.settingValue"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directorySetting resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->