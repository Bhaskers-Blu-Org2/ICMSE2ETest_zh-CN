# <a name="update-data-extension"></a>更新数据扩展插件

与请求正文中的属性更新的数据扩展插件 （[openTypeExtension](../resources/openTypeExtension.md)对象）︰

- 如果请求正文中的属性匹配的扩展中的现有属性的名称，扩展名中的数据更新。
- 否则该属性和它的数据被添加到该扩展。 

该扩展可以在消息、 事件或已登录的用户邮箱上 Office 365 中的联系人或 Outlook.com。 或者，它可以是一个事件或 post Office 365 组。 在扩展中的数据可以是基元类型或基元类型的数组。


## <a name="prerequisites"></a>先决条件

以下**范围**之一就是要求执行此 API，这取决于您正在创建中的扩展名的资源︰

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_
 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->

```http
PATCH /me/messages/<id>/extensions/<extensionId>
PATCH /users/<id|userPrincipalName>/messages/<id>/extensions/<extensionId>
PATCH /me/mailFolders/<id>/messages/<id>/extensions/<extensionId>

PATCH /me/events/<id>/extensions/<extensionId>
PATCH /users/<id|userPrincipalName>/events/<id>/extensions/<extensionId>

PATCH /me/contacts/<id>/extensions/<extensionId>
PATCH /users/<id|userPrincipalName>/contacts/<id>/extensions/<extensionId>

PATCH /groups/<id>/events/<id>/extensions/<extensionId>

PATCH /groups/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
PATCH /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
```


## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|相应的集合的实例的唯一标识符。 必需。|
|extensionId|string|这可以是唯一文本标识符的扩展，扩展名称或完全限定的名称，该连接的扩展类型和唯一文本标识符。 完全限定的名返回在`id`时创建扩展属性。 必需。|


## <a name="request-headers"></a>请求标头
| 名称       | 值 |
|:---------------|:----------|
| 授权 | 持有者 %令牌 %|
| 内容类型 | 应用程序/json |

## <a name="request-body"></a>请求正文

[OpenTypeExtension](../resources/openTypeExtension.md)对象的 JSON 体提供以下必需的名称-值对，并对这种扩展名更改或添加任何自定义数据。 JSON 有效负载中的数据可以是基元类型或基元类型的数组。

| 名称       | 值 |
|:---------------|:----------|
| @odata.type | Microsoft.Graph.OpenTypeExtension |
| extensionName | %unique_string% |


## <a name="response"></a>响应

如果成功，此方法返回`200 OK`响应代码和更新的[openTypeExtension](../resources/openTypeExtension.md)对象。


## <a name="example"></a>示例
#### <a name="request-1"></a>申请 1

第一个示例显示如何更新消息中的一个扩展。 最初由下面的 JSON 负载表示扩展︰

<!-- { "blockType": "ignored" } -->
```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00Z"
}
```

您可以按名称引用扩展︰

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

或者，您可以通过它的完全限定名引用扩展︰

<!-- { "blockType": "ignored" } -->
```http
PATCH https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')
```

您可以使用示例请求和以下请求正文更新通过上述扩展︰
- 更改`companyName`从`Wingtip Toys`到`Wingtip Toys (USA)`
- 更改`dealValue`从`500050`到`500100`
- 将新数据添加为自定义属性`updated`

<!-- { "blockType": "ignored" } -->
```http
{
    "@odata.type": "Microsoft.Graph.OpenTypeExtension",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Wingtip Toys (USA)",
    "dealValue": "500100",
    "expirationDate": "2015-12-03T10:00:00.000Z",
    "updated": "2015-10-29T11:00:00.000Z"
} 
```


#### <a name="response-1"></a>响应 1

这是响应这样无论用于引用该扩展的方式是相同的。

<!-- { "blockType": "ignored" } -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/beta/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Wingtip Toys (USA)",
    "dealValue": 500100,
    "expirationDate": "2015-12-03T10:00:00Z",
    "updated": "2015-10-29T11:00:00.000Z"
}
```

****

#### <a name="request-2"></a>请求 2

第二个示例演示如何更新组 post 过程中的扩展。 扩展最初由下面的 JSON 负载中，与`expirationDate`的值`2015-07-03T13:04:00Z`:

<!-- { "blockType": "ignored" } -->
```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2015-07-03T13:04:00Z",
    "DealValue": 1010100,
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```

下面是要更改的申请和请求正文`expirationDate`到`2016-07-30T11:00:00Z`:

<!-- {
  "blockType": "request",
  "name": "update_opentypeextension"
}-->
```http
PATCH https://graph.microsoft.com/beta/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate')
Content-type: application/json

{
   "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
   "extensionName": "Com.Contoso.Estimate",
   "companyName": "Contoso",
   "expirationDate": "2016-07-30T11:00:00.000Z",
   "DealValue": 1010100,
   "topPicks": [
       "Employees only",
       "Add spouse or guest",
       "Add family"
    ]
}
```

#### <a name="response-2"></a>2 响应

这里是第二个示例显示已更新的响应`expirationDate`在扩展中。

<!-- {  
  "blockType": "response",  
  "truncated": true,  
  "@odata.type": "microsoft.graph.opentypeextension"  
} --> 
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA%3D%3D')/posts('AAMkADJiUg96QZUkA-ICwMubAADDEd7UAAA%3D')/extensions/$entity",
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Estimate",
    "extensionName": "Com.Contoso.Estimate",
    "companyName": "Contoso",
    "expirationDate": "2016-07-30T11:00:00Z",
    "DealValue": 1010100,
    "Strings@odata.type": "#Collection(String)",
    "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
    ]
}
```

<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update opentypeextension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
} -->
