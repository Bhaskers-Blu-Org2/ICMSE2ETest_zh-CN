# <a name="contact-resource-type"></a>资源类型，请与联系

联系人是您可以在这里组织和保存信息与通信的组织和个人的 Outlook 中的一项。 在联系人文件夹中包含的联系人。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "extensions",
    "photo"
  ],
  "@odata.type": "microsoft.graph.contact"
}-->

```json
{
  "assistantName": "string",
  "birthday": "String (timestamp)",
  "categories": ["string"],
  "changeKey": "string",
  "children": ["string"],
  "companyName": "string",
  "createdDateTime": "String (timestamp)",
  "department": "string",
  "displayName": "string",
  "emailAddresses": [{"@odata.type": "microsoft.graph.emailAddress"}],
  "fileAs": "string",
  "gender": "string",
  "generation": "string",
  "givenName": "string",
  "id": "string (identifier)",
  "imAddresses": ["string"],
  "initials": "string",
  "jobTitle": "string",
  "lastModifiedDateTime": "String (timestamp)",
  "manager": "string",
  "middleName": "string",
  "nickName": "string",
  "officeLocation": "string",
  "parentFolderId": "string",
  "personalNotes": "string",
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "postalAddresses": [{"@odata.type": "microsoft.graph.physicalAddress"}],
  "profession": "string",
  "spouseName": "string",
  "surname": "string",
  "title": "string",
  "websites": [{"@odata.type": "microsoft.graph.website"}],
  "weddingAnniversary": "date",
  "yomiCompanyName": "string",
  "yomiGivenName": "string",
  "yomiSurname": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|assistantName|String|联系人助理的名称。|
|生日|方法|联系人的生日。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|类别|字符串集合|与联系人关联的类别。|
|更改密钥|String|标识联系人的版本。 每次更改联系人，那么也将更改。 这样，可以将更改应用于该对象的正确版本的 Exchange。|
|儿童|字符串集合|联系人子女的姓名。|
|公司名称|String|联系人的公司名称。|
|createdDateTime|方法|创建联系人的时间。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|部门|String|联系人的部门。|
|显示名称|String|联系人的显示名称。|
|emailAddresses|[电子邮件地址](emailaddress.md)集合|联系人的电子邮件地址。|
|表示为|String|该联系人的名称存档。|
|性别 |String |联系人的性别。 |
|生成|String|联系人的生成。|
|givenName|String|联系人的名字。|
|id|String|联系人的唯一标识符。 只读的。|
|imAddresses|字符串集合|联系人的即时消息 (IM) 地址。|
|首字母缩写|String|联系人的姓名首字母缩写。|
|职务|String|联系人的职务。|
|lastModifiedDateTime|方法|该联系人已修改的时间。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|经理|String|联系人的经理的姓名。
|称谓|String|联系人的中间名。|
|昵称|String|联系人的昵称。|
|办公室|String|联系人的办公室位置。|
|parentFolderId|String|联系人的父文件夹 ID。|
|personalNotes|String|有关联系人的用户的说明。|
|电话 |[电话](phone.md)集合 |例如，住宅电话、 移动电话和业务电话与联系人的电话号码。 |
|postalAddresses |[physicalAddress](physicalAddress.md)集合 |与联系人相关联的地址，如家庭地址和公司地址。 |
|职业|String|联系人的职业。|
|配偶姓名|String|联系人的配偶的姓名。|
|姓氏|String|联系人的姓氏。|
|title|字符串|联系人的标题。|
|网站 |[网站](website.md)集合|与联系人关联的网站。 |
|weddingAnniversary |日期 |联系人的结婚纪念日。 |
|yomiCompanyName|String|拼音的日本公司的联系人名称。|
|yomiGivenName|String|拼音日文名字 （名字） 的联系人。|
|yomiSurname|String|拼音日语 surname （姓氏） 的联系人。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|扩展|[扩展](extension.md)集合|开放式类型数据扩展插件定义联系人的集合。 只读的。 可以为 null。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md)集合| 多值扩展属性定义联系人的集合。 只读的。 可以为 null。|
|照片|[照片](profilephoto.md)| 可选联系人图片。 您可以获取或设置联系人的照片。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md)集合| 单值扩展属性定义联系人的集合。 只读的。 可以为 null。|


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取联系人](../api/contact_get.md) | [联系人](contact.md) |读取属性和联系人对象的关系。|
|[创建](../api/user_post_contacts.md) | [联系人](contact.md) |将联系人添加到根的联系人文件夹或另一个联系人文件夹的联系人终结点。|
|[更新](../api/contact_update.md) | [联系人](contact.md) |更新联系人对象。 |
|[删除](../api/contact_delete.md) | 无 |删除联系人对象。 |
|[创建数据扩展插件](../api/opentypeextension_post_opentypeextension.md) |[openTypeExtension](opentypeextension.md)| 创建一个开放类型数据扩展，添加新的或现有的资源实例中的自定义属性。|
|[获取数据扩展插件](../api/opentypeextension_get.md) |[openTypeExtension](opentypeextension.md)集合| 得到一个**openTypeExtension**对象或对象标识的名称或完全限定的名称。|
|[创建扩展的单值属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[联系人](contact.md)  |在新的或现有的联系人中创建一个或多个单值扩展的属性。   |
|[与单值扩展属性获取联系人](../api/singlevaluelegacyextendedproperty_get.md)  | [联系人](contact.md) | 获取包含扩展属性，通过使用一个单值联系人`$expand`或`$filter`。 |
|[创建扩展属性的多值](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [联系人](contact.md) | 在新的或现有的联系人中创建一个或多个多值扩展的属性。  |
|[带有扩展属性的多值获取联系人](../api/multivaluelegacyextendedproperty_get.md)  | [联系人](contact.md) | 获取包含多值扩展的属性通过使用`$expand`。 |



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "contact resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->