# <a name="bucket-resource-type"></a>地址散列表元资源类型

桶资源的任务表示桶 （或"自定义列"） 在 Office 365 计划中。 它包含在[计划](plan.md)中，并且可以有[任务](task.md)的集合。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "tasks"
  ],
  "@odata.type": "microsoft.graph.bucket"
}-->

```json
{
  "id": "string (identifier)",
  "name": "string",
  "orderHint": "string",
  "planId": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|String| 只读的。 存储桶的 id。 它是 28 个字符长，并且区分大小写。 对服务执行[格式验证](tasks_identifiers_disclaimer.md)。|
|name|String| 存储桶的名称。 |
|orderHint|String| 用于任务板视图中设置存储桶的相对顺序。 考虑三个存储桶的顺序︰ `'E'`， `'F'`， `'G'`。 以`'F'`第一个桶，设置其`'orderHint'`为小于的`'x'`。 比较是序号字符串比较。|
|planId|String| 桶属于计划 id。 |

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|任务|[任务](task.md)集合| 只读的。 可以为 null。 桶中的任务的集合。 |

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取存储桶](../api/bucket_get.md) | [地址散列表元](bucket.md) |读取属性和桶对象的关系。|
|[列表中的任务](../api/bucket_list_tasks.md) |[任务](task.md)集合| 获取任务对象集合。|
|[创建存储桶](../api/bucket_post_buckets.md) | [地址散列表元](bucket.md)   | 创建新的存储桶对象。 |
|[更新存储桶](../api/bucket_update.md) | 无 |更新地址散列表元对象。 |
|[删除存储桶](../api/bucket_delete.md) | 无 |删除地址散列表元对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "bucket resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
