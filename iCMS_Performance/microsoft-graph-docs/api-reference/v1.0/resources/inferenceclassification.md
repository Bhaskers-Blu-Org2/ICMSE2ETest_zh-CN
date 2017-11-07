# <a name="inferenceclassification-resource-type"></a>inferenceClassification 资源类型

若要启用对用户有更多相关的或重要的焦点的用户的邮件分类。 

有关详细信息，请参阅[管理专注于收件箱](manage_focused_inbox.md)。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[创建 inferenceClassificationOverride](../api/inferenceclassification_post_overrides.md) |[inferenceClassificationOverride](inferenceclassificationoverride.md)| 创建发件人标识 SMTP 地址重写。 未来从消息的 SMTP 地址将一直归在重写中指定。|
|[列表会覆盖](../api/inferenceclassification_list_overrides.md) |[inferenceClassificationOverride](inferenceclassificationoverride.md)集合| 获取用户设置始终将来自特定发件人的邮件分类以特定的方式重写。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|string| 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|重写|[inferenceClassificationOverride](inferenceclassificationoverride.md)集合| 一套覆盖用户可以始终将来自特定发件人以某些方式分类︰ `focused`，或`other`。 只读的。 可以为 null。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.inferenceClassification"
}-->

```json
{
  "id": "string (identifier)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "inferenceClassification resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->