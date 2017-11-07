# <a name="connectorgroup-resource-type"></a>connectorGroup 资源类型




## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 connectorGroup](../api/connectorgroup_get.md) | [connectorGroup](connectorgroup.md) |读取属性和关系的 connectorGroup 对象。|
|[创建应用程序](../api/connectorgroup_post_applications.md) |[应用程序](application.md)| 将应用程序与连接器组由过账到的应用程序集合相关联。|
|[列出应用程序](../api/connectorgroup_list_applications.md) |[应用程序](application.md)集| 获取关联的应用程序对象集合。|
|[创建连接器](../api/connectorgroup_post_members.md) |[连接器](connector.md)| 由过账到的成员集合的接口组添加连接符。|
|[列表成员](../api/connectorgroup_list_members.md) |[连接器](connector.md)的集合| 获取一个连接器对象集合。|
|[更新](../api/connectorgroup_update.md) | [connectorGroup](connectorgroup.md)    |更新 connectorGroup 对象。 |
|[删除](../api/connectorgroup_delete.md) | 无 |删除 connectorGroup 对象。 在删除连接器组之前必须删除所有连接器。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|connectorGroupType|string| 将组与一起使用的连接器类型。 可能的值为︰ `applicationProxy`。|
|id|String| ConnectorGroup 对象 id|
|后|Boolean| 指示如果 connectorGroup 的默认接口组。 只有单个连接器组可以是默认的 connectorGroup，并由系统设置。|
|name|String| 与 connectorGroup 相关联的名称。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|应用程序|[应用程序](application.md)集| 只读的。 可以为 null。|
|成员|[连接器](connector.md)的集合| 只读的。 可以为 null。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.connectorGroup"
}-->

```json
{
  "connectorGroupType": "string",
  "id": "String (identifier)",
  "isDefault": true,
  "name": "String"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "connectorGroup resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
