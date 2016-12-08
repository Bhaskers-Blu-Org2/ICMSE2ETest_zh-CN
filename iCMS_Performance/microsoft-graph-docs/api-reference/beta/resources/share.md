# <a name="share-resource-type"></a>共享资源类型



## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "items"
  ],
  "@odata.type": "microsoft.graph.share"
}-->

```json
{
  "id": "string (identifier)",
  "name": "string",
  "owner": {"@odata.type": "microsoft.graph.identitySet"}
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|String| 只读的。|
|name|String||
|所有者|[identitySet](identityset.md)||

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|Items|[driveItem](driveitem.md)集合| 只读的。 可以为 null。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取共享](../api/share_get.md) | [共享](share.md) |读取属性和共享对象的关系。|
|[创建项目](../api/share_post_items.md) |[driveItem](driveitem.md)| 由过账到项目集合中创建新项。|
|[列表项](../api/share_list_items.md) |[driveItem](driveitem.md)集合| 获取一个项的对象集合。|
|[更新](../api/share_update.md) | [共享](share.md)   |更新共享对象。 |
|[删除](../api/share_delete.md) | 无 |删除共享对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "share resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
