# <a name="contactfolder-resource-type"></a>contactFolder 资源类型

该文件夹中的联系人。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 contactFolder](../api/contactfolder_get.md) | [contactFolder](contactfolder.md) |通过使用联系人文件夹 ID 获取联系人文件夹|
|[更新](../api/contactfolder_update.md) | [contactFolder](contactfolder.md) |更新 contactFolder 对象。 |
|[删除](../api/contactfolder_delete.md) | 无 |删除 contactFolder 对象。 |
|[列表 childFolders](../api/contactfolder_list_childfolders.md) |[ContactFolder](contactfolder.md)集合| 获取指定联系人文件夹下的子文件夹的集合。|
|[创建子 contactFolder](../api/contactfolder_post_childfolders.md) |[ContactFolder](contactfolder.md)| 为指定文件夹的子文件夹中创建新的 contactFolder。|
|[文件夹中的联系人列表](../api/contactfolder_list_contacts.md) |[联系人](contact.md)集合| 获取默认的联系人文件夹中已登录的用户的联系人集合 (`.../me/contacts`)，或从指定的联系人文件夹。|
|[在文件夹中创建联系人](../api/contactfolder_post_contacts.md) |[联系人](contact.md)| 添加联系人到根的联系人文件夹或`contacts`的另一个联系人文件夹的终结点。|
|[创建扩展的单值属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[contactFolder](contactFolder.md)  |在新的或现有的 contactFolder 中创建一个或多个单值扩展的属性。   |
|[获得 contactFolder 与单值扩展属性](../api/singlevaluelegacyextendedproperty_get.md)  | [contactFolder](contactFolder.md) | 获取包含扩展属性，通过使用一个单值的 contactFolders`$expand`或`$filter`。 |
|[创建扩展属性的多值](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [contactFolder](contactFolder.md) | 在新的或现有的 contactFolder 中创建一个或多个多值扩展的属性。  |
|[获得 contactFolder 与多值扩展属性](../api/multivaluelegacyextendedproperty_get.md)  | [contactFolder](contactFolder.md) | 获取包含多值扩展的属性通过使用 contactFolder `$expand`。 |



## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|显示名称|String|该文件夹的显示名称。|
|id|String|联系人文件夹的唯一标识符。 只读的。|
|parentFolderId|String|该文件夹的父文件夹 ID。|
|wellKnownName|string|如果该文件夹是公认的文件夹的文件夹名称。 目前`contacts`是唯一可识别的联系人文件夹。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|childFolders|[ContactFolder](contactfolder.md)集合|子文件夹中的文件夹的集合。 导航属性。 只读的。 可以为 null。|
|联系人|[联系人](contact.md)集合|文件夹中的联系人。 导航属性。 只读的。 可以为 null。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)集合| 多值为 contactFolder 定义的扩展属性的集合。 只读的。 可以为 null。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md)集合| 单值为 contactFolder 定义的扩展属性的集合。 只读的。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "childFolders",
    "contacts"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.contactFolder"
}-->

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "parentFolderId": "string",
  "wellKnownName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "contactFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
