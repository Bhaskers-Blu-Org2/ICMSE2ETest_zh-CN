# <a name="subscription-resource-type"></a>预订资源类型
一个订阅允许一个客户端应用程序接收 Microsoft Graph 数据有关的通知。 当前订阅启用以下数据集︰

1. 邮件、 事件和从 Outlook 联系人
1. 从办公室组对话。


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.subscription"
}-->

```json
{
  "changeType": "string",
  "notificationUrl": "string",
  "resource": "string",
  "expirationDateTime": "string (timestamp)",
  "id": "string (identifier)",
  "clientState": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|误差|string|指示中的订阅资源，将引发通知的更改类型。 受支持的值是︰ `created`， `updated`， `deleted`。 可以使用以逗号分隔的列表来组合多个值。|
|notificationUrl|string|将接收通知的终结点的 URL。 该 URL 必须使用 HTTPS 协议。|
|资源|string|指定要监视的更改的资源。 不包含基 URL ("https://graph.microsoft.com/v1.0/")。|
|expirationDateTime|[日期时间](http://tools.ietf.org/html/rfc3339)|指定的日期和时间的 webhook 订阅过期时。 时间以 UTC，也可以是一段时间从不同的预订创建预订的资源。  请参阅下表中的最大值。|
|clientState|string|指定的值`clientState`中每个通知服务发送的属性。 最大长度为 255 个字符。 客户端可以检查通知进行比较的值来自于服务`clientState`属性与该订阅的值一起发送`clientState`收到的每个通知的属性。|
|id|string|预订的唯一标识符。 只读的。|

## <a name="maximum-expiration-times-per-resource"></a>每个资源的最大过期时间
| 资源 | 最大的过期时间 |
|:---------------------|:--------------------|
|邮件| 4230 分钟。|
|日历| 4230 分钟。|
|联系人| 4230 分钟。|
|组对话| 4230 分钟。|

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[创建订阅](../api/subscription_post_subscriptions.md) | [订阅](subscription.md) |订阅 Microsoft Graph 数据发生更改时接收通知侦听器应用程序。|
|[更新订阅](../api/subscription_update.md) | [订阅](subscription.md) |通过更新其过期时间将续订订阅。|
|[获取订阅](../api/subscription_get.md) | [订阅](subscription.md) |读取属性和订阅对象的关系。|
|[删除订阅](../api/subscription_delete.md) | 无 |删除订阅对象。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "subscription resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
