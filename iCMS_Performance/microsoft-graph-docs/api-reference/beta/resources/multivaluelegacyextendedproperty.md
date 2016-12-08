# <a name="multivaluelegacyextendedproperty-resource-type"></a>multiValueLegacyExtendedProperty 资源类型

扩展的属性包含的值的集合。

有关何时使用 Office 365 的数据扩展或扩展的属性，以及如何指定的扩展的属性的详细信息，请参阅[扩展属性概述](../resources/extended-properties-overview.md)。

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[发布](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | 受支持的资源实例︰[消息](../resources/message.md)、 [mailFolder](../resources/mailfolder.md)、[事件](../resources/event.md)、[日历](../resources/calendar.md)、[联系人](../resources/contact.md)或[contactFolder](../resources/contactfolder.md)，但组无法[开机自检](../resources/post.md)。 | 新的或现有的受支持的资源实例中创建的**multiValueLegacyExtendedProperty** 。 |
|[获取](../api/multivaluelegacyextendedproperty_get.md) |受支持的资源实例 （[消息](../resources/message.md)、 [mailFolder](../resources/mailfolder.md)、[事件](../resources/event.md)、[日历](../resources/calendar.md)、[联系人](../resources/contact.md)、 [contactFolder](../resources/contactfolder.md)，或组[过帐](../resources/post.md)） 与[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)对象扩展。 |获取扩展的属性使用的资源实例`$expand`。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|string|属性标识符。 只读的。|
|value|字符串集合|属性值的集合。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.multivaluelegacyextendedproperty"
}-->

```json
{
  "id": "string (identifier)",
  "value": ["string"]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "multiValueLegacyExtendedProperty resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->