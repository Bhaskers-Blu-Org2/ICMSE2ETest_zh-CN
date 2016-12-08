# <a name="inferenceclassificationoverride-resource-type"></a>inferenceClassificationOverride 资源类型

表示收到来自特定发件人的邮件的用户的重写应始终被归为。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[更新](../api/inferenceclassificationoverride_update.md) | [inferenceClassificationOverride](inferenceclassificationoverride.md) |更改为指定重写**ClassifyAs**字段。 |
|[删除](../api/inferenceclassificationoverride_delete.md) | 无 |删除重写由其 id。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|classifyAs|string| 指定如何将传入消息从特定发件人应始终归为。 可能的值为︰ `focused`， `other`。|
|id|string| 重写的唯一标识符。 只读的。|
|senderEmailAddress|[电子邮件地址](emailaddress.md)|为其创建重写该发件人电子邮件地址信息。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.inferenceClassificationOverride"
}-->

```json
{
  "classifyAs": "string",
  "id": "string (identifier)",
  "senderEmailAddress": {"@odata.type": "microsoft.graph.emailAddress"}
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "inferenceClassificationOverride resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->