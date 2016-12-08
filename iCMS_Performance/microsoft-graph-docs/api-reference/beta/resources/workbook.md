# <a name="workbook-resource-type"></a>工作簿资源类型

工作簿是顶级对象，其中包含如工作表、 表、 范围等相关的工作簿对象。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[列表名称](../api/workbook_list_names.md) |[NamedItem](nameditem.md)集合| 获得 NamedItem 对象集合。|
|[创建表](../api/workbook_post_tables.md) |[表](table.md)| 由过账到 tables 集合中创建新表。|
|[列表中的表](../api/workbook_list_tables.md) |[表](table.md)集合| 获取表的对象集合。|
|[列表的工作表](../api/workbook_list_worksheets.md) |[工作表](worksheet.md)集合| 获取工作表对象集合。|

## <a name="properties"></a>属性
无

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|名称|[NamedItem](nameditem.md)集合|表示工作簿范围内的已命名项目 （称为范围和常量） 的集合。 只读的。|
|tables|[表](table.md)集合|表示与工作簿关联的表的集合。 只读的。|
|Worksheets|[工作表](worksheet.md)集合|代表工作表与工作簿关联的集合。 只读的。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Workbook resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->