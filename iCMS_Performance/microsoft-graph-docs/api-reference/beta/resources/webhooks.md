# <a name="working-with-webhooks-in-microsoft-graph"></a>与在 Microsoft Graph 中 Webhooks 的工作

Microsoft Graph REST API，使用 webhook 机制来将通知传递到客户端。 客户端是 web 服务，用于配置自己的 URL 以接收通知。 客户端应用程序使用通知更新后更改其状态。

使用 Microsoft Graph REST API，应用程序可以订阅更改以下资源︰

* 消息
* 事件
* 联系人
* 组对话
* 驱动器的根项目

Microsoft Graph 接受订阅请求之后，它将通知订阅中指定的 URL。 应用程序然后将根据其业务逻辑的执行操作。 例如，读取更多数据，更新缓存和视图，等等。

在它们到期之前，应用程序应续订其订阅。 他们可以在任何时候停止获取通知取消。

在 GitHub 上看到下面的代码示例。

* [Microsoft Graph Node.js Webhooks 样本](https://github.com/OfficeDev/Microsoft-Graph-Nodejs-Webhooks)
* [ASP.NET 的 Microsoft Graph Webhooks 示例](https://github.com/OfficeDev/Microsoft-Graph-ASPNET -Webhooks)

让我们看一看订阅过程。

# <a name="creating-a-subscription"></a>创建订阅

创建订阅是第一步开始接收通知的资源。 预订流程如下所示︰

1. 客户端发送订阅 （开机自检） 请求对特定资源。
2. Microsoft Graph 将验证请求。
  * 如果请求有效，Microsoft Graph 将发送到通知 URL 验证令牌。
  * 如果该请求无效，Microsoft Graph 将发送错误响应代码和详细信息。
3. 客户端发送回 Microsoft Graph 的验证令牌。

客户端必须存储订阅 ID 关联的相应订阅的通知。

## <a name="characteristics-of-subscriptions"></a>订阅的特征

您可以创建预订的资源，如消息、 事件、 联系人和驱动器根项。

您可以创建为特定文件夹订阅︰`https://graph.microsoft.com/beta/me/mailfolders('inbox')/messages`

为顶级资源︰`https://graph.microsoft.com/beta/me/messages`

或在一个驱动器上的根项︰`https://graph.microsoft.com/beta/me/drive/root`

在大多数情况下创建的订阅要求读到的资源范围。 例如，若要得到通知消息，您的应用程序需要`mail.read`权限。 请注意当前`Files.ReadWrite`是驱动器根项目必需的权限。

订阅过期。 当前的最长有效期为三天减 9 0 分钟从创建时。 应用程序需要在截止时间之前续订其订阅。 否则，他们将需要创建新的订阅。

## <a name="notification-url-validation"></a>通知 URL 验证

Microsoft Graph 在创建订阅之前验证订阅请求中的通知 URL。 验证过程，如下所示︰

1. Microsoft Graph 将 POST 请求发送到通知 URL:

  ```
  POST https://{notificationUrl}?validationToken={TokenDefinedByMicrosoftGraph}
  ClientState: {Data sent in ClientState value in subscription request (if any)}
  ```
 
2. 在 10 秒内，客户端必须具有以下特性提供的响应︰

  * 200 (OK) 状态代码。
  * 内容类型必须是纯/文本。 
  * 正文必须包括由 Microsoft Graph 提供的验证令牌。

客户端应放弃之后，在响应中提供它的验证令牌。

## <a name="subscription-request-example"></a>订阅请求示例

```
POST https://graph.microsoft.com/beta/subscriptions
Content-Type: application/json
{
  "changeType": "created,updated",
  "notificationURL": "https://webhook.azurewebsites.net/notificationClient",
  "resource": "/me/mailfolders('inbox')/messages",
  "expirationDateTime": "2016-03-20T11:00:00.0000000Z",
  "clientState": "SecretClientState"
}
```

误差、 notificationURL、 资源和 expirationDateTime 属性是必需的。 请参阅[订阅资源类型](subscription.md)的属性定义和值。 虽然 clientState 不是必需的则必须包括能符合我们建议的通知处理过程。

如果成功，Microsoft Graph 将返回`200 OK`代码和[订阅](subscription.md)对象的正文中。

# <a name="renewing-a-subscription"></a>续订订购

客户端可以续订具有特定到期日期的请求的时间从最多三天。 ExpirationDateTime 属性是必需的。

## <a name="subscription-renewal-example"></a>订购续订示例

```
PATCH https://graph.microsoft.com/beta/subscriptions/<id>;
Content-Type: application/json
{
  "expirationDateTime": "2016-03-22T11:00:00.0000000Z"
}
```

如果成功，Microsoft Graph 将返回`200 OK`代码和[订阅](subscription.md)对象的正文中。 订阅对象包括新的 expirationDateTime 值。 

# <a name="deleting-a-subscription"></a>删除订阅

客户端可以通过停止接收通知删除订阅使用其 id。

```
DELETE https://graph.microsoft.com/beta/subscriptions/<id>
```

如果成功，Microsoft Graph 将返回`204 No Content`代码。

# <a name="notifications"></a>通知

在客户端启动创建订阅后接收通知。 资源发生更改时，Microsoft Graph 将 POST 请求发送到通知 URL 中。 客户端只能获取指定的更改类型，如*创建*通知。

## <a name="notification-properties"></a>通知属性

通知对象具有以下属性︰

* id — 属于此通知的订阅 ID。
* expirationDateTime-订阅过期时间。
* clientState-订阅请求中指定的 clientState 属性。
* 误差的引发通知的事件类型。 例如，在邮件中*创建*接收或*更新*将邮件标记为读取。
* 资源的 URI 的资源相对于`https://graph.microsoft.com`。 
* resourceData-依赖的资源的对象被订阅了。
  * @odata.type的在 Microsoft Graph 描述指定的对象 OData 实体类型。
  * @odata.id-OData 标识符的对象。
  * @odata.etag表示对象的版本-HTTP 实体标记。
  * Id 的对象的标识符。

> 注意︰ 在 resourceData 中提供的 Id 值是有效通知已排入队列的时间。 一些操作，如将邮件移到其他文件夹中，可能会导致资源的 Id 进行更改。


## <a name="notification-example"></a>通知示例

当用户收到一封电子邮件时，Microsoft Graph 将发送通知如下所示︰

```
{
  "value":[
  {
    "id":"<subscription_guid>",
    "expirationDateTime":"\"2016-03-19T22:11:09.952Z\"",
    "clientState":"SecretClientState",
    "changeType":"Created",
    "resource":"Users/<user_guid>@<tenant_guid>/Messages/<long_id_string>",
    "resourceData":
    {
      "@odata.type":"#Microsoft.Graph.Message",
      "@odata.id":"Users/<user_guid>@<tenant_guid>/Messages/<long_id_string>",
      "@odata.etag":"W/\"CQAAABYAAADkrWGo7bouTKlsgTZMr9KwAAAUWRHf\"",
      "Id":"<long_id_string>"
    }
  }
  ]
}
```

请注意，值对象包含一个列表。 如果有很多排队的通知，Microsoft Graph 在单个请求中发送它们。

## <a name="processing-the-notification"></a>处理通知

接收通知的应用程序启动后它必须处理它们。 您的应用程序处理通知时必须执行的最小任务如下︰

1. 验证`clientState`属性。 在通知中的 clientState 属性必须匹配与订阅请求提交。
  > 注意︰ 如果这不是真的，您不应考虑这有效的通知。 此外应调查通知来自何处，并采取适当的措施。
2. 更新应用程序基于您的业务逻辑。
3. 发送`202 - Accepted`在 Microsoft Graph 您响应的状态代码。 如果 Microsoft Graph 没有收到 2xx 类代码，它将重试重新通知发送的次数。
  > 应发送`202 - Accepted`状态代码即使 clientState 属性不匹配一个订阅请求提交。

对于其他通知请求中重复。

# <a name="additional-resources"></a>其他资源

* [预订资源类型](subscription.md)
* [获取订阅](../api/subscription_get.md)
* [创建订阅](../api/subscription_post_subscriptions.md)
* [Microsoft Graph Node.js Webhooks 样本](https://github.com/OfficeDev/Microsoft-Graph-Nodejs-Webhooks)
* [ASP.NET 的 Microsoft Graph Webhooks 示例](https://github.com/OfficeDev/Microsoft-Graph-ASPNET-Webhooks)
