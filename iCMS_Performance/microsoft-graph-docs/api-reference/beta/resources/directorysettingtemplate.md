# <a name="directorysettingtemplate-resource-type"></a>directorySettingTemplate 资源类型

表示供租户的系统定义的设置的目录设置模板。 [目录设置](directorysetting.md)可以创建基于可用的 directorySettingTemplates，并从其预设的默认设置发生更改的值。 无法创建、 更新或删除目录设置模板。 这些设置可以表示租户范围的设置，也可以表示特定实体设置。  目前，唯一可用的模板应用到办公室组，包括设置，如是否用户可以创建组或邀请客人从组织外部成为组的成员。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 directorySettingTemplate](../api/directorysettingtemplate_get.md) | [directorySettingTemplate](directorysettingtemplate.md) |阅读的一个系统定义 directorySettingTemplate 对象的特定属性。|
|[列表 directorySettingTemplate](../api/directorysettingtemplate_list.md) | [DirectorySettingTemplate 的集合](directorysettingtemplate.md) |列出的所有系统定义 directorySettingTemplate 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|description|string|模板的说明。 只读的。|
|显示名称|string|显示的模板的名称。 只读的。 |
|id|string| 模板的唯一标识符。 只读的。|
|values|[settingTemplateValue](settingtemplatevalue.md)集合| 列出可用的设置、 默认值和构成此模板类型的组的 settingTemplateValues 的集合。  只读的。 |

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.directorySettingTemplate"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "values": [{"@odata.type": "microsoft.graph.settingTemplateValue"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directorySettingTemplate resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->