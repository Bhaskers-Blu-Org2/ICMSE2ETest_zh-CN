# <a name="send-a-sharing-invitation"></a>发送共享邀请

发送共享邀请到现有项。 共享邀请创建唯一的共享链接，并向包括共享邀请的收件人发送一封电子邮件。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /drive/items/<item-id>/invite
POST /groups/<group-id>/drive/items/<item-id>/invite
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
在请求正文中，使用以下参数中提供的 JSON 对象。

| 参数      | 类型                                                        | 说明                                                                                                |
|:---------------|:------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------|
| 收件人     | [driveRecipient](../resources/driverecipient.md)集合 | 共享邀请的收件人电子邮件地址的列表。                                            |
| 消息        | String                                                      | 纯文本格式的邮件包含共享邀请。 最大长度 2000年个字符。 |
| requireSignIn  | Boolean                                                     | 指定邀请的收件人必须登录以查看共享的项目。            |
| sendInvitation | Boolean                                                     | 指定是否为电子邮件或张贴内容生成 (false) 或如果只是将权限创建 (true)。            |
| 角色          | 字符串集合                                           | 指定的角色中被授予共享邀请的收件人。                         |


## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[权限](../resources/permission.md)集合的对象。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "item_invite"
}-->
```http
POST https://graph.microsoft.com/beta/me/drive/items/<item-id>/invite
Content-type: application/json

{
  "recipients": [ { "email": "dan@contoso.com" } ],
  "message": "Here's the file I mentioned during our meeting.",
  "requireSignIn": true,
  "sendInvitation": true,
  "roles": [ "read" ]
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.permission",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 939

{
  "value": [
    {
      "grantedTo": {
        "application": {
          "displayName": "displayName-value",
          "id": "id-value"
        },
        "device": {
          "displayName": "displayName-value",
          "id": "id-value"
        },
        "user": {
          "displayName": "displayName-value",
          "id": "id-value"
        }
      },
      "id": "id-value",
      "invitation": {
        "email": "email-value",
        "redeemedBy": "redeemedBy-value",
        "signInRequired": true
      },
      "inheritedFrom": {
        "driveId": "driveId-value",
        "id": "id-value",
        "path": "path-value"
      },
      "link": {
        "application": {
          "displayName": "displayName-value",
          "id": "id-value"
        },
        "type": "type-value",
        "webUrl": "webUrl-value"
      },
      "roles": [
        "roles-value"
      ]
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->

<!-- {
  "type": "#page.annotation",
  "description": "item: invite",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
