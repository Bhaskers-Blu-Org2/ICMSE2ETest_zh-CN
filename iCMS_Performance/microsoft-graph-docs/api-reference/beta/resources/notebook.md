# <a name="notebook-resource-type"></a>笔记本的资源类型

OneNote 笔记本中。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "sectionGroups",
    "sections"
  ],
  "@odata.type": "microsoft.graph.notebook"
}-->

```json
{
  "createdBy": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "isDefault": true,
  "isShared": true,
  "lastModifiedBy": "string",
  "lastModifiedTime": "String (timestamp)",
  "links": {"@odata.type": "microsoft.graph.notebookLinks"},
  "name": "string",
  "sectionGroupsUrl": "string",
  "sectionsUrl": "string",
  "self": "string",
  "userRole": "String"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|创建者|String|创建笔记本的用户。 只读的。|
|createdTime|方法|日期和时间创建笔记本时。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|id|String|笔记本的唯一标识符。 只读的。|
|后|Boolean|指示这是否为用户的默认笔记本。 只读的。|
|isShared|Boolean|指示是否共享笔记本。 如果为 true，则所有者以外的用户可以看到笔记本中的内容。 只读的。|
|lastModifiedBy|String|上次修改笔记本的用户。 只读的。|
|lastModifiedTime|方法|日期和上次修改该笔记本的时间。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|链接|[NotebookLinks](notebooklinks.md)|用于打开此笔记本的链接。 `oneNoteClientURL`链接打开笔记本时，OneNote 本机客户端中如果安装它。 `oneNoteWebURL`链接打开笔记本时，OneNote 在线中。|
|name|String|该笔记本的名称。|
|sectionGroupsUrl|String|对于 URL`sectionGroups`导航属性，它返回在笔记本中的所有节组。 只读的。|
|sectionsUrl|String|对于 URL`sections`导航属性，它返回在笔记本中的所有节。 只读的。|
|自|String|终结点可以从哪里获得有关笔记本电脑的详细信息。 只读的。|
|userRole|String|可能的值为︰ `Owner`， `Contributor`， `Reader`， `None`。 负责人表示对笔记本所有者级别的访问权限。 参与者表示对笔记本读/写访问。 读者表示笔记本的只读访问权限。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|sectionGroups|[SectionGroup](sectiongroup.md)集合|在笔记本中分区组。 只读的。 可以为 null。|
|Sections|[部分](section.md)集合|笔记本中的分区。 只读的。 可以为 null。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取笔记本](../api/notebook_get.md) | [笔记本](notebook.md) |读取的属性和关系的笔记本。|
|[创建分区组](../api/notebook_post_sectiongroups.md) |[SectionGroup](sectiongroup.md)| 由过账到的 sectionGroups 集合中指定的笔记本中创建分区组。|
|[列表中的节组](../api/notebook_list_sectiongroups.md) |[SectionGroup](sectiongroup.md)集合| 获取指定的笔记本中的节组的集合。|
|[创建分区](../api/notebook_post_sections.md) |[部分](section.md)| 由过账到 sections 集合指定笔记本中创建一个分区。|
|[列表中的节](../api/notebook_list_sections.md) |[部分](section.md)集合| 获取指定的笔记本中的分区的集合。|
|[copyNotebook](../api/notebook_copynotebook.md)| 无 | 复制一个笔记本。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notebook resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
