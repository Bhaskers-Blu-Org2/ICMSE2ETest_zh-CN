# <a name="get-multivaluelegacyextendedproperty"></a>获得 multiValueLegacyExtendedProperty

获取包含多值扩展的属性使用的资源实例`$expand`。

使用查询参数`$expand`，可获得指定的实例，使用指定的扩展属性扩展。 目前获得[multiValueLegacyExtendedProperty](../resources/multiValueLegacyExtendedProperty.md)对象，表示扩展的属性的唯一办法。

支持以下用户资源︰

- [消息](../resources/message.md)
- [mailFolder](../resources/mailfolder.md)
- [事件](../resources/event.md)
- [日历](../resources/calendar.md)
- [联系人](../resources/contact.md)
- [contactFolder](../resources/contactfolder.md) 

以及下面的组资源︰

- 组[事件](../resources/event.md)
- 组[日历](../resources/calendar.md)
- 组[过帐](../resources/post.md) 

有关何时使用 Office 365 的数据扩展或扩展的属性，以及如何指定的扩展的属性的详细信息，请参阅[扩展属性概述](../resources/extended-properties-overview.md)。

## <a name="prerequisites"></a>先决条件
以下**范围**之一需要执行此 API，这取决于所获取的资源︰

- _Mail.Read_
- _Calendars.Read_
- _Contacts.Read_
- _Group.Read.All_ 
 
## <a name="http-request"></a>HTTP 请求

获取使用扩展属性相匹配的筛选器的**id**属性在扩展的资源实例。 请确保[URL 编码](http://www.w3schools.com/tags/ref_urlencode.asp)对应用的筛选器字符串中的空白字符。

获取**消息**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/messages/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /me/mailFolders/<id>/messages/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
得到一个**mailFolder**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/mailFolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

获取**事件**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/events/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
获取**日历**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/calendars/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/calendars/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
获取**联系人**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /me/contactFolders/<id>/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>/contacts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
得到一个**contactFolder**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/contactfolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```
获取组**事件**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/events/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

获取组**过帐**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/threads/<id>/posts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /groups/<id>/conversations/<id>/threads/<id>/posts/<id>?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id_value|String|要匹配的扩展属性的 ID。 它必须遵循一种受支持的格式。 有关详细信息，请参阅[Outlook 扩展属性概述](../resources/extended-properties-overview.md)。 必需。|


## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码。 

响应正文中包含一个对象，表示扩展与匹配的[multiValueLegacyExtendedProperty](../resources/multivaluelegacyextendedproperty.md)对象的请求的资源实例。

## <a name="example"></a>示例
##### <a name="request"></a>请求
本示例获得并通过包含多值扩展的属性扩展指定的事件。 筛选器将返回具有**id**匹配字符串的扩展的属性`StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation`（使用 URL 编码删除此处为了便于阅读）。

<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/beta/me/events('AAMkAGE1M2_bs88AACbuFiiAAA=')?$expand=multiValueExtendedProperties($filter=id%20eq%20'StringArray%20{66f5a359-4659-4830-9070-00050ec6ac6e}%20Name%20Recreation')
```
##### <a name="response"></a>响应

响应正文包括指定事件的所有属性和筛选器中要返回的扩展的属性。

注意︰ 此处所示的**事件**对象将被截断为简洁起见。 从实际调用将返回的所有属性。

<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/events/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/events('AAMkAGE1M2_bs88AACbuFiiAAA=')",
    "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAm8k15A==\"",
    "id": "AAMkAGE1M2_bs88AACbuFiiAAA=",
    "start": {
        "dateTime": "2015-11-26T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2015-11-30T05:00:00.0000000",
        "timeZone": "UTC"
    },
    "organizer": {
        "emailAddress": {
            "name": "Christine Irwin",
            "address": "christine@contoso.com"
        }
    },
    "multiValueExtendedProperties@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/events('AAMkAGE1M2_bs88AACbuFiiAAA%3D')/multiValueExtendedProperties",
    "multiValueExtendedProperties": [
        {
            "id": "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
            "value": [
                "Food",
                "Hiking",
                "Swimming"
            ]
        }
    ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get multiValueLegacyExtendedProperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->