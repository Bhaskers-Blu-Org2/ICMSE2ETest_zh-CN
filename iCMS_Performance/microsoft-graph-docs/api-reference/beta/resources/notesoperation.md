# <a name="notesoperation-resource-type"></a>notesOperation 资源类型

某些长期运行 OneNote 的操作状态。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.notesoperation"
}-->

```json
{
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.notesOperationError"},
  "id": "string (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "resourceId": "string",
  "resourceLocation": "string",
  "status": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|createdDateTime| 方法 |操作的开始时间。|
|错误|[notesOperationError](notesoperationerror.md)|由操作返回的错误。|
|id|string|操作 id。 只读的。|
|lastActionDateTime| 方法 |上一次操作的操作时间。|
|资源 Id|string|该资源 id。|
|resourceLocation|string|资源的 URI 的对象。 例如，复制的页或节的资源的 URI。 |
|status|string|操作的当前状态︰ `notstarted`， `running`， `completed`，`failed` |

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取操作](../api/notesoperation_get.md) | [NotesOperation](notesoperation.md) |获取操作的状态。 |


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notesOperation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
