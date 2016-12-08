# <a name="create-data-extension"></a>创建数据扩展插件

创建的数据扩展插件 （[openTypeExtension](../resources/openTypeExtension.md)对象），并添加新的或现有的资源实例中的自定义属性。 

资源可以是消息、 日历事件，或在已登录的用户邮箱上 Office 365 或 Outlook.com 与联系。 或者，它可以是一个事件或 post Office 365 组。 


## <a name="prerequisites"></a>先决条件

以下**范围**之一就是要求执行此 API，这取决于您正在创建中的扩展名的资源︰

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_
 
## <a name="http-request"></a>HTTP 请求
在新的或现有的资源实例，可以创建一个扩展。

若要创建_新_的资源实例中扩展，用作同一的其余请求创建实例，并请求正文中包含的新资源实例_和扩展_属性。
注意一些资源，以多种方式支持创建。 创建这些资源实例的详细信息，请参阅创建[消息](../resources/message.md)、[事件](../api/user_post_events.md)、[联系人](../api/user_post_contacts.md)、[组事件](../api/group_post_events.md)和[组公告](../resources/post.md)的相应主题。 
 
以下是请求的语法。 

<!-- { "blockType": "ignored" } -->
```http
POST /me/messages
POST /users/<id|userPrincipalName>/messages
POST /me/mailFolders/<id>/messages

POST /me/events
POST /users/<id|userPrincipalName>/events

POST /me/contacts
POST /users/<id|userPrincipalName>/contacts

POST /groups/<id>/events

POST /groups/<id>/threads/<id>/posts/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/reply
POST /groups/<id>/threads/<id>/reply
POST /groups/<id>/conversations/<id>/threads/<id>/reply
POST /groups/<id>/threads
POST /groups/<id>/conversations
```

以现有资源实例中创建一个扩展，在请求中，指定的实例并在请求正文中包含扩展名。

<!-- { "blockType": "ignored" } -->
```http
POST /me/messages/<id>/extensions
POST /users/<id|userPrincipalName>/messages/<id>/extensions
POST /me/mailFolders/<id>/messages/<id>/extensions

POST /me/events/<id>/extensions
POST /users/<id|userPrincipalName>/events/<id>/extensions

POST /me/contacts/<id>/extensions
POST /users/<id|userPrincipalName>/contacts/<id>/extensions

POST /groups/<id>/events/<id>/extensions

POST /groups/<id>/threads/<id>/posts/<id>/extensions
POST /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/extensions
```


## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|相应的集合中的对象的唯一标识符。 必需。|


## <a name="request-headers"></a>请求标头
| 名称       | 值 |
|:---------------|:----------|
| 授权 | 持有者 %令牌 %|
| 内容类型 | 应用程序/json |

## <a name="request-body"></a>请求正文

提供以下必需的名称-值对，以及任何其他自定义数据的[openTypeExtension](../resources/openTypeExtension.md)，JSON 体。 JSON 有效负载中的数据可以是基元类型或基元类型的数组。

| 名称       | 值 |
|:---------------|:----------|
| @odata.type | Microsoft.Graph.OpenTypeExtension |
| extensionName | %unique_string% |

在_新_的资源实例中，除了新的**openTypeExtension**对象，创建一个扩展时提供该资源实例 （[消息](../resources/message.md)、[事件](../resources/event.md)、[联系人](../resources/contact.md)，或[组 post](../resources/post.md)对象） 的 JSON 表示。

## <a name="response"></a>响应

#### <a name="response-code"></a>响应代码
成功创建一个扩展操作返回与相同的响应代码，使用操作时要创建的资源实例将不带扩展名。 根据操作，它可以是`201 Created`或`202 Accepted`。 请参阅用于创建该实例的相应主题。

#### <a name="response-body"></a>响应正文
当创建_新_的资源实例通过 POST 操作集合上的[消息](../resources/message.md)、[事件](../resources/event.md)或[联系](../resources/contact.md)对象扩展，响应正文包括使用[openTypeExtension](../resources/openTypeExtension.md)扩展的新实例。 

当在_新_[组后](../resources/post.md)创建一个扩展，该响应包括响应代码但不是响应正文。

当_现有_资源实例中创建一个扩展，响应正文包含**openTypeExtension**对象。
 


## <a name="example"></a>示例
##### <a name="request-1"></a>申请 1

第一个示例相同的调用中创建一条消息和一个扩展名。 请求正文包含下列内容︰

- **主题**、**正文**和**toRecipients**属性典型的新消息。 
- 并扩展︰

  - 该类型`Microsoft.Graph.OpenTypeExtension`。 
  - 扩展名称"Com.Contoso.Referral"。 
  - 其他数据存储为 JSON 有效负载中的 3 个自定义属性︰ `companyName`， `expirationDate`，和`dealValue`。  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_1"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages

{
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "You should be proud!"
  },
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com"
      }
    }
  ],
  "extensions": [
    {
      "@odata.type": "Microsoft.Graph.OpenTypeExtension",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```

##### <a name="response-1"></a>响应 1

这里是第一个示例中的响应。 响应正文包括新邮件中，以及新的扩展的以下属性︰

- **Id**属性的完全限定名称`Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`。 
- 默认属性**extensionName**请求中指定。
- 作为 3 个自定义属性存储请求中指定的自定义数据。

注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages/$entity",
  "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj\"",
  "id": "AAMkAGEbs88AAB84uLuAAA=",
  "createdDateTime": "2015-10-30T03:03:43Z",
  "lastModifiedDateTime": "2015-10-30T03:03:43Z",
  "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj",
  "categories": [ ],
  "receivedDateTime": "2015-10-30T03:03:43Z",
  "sentDateTime": "2015-10-30T03:03:43Z",
  "hasAttachments": false,
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r
\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nYou should be proud!\r\n</body>\r
\n</html>\r\n"
  },
  "bodyPreview": "You should be proud!",
  "importance": "Normal",
  "parentFolderId": "AQMkAGEwAAAIBDwAAAA==",
  "sender": null,
  "from": null,
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com",
        "name": "John Doe"
      }
    }
  ],
  "ccRecipients": [ ],
  "bccRecipients": [ ],
  "replyTo": [ ],
  "conversationId": "AAQkAGEFGugh3SVdMzzc=",
  "isDeliveryReceiptRequested": false,
  "isReadReceiptRequested": false,
  "isRead": true,
  "isDraft": true,
  "webLink": "https://outlook.office.com/owa/?
ItemID=AAMkAGEbs88AAB84uLuAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "inferenceClassification": "Focused",
  "extensions@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages
('AAMkAGEbs88AAB84uLuAAA%3D')/extensions",
  "extensions": [
    {
      "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
      "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
      "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```


****

##### <a name="request-2"></a>请求 2

第二个示例创建一个扩展中指定的消息。 请求正文包括以下扩展︰

- 该类型`Microsoft.Graph.OpenTypeExtension`。 
- 扩展名称"Com.Contoso.Referral"。
- 其他数据存储为 JSON 有效负载中的 3 个自定义属性︰ `companyName`， `dealValue`，和`expirationDate`。  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_2"
}-->
```http
POST https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions

{ 
  "@odata.type" : "Microsoft.Graph.OpenTypeExtension", 
  "extensionName" : "Com.Contoso.Referral", 
  "companyName" : "Wingtip Toys", 
  "dealValue" : 500050, 
  "expirationDate" : "2015-12-03T10:00:00.000Z" 
} 
```

##### <a name="response-2"></a>2 响应

这里是第二个示例的响应。 响应正文包括以下新的扩展︰

- 默认属性**extensionName**。
- **Id**属性的完全限定名称`Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral`。 
- 要存储自定义数据。  

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00.000Z"
}
```

****

##### <a name="request-3"></a>请求 3

第三个示例中指定的组事件创建扩展。 请求正文包括以下扩展︰

- 该类型`Microsoft.Graph.OpenTypeExtension`。 
- 扩展名称"Com.Contoso.Deal"。
- 其他数据存储为 JSON 有效负载中的 3 个自定义属性︰ `companyName`， `dealValue`，和`expirationDate`。  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_3"
}-->
```http
POST https://graph.microsoft.com/beta/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl17IsAAA=')/extensions 

{
  "@odata.type" : "Microsoft.Graph.OpenTypeExtension",
  "extensionName" : "Com.Contoso.Deal",
  "companyName" : "Alpine Skis",
  "dealValue" : 1010100,
  "expirationDate" : "2015-07-03T13:04:00.000Z"
}
```

##### <a name="response-3"></a>3 响应

以下是从第三个示例请求的响应。

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl7IsAAA%3D')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Deal",
    "extensionName": "Com.Contoso.Deal",
    "companyName": "Alpine Skis",
    "dealValue": 1010100,
    "expirationDate": "2015-07-03T13:04:00Z"
}
```

****

##### <a name="request-4"></a>申请 4

第四个示例创建新的组帖子，使用现有的组过帐到同一**答复**操作调用扩展。 **答复**动作创建新的公告，并在帖子中嵌入一个新的扩展。 请求正文包含一个**发布**属性，因而也包含**主体**的新的张贴内容，并新扩展的以下数据︰

- 该类型`Microsoft.Graph.OpenTypeExtension`。 
- 扩展名称"Com.Contoso.HR"。
- 其他数据存储为 JSON 有效负载中的 3 个自定义属性︰ `companyName`， `expirationDate`，和字符串的数组`topPicks`。

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_4"
}-->
```http
POST https://graph.microsoft.com/beta/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAAC1heiSAAA=')/reply 

{
  "post": {
    "body": {
      "contentType": "html",
      "content": "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>"
    },
  "extensions": [
    {
      "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
      "extensionName": "Com.Contoso.HR",
      "companyName": "Contoso",
      "expirationDate": "2015-07-03T13:04:00.000Z",
      "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
      ]
    }
  ]        
  }
}
```

##### <a name="response-4"></a>响应 4

以下是从第四个示例响应。 成功创建新的组中的扩展 HTTP 202 响应代码中发布结果。

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
Content-type: text/plain
Content-Length: 0
```


****

##### <a name="request-5"></a>申请 5

第五个示例创建新的组帖子使用同一个 POST 操作创建对话扩展。 POST 操作创建新对话、 线程和开机自检，并在帖子中嵌入一个新的扩展。 请求正文包括**主题**和**线程**属性和子**发布**对象的新的对话。 **发布**对象又包含**正文**中新开机自检，并为扩展下面的数据︰

- 该类型`Microsoft.Graph.OpenTypeExtension`。 
- 扩展名称"Com.Contoso.HR"。
- 其他数据存储为 JSON 有效负载中的 3 个自定义属性︰ `companyName`， `expirationDate`，和字符串的数组`topPicks`。

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_5"
}-->
```http
POST https://graph.microsoft.com/beta/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations

{
  "Topic": "Does anyone have a second?",
  "Threads": [
    {
      "Posts": [
        {
          "Body": {
            "ContentType": "HTML",
            "Content": "This is urgent!"
          },
          "Extensions": [
            {
              "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
              "extensionName": "Com.Contoso.Benefits",
              "companyName": "Contoso",
              "expirationDate": "2016-08-03T11:00:00.000Z",
              "topPicks": [
                "Employees only",
                "Add spouse or guest",
                "Add family"
              ]  
            }  
          ] 
        } 
      ]  
    } 
  ]
}
```

##### <a name="response-5"></a>5 的响应

这是响应第五个示例，其中包含新的会话和线程 id。 这个新的线程包含自动创建的过帐，又包含新的扩展。 

注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

此线程中，在获取新的扩展，第一个[得到所有帖子](../api/conversationthread_list_posts.md)和最初应该只有一个。 然后应用该张贴内容的 ID 和扩展名称`Com.Contoso.Benefits`为[获取扩展名](../api/opentypeextension_get.md)。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversation"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations/$entity",
    "id": "AAQkADJToRlbJ5Mg7TFM7H-j3Y=",
    "threads@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations('AAQkADJToRlbJ5Mg7TFM7H-j3Y%3D')/threads",
    "threads": [
        {
            "id": "AAQkADJDtMUzsf_PdhAAswJOhGVsnkyDtMUzsf_Pdg=="
        }
    ]
}

```


<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create extension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
