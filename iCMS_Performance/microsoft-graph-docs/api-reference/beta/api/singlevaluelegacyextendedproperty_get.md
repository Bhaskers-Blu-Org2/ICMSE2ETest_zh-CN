# <a name="get-singlevaluelegacyextendedproperty"></a>获得 singleValueLegacyExtendedProperty

获取包含扩展属性，通过使用一个单值的资源实例`$expand`或`$filter`。

使用查询参数`$expand`，可获得指定的实例，使用指定的扩展属性扩展。 目前获得[singleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md)对象，表示扩展的属性的唯一办法。

使用查询参数`$filter`使您能够指定资源具有扩展的属性匹配的筛选器的**id**和**值**属性的所有实例。 该筛选器应用于已登录的用户邮箱中的资源的所有实例。

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

#### <a name="get-a-resource-instance-using-expand"></a>获取一个资源实例使用`$expand`
获取使用扩展属性相匹配的筛选器的**id**属性在扩展的资源实例。 请确保[URL 编码](http://www.w3schools.com/tags/ref_urlencode.asp)对应用的筛选器字符串中的空白字符。

获取**消息**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/messages/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /me/mailFolders/<id>/messages/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
得到一个**mailFolder**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/mailFolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```

获取**事件**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/events/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/events/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
获取**日历**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/calendars/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/calendars/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
获取**联系人**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /me/contactFolders/<id>/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>/contacts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
得到一个**contactFolder**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/contactfolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```
获取组**事件**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/events/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```

获取组**过帐**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/threads/<id>/posts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
GET /groups/<id>/conversations/<id>/threads/<id>/posts/<id>?$expand=singleValueExtendedProperties($filter=id eq '{id_value}')
```

#### <a name="get-resource-instances-using-filter"></a>获取使用的资源实例`$filter`

获取支持的资源具有扩展的属性匹配的筛选器的**id**和**值**属性的实例。 请确保您对[URL 编码](http://www.w3schools.com/tags/ref_urlencode.asp)正斜杠和空间以下筛选器字符串中的字符。


获取**消息**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/messages?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /me/mailFolders/<id>/messages?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
获得**mailFolder**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailFolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/mailFolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```

获取**事件**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/events?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/events?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
获取**日历**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/calendars?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/calendars?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
获取**联系人**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /me/contactFolders/<id>/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/contactFolders/<id>/contacts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
获得**contactFolder**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/contactfolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /users/<id|userPrincipalName>/contactFolders?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```
获取组**事件**实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/events?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```

获取组**过帐**的实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /groups/<id>/threads/<id>/posts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
GET /groups/<id>/conversations/<id>/threads/<id>/posts?$filter=singleValueExtendedProperties/Any(ep: ep/id eq '{id_value}' and ep/value eq '{property_value}')
```

## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id_value|String|要匹配的扩展属性的 ID。 它必须遵循一种受支持的格式。 有关详细信息，请参阅[Outlook 扩展属性概述](../resources/extended-properties-overview.md)。 必需。|
|property_value|String|要匹配的扩展属性值。 要求在上面的**HTTP 请求**部分中列出的位置。|

## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<code>|


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码。

#### <a name="get-resource-instance-using-expand"></a>获取资源实例使用`$expand`
响应正文中包含一个对象，表示扩展与匹配的[singleValueLegacyExtendedProperty](../resources/singlevaluelegacyextendedproperty.md)对象的请求的资源实例。
  
#### <a name="get-resource-instances-using-filter"></a>获取使用的资源实例`$filter`
响应正文包含一个或多个对象表示包含匹配的扩展的属性的资源实例。 响应正文不包括扩展的属性。

## <a name="example"></a>示例
#### <a name="request-1"></a>申请 1

第一个示例获取，并通过包括单值扩展属性扩展指定的消息。 筛选器将返回具有**id**匹配字符串的扩展的属性`String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color`（使用 URL 编码删除此处为了便于阅读）。

<!-- {
  "blockType": "request",
  "name": "get_singlevaluelegacyextendedproperty_1"
}-->
```http
GET https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')?$expand=singleValueExtendedProperties($filter=id%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color')
```
##### <a name="response-1"></a>响应 1
响应正文包括指定的消息的所有属性和筛选器中要返回的扩展的属性。

注意︰ 此处所示的**消息**对象将被截断为简洁起见。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages/$entity",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AACbyS4H\"",
    "id": "AAMkAGE1M2_bs88AACHsLqWAAA=",
    "subject": "RE: Talk about emergency prep",
    "sender": {
        "emailAddress": {
            "name": "Christine Irwin",
            "address": "christine@contoso.com"
        }
    },
    "from": null,
    "toRecipients": [
        {
            "emailAddress": {
                "name": "Christine Irwin",
                "address": "christine@contoso.com"
            }
        }
    ],
    "singleValueExtendedProperties@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2_bs88AACHsLqWAAA%3D')/singleValueExtendedProperties",
    "singleValueExtendedProperties": [
        {
            "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
            "value": "Green"
        }
    ]
}
```

****

#### <a name="request-2"></a>请求 2

第二个示例获取具有单值扩展的筛选器中指定属性的消息。 筛选器将返回具有扩展的属性︰
- 它与字符串相匹配的**id** `String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color` （使用 URL 编码删除此处为了便于阅读）。
- 其**值**的`Green`。

<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/api/beta/Me/messages?$filter=singleValueExtendedProperties%2FAny(ep%3A%20ep%2Fid%20eq%20'String%20{66f5a359-4659-4830-9070-00047ec6ac6e}%20Name%20Color'%20and%20ep%2Fvalue%20eq%20'Green')
```

##### <a name="response-2"></a>2 响应

成功的响应将由`HTTP 200 OK`响应代码和响应正文包括与筛选器匹配的扩展属性的消息的所有属性。 响应正文是类似于响应中[获取消息集合](../api/user_list_messages.md)。 响应不包含匹配的扩展的属性。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get singleValueLegacyExtendedProperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->