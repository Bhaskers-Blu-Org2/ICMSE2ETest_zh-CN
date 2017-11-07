# <a name="page-resource-type"></a>页面资源类型

OneNote 笔记本中的页面。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "parentNotebook",
    "parentSection"
  ],
  "@odata.type": "microsoft.graph.page"
}-->

```json
{
  "content": "stream",
  "contentUrl": "string",
  "createdByAppId": "string",
  "createdTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedTime": "String (timestamp)",
  "level": 1024,
  "links": {"@odata.type": "microsoft.graph.pageLinks"},
  "order": 1024,
  "self": "string",
  "title": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|内容|Stream|页的 HTML 内容。|
|contentUrl|String|页的 HTML 内容的 URL。  只读的。|
|createdByAppId|String|创建页面的应用程序的唯一标识符。 只读的。|
|createdTime|方法|日期和时间创建页面时。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|id|String|页的唯一标识符。  只读的。|
|lastModifiedTime|方法|日期和上次修改网页的时间。 时间戳表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|级别|Int32|页上的缩进级别。 只读的。|
|链接|[PageLinks](pagelinks.md)|打开数据访问页的链接。 `oneNoteClientURL`链接在如果安装 OneNote 的本机客户端中打开页面。 `oneNoteWebUrl`链接在线 OneNote 中打开页面。 只读的。|
|顺序|Int32|其父节中页的顺序。 只读的。|
|自|String|终结点可以从哪里获得有关该页面的详细信息。 只读的。|
|title|字符串|网页的标题。 |

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|parentNotebook|[笔记本](notebook.md)|包含页的笔记本。  只读的。|
|parentSection|[部分](section.md)|包含该页面的部分。 只读的。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取页](../api/page_get.md) | [页面](page.md) |读取的属性和关系的页面。|
|[更新页面内容](../api/page_update.md) | 无 |更新页上的 HTML 的内容。 |
|[删除页](../api/page_delete.md) | 无 |删除该页面。 |
|[copyToSection](../api/page_copytosection.md)| 无 |将页面复制到一个特定的分区。|


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "page resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->