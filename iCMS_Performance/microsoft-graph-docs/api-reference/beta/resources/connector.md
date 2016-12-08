# <a name="connector-resource-type"></a>连接器资源类型


<!-- Not supported items
|[Create connectorGroup](../api/connector_post_memberof.md) |[connectorGroup](connectorgroup.md)| Associate a connector with a new connectorGroup by posting to the memberOf collection.|
|[Update](../api/connector_update.md) | [connector](connector.md)   | Connectors are created when they are registed with the tenant. |
|[Delete](../api/connector_delete.md) | None |Delete connector object. |

-->

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取接口](../api/connector_get.md) | [连接器](connector.md) |读取属性和连接器对象的关系。|
|[列表 memberOf](../api/connector_list_memberof.md) |[connectorGroup](connectorgroup.md)集合| 获取与连接器相关联的 connectorGroup 对象。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|externalIp|String|作为接头机服务检测到外部的 IP 地址。 只读的|
|id|String| 连接器对象 id。 <BR>只读的。|
|计算机名|String| 连接器正在其运行的计算机的名称。 <BR>只读的|
|status|string| 指示连接器的状态。 可能的值为︰ `active`， `inactive`。 只读的 |

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|memberOf|[connectorGroup](connectorgroup.md)集合| 连接是的成员 connectorGroup。<br>只读的。 |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.connector"
}-->

```json
{
  "externalIp": "String",
  "id": "String (identifier)",
  "machineName": "String",
  "status": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "connector resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
