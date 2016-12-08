# <a name="sectiongroup-resource-type"></a>sectionGroup 资源类型

OneNote 笔记本中的分区组。 节组可以包含节和节组。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "parentNotebook",
    "parentSectionGroup",
    "sectionGroups",
    "sections"
  ],
  "@odata.type": "microsoft.graph.sectiongroup"
}-->

```json
{
  "createdBy": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedBy": "string",
  "lastModifiedTime": "String (timestamp)",
  "name": "string",
  "sectionGroupsUrl": "string",
  "sectionsUrl": "string",
  "self": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|创建者|String|创建分区组的用户。 只读的。|
|createdTime|方法|日期和时间创建的节组的。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|id|String|节组的唯一标识符。 只读的。|
|lastModifiedBy|String|上次修改用户的节组。 只读的。| 
|lastModifiedTime|方法|日期和上次修改的节组的时间。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|name|String|节组的名称。|
|sectionGroupsUrl|String|对于 URL`sectionGroups`导航属性，它返回所有节组的节组中。 只读的。| 
|sectionsUrl|String|对于 URL`sections`导航属性，它返回该节组中的所有节。 只读的。|
|自|String|终结点可以从哪里获得有关的节组的详细信息。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|parentNotebook|[笔记本](notebook.md)|包含的节组的笔记本。 只读的。|
|parentSectionGroup|[SectionGroup](sectiongroup.md)|包含的节组的节组。 只读的。|
|sectionGroups|[SectionGroup](sectiongroup.md)集合|在节中节组。 只读的。 可以为 null。|
|Sections|[部分](section.md)集合|中的节组的节。 只读的。 可以为 null。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取分区组](../api/sectiongroup_get.md) | [SectionGroup](sectiongroup.md) |读取的属性和关系的节组。|
|[创建分区组](../api/sectiongroup_post_sectiongroups.md) |[SectionGroup](sectiongroup.md)| 创建由过账到的 sectionGroups 集合中指定的节组的节组。|
|[列表中的节组](../api/sectiongroup_list_sectiongroups.md) |[SectionGroup](sectiongroup.md)集合| 获取中指定的节组的节组的集合。|
|[创建分区](../api/sectiongroup_post_sections.md) |[部分](section.md)| 创建由过账到 sections 集合中指定的节组的节。|
|[列表中的节](../api/sectiongroup_list_sections.md) |[部分](section.md)集合| 获取集合中指定的节组的节。|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sectionGroup resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->