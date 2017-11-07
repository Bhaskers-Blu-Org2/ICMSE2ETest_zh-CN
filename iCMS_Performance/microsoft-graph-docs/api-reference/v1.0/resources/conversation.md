# <a name="conversation-resource-type"></a>对话资源类型

对话是集合的[线程](conversationthread.md)和线程包含发送到该线程。 所有主题和帖子的对话中都共享相同的主题。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[列表中的对话](../api/group_list_conversations.md) | [对话](conversation.md)集合 |此组中获取会话的列表。|
|[创建](../api/group_post_conversations.md) |[对话](conversation.md)| 通过包括线程和公告创建一个新的会话。|
|[获取对话](../api/conversation_get.md) | [对话](conversation.md) |读取属性和关系的对话对象。|
|[删除](../api/conversation_delete.md) | 无 |删除对话对象。 |
|[列出会话线程](../api/conversation_list_threads.md) |[conversationThread](conversationthread.md)集合| 在组对话中获得的所有线程。|
|[创建会话线程](../api/conversation_post_threads.md) |[conversationThread](conversationthread.md)集合| 指定会话中创建线程。|


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|hasAttachments|Boolean|指示是否在此对话中的张贴内容的任何具有至少一个附件。|
|id|String|会话的唯一标识符。 只读的。|
|lastDeliveredDateTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|预览|String|从主体在此 converstaion 的最新公告的简短摘要。|
|主题|String|对话的主题。 可以设置此属性，当创建对话，但不能对其进行更新。|
|uniqueSenders|字符串集合|发送消息到此对话中的所有用户。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|线程|[conversationThread](conversationthread.md)集合|在对话中的所有会话线程的集合。 导航属性。 只读的。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "threads"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.conversation"
}-->

```json
{
  "hasAttachments": true,
  "id": "string (identifier)",
  "lastDeliveredDateTime": "String (timestamp)",
  "preview": "string",
  "topic": "string",
  "uniqueSenders": ["string"]
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "conversation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
