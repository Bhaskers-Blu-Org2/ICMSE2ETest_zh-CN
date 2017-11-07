# <a name="create-single-value-extended-property"></a>创建扩展的单值属性

在新的或现有的资源实例中创建一个或多个单值扩展的属性。 

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

则需要执行此 API，这取决于您正在创建的扩展的属性中的资源**范围**内的下列之一︰

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_
 
## <a name="http-request"></a>HTTP 请求
在新的或现有的资源实例中，您可以创建扩展的属性。

若要创建_新_的资源实例中的一个或多个扩展的属性、 创建实例，使用相同的其余请求和请求正文中包含的新资源实例的_扩展的属性和_属性。
注意一些资源，以多种方式支持创建。 创建这些资源实例的详细信息，请参阅用于创建[消息](../resources/message.md)、 [mailFolder](../api/user_post_mailfolders.md)、[事件](../api/user_post_events.md)、[日历](../api/user_post_calendars.md)、[联系](../api/user_post_contacts.md)、 [contactFolder](../api/user_post_contactfolders.md)、[组事件](../api/group_post_events.md)和[组过帐](../resources/post.md)相应的主题。 
 
以下是请求的语法。 

<!-- { "blockType": "ignored" } -->
```http
POST /me/messages
POST /users/<id|userPrincipalName>/messages
POST /me/mailFolders/<id>/messages

POST /me/mailFolders
POST /users/<id|userPrincipalName>/mailFolders

POST /me/events
POST /users/<id|userPrincipalName>/events

POST /me/calendars
POST /users/<id|userPrincipalName>/calendars

POST /me/contacts
POST /users/<id|userPrincipalName>/contacts

POST /me/contactFolders
POST /users/<id|userPrincipalName>/contactFolders

POST /groups/<id>/events

POST /groups/<id>/threads/<id>/posts/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/reply
POST /groups/<id>/threads/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/reply
POST /groups/<id>/threads
POST /groups/<id>/conversations
```

以现有资源实例中创建一个或多个扩展的属性，请在请求中，指定的实例并在请求正文中包括扩展的属性。

**请注意**不能在现有的组张贴内容中创建扩展的属性。

<!-- { "blockType": "ignored" } -->
```http
PATCH /me/messages/<id>
PATCH /users/<id|userPrincipalName>/messages/<id>
PATCH /me/mailFolders/<id>/messages/<id>

PATCH /me/mailFolders/<id>
PATCH /users/<id|userPrincipalName>/mailFolders/<id>

PATCH /me/events/<id>
PATCH /users/<id|userPrincipalName>/events/<id>

PATCH /me/calendars/<id>
PATCH /users/<id|userPrincipalName>/calendars/<id>

PATCH /me/contacts/<id>
PATCH /users/<id|userPrincipalName>/contacts/<id>

PATCH /me/contactFolders/<id>
PATCH /users/<id|userPrincipalName>/contactFolders/<id>

PATCH /groups/<id>/events/<id>
```


## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|其**id**属性，相应的集合中所表示的对象的唯一标识符。 必需。|
|_正文参数_|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md)集合| 一个或多个单值扩展属性的数组。 |
|id|String|对于**singleValueExtendedProperties**集合中每个属性，指定此标识属性。 它必须遵循一种受支持的格式。 有关详细信息，请参阅[Outlook 扩展属性概述](../resources/extended-properties-overview.md)。 必需。|
|value|string|对于**singleValueExtendedProperties**集合中每个属性，指定的属性值。 必需。|


## <a name="request-headers"></a>请求标头
| 名称       | 值 |
|:---------------|:----------|
| 授权 | 持有者 %令牌 %|
| 内容类型 | 应用程序/json |

## <a name="request-body"></a>请求正文

提供的资源实例的**singleValueExtendedProperties**集合属性中的每个[singleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md)对象的 JSON 体。

在_新_的资源实例中，除了新的**singleValueExtendedProperties**集合，创建扩展的属性时提供的 JSON 表示形式的资源实例 （即，[消息](../resources/message.md)、 [mailFolder](../resources/mailfolder.md)、[事件](../resources/event.md)等）

## <a name="response"></a>响应

#### <a name="response-code"></a>响应代码
操作成功地返回一个新的资源实例中创建扩展的属性`201 Created`，只是新组公告，具体取决于使用，该方法操作可以返回`200 OK`或`202 Accepted`。

在现有的资源实例，成功创建操作返回`200 OK`。 


#### <a name="response-body"></a>响应正文

在创建扩展的属性时，该响应包括只有新的或现有实例，但不是新的扩展的属性。 若要查看新创建的扩展的属性，[获取扩展的扩展属性的实例](../api/singlevaluelegacyextendedproperty_get.md)。

创建时扩展的属性在[分组后](../resources/post.md)_新_答复的线程或开机自检，该响应包括只有一个响应代码但不是新的帖子也扩展的属性。



## <a name="example"></a>示例
##### <a name="request-1"></a>申请 1

第一个示例中相同的 POST 操作创建一个新事件和单值的扩展的属性。 您通常要包括的新的事件的属性，除了请求正文包括**singleValueExtendedProperties**集合，其中包含一个单值扩展的属性和以下属性︰

- **id**指定的属性类型为`String`，GUID，并名为的属性`Fun`。
- **值**指定`Food`的值为`Fun`属性。 

<!-- { "blockType": "ignored" } -->
```http
POST https://graph.microsoft.com/beta/me/events
Content-Type: application/json

{
  "subject": "Celebrate Thanksgiving",
  "body": {
    "contentType": "HTML",
    "content": "Let's get together!"
  },
  "start": {
      "dateTime": "2015-11-26T18:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2015-11-26T23:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "Terrie@contoso.com",
        "name": "Terrie Barrera"
      },
      "type": "Required"
    }
  ],
  "singleValueExtendedProperties": [
     {
           "id":"String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
           "value":"Food"
     }
  ]
}
```

##### <a name="response-1"></a>响应 1

成功的响应将由`HTTP 201 Created`响应代码，并在类似于响应从[创建只是事件](../api/user_post_events.md)响应正文中包含新的事件。 响应不包含任何新创建的扩展的属性。

若要查看新创建的扩展的属性，[获取扩展属性使用扩展事件](../api/singlevaluelegacyextendedproperty_get.md)。


****

##### <a name="request-2"></a>请求 2

第二个示例创建一个单值扩展属性指定现有的消息。 扩展属性是**singleValueExtendedProperties**数组的唯一元素。 请求正文包含扩展的属性的如下︰
- **id**指定的属性类型为`String`，GUID，并名为的属性`Color`。
- **值**指定`Green`的值为`Color`属性。

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2_bs88AACHsLqWAAA=')

Content-Type: application/json

{
  "singleValueExtendedProperties": [
      {
         "id":"String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
         "value":"Green"
      }
    ]
}
```

##### <a name="response-2"></a>2 响应

成功的响应将由`HTTP 200 OK`响应代码，并在类似于响应更新[消息](../api/message_update.md)响应正文中包含指定的消息。 响应不包含新创建扩展属性。

若要查看新创建的扩展的属性，[使用扩展属性扩展消息](../api/singlevaluelegacyextendedproperty_get.md)。

<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create a single-value extended property",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->

