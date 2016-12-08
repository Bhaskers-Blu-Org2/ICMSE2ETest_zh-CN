# <a name="permission-resource-type"></a>权限的资源类型

提供了有关[driveItem](driveitem.md)的授予的权限的信息。

权限具有许多不同的形式。 该**权限**资源代表这些不同的形式，通过对**权限**的资源的属性。

## <a name="methods"></a>方法

| 方法                                              | 返回类型                            | 说明                                             |
|:----------------------------------------------------|:---------------------------------------|:--------------------------------------------------------|
| [列表权限](../api/item_list_permissions.md) | [权限](permission.md)集 | 列表项的权限。                        |
| [获得权限](../api/permission_get.md)          | [权限](permission.md)            | 读取属性和关系的权限对象。 |
| [添加](../api/item_invite.md)                        | [权限](permission.md)            | 向项目中添加新的权限。                         |
| [更新](../api/permission_update.md)               | [权限](permission.md)            | 更新的权限对象。                               |
| [删除](../api/permission_delete.md)               | 无                                   | 删除的权限对象。                               |


## <a name="properties"></a>属性

| 属性      | 类型                                      | 说明                                                                                                                           |
|:--------------|:------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| id            | String                                    | 在该项目的所有权限的权限的唯一标识符。 只读的。                                                 |
| grantedTo     | [identitySet](identityset.md)             | 用户类型权限、 用户和应用程序的此权限的详细信息。 只读的。                                    |
| 邀请    | [sharingInvitation](sharinginvitation.md) | 任何相关联的共享邀请此权限的详细信息。 只读的。                                                          |
| inheritedFrom | [itemReference](itemreference.md)         | 如果它从祖先继承，提供参考的当前权限的上级。 只读的。                       |
| 链接          | [sharingLink](sharinglink.md)             | 如果它是链接类型权限，提供链接的详细信息的当前权限。 只读的。                                     |
| 角色          | 字符串数组                          | 类型的权限，例如`read`。 有关角色的完整列表，请参阅下面。 只读的。                                                 |
| shareId       | String                                    | 此权限的的唯一标记。 只读的。 |


## <a name="roles-enumeration"></a>角色枚举

| 角色  | 详细信息                                                                        |
|:------|:-------------------------------------------------------------------------------|
| 阅读  | 提供用于读取元数据和项的内容。            |
| 写入 | 提供可读取和修改的元数据和项的内容的能力。 |

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "link", "grantedTo", "invitation", "inheritedFrom", "shareId" ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.permission"
}-->
```json
{
  "id": "string (identifier)",
  "grantedTo": {"@odata.type": "microsoft.graph.identitySet"},
  "inheritedFrom": {"@odata.type": "microsoft.graph.itemReference"},
  "invitation": {"@odata.type": "microsoft.graph.sharingInvitation"},
  "link": {"@odata.type": "microsoft.graph.sharingLink"},
  "roles": ["string"],
  "shareId": "string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "permission resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
