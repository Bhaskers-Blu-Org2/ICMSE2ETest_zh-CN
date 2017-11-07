# <a name="conversationthread-resource-type"></a>conversationThread 资源类型
ConversationThread 是一套[发](post.md)。

最后一个帖子收件人集合是整个主线的聚合的收件人。 线程可以拥有不断增长的收件人集合。
从线程中移除某个收件人时，将创建一个新线程。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[列表线程](../api/group_list_threads.md) | [conversationThread](conversationthread.md)集合 |获取一组的所有线程。|
|[创建线程](../api/group_post_threads.md) | [conversationThread](conversationthread.md) |通过首先创建一个线程启动一个新的会话。 在组中创建新会话、 会话线程和开机自检。|
|[获得 conversationThread](../api/conversationthread_get.md) | [conversationThread](conversationthread.md) |获取所属的组的特定线程。 |
|[更新](../api/conversationthread_update.md) | [conversationThread](conversationthread.md)  |更新 conversationThread 对象。 |
|[删除](../api/conversationthread_delete.md) | 无 |删除 conversationThread 对象。 |
|[回复](../api/conversationthread_reply.md)|无|通过创建新的公告实体回复此线程。|
|[公告列表](../api/conversationthread_list_posts.md) |[过帐](post.md)的集合| 获取指定线程的公告。 |

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|String| 只读的。|
|toRecipients|[收件人](recipient.md)集合|收件人︰ 收件人线程。|
|ccRecipients|[收件人](recipient.md)集合|电子邮件抄送收件人线程。|
|主题|String|对话的主题。 可以设置此属性，当创建对话，但不能对其进行更新。||
|hasAttachments|Boolean|指示是否在此线程中发送的任何有至少一个附件。|
|lastDeliveredDateTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|uniqueSenders|字符串集合|向此线程发送消息的所有用户。|
|预览|String|从主体在此 converstaion 的最新公告的简短摘要。|
|isLocked|Boolean|指示线程是否处于锁定状态。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|公告|[过帐](post.md)的集合| 只读的。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "posts"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.conversationThread"
}-->

```json
{
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "hasAttachments": true,
  "id": "string (identifier)",
  "isLocked": true,
  "lastDeliveredDateTime": "String (timestamp)",
  "preview": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "topic": "string",
  "uniqueSenders": ["string"]
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "conversationThread resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
