# <a name="create-subscription"></a>创建订阅

订阅 Microsoft 图表上的数据发生变化时接收通知侦听器应用程序。
## <a name="prerequisites"></a>先决条件
以下之一**作用域**，这取决于目标资源，需执行此 API: *Mail.Read*、 *Calendars.Read*、 *Contacts.Read*或*Group.Read.All* 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->

```http
POST /subscriptions

```

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[订阅](../resources/subscription.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是请求的示例的用户将收到新邮件时发送通知。
<!-- {
  "blockType": "request",
  "name": "create_subscription_from_subscriptions"
}-->
```http
POST https://graph.microsoft.com/v1.0/subscriptions
Content-type: application/json

{
   "changeType": "created,updated",
   "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
   "resource": "me/mailFolders('Inbox')/messages",
   "expirationDateTime":"2016-11-20T18:23:45.9356913Z",
   "clientState": "subscription-identifier"
}
```
在请求正文中，提供[订阅](../resources/subscription.md)对象的 JSON 的表示。
*ClientState*字段是可选的。

##### <a name="resources-examples"></a>资源的示例
预订的资源属性的有效值如下︰

| 资源类型 | 示例 |
|:------ |:----- |
|邮件|我/mailfolders('inbox')/消息<br />我 / 消息|
|联系人|我 / 联系|
|日历|我 / 事件|
|对话|groups('*{id}*')/对话|

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.subscription"
} -->
```http
HTTP/1.1 201 Created

{
  "id":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource":"me/mailFolders('Inbox')/messages",
  "changeType":"created, updated",
  "clientState":"subscription-identifier",
  "notificationUrl":"https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "expirationDateTime":"2016-11-20T18:23:45.9356913Z"
}
```
## <a name="subscription-validation"></a>验证订阅
为了避免错误定向到任意 Url，通知的订阅的订阅通知终结点必须能够响应验证请求。 在处理的过程中`POST`到`/subscriptions`端点，Microsoft Graph 将发送`POST`请求回您`notificationUrl`采用以下形式︰ 
```http
POST https://webhook.azurewebsites.net/api/send/myNotifyClient?validationToken=<token>
```
通知终结点必须发送 200 响应值与`<token>`以及其正文的内容类型为`text/plain`，如下所示，在 10 秒钟之内; 否则为创建请求将被丢弃。
```http
HTTP/1.1 200 OK
Content-type: text/plain
Content-length: 7
<token>
```
##### <a name="notification-payload"></a>通知负载
当订阅的资源更改，webhooks 设施发送通知到通知 URL 使用以下的有效载荷。  通知终结点必须在 30 秒以其他方式通知尝试将重新在以指数级增加的时间间隔内发送 200 或 204 没有响应正文的响应。  以一致的方式采取 30 秒或更长的服务可能会阻止和接收 sparser 的通知组。

服务还可以返回 422 响应，从收到通知的情况下该订阅将被自动删除并通知该流将会停止。

根据订阅资源，其他的 resourceData 字段可能会提供其他信息。

```http
{
   "value":[
      {
         "subscriptionId":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
         "subscriptionExpirationDateTime":"2015-11-20T18:23:45.9356913Z",
         "clientState":"subscription-identifier",
         "changeType":"Created",
         "resource":"Users/ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4/messages/AAMkADMxZmEzMDM1LTFjODQtNGVkMC04YzY3LTBjZTRlNDFjNGE4MwBGAAAAAAAr-q_ZG7oXSaqxum7oZW5RBwCoeN6SYXGLRrvRm_CYrrfQAAAAAAEMAACoeN6SYXGLRrvRm_CYrrfQAACvtMe6AAA=",
         "resourceData":{
            "@odata.type":"#Microsoft.Graph.Message",
            "@odata.id":"Users/ddfcd489-628b-7d04-b48b-20075df800e5@1717622f-1d94-c0d4-9d74-f907ad6677b4/messages/AAMkADMxZmEzMDM1LTFjODQtNGVkMC04YzY3LTBjZTRlNDFjNGE4MwBGAAAAAAAr-q_ZG7oXSaqxum7oZW5RBwCoeN6SYXGLRrvRm_CYrrfQAAAAAAEMAACoeN6SYXGLRrvRm_CYrrfQAACvtMe6AAA=",
            "@odata.etag":"W/\"CQAAABYAAACoeN6SYXGLRrvRm+CYrrfQAACvvGdb\"",
            "Id":"AAMkADMxZmEzMDM1LTFjODQtNGVkMC04YzY3LTBjZTRlNDFjNGE4MwBGAAAAAAAr-q_ZG7oXSaqxum7oZW5RBwCoeN6SYXGLRrvRm_CYrrfQAAAAAAEMAACoeN6SYXGLRrvRm_CYrrfQAACvtMe6AAA="
         }
      }
   ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create subscription",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
