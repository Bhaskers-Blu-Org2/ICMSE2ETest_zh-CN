# <a name="driverecipient-resource-type"></a>driveRecipient 资源类型

该收件人资源代表[邀请](../api/item_invite.md)操作单个收件人。

## <a name="json-representation"></a>JSON 表示形式

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.driveRecipient", "optionalProperties": ["alias", "objectId", "email"] } -->
```json
{
  "email": "string",
  "alias": "string",
  "objectId": "string",
}
```

## <a name="properties"></a>属性
收件人资源应具有以下属性。

| 属性名称 | 类型   | 说明                                                                                             |
|:--------------|:-------|:--------------------------------------------------------------------------------------------------------|
| 电子邮件         | String | 如果收件人有关联的电子邮件地址的收件人电子邮件地址。                  |
| 别名         | String | 电子邮件地址不可用的情况下的域对象的别名 （例如安全组）。 |
| 对象 Id      | String | 在目录中的收件人的唯一标识符。                                               |

## <a name="remarks"></a>备注
当使用[邀请](../api/item_invite.md)来添加权限，driveRecipient 可以指定**电子邮件**、**别名**或**对象 Id**。 这些值中的只有一个是必需的。

<!-- {
  "type": "#page.annotation",
  "description": "Recipients resource defines a single recipient for the sharing invitation and permissions collection.",
  "keywords": "sharing,share,permissions,action.invite,invite,email",
  "section": "documentation"
} -->
