# <a name="person-resource-type"></a>人的资源类型

一种聚合的人通过邮件、 联系人和社交网络的信息。 人可以是当地联系人、 来自社交网络的联系人、 您所在组织的目录和最新通信 （例如电子邮件和 Skype） 的人员。

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得某人](../api/person_get.md) | [人员](person.md) |读取属性和一个 person 对象的关系。|


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|生日|string|联系人的生日。|
|公司名称|string|人的公司的名称。|
|部门|string|人的部门。|
|显示名称|string|人的显示名称。|
|emailAddresses|[rankedEmailAddress](rankedemailaddress.md)集合|此人的电子邮件地址。|
|givenName|string|此人的名字。|
|id|string|用户的唯一标识符。 只读的。|
|isFavorite|布尔|`true`如果用户已标记为收藏此人。|
|mailboxType|string|此人的电子邮件地址表示的邮箱的类型。|
|办公室|string|该人员的办公室位置。|
|personNotes|string|自由格式的笔记采取关于此人。|
|personType|string|人，例如通讯组列表的类型。|
|电话|[电话](phone.md)集合|此人的电话号码。|
|postalAddresses|[位置](location.md)的集合|人的地址。|
|职业|string|此人的职业。|
|来源|[personDataSource](persondatasource.md)集合|源用户数据的来源，例如目录或 Outlook 联系人。|
|姓氏|string|该人员的姓。|
|title|string|该人员的职位。|
|范围内|string|用户主要名称 (UPN) 的人。 UPN 是基于互联网标准[RFC 822](http://www.ietf.org/rfc/rfc0822.txt)人为互联网式登录名。 按照惯例，这应映射到该联系人的电子邮件名称。 常规格式是alias@domain.|
|网站|[网站](website.md)集合|人的网站。|
|yomiCompany|string|人的公司的日文拼音名称。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.person"
}-->

```json
{
  "birthday": "string",
  "companyName": "string",
  "department": "string",
  "displayName": "string",
  "emailAddresses": [{"@odata.type": "microsoft.graph.rankedEmailAddress"}],
  "givenName": "string",
  "id": "string (identifier)",
  "isFavorite": true,
  "mailboxType": "string",
  "officeLocation": "string",
  "personNotes": "string",
  "personType": "string",
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "postalAddresses": [{"@odata.type": "microsoft.graph.location"}],
  "profession": "string",
  "sources": [{"@odata.type": "microsoft.graph.personDataSource"}],
  "surname": "string",
  "title": "string",
  "userPrincipalName": "string",
  "websites": [{"@odata.type": "microsoft.graph.website"}],
  "yomiCompany": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "person resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
