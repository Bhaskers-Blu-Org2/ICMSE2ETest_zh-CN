# <a name="update-contact"></a>更新联系人

更新联系人对象的属性。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Contacts.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
[请联系](../resources/contact.md)来自用户的默认值[contactFolder](../resources/contactfolder.md)。
```http
PATCH /me/contacts/<id>
PATCH /users/<id | userPrincipalName>/contacts/<id>
```
[请联系](../resources/contact.md)来自用户的前级[contactFolder](../resources/contactfolder.md)。
```http
PATCH /me/contactFolders/<id>/contacts/<id>
PATCH /users/<id | userPrincipalName>/contactFolders/<id>/contacts/<id>
```
[联系](../resources/contact.md) [contactFolder](../resources/mailfolder.md)子文件夹中。  下面的示例演示一个嵌套级别的但联系人可以位于中子级的子级，等等。
```http
PATCH /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
PATCH /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |
| 内容类型  | 应用程序/json。 必需。  |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|assistantName|String|联系人助理的名称。|
|生日|方法|联系人的生日。|
|类别|String|与联系人关联的类别。|
|儿童|String||
|公司名称|String|联系人的公司名称。|
|部门|String|联系人的部门。|
|显示名称|String|联系人的显示名称。|
|emailAddresses|[电子邮件地址](../resources/emailaddress.md)集合|联系人的电子邮件地址。|
|表示为|String|该联系人的名称存档。|
|性别 |String |联系人的性别。 |
|生成|String|联系人的生成。|
|givenName|String|联系人的名字。|
|imAddresses|String|联系人的即时消息 (IM) 地址。|
|首字母缩写|String|联系人的姓名首字母缩写。|
|职务|String|联系人的职务。|
|经理|String|联系人的经理的姓名。
|称谓|String|联系人的中间名。|
|昵称|String|联系人的昵称。|
|办公室|String|联系人的办公室位置。|
|parentFolderId|String|联系人的父文件夹 ID。|
|personalNotes|String|有关联系人的用户的说明。|
|电话 |[电话](../resources/phone.md)集合 |例如，住宅电话、 移动电话和业务电话与联系人的电话号码。 |
|postalAddresses |[physicalAddress](../resources/physicalAddress.md)集合 |与联系人相关联的地址，如家庭地址和公司地址。 |
|职业|String|联系人的职业。|
|配偶姓名|String|联系人的配偶的姓名。|
|姓氏|String|联系人的姓氏。|
|title|字符串|联系人的标题。|
|网站 |[网站](../resources/website.md)集合|与联系人关联的网站。 |
|weddingAnniversary |日期 |联系人的结婚纪念日。 |
|yomiCompanyName|String|拼音的日本公司的联系人名称。 此属性是可选的。|
|yomiGivenName|String|拼音日文名字 （名字） 的联系人。 此属性是可选的。|
|yomiSurname|String|拼音日语 surname （姓氏） 的联系人。 此属性是可选的。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和响应正文中的更新[，请与联系](../resources/contact.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_contact"
}-->
```http
PATCH https://graph.microsoft.com/beta/me/contacts/<id>
Content-type: application/json
Content-length: 1977

{
  "postalAddresses": [{
    "type": "business",
    "postOfficeBox": "P.O. Box 100",
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "countryOrRegion": "USA",
    "postalCode": "98121"
  }],
  "birthday": "1974-07-22"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.contact"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 1977

{
  "id": "AAMkAGI2THk0AAA=",
  "createdDateTime": "2014-10-19T23:08:24Z",
  "lastModifiedDateTime": "2014-10-19T23:08:24Z",
  "changeKey": "EQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIa4",
  "categories": [],
  "parentFolderId": "AAMkAGI2AAEOAAA=",
  "birthday": "1974-07-22",
  "fileAs": "Fort, Garth",
  "displayName": "Garth Fort",
  "givenName": "Garth",
  "initials": "G.F.",
  "middleName": null,
  "nickName": "Garth",
  "surname": "Fort",
  "title": null,
  "yomiGivenName": null,
  "yomiSurname": null,
  "yomiCompanyName": null,
  "generation": null,
  "emailAddresses": [
    {
      "name": "Garth",
      "address": "garth@a830edad9050849NDA1.onmicrosoft.com"
    }
  ],
  "imAddresses": [
    "sip:garthf@a830edad9050849nda1.onmicrosoft.com"
  ],
  "jobTitle": "Web Marketing Manager",
  "companyName": "Contoso, Inc.",
  "department": "Sales & Marketing",
  "officeLocation": "20/1101",
  "profession": null,
  "assistantName": null,
  "manager": null,
  "phones": [{
    "type": "business",
    "number": "+1 918 555 0101"
  }],
  "postalAddresses": [{
    "type": "business",
    "postOfficeBox": "P.O. Box 100",
    "street": "123 Some street",
    "city": "Seattle",
    "state": "WA",
    "countryOrRegion": "USA",
    "postalCode": "98121"
  }],
  "spouseName": null,
  "personalNotes": null,
  "children": [], 
  "gender": null,
  "websites": [{
      "type": "work",
      "address": "http://www.contoso.com",
      "name": "Contoso"
  }],
  "weddingAnniversary": null,
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->