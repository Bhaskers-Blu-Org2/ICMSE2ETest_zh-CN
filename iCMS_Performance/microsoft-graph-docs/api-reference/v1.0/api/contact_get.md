# <a name="get-contact"></a>获取联系人

检索的属性和关系的联系人对象。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Contacts.Read;Contacts.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
[请联系](../resources/contact.md)来自用户的默认值[contactFolder](../resources/contactfolder.md)。
```http
GET /me/contacts/<id>
GET /users/<id | userPrincipalName>/contacts/<id>
```
[请联系](../resources/contact.md)来自用户的前级[contactFolder](../resources/contactfolder.md)。
```http
GET /me/contactfolders/<Id>/contacts/<id>
GET /users/<id | userPrincipalName>/contactfolders/<id>/contacts/<id>
```
[联系](../resources/contact.md) [contactFolder](../resources/mailfolder.md)子文件夹中。 下面的示例演示一个嵌套级别的但联系人可以位于中子级的子级，等等。
```http
GET /me/contactFolder/<id>/childFolders/<id>/.../contacts/<id>
GET /users/<id | userPrincipalName>/contactFolders/<id>/childFolders/<id>/contacts/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
|名称|值|说明|
|:---------------|:--------|:-------|
|$ expand|字符串|关系展开，并在响应中包含以逗号分隔的列表。 请参阅支持的名称的[联系人](../resources/contact.md)对象关系表。 |
|$select|字符串|要在响应中包含的属性的逗号分隔列表。|

## <a name="request-headers"></a>请求标头
| 页眉       | 值 |
|:---------------|:--------|
| 授权  | 持有者<token>。 必需。  |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[联系人](../resources/contact.md)对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_contact"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/contacts/<id>
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
  "businessHomePage": "http://www.contoso.com",
  "assistantName": null,
  "manager": null,
  "homePhones": [],
  "mobilePhone": null,
  "businessPhones": [
    "+1 918 555 0101"
  ],
  "homeAddress": {},
  "businessAddress": {
      "street": "10 Contoso Way",
      "city": "Redmond",
      "state": "WA",
      "countryOrRegion": "USA",
      "postalCode": "98075"  
  },
  "otherAddress": {},
  "spouseName": null,
  "personalNotes": null,
  "children": []
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get contact",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
