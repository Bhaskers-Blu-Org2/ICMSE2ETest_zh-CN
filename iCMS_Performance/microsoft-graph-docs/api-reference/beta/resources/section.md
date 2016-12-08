# <a name="section-resource-type"></a>部分资源类型

OneNote 笔记本中的分区。 节可以包含页面。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "pages",
    "parentNotebook",
    "parentSectionGroup"
  ],
  "@odata.type": "microsoft.graph.section"
}-->

```json
{
  "createdBy": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "isDefault": true,
  "lastModifiedBy": "string",
  "lastModifiedTime": "String (timestamp)",
  "name": "string",
  "pagesUrl": "string",
  "self": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|创建者|String|创建的用户的部分。 只读的。|
|createdTime|方法|创建日期和时间时明时。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|id|String|部分中的唯一标识符。  只读的。|
|后|Boolean|指示这是否为用户的默认节。 只读的。|
|lastModifiedBy|String|上次修改用户部分。 只读的。|
|lastModifiedTime|方法|日期和上次修改部分时间。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|name|String|节的名称。 |
|pagesUrl|String|`pages`可以获取详细信息的所有页面一节中的终结点。 只读的。|
|自|String|终结点位置您可以获取有关部分的详细信息。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|页面|[页](page.md)集合|在部分中的页的集合。  只读的。 可以为 null。|
|parentNotebook|[笔记本](notebook.md)|包含内容的笔记本。  只读的。|
|parentSectionGroup|[SectionGroup](sectiongroup.md)|节组中包含的节。  只读的。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取节](../api/section_get.md) | [部分](section.md) |读取属性和部分的关系。|
|[创建页](../api/section_post_pages.md) |[页面](page.md)| 由过账到的页集合中指定的节中创建的页。|
|[列表页](../api/section_list_pages.md) |[页](page.md)集合| 获取中指定节的页的集合。|
|[copyToNotebook](../api/section_copytonotebook.md)|无|复制到笔记本中特定的节。|
|[copyToSectionGroup](../api/section_copytosectiongroup.md)|无|复制到特定的节组的节。|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "section resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
