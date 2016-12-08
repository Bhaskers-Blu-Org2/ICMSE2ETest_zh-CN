# <a name="delete-data-extension"></a>删除数据扩展插件

从指定实例的资源中删除的数据扩展插件 （[openTypeExtension](../resources/openTypeExtension.md)对象）。 

资源可以是用户的邮件、 日历事件或已登录的 Office 365 或 Outlook.com 上的联系人。 或者，它可以是一个事件或 post Office 365 组。

## <a name="prerequisites"></a>先决条件

以下**范围**之一需要执行此 API，这取决于您正在删除从扩展的资源︰

- _Mail.ReadWrite_
- _Calendars.ReadWrite_
- _Contacts.ReadWrite_
- _Group.ReadWrite.All_

 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
DELETE /me/messages/<id>/extensions/<extensionId>
DELETE /users/<id|userPrincipalName>/messages/<id>/extensions/<extensionId>
DELETE /me/mailFolders/<id>/messages/<id>/extensions/<extensionId>

DELETE /me/events/<id>/extensions/<extensionId>
DELETE /users/<id|userPrincipalName>/events/<id>/extensions/<extensionId>

DELETE /me/contacts/<id>/extensions/<extensionId>
DELETE /users/<id|userPrincipalName>/contacts/<id>/extensions/<extensionId>

DELETE /groups/<id>/events/<id>/extensions/<extensionId>

DELETE /groups/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
DELETE /groups/<id>/conversations/<id>/threads/<id>/posts/<id>/extensions/<extensionId>
```

## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|id|string|相应的集合中的实例的唯一标识符。 必需。|
|extensionId|string|这可以是唯一文本标识符为扩展，扩展名称或完全限定的名称，该连接的扩展类型和唯一文本标识符。 完全限定的名返回在`id`时创建扩展属性。 必需。|


## <a name="request-headers"></a>请求标头
| 名称       | 值 |
|:---------------|:----------|
| 授权 | 持有者 %令牌 %|


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。


## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
第一个示例按名称引用扩展并删除指定的消息中的扩展名。
<!-- {
  "blockType": "request",
  "name": "delete_opentypeextension"
}-->
```http
DELETE https://graph.microsoft.com/beta/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions('Com.Contoso.Referral')
```

第二个示例删除指定的组事件中的一个扩展。

<!-- { "blockType": "ignored" } -->
```http
DELETE https://graph.microsoft.com/beta/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVlN17IsAAA=')/extensions('Com.Contoso.Referral')
```

 

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": false
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete opentypeextension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->