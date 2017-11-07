# <a name="mailfolder-resource-type"></a>mailFolder 资源类型

用户的邮箱，如收件箱、 草稿和已发送的邮件中 mailFolder。 MailFolders 可以包含消息和子 mailFolders。


## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 mailFolder](../api/mailfolder_get.md) | [mailFolder](mailfolder.md) |读取属性和关系的 mailFolder 对象。|
|[创建 MailFolder](../api/mailfolder_post_childfolders.md) |[MailFolder](mailfolder.md)| 创建下由过账到 childFolders 集合的当前一个新的 mailFolder。|
|[列表 childFolders](../api/mailfolder_list_childfolders.md) |[MailFolder](mailfolder.md)集合| 获取指定文件夹下的文件夹集合。 您可以使用`.../me/MailFolders`以获取顶级文件夹集合并导航到另一个文件夹的快捷方式。|
|[创建邮件](../api/mailfolder_post_messages.md) |[消息](message.md)| 由过账到的邮件集合中当前 mailFolder 创建一个新邮件。|
|[列表中的邮件](../api/mailfolder_list_messages.md) |[消息](message.md)集合| 获取已登录的用户邮箱中的所有邮件或邮箱中的指定文件夹中的邮件。|
|[更新](../api/mailfolder_update.md) | [mailFolder](mailfolder.md)|更新指定的 mailFolder 对象。 |
|[删除](../api/mailfolder_delete.md) | 无 |删除指定的 mailFolder 对象。 |
|[复制](../api/mailfolder_copy.md)|[MailFolder](mailfolder.md)|MailFolder 和其内容复制到另一个 mailFolder。|
|[移动](../api/mailfolder_move.md)|[MailFolder](mailfolder.md)|移动到另一个 mailFolder mailFolder 及其内容。|


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|childFolderCount|Int32|在当前的 mailFolder 的直接子 mailFolders 号。|
|显示名称|String|MailFolder 显示名称。|
|id|String|MailFolder 的唯一标识符。 您可以使用以下已知的名称访问对应的文件夹︰ 收件箱、 草稿、 已发送邮件、 DeletedItems。|
|parentFolderId|String|MailFolder 的父 mailFolder 的唯一标识符。|
|totalItemCount|Int32|在 mailFolder 中的项的数目。|
|unreadItemCount|Int32|在 mailFolder 中项数的值标记为未读。|

**访问项目有效地计算**

文件夹的 TotalItemCount 和 UnreadItemCount 的属性，可以方便地计算读取文件夹中的项目数。
它们使您可以避免查询可以产生大量的滞后时间如下︰
```
https://outlook.office.com/api/v1.0/me/folders/inbox/messages?$count=true&$filter=isread%20eq%20false
```
MailFolders 在 Outlook 中的可以包含多个类型的项目，例如，可以包含收件箱会议不同于邮件项目请求项。 TotalItemCount 和 UnreadItemCount mailFolder，而不考虑它们的项目类型中包含项目。


## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|childFolders|[MailFolder](mailfolder.md)集合|在 mailFolder 中子文件夹的集合。|
|消息|[消息](message.md)集合|在 mailFolder 中的消息的集合。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "childFolders",
    "messages"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.mailFolder"
}-->

```json
{
  "childFolderCount": 1024,
  "displayName": "string",
  "id": "string (identifier)",
  "parentFolderId": "string",
  "totalItemCount": 1024,
  "unreadItemCount": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "mailFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
