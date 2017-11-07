# <a name="update-subscription"></a>更新订阅

通过扩展其到期时间续订。

在禁止由单个资源类型的日期过期订阅资源。  为了不错过通知，应该很好地其到期日期提前续订订阅。  单个的到期日期，请参阅[订阅](../resources/subscription.md)。
## <a name="prerequisites"></a>先决条件
以下之一**作用域**，这取决于目标资源，需执行此 API: *Mail.Read*、 *Calendars.Read*、 *Contacts.Read*、 *Group.Read.All*或*Files.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /subscriptions/<id>
```

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和[订阅](../resources/subscription.md)对象在响应正文中的。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_subscription"
}-->
```http
PATCH https://graph.microsoft.com/beta/subscriptions/<id>
Content-type: application/json

{
   "expirationDateTime":"2016-11-22T18:23:45.9356913Z"
}
```

##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.subscription"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 252

{
  "id":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource":"me/messages",
  "changeType":"created,updated",
  "clientState":"subscription-identifier",
  "notificationUrl":"https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "expirationDateTime":"2016-11-22T18:23:45.9356913Z"
}
```


<!-- {
  "type": "#page.annotation",
  "description": "Update subscription",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
