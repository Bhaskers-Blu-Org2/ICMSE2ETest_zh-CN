# <a name="privilegedrolesummary-resource-type"></a>privilegedRoleSummary 资源类型

统计信息汇总为一个特定的角色。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 privilegedRoleSummary](../api/privilegedrolesummary_get.md) | [privilegedRoleSummary](privilegedrolesummary.md) |读取属性和关系的 privilegedRoleSummary 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|elevatedCount|int32|拥有该角色分配和角色的用户数将被激活。|
|id|string| 角色的唯一标识符。 只读的。|
|managedCount|int32|已分配的角色的用户，但该角色的数目被停用。|
|mfaEnabled|布尔|**如此**如果角色激活要求 MFA。 **假**如果角色激活不需要 MFA。|
|status|string| 可能的值为︰ `ok`， `bad`。 值取决于的比率 (managedCount / usersCount)。 如果该比率小于预先定义的阈值，`ok`将返回。 否则为`bad`将返回。|
|usersCount|int32|分配角色的用户数。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedRoleSummary"
}-->

```json
{
  "elevatedCount": 1024,
  "id": "string (identifier)",
  "managedCount": 1024,
  "mfaEnabled": true,
  "status": "string",
  "usersCount": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedRoleSummary resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->