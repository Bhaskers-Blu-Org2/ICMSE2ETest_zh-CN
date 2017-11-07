# <a name="get-automatic-reply-settings"></a>获取自动答复设置

获取该用户的邮箱的设置。 这包括自动答复 （通知自动收到电子邮件的人）、 区域设置 （语言和国家/地区） 和时区设置。

您可以查看所有邮箱设置，或者，获得特定设置。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Mailboxsettings.ReadWrite*  

## <a name="http-request"></a>HTTP 请求
若要获取所有邮箱设置，其中包括自动答复设置。
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailboxSettings
GET /users/<id|userPrincipalName>/mailboxSettings
```

若要获得特定设置-例如，仅自动答复设置、 区域设置或时区。
<!-- { "blockType": "ignored" } -->
```http
GET /me/mailboxSettings/automaticRepliesSetting
GET /users/<id|userPrincipalName>/mailboxSettings/automaticRepliesSetting

GET /me/mailboxSettings/language
GET /users/<id|userPrincipalName>/mailboxSettings/language

GET /me/mailboxSettings/timeZone
GET /users/<id|userPrincipalName>/mailboxSettings/timeZone
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应并在响应正文中的以下请求对象之一︰

- [mailboxSettings](../resources/mailboxsettings.md)对象
- [automaticRepliesSetting](../resources/automaticRepliesSetting.md)对象
- [localeInfo](../resources/localeinfo.md)对象
- 字符串 （对于**时区**）

## <a name="example"></a>示例
##### <a name="request-1"></a>申请 1
第一个示例获取邮箱的所有设置中已登录的用户的邮箱，其中包括自动答复设置、 时区和语言设置。
<!-- {
  "blockType": "request",
  "name": "get_mailboxsettings_1"
}-->
```http
GET https://graph.microsoft.com/beta/me/mailboxSettings
```
##### <a name="response-1"></a>响应 1
该响应包括邮箱的所有设置。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.mailboxSettings"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/mailboxSettings",
    "automaticRepliesSetting": {
        "status": "Scheduled",
        "externalAudience": "All",
        "scheduledStartDateTime": {
            "dateTime": "2016-03-14T07:00:00.0000000",
            "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
            "dateTime": "2016-03-28T07:00:00.0000000",
            "timeZone": "UTC"
        },
        "internalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
        "externalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "timeZone":"UTC",
    "language":{
      "locale":"en-US",
      "displayName":"English (United States)"
    }
}
```

##### <a name="request-2"></a>请求 2
第二个示例获取特别是已登录的用户邮箱的自动答复设置。
<!-- {
  "blockType": "request",
  "name": "get_mailboxsettings_2"
}-->
```http
GET https://graph.microsoft.com/beta/me/mailboxSettings/automaticRepliesSetting
```
##### <a name="response-2"></a>2 响应
该响应包括仅自动答复设置。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.automaticRepliesSetting"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/api/beta/$metadata#Me/mailboxSettings/automaticRepliesSetting",
    "status": "alwaysEnabled",
    "externalAudience": "None",
    "scheduledStartDateTime": {
        "dateTime": "2016-03-19T02:00:00.0000000",
        "timeZone": "UTC"
    },
    "scheduledEndDateTime": {
        "dateTime": "2016-03-20T02:00:00.0000000",
        "timeZone": "UTC"
    },
    "internalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "externalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get automatic reply settings",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->