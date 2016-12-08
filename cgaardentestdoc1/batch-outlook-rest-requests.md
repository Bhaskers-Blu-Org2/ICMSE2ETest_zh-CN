ms。TocTitle︰ 批次 Outlook 其余请求 （预览） 标题︰ 发送 Outlook 其余请求分批 （预览） 说明︰ 如何批处理多个其他请求在一起以形成单个 HTTP 请求并将多个 HTTP 连接从降低系统开销。
ms。ContentId: a842854e-46b3-47d9-8899-c27b481f4e78 <<<<<<< 头 ms.topic︰ 参考 (API) ms.date: 2016 5 月 16， =======
ms.date: 9 月 13，2016年
>>>>>>> 转移

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="send-outlook-rest-requests-in-batches-preview"></a>将 Outlook 其余请求发送分批 （预览）

[!INCLUDE [Add the Outlook REST API filters--beta default v1 v2 disabled](../includes/controls/addOutlookversion_betadefault_v1v2disabled.html)]    


 _**适用于︰**联机交换 |Office 365 |Hotmail.com |Live.com |MSN.com |Outlook.com |Passport.com_

<p class="previewnote">本文档介绍了目前在预览中的单个批处理请求以发送 Outlook 其余部分的多个请求。 预览功能可能会发生更改之前终止的对象，并使用它们的代码都可能会断开。 因此，一般情况下应使用 API 的生产版本在生产代码中 如果可用，2.0 版目前的首选的版本。</p>

批处理使您能够将多个 Outlook 其余请求放在单个 HTTP 批处理请求，减少了 HTTP 连接和开销。 在批处理请求访问已登录的用户，通过 Azure Active Directory Office 365 中或在 Microsoft 帐户 （Hotmail.com，Live.com，MSN.com、 Outlook.com 或 Passport.com） 来保护的数据。 


**请注意**为引用的简单起见，本文的其余部分使用**"Outlook.com"以包括这些 Microsoft 帐户域**。 

## <a name="overview"></a>概述

其余部分请求需要 HTTP 连接的客户端和服务器，它会导致一定数量的系统开销之间。 批处理，您可以通过组合到单个 HTTP POST 请求到 $batch 的终结点的多个 REST API 调用来减少连接开销︰  
```
POST https://outlook.office.com/api/{version}/$batch
```
批请求可以包含多达 20 个单独 REST API 调用，它可以是数据查询 （如有） 或更改 （例如过帐） 操作。 您可以指定[更愿意](#PreferContinueOnError)头以具有一个或多个的其余部分调用失败的情况下，即使继续批次。

批处理是在同步大量数据尤其有用。 在同一批次 API 调用可以访问不同的资源，如消息和事件，属于同一个已登录的用户的邮箱。 

如果您需要进行 20 多个电话，或完成呼叫的顺序很重要，请使用多个批处理请求。


## <a name="example"></a>示例

一个最简单的例子说明了批处理。 下面的批处理请求放置在单个批处理中 2 Outlook REST API 调用︰
1. 获取已登录的用户的所有事件
2. 发布一条消息。

### <a name="batch-request"></a>批处理请求

```
POST https://outlook.office.com/api/beta/$batch HTTP/1.1

Authorization: Bearer aGFwcHlnQGRr==
Host: outlook.office.com
Content-Type: multipart/mixed; boundary=batch_myBatchId


--batch_myBatchId
Content-Type: application/http
Content-Transfer-Encoding: binary

GET  /api/beta/me/events?$select=subject,organizer    HTTP/1.1


--batch_myBatchId
Content-Type: application/http
Content-Transfer-Encoding: binary

POST  /api/beta/me/sendmail    HTTP/1.1
Content-Type: application/json

{
  "Message": {
    "Subject": "Meet for lunch?",
    "Body": {
      "ContentType": "Text",
      "Content": "The new cafeteria is open."
    },
    "ToRecipients": [
      {
        "EmailAddress": {
          "Address": "rufus@contoso.com"
        }
      }
    ]
  }
}


--batch_myBatchId--
```

### <a name="batch-response"></a>批响应

批响应包括单独的响应代码和主体，在适用的情况下，批处理请求以及单个调用。 

```
HTTP/1.1 200 OK
Content-Type: multipart/mixed; boundary=batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09
Content-Length: 12898

--batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09
Content-Type: application/http
Content-Transfer-Encoding: binary

HTTP/1.1 200 OK
OData-Version: 4.0
Content-Type: application/json;odata.metadata=minimal;odata.streaming=true;IEEE754Compatible=false;charset=utf-8

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Events(Subject,Organizer)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Events('AAMkAGEtk-hAAA=')",
            "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAX791Eg==\"",
            "Id": "AAMkAGEtk-hAAA=",
            "Subject": "Standup meeting",
            "Organizer": {
                "EmailAddress": {
                    "Address": "rufus@contoso.com",
                    "Name": "Rufus Tallent"
                }
            }
        },

        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/Events('AAMkAGED3CAAA=')",
            "@odata.etag": "W/\"mODEKWhc/Um6lA3uPm7PPAAAD6Ir3g==\"",
            "Id": "AAMkAGED3CAAA=",
            "Subject": "Discuss the campaign",
            "Organizer": {
                "EmailAddress": {
                    "Address": "basil@contoso.com",
                    "Name": "Basil Pearsall"
                }
            }
        }
    ]
}
--batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09
Content-Type: application/http
Content-Transfer-Encoding: binary

HTTP/1.1 202 Accepted

--batchresponse_8faca3a8-183c-4dea-b396-25ac7dd77e09--
```

****

## <a name="batch-details"></a>批次详细信息

### <a name="endpoint-url"></a>终结点的 URL

若要发送多个 Outlook 其余请求一批，不要开机 $batch 终结点︰
```
POST https://outlook.office.com/api/{version}/$batch HTTP/1.1
```

**关注** 当使用根 URL https://outlook.office.com，以获得最佳性能时，添加**x AnchorMailbox**标头并将其设置为用户的电子邮件地址。 此外，处理其中 Outlook.com 用户邮箱尚未尚未启用 Outlook REST api-检查错误代码 MailboxNotEnabledForRESTAPI 和 MailboxNotSupportedForRESTAPI 的情况。 详细信息，请参阅[此处](..\api\use-outlook-rest-api.md#OutlookRESTCaution)。 

**在中国的开发人员注意事项** 

- 如果您正在开发的应用程序_针对 Office 365 提供_中国，您应该继续使用[中国的 Office 365 的 API 端点](..\api\o365-china-endpoints.md)。

- 如果您正在创建的应用程序_的 Outlook.com_在中国，您必须使用[第 2 版的应用程序模型的预览](..\api\use-outlook-rest-api.md#RegAuthConverged)和以下 Outlook REST 端点︰`https://outlook.office.com/api/{version}`


###<a name="version-of-api"></a>API 版本

批处理正在预览状态中，只在测试版命名空间中可用，因此指定`{version}`与`beta`:

`https://outlook.office.com/api/beta/$batch`

由于在调用批处理请求和其他批次必须使用相同的主机和版本的 API，您当前批次仅公开测试版 Outlook 其余部分调用。 

**关注**请记下可能包含在批处理的一些 API 调用在正式供货时，如 2.0 版和 1.0 版的版本比 beta 版本中不同响应。 一般情况下，如果您决定使用 API 调用在 beta 版中的增强的预览状态，计划验证您的应用程序中的功能和适应重大更改。
 

###<a name="target-user"></a>目标用户

您可以分组 Outlook REST API 调用同一个批处理中的已登录的用户的邮箱。 邮箱可以在 Office 365 或 Outlook.com。

### <a name="authentication"></a>身份验证

类似于单个请求以发送[Outlook REST API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)调用，应**授权**请求标头中包含一个有效的访问令牌。 如果您指定批处理请求的标头，访问令牌应提供该批处理中的所有调用的必要权限。
或者您可以指定访问令牌的特定调用批处理中，如果该调用需要一个不同的访问令牌。
 
获取一个访问令牌要求您注册并标识您的应用程序，并获得相应的授权。 
有关部分[了解详细信息](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)，可以简化注册和授权的选项。 正如您了解有关批处理请求的详细信息，请记住这一点。

### <a name="batch-request-headers"></a>批请求标头

包括为每个批处理请求以下标头︰

```
Host: outlook.office.com
Content-Type: multipart/mixed; boundary=batch_<batchId> 
```

其中`{batchId}`标识一批，并用于分隔在批处理中的请求。 它可以是一个 GUID 或区分的任何字符串。

在适当的位置，您可以包括其他标头。 如**内容类型**与内容相关的标题，但批处理请求中的标头通常应用于批处理中的每个操作。 如果在批处理请求和批处理中的特定操作指定一个标头，后者会优先而适用于该操作。   


### <a name="batch-request-body"></a>批请求正文

开始在一个批处理中的每个操作使用以下命令行︰
```
--batch_{batchId} 
Content-Type: application/http 
Content-Transfer-Encoding: binary 
```
结束与此批次中的最后一道工序︰
```
--batch_{batchId}--
```


### <a name="operations-in-a-batch"></a>批处理操作
可以在批处理请求中指定最多 20 个操作。

在批处理中的操作可以是数据的查询、 修改、 操作或函数调用请求。 而不需要重复完整的 Url 和状态为批处理中的每个操作的所有标题，请确保包括特定的标头和请求正文，如果他们所需的操作。

### <a name="relative-urls-within-a-batch"></a>在一个批处理中的相对 Url
指定完整的 URL 操作的替代方法，您可以包括相对 URL。 例如，在下面的示例获取请求指定一个 URL，`/api/beta/me/events`相对于批处理请求中指定的主机`https://outlook.office.com`。

```
POST https://outlook.office.com/api/beta/$batch HTTP/1.1

User-Agent: YouRock
Authorization: Bearer {accessToken}
Host: outlook.office.com
Content-Type: multipart/mixed; boundary=batch_<myBatchID>

--batch_{batchID}
Content-Type: application/http
Content-Transfer-Encoding: binary

GET  /api/beta/me/events?$select=subject,organizer    HTTP/1.1

--batch_{batchID>}--

```

### <a name="processing-a-batch-request"></a>处理批处理请求
批处理请求处理它本身作为一个请求并返回其自己的响应代码。 用正确的标头格式良好的批处理请求返回 HTTP 200 确定。 但是这并不意味着为批次中的所有请求都均成功。 批处理请求主体中的每个请求又分别处理，然后返回响应代码和任何响应正文和错误消息。

服务器可以按任何顺序执行批处理操作。 如果您必须按特定顺序执行的操作，您不应该将它们放在同一个批处理请求中。 相反，通过自身发送一次操作，发送下一个之前等待响应。

<a name="PreferContinueOnError"></a>

默认情况下，处理上的第一个操作，将返回一个错误停止。 您可以指定下面的标头进行处理忽略错误并继续执行批处理中的下一步操作︰

```
Prefer: odata.continue-on-error
```



<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

无论您是准备开始构建应用程序，或只是想要了解更多，我们有您的要求。

- [开始使用邮件、 日历和联系人 REST Api](http://dev.outlook.com/RestGettingStarted)。

- 探讨使用交互式[API 沙盒](https://apisandbox.msdn.microsoft.com/)Office 365 Api。

- 需要示例？ [我们已经有了](..\howto\starter-projects-and-code-samples.md)。


或者，了解有关使用 Office 365 的平台︰

- [在 Outlook 开发人员中心上的 outlook REST API，](http://dev.outlook.com/RestGettingStarted/Overview)

- [在 Office 365 的平台上开发的概述](..\howto\platform-development-overview.md)

- [Office 365 的应用程序的身份验证和资源授权](..\howto\common-app-authentication-tasks.md)

- [手动注册您的应用程序 Azure 的广告，这样它可以访问 Office 365 的 Api](..\howto\add-common-consent-manually.md)

- [邮件的 REST Api 引用](..\api\mail-rest-operations.md)

- [日历的 REST Api 参考](..\api\calendar-rest-operations.md)

- [联系其他 Api 参考](..\api\contacts-rest-operations.md)

- [任务 REST API （预览）](..\api\task-rest-operations.md) 

- [资源引用的邮件、 日历、 联系人和任务 REST Api](..\api\complex-types-for-mail-contacts-calendar.md)

- [Office 365 的数据扩展 REST API 参考](..\api\extensions-rest-operations.md)

- [人们 REST API 参考](..\api\people-rest-operations.md)

- [通知其他 API 参考](..\api\notify-rest-operations.md)

- [用户照片 REST API 参考](..\api\photo-rest-operations.md)

[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]
