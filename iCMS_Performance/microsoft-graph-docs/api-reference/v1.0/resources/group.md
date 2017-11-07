# <a name="group-resource-type"></a>组资源类型

表示一个 Azure Active Directory 组，可以为 Office 365 组、 动态组或安全组。
从[directoryObject](directoryobject.md)继承。


## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[创建组](../api/group_post_groups.md) | [组](group.md) |创建新的组指定。 它可以是一个 Office 365 组、 动态组或安全组。|
|[获取组](../api/group_get.md) | [组](group.md) |读取属性和组对象的关系。|
|[更新组](../api/group_update.md) | [组](group.md) |更新组对象的属性。 |
|[删除组](../api/group_delete.md) | 无 |删除组对象。 |
|[列出所有者](../api/group_list_owners.md) |[directoryObject](directoryobject.md)集合| 从**所有者**导航属性获取组的所有者。|
|[添加所有者](../api/group_post_owners.md) |[directoryObject](directoryobject.md)| 由过账到 （安全组和已启用邮件的安全组仅支持） 的**所有者**导航属性添加新组的所有者。|
|[列表成员](../api/group_list_members.md) |[directoryObject](directoryobject.md)集合| 获取用户和组的直接**成员**导航属性来自此组的成员。|
|[添加成员](../api/group_post_members.md) |[directoryObject](directoryobject.md)| 由过账到**成员**导航属性 （对于安全组和已启用邮件的安全组仅支持），可以将用户或组添加到该组。|
|[删除成员](../api/group_delete_members.md) | 无 |从 Office 365 组、 安全组或**成员**导航属性通过已启用邮件的安全组中删除成员。 您可以删除用户或其他组。 |
|[列表 memberOf](../api/group_list_memberof.md) |[directoryObject](directoryobject.md)集合| 获取此组是从**memberOf**导航属性直接成员的组。|
|[checkMemberGroups](../api/group_checkmembergroups.md)|字符串集合|检查有列表中的组成员资格。 该函数是可传递的。|
|[getMemberGroups](../api/group_getmembergroups.md)|字符串集合|返回所有组的组的成员。 该函数是可传递的。|
|[getMemberObjects](../api/group_getmemberobjects.md)|字符串集合|返回的所有组的组的成员。 该函数是可传递的。 |
|[事件列表](../api/group_list_events.md) |[事件](event.md)集合| 获取一个事件对象集合。|
|[创建事件](../api/group_post_events.md) |[事件](event.md)| 由过账到的事件集合中创建新的事件。|
|[日历视图列表](../api/group_list_calendarview.md) |[事件](event.md)集合| 在指定的时间窗口中获取的事件的集合。|
|[列表中的对话](../api/group_list_conversations.md) |[对话](conversation.md)集合| 获取会话对象集合。|
|[创建对话](../api/group_post_conversations.md) |[对话](conversation.md)| 由过账到对话集合中创建一个新的会话。|
|[列表线程](../api/group_list_threads.md) |[ConversationThread](conversationthread.md)集合| 获取一组的所有线程。|
|[列表 acceptedSenders](../api/group_list_acceptedsenders.md) |[directoryObject](directoryobject.md)集合| 获得 acceptedSenders 列表中为此组中的用户或组的列表。|
|[添加 acceptedSender](../api/group_post_acceptedsenders.md) |[directoryObject](directoryobject.md)| 将用户或组添加到 acceptSenders 集合。|
|[删除 acceptedSender](../api/group_delete_acceptedsenders.md) |[directoryObject](directoryobject.md)| 从 acceptedSenders 集合中移除用户或组。|
|[列表 rejectedSenders](../api/group_list_rejectedsenders.md) |[directoryObject](directoryobject.md)集合| 获得 rejectedSenders 列表中为此组中的用户或组的列表。|
|[添加 rejectedSender](../api/group_post_rejectedsenders.md) |[directoryObject](directoryobject.md)| RejectedSenders 集合中添加新用户或组。|
|[删除 rejectedSender](../api/group_delete_rejectedsenders.md) |[directoryObject](directoryobject.md)| 从 rejectedSenders 集合中移除新新用户或组。|
|[addFavorite](../api/group_addfavorite.md)|无|将组添加到列表中的当前用户的收藏夹组。 只有 Office 365 组的支持。|
|[removeFavorite](../api/group_removefavorite.md)|无|从当前用户的收藏夹组的列表中删除组。 只有 Office 365 组的支持。|
|[subscribeByMail](../api/group_subscribebymail.md)|无|将 isSubscribedByMail 属性设置为**true**。 使当前用户都可以接收电子邮件对话。 只有 Office 365 组的支持。|
|[unsubscribeByMail](../api/group_unsubscribebymail.md)|无|将 isSubscribedByMail 属性设置为**false**。 禁用当前用户接收电子邮件对话。 只有 Office 365 组的支持。|
|[resetUnseenCount](../api/group_resetunseencount.md)|无|重置为 0 的当前用户上次访问后没有见过的所有帖子的 unseenCount。 只有 Office 365 组的支持。|


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|allowExternalSenders|Boolean|默认值为**false**。 指示外部成员可以向组发送电子邮件。 您可以设置该属性中的修补程序请求组;不要在初始创建该组的 POST 请求中设置它。|
|autoSubscribeNewMembers|Boolean|默认值为**false**。 指示将自动订阅接收电子邮件通知将新成员添加到组中。 您可以设置该属性中的修补程序请求组;不要在初始创建该组的 POST 请求中设置它。|
|description|字符串|组的可选说明。 |
|显示名称|String|组的显示名称。 将创建一个组并在更新过程中不能清除时，该属性是必需的。 $Filter 和 $orderby 的支持。|
|groupTypes|字符串集合| 指定要创建组的类型。 可能的值为动态组**统一**创建 Office 365 组或**DynamicMembership** 。  对于所有其他组类型，如已启用安全性的组，并启用了电子邮件的安全组，不设置此属性。|
|id|String|组的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键。 不可以为 null。 只读的。|
|isSubscribedByMail|Boolean|默认值为**true**。 指示当前用户是否订阅接收电子邮件对话。|
|邮件|String|对于组，例如，SMTP 地址"serviceadmins@contoso.onmicrosoft.com".只读的。 支持 $filter。|
|mailEnabled|Boolean|指定是否已启用邮件的组。 组的**securityEnabled**属性也是**如此**，如果是已启用邮件的安全组;否则，组是 Microsoft Exchange 通讯组。|
|mailNickname|String|组中的邮件别名。 在创建组时，必须指定此属性。 支持 $filter。|
|onPremisesLastSyncDateTime|方法|指示上一次的对象与内部目录同步。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。 支持 $filter。|
|onPremisesSecurityIdentifier|String|从内部同步到云的组包含内部安全标识符 (SID)。 只读的。 |
|onPremisesSyncEnabled|Boolean|**如此**如果此对象同步从本地目录中。**假**如果此对象最初从内部目录同步，但不会再同步;**null**如果该对象已永远不会从内部目录 （默认值） 进行同步。 只读的。 支持 $filter。|
|代理地址|字符串集合| **Any**运算符，则需要为多值属性的筛选器表达式。 只读的。 不可以为 null。 支持 $filter。 |
|securityEnabled|Boolean|指定组是否是一个安全组。 组的**mailEnabled**属性也是如此，如果是已启用邮件的安全组;否则，它是一个安全组。 必须为**false**的 Office 365 组。 支持 $filter。|
|unseenCount|Int32|当前用户没有见过他上次访问后的帖子数。|
|visibility|String| 指定 Office 365 组的可见性。 可能的值有︰**私有**、**公共**、 或空 （这将被解释为**公用**）。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|acceptedSenders|[directoryObject](directoryobject.md)集合|允许此组中创建的或日历事件的用户或组的列表。 如果此列表为非空则只有用户或组列出允许过帐。|
|calendar|[日历](calendar.md)|组的日历。 只读的。|
|日历视图|[事件](event.md)集合|日历的日历视图中。 只读的。|
|对话|[对话](conversation.md)集合|该组的对话。|
|createdOnBehalfOf|[directoryObject](directoryobject.md)| 只读的。|
|驱动器|[驱动器](drive.md)|组的驱动器。 只读的。|
|事件|[事件](event.md)集合|该组的事件。|
|memberOf|[directoryObject](directoryobject.md)集合|属于此组的成员的组。 HTTP 方法︰ 获取 （支持的所有组）。 只读的。 可以为 null。|
|成员|[directoryObject](directoryobject.md)集合| 用户、 联系人和组，此组的成员。 HTTP 方法︰ 获取 （受支持的所有组），开机自检 （支持安全组和安全性已启用邮件的组），删除 （仅用于安全组支持） 只读的。 可以为 null。|
|所有者|[directoryObject](directoryobject.md)集合|组的所有者。 所有者是一套非管理员用户有权修改此对象。 HTTP 方法︰ 获取 （受支持的所有组），开机自检 （支持安全组和安全性已启用邮件的组），删除 （仅用于安全组支持） 只读的。 可以为 null。|
|照片|[profilePhoto](profilephoto.md)| 该组的个人资料照片 |
|rejectedSenders|[directoryObject](directoryobject.md)集合|不允许在此组中创建张贴内容或日历事件的用户或组的列表。 可为 Null|
|线程|[conversationThread](conversationthread.md)集合| 该组的会话线程。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "acceptedSenders",
    "appRoleAssignments",
    "calendar",
    "calendarView",
    "conversations",
    "createdOnBehalfOf",
    "drive",
    "events",
    "memberOf",
    "members",
    "owners",
    "photo",
    "rejectedSenders",
    "threads"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.group"
}-->

```json
{
  "allowExternalSenders": true,
  "autoSubscribeNewMembers": true,
  "description": "string",
  "displayName": "string",
  "groupTypes": ["string"],
  "id": "string (identifier)",
  "isSubscribedByMail": true,
  "mail": "string",
  "mailEnabled": true,
  "mailNickname": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSecurityIdentifier": "string",
  "onPremisesSyncEnabled": true,
  "proxyAddresses": ["string"],
  "securityEnabled": true,
  "unseenCount": 1024,
  "visibility": "string",
  "acceptedSenders": [ { "@odata.type": "microsoft.graph.directoryObject"} ],
  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "calendarView": [{ "@odata.type": "microsoft.graph.event" }],
  "conversations": [ { "@odata.type": "microsoft.graph.conversation" }],
  "createdOnBehalfOf": { "@odata.type": "microsoft.graph.directoryObject" },
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "events": [ { "@odata.type": "microsoft.graph.event" }],
  "memberOf": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "members": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "owners": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "rejectedSenders": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "threads": [ { "@odata.type": "microsoft.graph.conversationThread" }]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
