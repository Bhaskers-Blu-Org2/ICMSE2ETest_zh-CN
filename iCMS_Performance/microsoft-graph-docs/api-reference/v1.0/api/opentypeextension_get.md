# <a name="get-data-extension"></a>获取数据扩展插件

获取由名称或完全限定的名称标识的数据扩展插件 （[openTypeExtension](../resources/openTypeExtension.md)对象）。

支持开放类型 Office 365 数据扩展的资源包括邮件、 日历事件或已登录的用户的 Office 365 或 Outlook.com 上的联系人。 或者，它可以是一个事件或 post Office 365 组。
根据资源类型中，有几种方法得到的数据扩展插件。

|**获取描述**|**受支持的资源**|**响应正文**|
|:-----|:-----|:-----|
|在已知的资源实例中获取特定扩展名。|消息、 事件、 联系人、 组事件、 组公告 | 数据扩展。|
|获取扩展具有特定扩展名的已知的资源实例。|消息、 事件、 联系人、 组事件|使用数据扩展插件扩展的资源实例。|
|找到并展开具有特定扩展名的资源实例。 |消息、 事件、 联系人、 组事件|使用数据扩展插件扩展资源实例。|


## <a name="prerequisites"></a>先决条件

以下**范围**之一就是要求执行此 API，这取决于您将获得从扩展的资源︰

- _Mail.Read_
- _Calendars.Read_
- _Contacts.Read_
- _Group.Read.All_
 
## <a name="http-request"></a>HTTP 请求


在已知的资源实例中获取特定扩展名︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<Id>/extensions/<extensionId>
GET /users/<Id|userPrincipalName>/messages/<Id>/extensions/<extensionId>
GET /me/mailFolders/<Id>/messages/<Id>/extensions/<extensionId>

GET /me/events/<Id>/extensions/<extensionId>
GET /users/<Id|userPrincipalName>/events/<Id>/extensions/<extensionId>

GET /me/contacts/<Id>/extensions/<extensionId>
GET /users/<Id|userPrincipalName>/contacts/<Id>/extensions/<extensionId>

GET /groups/<Id>/events/<Id>/extensions/<extensionId>

GET /groups/<Id>/threads/<Id>/posts/<Id>/extensions/<extensionId>
GET /groups/<Id>/conversations/<Id>/threads/<Id>/posts/<Id>/extensions/<extensionId>
```

若要获取使用的扩展名匹配筛选器的**id**属性在扩展一个已知的资源实例︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/messages/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /me/mailFolders/<Id>/messages/<Id>?$expand=extensions($filter=id eq '<extensionId>')

GET /me/events/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/events/<Id>?$expand=extensions($filter=id eq '<extensionId>')

GET /me/contacts/<Id>?$expand=extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/contacts/<Id>?$expand=extensions($filter=id eq '<extensionId>')

GET /groups/<Id>/events/<Id>?$expand=extensions($filter=id eq '<extensionId>')
```

若要筛选包含扩展名匹配的筛选器的**id**属性，以及如何获取这些实例的资源实例的扩展具有扩展名︰
<!-- { "blockType": "ignored" } -->
```http
GET /me/messages?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/messages?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /me/mailFolders/<Id>/messages?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')

GET /me/events?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/events?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')

GET /me/contacts?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
GET /users/<Id|userPrincipalName>/contacts?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')

GET /groups/<Id>/events?$filter=Extensions/any(f:f/id eq '<extensionId>')&$expand=Extensions($filter=id eq '<extensionId>')
```


## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|Id|string|占位符消息、 事件、 联系人等相应的集合中的对象的唯一标识符。 必需。 不要混淆与**openTypeExtension**的**id**属性。|
|extensionId|string|这是唯一文本标识符的扩展，扩展名称或完全限定的名称，该连接的扩展类型和唯一文本标识符占位符。 当创建扩展**id**属性返回完全限定的名。 必需。|


## <a name="optional-query-parameters"></a>可选的查询参数

请确保您对[URL 编码](http://www.w3schools.com/tags/ref_urlencode.asp)空格字符`$filter`字符串。

|**名称**|**值**|**说明**|
|:---------------|:--------|:-------|
|$filter|字符串|返回其**id**匹配的扩展名`extensionId`参数的值。|
|$filter 与**任何**运算符|string|返回的资源集合的实例，包含具有其**id**匹配的扩展`extensionId`参数的值。| 
|$ expand|字符串|将扩展以包含扩展的资源实例。 |


## <a name="request-headers"></a>请求标头
| 名称       | 值 |
|:---------------|:----------|
| 授权 | 持有者 %令牌 %|


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和[openTypeExtension](../resources/opentypeextension.md)对象在响应正文中的。
获取查询中，根据不同精确响应正文。
## <a name="example"></a>示例

#### <a name="request-1"></a>申请 1

第一个示例演示引用扩展的两种方式，获取扩展名中指定的消息。 响应是无论用于引用该扩展的方式相同。

首先，通过它的名称︰ 

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_1"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

其次，由其 ID （完全限定的名称）︰

<!-- { "blockType": "ignored" } -->
```http
GET https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```

#### <a name="response-1"></a>响应 1
这里是第一个示例中的响应。
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00Z"
}
```

****


#### <a name="request-2"></a>请求 2

第二个示例按名称引用扩展并获取扩展名中指定的组事件。

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_2"
}-->
```http
GET https://graph.microsoft.com/v1.0/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl17IsAAA=')/extensions('Com.Contoso.Deal') 
```

#### <a name="response-2"></a>2 响应

这里是第二个示例中的响应。

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl7IsAAA%3D')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Deal",
    "extensionName": "Com.Contoso.Deal",
    "companyName": "Alpine Skis",
    "dealValue": 1010100,
    "expirationDate": "2015-07-03T13:04:00Z"
}
```

****

#### <a name="request-3"></a>请求 3

第三个示例获取，并通过包括从筛选器返回扩展名为扩展指定的消息。 筛选器返回其**id**匹配的完全限定的名称的扩展名。

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_3"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')?$expand=extensions($filter=id%20eq%20'Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```


#### <a name="response-3"></a>3 响应

然后还有第三个示例的响应。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages/$entity",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM\"",
    "id": "AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===",
    "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM",
    "categories": [
    ],
    "createDateTime": "2015-06-19T02:03:31Z",
    "lastModifiedDateTime": "2015-08-13T02:28:00Z",
    "subject": "Attached is the requested info",
    "bodyPreview": "See the images attached.",
    "body": {
        "contentType": "HTML",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none;\"><!-- P {margin-top:0;margin-bottom:0;} --></style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>See the images attached. <br>\r\n</p>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "importance": "Normal",
    "hasAttachments": true,
    "parentFolderId": "AQMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===QAAAA==",
    "from": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "sender": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "address": "wendy@contoso.com",
                "name": "Wendy Molina"
            }
        }
    ],
    "ccRecipients": [
    ],
    "bccRecipients": [
    ],
    "replyTo": [
    ],
    "conversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===mivdTmQ=",
    "receivedDateTime": "2015-06-19T02:05:04Z",
    "sentDateTime": "2015-06-19T02:04:59Z",
    "isDeliveryReceiptRequested": false,
    "isReadReceiptRequested": false,
    "isDraft": false,
    "isRead": true,
    "webLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===%2FNJTqt5NqHlVnKVBwCY4MQpaFz9SbqUDe4%2Bbs88AAAAAAEJAACY4MQpaFz9SbqUDe4%2Bbs88AAApA4JMAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "Focused",
    "extensions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('desmond40contoso.com')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions", 
    "extensions": [ 
      { 
        "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
        "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
        "extensionName": "Com.Contoso.Referral",
        "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
        "companyName": "Wingtip Toys",
        "dealValue": 500050,
        "expirationDate": "2015-12-03T10:00:00Z"
      }
     ]
}
```

****

#### <a name="request-4"></a>申请 4

第四个示例由其完全限定名引用扩展并指定的组 post 过程中获取的扩展名。

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_4"
}-->
```http
GET https://graph.microsoft.com/v1.0/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate') 
```

#### <a name="response-4"></a>响应 4

以下是从第四个示例响应。 

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2015-07-03T13:04:00Z",
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```


#### <a name="request-5"></a>申请 5

第五个示例查看已登录的用户邮箱中的所有邮件，查找那些包含扩展名匹配的筛选器，并展开他们通过包括扩展名。 筛选器将返回具有匹配扩展名的**id**属性的扩展`Com.Contoso.Referral`。

<!-- {
  "blockType": "request",
  "name": "get_opentypeextension_5"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=Extensions/any(f:f/id%20eq%20'Com.Contoso.Referral')&$expand=Extensions($filter=id%20eq%20'Com.Contoso.Referral')
```


####<a name="response-5"></a>5 的响应

在第五个示例为此响应中，只有一个消息中没有具有其**id**等于扩展的用户邮箱`Com.Contoso.Referral`。

注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages",
  "value": [
  {

    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')",
    "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM\"",
    "id": "AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===",
    "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AABNsWMM",
    "categories": [
    ],
    "createDateTime": "2015-06-19T02:03:31Z",
    "lastModifiedDateTime": "2015-08-13T02:28:00Z",
    "subject": "Attached is the requested info",
    "bodyPreview": "See the images attached.",
    "body": {
        "contentType": "HTML",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<style type=\"text/css\" style=\"display:none;\"><!-- P {margin-top:0;margin-bottom:0;} --></style>\r\n</head>\r\n<body dir=\"ltr\">\r\n<div id=\"divtagdefaultwrapper\" style=\"font-size:12pt;color:#000000;background-color:#FFFFFF;font-family:Calibri,Arial,Helvetica,sans-serif;\">\r\n<p>See the images attached. <br>\r\n</p>\r\n</div>\r\n</body>\r\n</html>\r\n"
    },
    "importance": "Normal",
    "hasAttachments": true,
    "parentFolderId": "AQMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===QAAAA==",
    "from": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "sender": {
        "emailAddress": {
            "address": "desmond@contoso.com",
            "name": "Desmond Raley"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "address": "wendy@contoso.com",
                "name": "Wendy Molina"
            }
        }
    ],
    "ccRecipients": [
    ],
    "bccRecipients": [
    ],
    "replyTo": [
    ],
    "conversationId": "AAQkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===mivdTmQ=",
    "receivedDateTime": "2015-06-19T02:05:04Z",
    "sentDateTime": "2015-06-19T02:04:59Z",
    "isDeliveryReceiptRequested": false,
    "isReadReceiptRequested": false,
    "isDraft": false,
    "isRead": true,
    "webLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===%2FNJTqt5NqHlVnKVBwCY4MQpaFz9SbqUDe4%2Bbs88AAAAAAEJAACY4MQpaFz9SbqUDe4%2Bbs88AAApA4JMAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "Focused",
    "extensions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('desmond40contoso.com')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions", 
    "extensions": [ 
      { 
        "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
        "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
        "extensionName": "Com.Contoso.Referral",
        "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
        "companyName": "Wingtip Toys",
        "dealValue": 500050,
        "expirationDate": "2015-12-03T10:00:00Z"
      }
     ]
  }
  ]
}

```



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get openTypeExtension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
