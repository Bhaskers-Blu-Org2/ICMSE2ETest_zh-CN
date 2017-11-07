---
ms.Toctitle: Outlook Mail REST API reference
title: "Outlook 邮件 REST API 参考"
description: "引用与 REST API，邮件和客户端库提供访问文件夹、 电子邮件和电子邮件附件的 Api 进行交互的方式。"
ms.ContentId: aaf0a812-2ddb-4a63-969f-88916c96ab01
ms.date: October 5, 2016
ms.openlocfilehash: ba5f1561f54ca0067098ef93336a84df0a621647
ms.sourcegitcommit: 4648ef0fb81b465cef7e8ccad197fe9b9edabc33
translationtype: MT
---
[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="outlook-mail-rest-api-reference"></a>Outlook 邮件 REST API 参考

[!INCLUDE [Add the Outlook REST API filters--v2 default](../includes/controls/addOutlookVersion_v2default.html)]

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<p class="previewnote">本文档介绍了 API 的@-mentions,取消订阅消息、 快速答复和参考附件的所有当前在预览。 预览功能可能会发生更改之前终止的对象，并使用它们的代码都可能会断开。 因此，一般情况下应使用 API 的生产版本在生产代码中 如果可用，2.0 版目前的首选的版本。</p>

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


 _**适用于︰**联机交换 |Office 365 |Hotmail.com |Live.com |MSN.com |Outlook.com |Passport.com_

可以使用 Outlook 邮件 API 读取、 创建和发送邮件和附件、 查看和响应事件消息和管理受 Azure 的 Active Directory 中 Office 365 的文件夹。 它还提供了 Microsoft 客户专门在这些域中相同的功能︰ Hotmail.com，Live.com，MSN.com、 Outlook.com 和 Passport.com。


<!-- Can add the following sentence back once the client libraries have been updated for converged auth and outlook.com

You can access the Mail API by calling the corresponding REST APIs directly in your apps, or by using the Office 365 client libraries and SDKs.
-->

**请注意**为引用的简单起见，本文的其余部分使用**"Outlook.com"以包括这些 Microsoft 帐户域**。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

**在 beta 版本的 api 不感兴趣？** 使用该控件，在右上角并选择所需的版本。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

**在 2.0 版的 api 中不感兴趣？** 使用该控件，在右上角并选择所需的版本。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->




<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

**在 1.0 版的 api 不感兴趣？** 使用该控件，在右上角并选择所需的版本。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



## <a name="all-mail-api-operations"></a>所有邮件 API 操作

**消息操作**消息存储在邮箱文件夹中，因此消息端点通常包括包含邮件的文件夹。
通过 ID 或以下的已知文件夹名称或者指定一个文件夹︰ `Inbox`， `Drafts`， `SentItems`，或`DeletedItems`。

[获取邮件](#GetMessages) | [同步消息](#SynchronizeMessagesAPI) | [创建和发送邮件](#SendMessages) | [回复或回复所有邮件](#ReplyToMessages) | 
[正向新的或绘制消息](#ForwardMessages) | [更新消息](#UpdateMessages) | [删除邮件](#DeleteMessages) | [移动或复制邮件](#MoveCopyMessages) |  
[专注于收件箱管理](#ManageFocusedInbox) | [管理@-Mentions](#ManageMentions)（预览） |[取消订阅](#Unsubscribe)（预览） |[获取自动答复设置](#GetAutoReplySettings) | [更新自动答复设置](#UpdateAutoReplySettings) | 
[获取邮件提醒](#GetMailTips)（预览） |[获取附件](#GetAttachments) | 
[创建附件](#CreateAttachments) | [删除附件](#DeleteAttachments)


**文件夹操作**邮箱文件夹可以包含消息和其他文件夹。 您可以获得、 创建、 更改、 删除和管理文件夹。
可以使用以下的已知文件夹名称而不是 ID 来指定对应的文件夹︰ `Inbox`， `SentItems`， `Drafts`，或`DeletedItems`。

[获取文件夹](#GetFolders) | [同步文件夹](#SynchronizeFolders) | [创建文件夹](#CreateFolders) | [更新文件夹](#UpdateFolders) | [文件夹删除](#DeleteFolders) | [移动或复制文件夹](#MoveCopyFolders)

另请参见︰

[REST API 消息资源](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource) | [REST API 文件夹资源](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)

<a name="Overview"> </a>
## <a name="use-the-mail-rest-api"></a>使用邮件 REST API，

###<a name="authentication"></a>身份验证

像其他[Outlook REST API](..\api\use-outlook-rest-api.md#DefineOutlookRESTAPI)，为每个请求邮件 api 中，应包括有效的访问令牌。 获取一个访问令牌要求您注册并标识您的应用程序，并获得相应的授权。 您可以有关某些简化的注册和授权选项，让您[了解详细信息](..\api\use-outlook-rest-api.md#ShortRegAuthWorkflow)。
在继续进行邮件 API 中的特定操作，请记住这一点。

<a name="SupportedVersions"> </a>

###<a name="version-of-api"></a>API 版本

在所有版本的 Outlook REST API 支持邮件 REST API。 根据的特定版本，功能可能会有所不同。

###<a name="target-user"></a>目标用户

除非指定，否则所有邮件 API 请求都执行代表已登录的用户。 几个 API 子集，如专注于收件箱 API 中，可以执行中已登录的用户或用户指定的用户 ID，获取适当的权限。

Outlook 的 REST API 的通用于所有子集的详细信息，请参阅[使用 Outlook REST API](..\api\use-outlook-rest-api.md) 。

****


<a name="GetMessages"> </a>
##<a name="get-messages"></a>收到的邮件

从邮箱文件夹，您可以获得的消息集或单个邮件。

每个消息响应中的包含多个属性，其中包括[Body](..\api\complex-types-for-mail-contacts-calendar.md#MessageBody)属性。 消息正文可以是 HTML 或文本。 如果主体是 HTML，默认情况下，将其余部分响应中返回的正文内容之前删除**Body**属性中嵌入任何潜在的不安全 HTML (例如，JavaScript)。 若要获取整个、 原始 HTML 内容，包括以下 HTTP 请求标头︰
```
Prefer: outlook.allow-unsafe-html
```

REST API︰[获取消息集合 (REST)](#GetMessageCollection) | [得到一条消息 (REST)](#GetMessage)

客户端库︰[获取消息集合 （客户端）](#GetMessagesClient) | [得到一条消息 （客户端）](#GetMessageClient)

<a name="GetMessageCollection"> </a>
###<a name="get-a-message-collection-rest"></a>获取消息集合 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_ 
- _https://outlook.office.com/mail.read_
- _wl.imap_

**请注意**本节中的操作的行为因版本而异。 有关更多信息，请在页面右上角选择一个版本。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

从整个邮箱中已登录的用户 （不包括已删除邮件和混乱文件夹） 的获取消息集合。

```no-highlight
GET https://outlook.office.com/api/beta/me/messages
```

此外可以指定用户的邮箱中的文件夹，然后从该文件夹中获取消息集合。

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称，如果您收到了邮件从特定的文件夹。|

**请注意**默认情况下，响应中的每个消息包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定响应中返回仅每封邮件的**发件人**和**主题**属性。 请参阅示例响应中[收到一条消息 (REST)](#GetMessage)如果您不使用**$select**将返回消息的属性的完整列表。


**示例请求**

```
GET https://outlook.office.com/api/beta/me/MailFolders/sentitems/messages/?$select=Sender,Subject
```

**响应示例**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders('sentitems')/Messages(Sender,Subject)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIzAAAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqS\"",
            "Id": "AAMkAGI2TIzAAAA=",
            "Subject": "Meeting Notes",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy-AAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
            "Id": "AAMkAGI2TIy-AAA=",
            "Subject": "Contract Signing",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.type": "#Microsoft.OutlookServices.EventMessage",
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy9AAA=')",
            "@odata.etag": "W/\"CwAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqJ\"",
            "Id": "AAMkAGI2TIy9AAA=",
            "Subject": "Rob:Alex 1:1",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

从整个邮箱中已登录的用户 （不包括已删除邮件和混乱文件夹） 的获取消息集合。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages
```

此外可以指定用户的邮箱中的文件夹，然后从该文件夹中获取消息集合。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/messages
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称，如果您收到了邮件从特定的文件夹。|

**请注意**默认情况下，响应中的每个消息包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定响应中返回仅每封邮件的**发件人**和**主题**属性。 请参阅示例响应中[收到一条消息 (REST)](#GetMessage)如果您不使用**$select**将返回消息的属性的完整列表。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/MailFolders/sentitems/messages/?$select=Sender,Subject
```

**响应示例**

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('sentitems')/Messages(Sender,Subject)",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIzAAAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqS\"",
            "Id": "AAMkAGI2TIzAAAA=",
            "Subject": "Meeting Notes",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy-AAA=')",
            "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
            "Id": "AAMkAGI2TIy-AAA=",
            "Subject": "Contract Signing",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        },
        {
            "@odata.type": "#Microsoft.OutlookServices.EventMessage",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2TIy9AAA=')",
            "@odata.etag": "W/\"CwAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqJ\"",
            "Id": "AAMkAGI2TIy9AAA=",
            "Subject": "Rob:Alex 1:1",
            "Sender": {
                "EmailAddress": {
                    "Name": "Alex D",
                    "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
                }
            }
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

从收件箱中获取消息集合。 

```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages
```

此外可以指定用户的邮箱中的文件夹，然后从该文件夹中获取消息集合。

```no-highlight
GET https://outlook.office.com/api/v1.0/me/MailFolders/{folder_id}/messages
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称，如果您收到了邮件从特定的文件夹。|

**请注意**默认情况下，响应中的每个消息包含它的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定响应中返回仅每封邮件的**发件人**和**主题**属性。 请参阅示例响应中[收到一条消息 (REST)](#GetMessage)如果您不使用**$select**将返回消息的属性的完整列表。

[!code-REST-i[mail_api_get_message_collection](./_data/mail_api_get_message_collection.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

请求的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)集合中。 


****

<a name="GetMessage"> </a>
###<a name="get-a-message-rest"></a>收到一条消息 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

收到一条消息的 id。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
GET https://outlook.office.com/api/beta/me/messages/{message_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|

**示例请求**

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGI2THVSAAA=
```

**响应示例**

```
{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz\"",
    "Id": "AAMkAGI2THVSAAA=",
    "CreatedDateTime": "2014-10-20T00:41:57Z",
    "LastModifiedDateTime": "2014-10-20T00:41:57Z",
    "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz",
    "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
    "Categories": [],
    "ReceivedDateTime": "2014-10-20T00:41:57Z",
    "SentDateTime": "2014-10-20T00:41:53Z",
    "HasAttachments": true,
    "Subject": "Re: Meeting Notes",
    "Body": {
        "ContentType": "Text",
        "Content": "\n________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP\n"
    },
    "BodyPreview": "________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP",
    "Importance": "Normal",
    "ParentFolderId": "AAMkAGI2AAEMAAA=",
    "Sender": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Alex D",
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
            }
        }
    ],
    "CcRecipients": [],
    "BccRecipients": [],
    "ReplyTo": [],
    "ConversationId": "AAQkAGI2yEto=",
    "ConversationIndex": "AQHRh3zqrkAcds2kw==",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsRead": false,
    "IsDraft": false,
    "WebLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGI2THVSAAA%3D&exvsurl=1&viewmodel=ReadMessageItem"
}
```

 **响应类型**

请求的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

**请注意**默认情况下，该响应包括指定的消息的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定响应中返回仅此邮件的**发件人**和**主题**属性。

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGE1I5MTAAA=?$select=Sender,Subject
```



[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages/{message_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2THVSAAA=
```

**响应示例**

```
{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')",
    "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz\"",
    "Id": "AAMkAGI2THVSAAA=",
    "CreatedDateTime": "2014-10-20T00:41:57Z",
    "LastModifiedDateTime": "2014-10-20T00:41:57Z",
    "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTIKz",
    "Categories": [],
    "ReceivedDateTime": "2014-10-20T00:41:57Z",
    "SentDateTime": "2014-10-20T00:41:53Z",
    "HasAttachments": true,
    "Subject": "Re: Meeting Notes",
    "Body": {
        "ContentType": "Text",
        "Content": "\n________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP\n"
    },
    "BodyPreview": "________________________________________\nFrom: Alex D\nSent: Sunday, October 19, 2014 5:28 PM\nTo: Katie Jordan\nSubject: Meeting Notes\n\nPlease send me the meeting notes ASAP",
    "Importance": "Normal",
    "ParentFolderId": "AAMkAGI2AAEMAAA=",
    "Sender": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Katie Jordan",
            "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Alex D",
                "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com"
            }
        }
    ],
    "CcRecipients": [],
    "BccRecipients": [],
    "ReplyTo": [],
    "ConversationId": "AAQkAGI2yEto=",
    "IsDeliveryReceiptRequested": false,
    "IsReadReceiptRequested": false,
    "IsRead": false,
    "IsDraft": false,
    "WebLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGI2THVSAAA%3D&exvsurl=1&viewmodel=ReadMessageItem"
}
```

 **响应类型**

请求的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

**请注意**默认情况下，该响应包括指定的消息的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定响应中返回仅此邮件的**发件人**和**主题**属性。

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGE1I5MTAAA=?$select=Sender,Subject
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]


```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages/{message_id}
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|

[!code-REST-i[mail_api_get_message_by_id](./_data/mail_api_get_message_by_id.json)]


 **响应类型**

请求的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

**请注意**默认情况下，该响应包括指定的消息的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

下面的示例演示如何使用**$select**来指定响应中返回仅此邮件的**发件人**和**主题**属性。

```
GET https://outlook.office.com/api/v1.0/me/messages/AAMkAGEI5MTAAA=?$select=Sender,Subject
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="GetMessagesClient"> </a>
###<a name="get-a-message-collection-client"></a>获取消息集合 （客户端）

通过在收件箱中收到邮件`Me.Messages`快捷键属性。 要从另一文件夹中获取消息，使用该文件夹的**邮件**属性。
可用于以下的已知文件夹名称而不是 ID 对应的文件夹︰ `Inbox`， `SentItems`， `Drafts`， `DeletedItems`。

示例︰`outlookClient.Me.Folders["SentItems"].Messages.ExecuteAsync()`


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


**请注意**消息集合支持**选择**、**排序**，并**执行**查询表达式。

本示例将调用方法[创建 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets"  data-resources="OutlookServices.Mail" -->

<!--tested-->
```cs-i
var outlookClient = await CreateOutlookClientAsync("Mail");
    var messages = await outlookClient.Me.Folders["Inbox"].Messages
      .OrderByDescending(m => m.DateTimeReceived)
      .Take(10)
      .ExecuteAsync();

foreach(var message in messages.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Message '{0}' received at '{1}'.",
    message.Subject,
    message.DateTimeReceived.ToString());
}

```
```javascript-i
outlookClient.me.folders.getFolder('Inbox').messages.getMessages().orderBy('DateTimeReceived desc').fetchAll(10).then(function (result) {
    result.forEach(function (message) {
        console.log('Message "' + message.subject + '" received at "' + message.dateTimeReceived.toString() + '"');
    });
}, function(error) {
    console.log(error);
});
```

<!-- ENDSECTION -->

****

<a name="GetMessageClient"> </a>
###<a name="get-a-message-client"></a>收到一条消息 （客户端）

若要获得特定的消息，作为**消息**集合中的索引指定的消息 ID，或使用**GetById**方法。

****

<a name="SynchronizeMessagesAPI"></a>
##<a name="synchronize-messages"></a>同步邮件

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

您可以使用服务器上的邮件同步您的本地数据存储区。 邮件同步的每个文件夹操作，您可以在例如，同步收件箱中的所有邮件。 若要同步文件夹层次结构中您需要同步的每个文件夹单独的邮件。

API 支持检索所有文件夹中的邮件的完全同步和增量同步，以检索所有自上次完全同步后已更改的消息。

同步邮件文件夹通常需要两个或多个 GET 请求。 使 GET 请求更像您[收到的邮件](#GetMessages)，只是包括某些请求标头中， _deltaToken_或_skipToken_在适当的时候。

**请求标头**

- 您必须指定_更愿意︰ odata.track 更改_，包括除外的所有同步请求中的标头`skipToken`返回前一个同步请求。 在第一个响应中，寻找_首选项应用︰ odata.track 更改_标头，以确认该资源支持同步之前。

- 您可以指定_更愿意︰ odata.maxpagesize={x}_请求中返回的标头设置最大邮件数。

下面是典型的倒圆角，同步消息的︰

1. 使带有强制性的初始 GET 请求_更愿意︰ odata.track 更改_头。 初始同步请求响应始终返回_deltaToken_。 （第二个和后续 GET 请求不同于第一个 GET 请求包括_deltaToken_或_skipToken_在以前的响应中收到的。）

2. 如果第一个响应返回_首选项应用︰ odata.track 更改_标头，则可以进行同步处理的文件夹。

  - 进行第二个 GET 请求。 指定_更愿意︰ odata.track 更改_标头和_deltaToken_将返回从第一个 GET 操作以确定是否有任何其他消息。 第二个请求将返回其它消息，并且是_skipToken_ ，如果有更多的邮件可用或_deltaToken_如果最后一条消息已同步，在这种情况下，您可以停止。

  - 继续通过发送一个 GET 调用并将包括从以前的调用中返回_skipToken_同步。 停止时获得最终的响应，其中包含_@odata.deltaLink_ _deltaToken_同样的标头，它表示同步已完成。


### <a name="to-sync-messages-in-a-specific-folder"></a>若要同步特定的文件夹中的邮件

**初始请求**

```no-highlight
GET https://outlook.office365.com/api/beta/me/MailFolders('{folder_id}')/messages
```

**第二个请求或下一轮的第一个请求**

```no-highlight
GET https://outlook.office365.com/api/beta/me/MailFolders('{folder_id}')/messages/?$deltaToken={delta_token}
```

**第三个或后续的请求，在同一圈**

继续发送下一个同步请求，如果以前的响应中包含`skipToken`。 当您得到的响应，其中包含停止`@odata.deltaLink`标头`deltaToken`再次。

```no-highlight
GET https://outlook.office365.com/api/beta/me/MailFolders('{folder_id}')/messages/?$skipToken={skip_token}
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|更喜欢|odata.track 更改|指示请求的同步请求。 在一轮前 2 GET 请求时所需。|
|更喜欢|odata.maxpagesize|设置要在每个响应中返回的邮件数。 可选项。|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹名称进行同步。 必需。|
|deltaToken|String|标记，用于标识该文件夹的上一次的同步请求。 它将作为组成部分的值@odata.deltaLink在该上一同步响应。 所需的第二个 GET 请求。|
|skipToken|String|一个标记，它指示存在多个要下载的邮件。 如果它返回的值的一部分所需@odata.nextLink前一同步响应。|


默认情况下同步的文件夹中返回的所有属性和所有的邮件。 使用 $select 查询表达式中指定的属性，您需要为获得最佳性能。 始终返回的_Id_属性。 

同步支持查询表达式 $select，$top，$expand。 有是有限的支持 $filter 和 $orderby，以及不支持 $search。

* 唯一受支持的 $filter 表达式是"$filter = ReceivedDateTime + ge + {值}"或"$filter = ReceivedDateTime + gt + {值}"。
* 唯一受支持的 $orderby 表达式是"$orderby = ReceivedDateTime + desc"。 如果不包括 $orderby 表达式，则不保证退货单。
  
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

包含请求的消息中， _deltaToken_或_skipToken_ ，用于从服务器进行增量同步请求消息中的数据的附加页面的集合。 




**示例**

下面的示例演示一系列请求，若要同步特定的文件夹，其中包含 7 的消息。 在第一个同步请求指定一次 （_odata.maxpagesize_为 2），返回 2 的消息和仅每封邮件的**发件人**和**主题**属性。

- 最初的响应返回 2 消息， `deltaLink` ， `deltaToken`。 
- 第二个请求使用的`deltaToken`。 第二个响应返回 2 消息， `nextLink` ， `skipToken`。
- 完成同步，第三和第四个请求都使用`skipToken`返回前一个同步请求，直到第四同步响应返回`deltaLink`， `deltaToken`，在这种情况下此轮同步已完成。 保存`deltaToken`的同步的下一轮。 

**初始请求的示例**

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages?$select=Subject,Sender HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```


**初始响应的示例数据**

最初的响应包括`Preference-Applied: odata.track-changes`标头，表示此文件夹支持同步。 该答复还包括两条消息和一个`deltaToken`。

```
Preference-Applied: odata.track-changes

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADPAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9+\"",
      "Id":"AAMkAGI5MAAAwXADPAAA=",
      "Subject":"Updates from All Company",
      "Sender":{
        "EmailAddress":{
          "Name":"Contoso Demo on Yammer",
          "Address":"noreply@yammer.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADVAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+E\"",
      "Id":"AAMkAGI5MAAAwXADVAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Alex Darrow",
          "Address":"AlexD@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink":"https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA"
}
```

**示例的第二个请求**

第二个请求指定`deltaToken`以前的响应中返回。

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```

**示例的第二个响应数据**

第二个响应包括两个更多的邮件， `skipToken`，表明有更多要同步的文件夹中的邮件。

```
{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADQAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9/\"",
      "Id":"AAMkAGI5MAAAwXADQAAA=",
      "Subject":"International Launch Planning for XT2000",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADUAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+D\"",
      "Id":"AAMkAGI5MAAAwXADUAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Anne Wallace",
          "Address":"AnneW@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA"
}
```

**示例的第三个请求**

Thirs 请求包括`skipToken`以前的响应中返回。

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**第三个响应数据的示例**

第三个响应返回两个更多的邮件，另一个`skipToken`，仍表明有邮件要同步的文件夹中。

```
{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADTAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+C\"",
      "Id":"AAMkAGI5MAAAwXADTAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Pavel Bansky",
          "Address":"PavelB@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADSAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+B\"",
      "Id":"AAMkAGI5MAAAwXADSAAA=",
      "Subject":"Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA"
}
```

**示例的第四个请求**

第四个请求中包含`skipToken`从上面的回答。

```
GET https://outlook.office.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**第四个也是最后的响应的示例数据**

第四个响应返回在文件夹中，只剩下邮件和一个`deltaToken`表示同步已完成此文件夹。 保存`deltaToken`为该文件夹的同步的下一轮。

```
{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADRAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+A\"",
      "Id":"AAMkAGI5MAAAwXADRAAA=",
      "Subject":"Data sheets for the XT2000 ",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink": "https://outlook.office365.com/api/beta/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24deltaToken=0_zCBD5nm2dcGAFGk5qypL1PSyEAADBb9RkEAAAA"
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

您可以使用服务器上的邮件同步您的本地数据存储区。 邮件同步的每个文件夹操作，您可以在例如，同步收件箱中的所有邮件。 若要同步文件夹层次结构中您需要同步的每个文件夹单独的邮件。

API 支持检索所有文件夹中的邮件的完全同步和增量同步，以检索所有自上次完全同步后已更改的消息。

同步邮件文件夹通常需要两个或多个 GET 请求。 使 GET 请求更像您[收到的邮件](#GetMessages)，只是包括某些请求标头中， _deltaToken_或_skipToken_在适当的时候。

**请求标头**

- 您必须指定_更愿意︰ odata.track 更改_，包括除外的所有同步请求中的标头`skipToken`返回前一个同步请求。 在第一个响应中，寻找_首选项应用︰ odata.track 更改_标头，以确认该资源支持同步之前。

- 您可以指定_更愿意︰ odata.maxpagesize={x}_请求中返回的标头设置最大邮件数。

下面是典型的倒圆角，同步消息的︰

1. 使带有强制性的初始 GET 请求_更愿意︰ odata.track 更改_头。 初始同步请求响应始终返回_deltaToken_。 （第二个和后续 GET 请求不同于第一个 GET 请求包括_deltaToken_或_skipToken_在以前的响应中收到的。）

2. 如果第一个响应返回_首选项应用︰ odata.track 更改_标头，则可以进行同步处理的文件夹。

  - 进行第二个 GET 请求。 指定_更愿意︰ odata.track 更改_标头和_deltaToken_将返回从第一个 GET 操作以确定是否有任何其他消息。 第二个请求将返回其它消息，并且是_skipToken_ ，如果有更多的邮件可用或_deltaToken_如果最后一条消息已同步，在这种情况下，您可以停止。

  - 继续通过发送一个 GET 调用并将包括从以前的调用中返回_skipToken_同步。 停止时获得最终的响应，其中包含_@odata.deltaLink_ _deltaToken_同样的标头，它表示同步已完成。


### <a name="to-sync-messages-in-a-specific-folder"></a>若要同步特定的文件夹中的邮件

**初始请求**

```no-highlight
GET https://outlook.office365.com/api/v2.0/me/MailFolders('{folder_id}')/messages
```

**第二个请求或下一轮的第一个请求**

```no-highlight
GET https://outlook.office365.com/api/v2.0/me/MailFolders('{folder_id}')/messages/?$deltaToken={delta_token}
```

**第三个或后续的请求，在同一圈**

继续发送下一个同步请求，如果以前的响应中包含`skipToken`。 当您得到的响应，其中包含停止`@odata.deltaLink`标头`deltaToken`再次。

```no-highlight
GET https://outlook.office365.com/api/v2.0/me/MailFolders('{folder_id}')/messages/?$skipToken={skip_token}
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|更喜欢|odata.track 更改|指示请求的同步请求。 在一轮前 2 GET 请求时所需。|
|更喜欢|odata.maxpagesize|设置要在每个响应中返回的邮件数。 可选项。|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹名称进行同步。 必需。|
|deltaToken|String|标记，用于标识该文件夹的上一次的同步请求。 它将作为组成部分的值@odata.deltaLink在该上一同步响应。 所需的第二个 GET 请求。|
|skipToken|String|一个标记，它指示存在多个要下载的邮件。 如果它返回的值的一部分所需@odata.nextLink前一同步响应。|


默认情况下同步的文件夹中返回的所有属性和所有的邮件。 使用 $select 查询表达式中指定的属性，您需要为获得最佳性能。 始终返回的_Id_属性。 

同步支持查询表达式 $select，$top，$expand。 有是有限的支持 $filter 和 $orderby，以及不支持 $search。

* 唯一受支持的 $filter 表达式是"$filter = ReceivedDateTime + ge + {值}"或"$filter = ReceivedDateTime + gt + {值}"。
* 唯一受支持的 $orderby 表达式是"$orderby = ReceivedDateTime + desc"。 如果不包括 $orderby 表达式，则不保证退货单。
  
筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

包含请求的消息中， _deltaToken_或_skipToken_ ，用于从服务器进行增量同步请求消息中的数据的附加页面的集合。 




**示例**

下面的示例演示一系列请求，若要同步特定的文件夹，其中包含 7 的消息。 在第一个同步请求指定一次 （_odata.maxpagesize_为 2），返回 2 的消息和仅每封邮件的**发件人**和**主题**属性。

- 最初的响应返回 2 消息， `deltaLink` ， `deltaToken`。 
- 第二个请求使用的`deltaToken`。 第二个响应返回 2 消息， `nextLink` ， `skipToken`。
- 完成同步，第三和第四个请求都使用`skipToken`返回前一个同步请求，直到第四同步响应返回`deltaLink`， `deltaToken`，在这种情况下此轮同步已完成。 保存`deltaToken`的同步的下一轮。 

**初始请求的示例**

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages?$select=Subject,Sender HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```


**初始响应的示例数据**

最初的响应包括`Preference-Applied: odata.track-changes`标头，表示此文件夹支持同步。 该答复还包括两条消息和一个`deltaToken`。

```
Preference-Applied: odata.track-changes

{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADPAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9+\"",
      "Id":"AAMkAGI5MAAAwXADPAAA=",
      "Subject":"Updates from All Company",
      "Sender":{
        "EmailAddress":{
          "Name":"Contoso Demo on Yammer",
          "Address":"noreply@yammer.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADVAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+E\"",
      "Id":"AAMkAGI5MAAAwXADVAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Alex Darrow",
          "Address":"AlexD@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink":"https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA"
}
```

**示例的第二个请求**

第二个请求指定`deltaToken`以前的响应中返回。

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24deltatoken=MfzCBD5nm2dcGAFGk5qypL1PSyEAADFmX28BAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
Prefer: odata.track-changes
```

**示例的第二个响应数据**

第二个响应包括两个更多的邮件， `skipToken`，表明有更多要同步的文件夹中的邮件。

```
{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADQAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS9/\"",
      "Id":"AAMkAGI5MAAAwXADQAAA=",
      "Subject":"International Launch Planning for XT2000",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADUAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+D\"",
      "Id":"AAMkAGI5MAAAwXADUAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Anne Wallace",
          "Address":"AnneW@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA"
}
```

**示例的第三个请求**

Thirs 请求包括`skipToken`以前的响应中返回。

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28CAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**第三个响应数据的示例**

第三个响应返回两个更多的邮件，另一个`skipToken`，仍表明有邮件要同步的文件夹中。

```
{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADTAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+C\"",
      "Id":"AAMkAGI5MAAAwXADTAAA=",
      "Subject":"RE: Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Pavel Bansky",
          "Address":"PavelB@contoso.onmicrosoft.com"
        }
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADSAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+B\"",
      "Id":"AAMkAGI5MAAAwXADSAAA=",
      "Subject":"Latin American Ad Campaign - XT Series",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.nextLink":"https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA"
}
```

**示例的第四个请求**

第四个请求中包含`skipToken`从上面的回答。

```
GET https://outlook.office.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24select=Subject%2cSender&%24skipToken=MfzCAj5nm2dcGAFGk5qypL1PSyEAADFmX28DAAAA HTTP/1.1
Prefer: odata.maxpagesize=2
```

**第四个也是最后的响应的示例数据**

第四个响应返回在文件夹中，只剩下邮件和一个`deltaToken`表示同步已完成此文件夹。 保存`deltaToken`为该文件夹的同步的下一轮。

```
{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('AAMkAGI5MAAAwW-j-AAA%3D')/Messages(Subject,Sender)/$delta",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/v2.0/Users('f97adce1-d718-4a0e-9af8-b10167e3a346@0d76cf04-f6a0-46cc-947b-d2e1bdd98d11')/Messages('AAMkAGI5MAAAwXADRAAA=')",
      "@odata.etag":"W/\"CQAAABYAAAA+Z5tnXBgBRpOasqS9T0shAAAwYS+A\"",
      "Id":"AAMkAGI5MAAAwXADRAAA=",
      "Subject":"Data sheets for the XT2000 ",
      "Sender":{
        "EmailAddress":{
          "Name":"Engineering",
          "Address":"engineering@contoso.onmicrosoft.com"
        }
      }
    }
  ],
  "@odata.deltaLink": "https://outlook.office365.com/api/v2.0/Me/MailFolders('AAMkAGI5MAAAwW-j-AAA=')/messages/?%24deltaToken=0_zCBD5nm2dcGAFGk5qypL1PSyEAADBb9RkEAAAA"
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前在 2.0 版和测试版。 若要了解详细信息，在右上角的文章中使用控件并选择版本。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="SendMessages"> </a>
##<a name="create-and-send-messages"></a>创建和发送邮件

可以动态，发送一封新邮件或创建邮件草稿，然后将其发送。 您可以在任何文件夹中创建草稿。

REST API︰[发送新邮件在飞 (REST)](#SendMessageOnTheFly) | [创建邮件草稿 (REST)](#CreateNewDraft) | [发送邮件草稿 (REST)](#SendDraftMessages)

客户端库︰[发送新邮件在飞 （客户端）](#SendMessageOnTheFlyClient) | [创建邮件草稿 （客户端）](#CreateDraftClient) | [发送邮件草稿 （客户端）](#SendDraftClient)


<a name="SendMessageOnTheFly"> </a>
###<a name="send-a-new-message-on-the-fly-rest"></a>动态 (REST) 发送一封新邮件

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_

发送使用**SendMail**方法提供请求主体中的消息。 您可以包含一个或多个附件为同一操作中的调用通过**附件**集合属性中指定。 您还可以在已发送邮件文件夹中保存邮件。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/sendmail
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_正文参数_|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要发送的消息。|
|SavetoSentItems|布尔|指示是否将邮件保存在已发送邮件中。 默认值为**true**。|

指定具有必需的**ToRecipients**属性和请求主体中的任何可写[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性的**消息**参数。
**SaveToSentItems**参数是必需的只有当**假**。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/sendmail
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
          "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
      }
    ],
    "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
        "Name": "menu.md",
        "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "SaveToSentItems": "false"
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/sendmail
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_正文参数_|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要发送的消息。|
|SavetoSentItems|布尔|指示是否将邮件保存在已发送邮件中。 默认值为**true**。|

指定具有必需的**ToRecipients**属性和请求主体中的任何可写[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性的**消息**参数。
**SaveToSentItems**参数是必需的只有当**假**。


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/sendmail

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
          "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
      }
    ],
    "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
        "Name": "menu.md",
        "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "SaveToSentItems": "false"
}

```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/sendmail
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_正文参数_|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要发送的消息。|
|SavetoSentItems|布尔|指示是否将邮件保存在已发送邮件中。 默认值为**true**。|

指定具有必需的**ToRecipients**属性和请求主体中的任何可写[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性的**消息**参数。
**SaveToSentItems**参数是必需的只有当**假**。

[!code-REST-i[mail_api_sendmail](./_data/mail_api_sendmail.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="CreateNewDraft"> </a>
###<a name="create-a-draft-message-rest"></a>创建邮件草稿 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

创建一封新邮件的草稿。 可以在任何文件夹，可以选择[更新](#UpdateMessages)[发送](#SendDraftMessages)前请先创建草稿。
若要将保存到草稿文件夹，请使用`/me/messages`快捷方式。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
POST https://outlook.office.com/api/beta/me/messages
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|目标文件夹 ID，或`Inbox`或`Drafts`的已知文件夹的名称。|

指定请求主体中的任何可写的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性。

**示例请求**

```
POST https://outlook.office.com/api/beta/me/MailFolders/inbox/messages
Content-Type: application/json

{
  "Subject": "Did you see last night's game?",
  "Importance": "Low",
  "Body": {
    "ContentType": "HTML",
    "Content": "They were <b>awesome</b>!"
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
      }
    }
  ]
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k0AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5\"",
  "Id": "AAMkAGE0Mz7k0AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5",
  "Categories": [],
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "CreatedDateTime": "2014-10-18T20:06:51Z",
  "LastModifiedDateTime": "2014-10-18T20:06:51Z",
  "Subject": "Did you see last night's game?",
  "BodyPreview": "They were awesome!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nThey were <b>awesome</b>!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Low",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mpv2hisc=",
  "ConversationIndex": "AQHRf4zqrkAcds2kw==",
  "ReceivedDateTime": "2014-10-18T20:06:51Z",
  "SentDateTime": "2014-10-18T20:06:51Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/messages
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|目标文件夹 ID，或`Inbox`或`Drafts`的已知文件夹的名称。|

指定请求主体中的任何可写的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性。

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/MailFolders/inbox/messages
Content-Type: application/json

{
  "Subject": "Did you see last night's game?",
  "Importance": "Low",
  "Body": {
    "ContentType": "HTML",
    "Content": "They were <b>awesome</b>!"
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
      }
    }
  ]
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k0AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5\"",
  "Id": "AAMkAGE0Mz7k0AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0Ag5",
  "Categories": [],
  "CreatedDateTime": "2014-10-18T20:06:51Z",
  "LastModifiedDateTime": "2014-10-18T20:06:51Z",
  "Subject": "Did you see last night's game?",
  "BodyPreview": "They were awesome!",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n</head>\r\n<body>\r\nThey were <b>awesome</b>!\r\n</body>\r\n</html>\r\n"
  },
  "Importance": "Low",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mpv2hisc=",
  "ReceivedDateTime": "2014-10-18T20:06:51Z",
  "SentDateTime": "2014-10-18T20:06:51Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/messages
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|目标文件夹 ID，或`Inbox`或`Drafts`的已知文件夹的名称。|

指定请求主体中的任何可写的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性。

[!code-REST-i[mail_api_create_message_in_folder](./_data/mail_api_create_message_in_folder.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



 **响应类型**

草案的[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

****

<a name="SendDraftMessages"> </a>
###<a name="send-a-draft-message-rest"></a>发送邮件草稿 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_

使用**Send**方法发送[新邮件草稿](#CreateNewDraft)、[答复草稿](#CreateReplyDraft)、[全部答复草稿](#CreateReplyAllDraft)或[转发的草稿](#CreateForwardDraft)。
然后在已发送邮件文件夹中保存邮件。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/send
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|草稿信息发送的 ID。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz7k0AAA=/send
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/send
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|草稿信息发送的 ID。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz7k0AAA=/send
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/send
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|草稿信息发送的 ID。|

[!code-REST-i[mail_api_send_message_by_id](./_data/mail_api_send_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="SendMessageOnTheFlyClient"> </a>
###<a name="send-a-new-message-on-the-fly-client"></a>动态 （客户端） 发送一封新邮件

创建一条消息并将其传递给**SendMailAsync**方法。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
ItemBody body = new ItemBody
{
    Content = "It was <b>awesome</b>!",
    ContentType = BodyType.HTML
};
List<Recipient> toRecipients = new List<Recipient>();
toRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"
    }
});
toRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "pavelb@a830edad9050849NDA1.onmicrosoft.com"
    }
});
Message newMessage = new Message
{
    Subject = "Did you see last night's game?",
    Body = body,
    ToRecipients = toRecipients
};

// To send a message without saving to Sent Items, specify false for  
// the SavetoSentItems parameter.
await outlookClient.Me.SendMailAsync(newMessage, true);
```

<!-- ENDSECTION -->

****

<a name="CreateDraftClient"> </a>
###<a name="create-a-draft-message-client"></a>创建邮件草稿 （客户端）

创建邮件草稿，并将其传递给**AddMessageAsync**方法。 然后，您可以[更新该草案](#UpdateMessagesClient)并[将其发送](#SendDraftClient)。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
ItemBody body = new ItemBody
{
    Content = "I'm coming out a week later.",
    ContentType = BodyType.HTML
};
List<Recipient> toRecipients = new List<Recipient>();
toRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "katiej@a830edad9050849NDA1.onmicrosoft.com"
    }
});
Message draftMessage = new Message
{
    Subject = "Changed my travel plans",
    Body = body,
    ToRecipients = toRecipients,
    Importance = Importance.High
};

// Save the draft message. Saving to Me.Messages saves the message in the Drafts folder.
await outlookClient.Me.Messages.AddMessageAsync(draftMessage);

// Get the ID of the message.
string messageId = draftMessage.Id;
```

<!-- ENDSECTION -->

向**Me.Messages**集合中添加一条消息将草稿保存在草稿文件夹中，但您可以**消息**集合的任何文件夹中保存草稿。

示例︰`outlookClient.Me.Folders["AAMkADE3N..."].Messages.AddMessageAsync(newMessage)`

****

<a name="SendDraftClient"> </a>
###<a name="send-a-draft-message-client"></a>发送邮件草稿 （客户端）

通过调用**SendAsync**发送绘制消息。 您可以发送一个新草案、 答复、 全部答复或转发邮件。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
await outlookClient.Me.Messages[messageId].SendAsync();
```

<!-- ENDSECTION -->

****

<a name="ReplyToMessages"> </a>
##<a name="reply-or-reply-all-to-messages"></a>回复或回复邮件

**请注意**本节中的操作的行为因版本而异。 有关更多信息，请在页面右上角选择一个版本。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

可以答复一封邮件，添加注释或更新所有打一个电话，或者您可以首先创建答复草稿和合一任何消息属性调用，然后将草案发送的更新消息属性。

您可以答复仅发件人的邮件或答复所有收件人一次。


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

您可以用动态的注释回复或第一次可以创建答复草稿，然后更新并将该草案。
您可以答复仅发件人的邮件或答复所有收件人一次。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

您可以用动态的注释回复或第一次可以创建答复草稿，然后更新并将该草案。
您可以答复仅发件人的邮件或答复所有收件人一次。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


REST API︰[答复发件人动态 (REST)](#ReplyToSender) | [在动态 (REST) 的答复](#ReplyAll) | [创建答复邮件草稿 (REST)](#CreateReplyDraft) | [创建全部答复邮件草稿 (REST)](#CreateReplyAllDraft)

客户端库︰[回复或答复所有上飞 （客户端）](#ReplyOnTheFlyClient) | [创建的草稿答复或全部答复邮件草稿 （客户端）](#CreateDraftReplyClient)

<a name="ReplyToSender"> </a>
###<a name="reply-to-sender-on-the-fly-rest"></a>答复发件人动态 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

答复邮件的发件人、 添加注释或修改任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)都在一个**回复**电话。 然后在已发送邮件文件夹中保存邮件。

或者，您可以第一个[创建答复邮件草稿](#CreateReplyDraft)包括注释或更新任何消息属性，然后[发送](#SendDraftMessages)答复。


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/reply
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要更新答复邮件中的任何可写属性。 |

**请注意**

- 注释或**Body**属性可以指定`Message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)) 指定了**回复**应该**回复**和不在**从**收件人发送答复收件人。 


**示例请求**

下面的示例包含一个注释，添加一位收件人答复邮件。

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/reply
Content-Type: application/json

{
  "Message":{  
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"fannyd@contoso.onmicrosoft.com",
          "Name":"Fanny Downs"
        }
      },
      {
        "EmailAddress":{
          "Address":"randiw@contoso.onmicrosoft.com",
          "Name":"Randi Welch"
        }
      }
     ]
  },
  "Comment": "Fanny, Randi, would you name the group please?" 
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

通过指定注释并使用**Reply**方法答复邮件的发件人。 然后在已发送邮件文件夹中保存邮件。

或者，如果您需要修改的回复任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，您可以第一个[创建答复邮件草稿](#CreateReplyDraft)，[更新](#UpdateMessages)消息属性，然后[发送](#SendDraftMessages)答复。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/reply
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/reply
Content-Type: application/json

{
  "Comment": "Sounds great! See you tomorrow."
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

通过指定注释并使用**Reply**方法答复邮件的发件人。 然后在已发送邮件文件夹中保存邮件。

或者，如果您需要修改的回复任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，您可以第一个[创建答复邮件草稿](#CreateReplyDraft)，[更新](#UpdateMessages)消息属性，然后[发送](#SendDraftMessages)答复。

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/reply
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

[!code-REST-i[mail_api_send_reply_by_id](./_data/mail_api_send_reply_by_id.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****


<a name="ReplyAll"> </a>
###<a name="reply-all-on-the-fly-rest"></a>所有上飞 (REST) 的答复

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

通过指定注释和所有通过使用**全部答复**方法中修改任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)的回复，回复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。

或者，您可以第一个[创建全部答复邮件草稿](#CreateReplyAllDraft)包括注释和更新任何消息属性，然后[发送](#SendDraftMessages)答复。


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/replyall
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要更新的全部答复邮件中的任何可写属性。 |

**请注意**

- 注释或**Body**属性可以指定`Message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果**回复**指定在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822))，应该在**从**和**ToRecipients**发送**回复**和**ToRecipients**，在收件人的收件人不答复。 


**示例请求**

下面的示例包含一个注释，并添加全部答复邮件的附件。

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/ReplyAll
Content-Type: application/json

{
    "Message":{
      "Attachments": [ 
        { 
          "@odata.type": "#Microsoft.OutlookServices.FileAttachment", 
          "Name": "guidelines.md", 
          "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "Comment": "Please take a look at the attached guidelines before you decide on the name." 
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

指定注释，并使用**全部答复**方法通过回复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。

或者，如果您需要修改的回复任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，您可以第一个[创建全部答复邮件草稿](#CreateReplyAllDraft)，[更新](#UpdateMessages)消息属性，然后[发送](#SendDraftMessages)答复。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/replyall
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0MSz8DmAAA=/replyall
Content-Type: application/json

{
  "Comment": "Thanks for the heads up."
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

指定注释，并使用**全部答复**方法通过回复邮件的所有收件人。 然后在已发送邮件文件夹中保存邮件。

或者，如果您需要修改的回复任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，您可以第一个[创建全部答复邮件草稿](#CreateReplyAllDraft)，[更新](#UpdateMessages)消息属性，然后[发送](#SendDraftMessages)答复。


```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/replyall
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

[!code-REST-i[mail_api_send_reply_all_by_id](./_data/mail_api_send_reply_all_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




****

<a name="CreateReplyDraft"> </a>
###<a name="create-a-draft-reply-message-rest"></a>创建答复邮件草稿 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

创建包含注释或更新任何[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)中一个**CreateReply**调用的所有回复邮件的草稿。 然后可以[将发送](#SendDraftMessages)邮件草稿。


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/createreply
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要更新答复邮件中的任何可写属性。 |

**请注意**

- 注释或**Body**属性可以指定`Message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果**回复**指定在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822))，应该**从**中发送到收件人的**回复**，并不是收件人的答复。 


**示例请求**

下面的示例创建答复草稿，在请求正文中添加注释和收件人。

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createreply
Content-Type: application/json

{
  "Message":{  
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"fannyd@contoso.onmicrosoft.com",
          "Name":"Fanny Downs"
        }
      },
      {
        "EmailAddress":{
          "Address":"randiw@contoso.onmicrosoft.com",
          "Name":"Randi Welch"
        }
      }
     ]
  },
  "Comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
}

```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "Id": "AAMkADA1MTAAAH5JKoAAA=",
  "CreatedDateTime": "2016-03-15T08:33:43Z",
  "LastModifiedDateTime": "2016-03-15T08:33:43Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:33:43Z",
  "SentDateTime": "2016-03-15T08:33:43Z",
  "HasAttachments": false,
  "InternetMessageId": "<DM2PR00MB00571796B16132601E1F286CF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "Fanny, Randi, would you name the group if the project is approved, please?\r\n________________________________\r\nFrom: Fanny Downs\r\nSent: Friday, March 4, 2016 12:23:35 AM\r\nTo: Admin\r\nSubject: Re: Let's start a group\r\n\r\n\r\nThat's a gre",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTVGjIwpLvWmGtIo-aFE=",
  "ConversationIndex": "AQHRdar6akFxUaMjCku9aYa0ij9oUZ9IbLr7gBHStBQ=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKoAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

创建一个**CreateReply**调用中添加注释回复邮件的草稿。 然后可以[更新](#UpdateMessages)[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)和[发送](#SendDraftMessages)草稿。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/createreply
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createreply
Content-Type: application/json

{
  "Comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
}

```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "Id": "AAMkADA1MTAAAH5JKoAAA=",
  "CreatedDateTime": "2016-03-15T08:33:43Z",
  "LastModifiedDateTime": "2016-03-15T08:33:43Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:33:43Z",
  "SentDateTime": "2016-03-15T08:33:43Z",
  "HasAttachments": false,
  "InternetMessageId": "<DM2PR00MB00571796B16132601E1F286CF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "Fanny, Randi, would you name the group if the project is approved, please?\r\n________________________________\r\nFrom: Fanny Downs\r\nSent: Friday, March 4, 2016 12:23:35 AM\r\nTo: Admin\r\nSubject: Re: Let's start a group\r\n\r\n\r\nThat's a gre",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [ ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTVGjIwpLvWmGtIo-aFE=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKoAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

创建一个**CreateReply**调用中添加注释回复邮件的草稿。 然后可以[更新](#UpdateMessages)[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)和[发送](#SendDraftMessages)草稿。

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createreply
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要回复的消息的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAAqldOAAA=/createreply
Content-Type: application/json

{
  "Comment": "Fanny, Randi, would you name the group if the project is approved, please?" 
}

```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKoAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO\"",
  "Id": "AAMkADA1MTAAAH5JKoAAA=",
  "CreatedDateTime": "2016-03-15T08:33:43Z",
  "LastModifiedDateTime": "2016-03-15T08:33:43Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DO",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:33:43Z",
  "SentDateTime": "2016-03-15T08:33:43Z",
  "HasAttachments": false,
  "InternetMessageId": "<DM2PR00MB00571796B16132601E1F286CF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>Fanny, Randi, would you name the group if the project is approved, please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n<p>That's a great idea!<br>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "Fanny, Randi, would you name the group if the project is approved, please?\r\n________________________________\r\nFrom: Fanny Downs\r\nSent: Friday, March 4, 2016 12:23:35 AM\r\nTo: Admin\r\nSubject: Re: Let's start a group\r\n\r\n\r\nThat's a gre",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [ ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTVGjIwpLvWmGtIo-aFE=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKoAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




 **响应类型**

该草案答复[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)与**ToRecipient**、 **IsDraft**和其他预填充相应的属性。

****


<a name="CreateReplyAllDraft"> </a>
###<a name="create-a-draft-reply-all-message-rest"></a>创建全部答复邮件草稿 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

创建要包含注释或更新任何[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，都在一个**CreateReplyAll**调用的全部答复邮件的草稿。 然后可以[将发送](#SendDraftMessages)邮件草稿。


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/createreplyall
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|对全部答复消息的 ID 为。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要更新的全部答复邮件中的任何可写属性。 |

**请注意**

- 注释或**Body**属性可以指定`Message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 如果在原始邮件中，每个 Internet 邮件格式 ([RFC 2822](http://www.rfc-editor.org/info/rfc2822)) 指定了**回复**应该发送回复的**回复**和**ToRecipients**属性，在收件人和收件人不在**从**和**ToRecipients**属性。 


**示例请求**

下面的示例创建草稿进行答复，并在一次**CreateReplyAll**调用中添加附件和注释。

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaKAAA=/createreplyall
Content-Type: application/json

{
    "Message":{
      "Attachments": [ 
        { 
          "@odata.type": "#Microsoft.OutlookServices.FileAttachment", 
          "Name": "guidelines.md", 
          "ContentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk=" 
        } 
      ]
    },
    "Comment": "if the project gets approved, please take a look at the attached guidelines before you decide on the name." 
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKpAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DP\"",
  "Id": "AAMkADA1MTAAAH5JKpAAA=",
  "CreatedDateTime": "2016-03-15T08:37:34Z",
  "LastModifiedDateTime": "2016-03-15T08:37:34Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:37:34Z",
  "SentDateTime": "2016-03-15T08:37:34Z",
  "HasAttachments": true,
  "InternetMessageId": "<DM2PR00MB005732BE05BD669AC7CE056EF7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "RE: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body dir=\"ltr\">\r\nif the project gets approved, please take a look at the attached guidelines before you decide on the name.\r\n<b>From:</b> Admin<br>\r\n<b>Sent:</b> Tuesday, March 15, 2016 6:36:32 AM<br>\r\n<b>To:</b> Fanny Downs; Randi Welch<br>\r\n<b>Subject:</b> RE: Let's start a group\r\n<div>Fanny, Randi, would you name the group please?\r\n<b>From:</b> Fanny Downs<br>\r\n<b>Sent:</b> Friday, March 4, 2016 12:23:35 AM<br>\r\n<b>To:</b> Admin<br>\r\n<b>Subject:</b> Re: Let's start a group</font>\r\n</body>\r\n</html>"
  },
  "BodyPreview": "if the project gets approved, please take a look at the attached guidelines before you decide on the name.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:36:32 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubj",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTLvWmGtIo-aFE=",
  "ConversationIndex": "AQHRdar6akFxUaMjCku9aYa0ij9oUZ9IbLr7gBGx9qGAACHRQA==",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKpAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

创建一个**CreateReplyAll**调用中添加注释回复所有邮件的草稿。 然后可以[更新](#UpdateMessages)[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)和[发送](#SendDraftMessages)草稿。

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/createreplyall
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|对全部答复消息的 ID 为。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createreplyall
Content-Type: application/json

{
    "Comment": "If the project gets approved, please decide on the name." 
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k5AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF\"",
  "Id": "AAMkAGE0Mz7k5AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF",
  "Categories": [],
  "CreatedDateTime": "2014-10-18T21:21:06Z",
  "LastModifiedDateTime": "2014-10-18T21:21:06Z",
  "Subject": "RE: Check out the new Office 365 APIs",
  "BodyPreview": "If the project gets approved, please decide on the name.\r\n_________________________________\r\nFrom: Alex D\r\nSent: Saturday, October 18, 2014 9:18:18 PM\r\nTo: Katie Jordan; Garth Fort\r\nSubj",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2014-10-18T21:21:06Z",
  "SentDateTime": "2014-10-18T21:21:06Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createreplyall
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|对全部答复消息的 ID 为。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createreplyall
Content-Type: application/json

{
    "Comment": "If the project gets approved, please decide on the name." 
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k5AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF\"",
  "Id": "AAMkAGE0Mz7k5AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhF",
  "Categories": [],
  "CreatedDateTime": "2014-10-18T21:21:06Z",
  "LastModifiedDateTime": "2014-10-18T21:21:06Z",
  "Subject": "RE: Check out the new Office 365 APIs",
  "BodyPreview": "If the project gets approved, please decide on the name.\r\n_________________________________\r\nFrom: Alex D\r\nSent: Saturday, October 18, 2014 9:18:18 PM\r\nTo: Katie Jordan; Garth Fort\r\nSubj",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2014-10-18T21:21:06Z",
  "SentDateTime": "2014-10-18T21:21:06Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



 **响应类型**

该草案与**ToRecipient**、 **IsDraft**和预填充其他相应属性的全部答复[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

****

<a name="ReplyOnTheFlyClient"></a>
###<a name="reply-or-reply-all-on-the-fly-client"></a>回复或回复所有上飞 （客户端）

通过调用**ReplyAsync**或**ReplyAllAsync**在评论中回复直接向邮件的发件人或给所有的收件人。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
await outlookClient.Me.Messages[messageId].ReplyAsync("Count me in.");
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
await outlookClient.Me.Messages[messageId].ReplyAllAsync("Count me in.");
```

<!-- ENDSECTION -->

<a name="CreateDraftReplyClient"> </a>
###创建拔模回复所有邮件草稿 （客户端）

通过调用**CreateReplyAsync**或**CreateReplyAllAsync**创建拔模答复或全部答复消息。 然后，您可以[更新该草案](#UpdateMessagesClient)并[将其发送](#SendDraftClient)。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage replyDraft = await outlookClient.Me.Messages[messageId].CreateReplyAsync();

// Get the ID of the draft Reply message.
string replyMessageId = replyDraft.Id;
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IMessage replyAllDraft = await outlookClient.Me.Messages[messageId].CreateReplyAllAsync();

// Get the ID of the draft Reply All message.
string replyAllMessageId = replyAllDraft.Id;
```

<!-- ENDSECTION -->

**CreateReplyAsync**和**CreateReplyAllAsync**与**ToRecipients**、 **IsDraft**和其他预填充相应的属性创建邮件草稿。


****


<a name="ForwardMessages"> </a>
##<a name="forward-new-or-drafted-messages"></a>新的或绘制消息转发

**请注意**本节中的操作的行为因版本而异。 有关更多信息，请在页面右上角选择一个版本。
 
<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

可以转发邮件、 添加注释或更新所有打一个电话，或者您可以首先创建草稿和合一任何消息属性调用，然后将草案发送的更新消息属性。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

可以直接转发的邮件也可以创建转发邮件草稿、 更新，然后将其发送。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

可以直接转发的邮件也可以创建转发邮件草稿、 更新，然后将其发送。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



REST API︰[转发的邮件直接 (REST)](#ForwardDirectly) | [创建转发邮件 (REST)](#CreateForwardDraft)

客户端库︰[转发的邮件直接 （客户端）](#ForwardDirectlyClient) | [创建转发邮件草稿 （客户端）](#CreateDraftForwardClient)

<a name="ForwardDirectly"></a>
###<a name="forward-a-message-directly-rest"></a>转发邮件直接 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

转发邮件，添加注释或修改都在**前**一次调用任何[可更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)。 然后在已发送邮件文件夹中保存邮件。

或者，您可以第一个[创建转发邮件草稿](#CreateForwardDraft)包括注释或更新任何消息属性，然后[发送](#SendDraftMessages)邮件草稿。


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/forward
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要转发的邮件的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|ToRecipients|集合 （[收件人](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes)）|收件人列表中。|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要更新答复邮件中的任何可写属性。 |

**请注意**

- 注释或**Body**属性可以指定`Message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 您必须指定`ToRecipients`参数或的**ToRecipients**属性`Message`参数。 如果同时指定或指定既不会返回 HTTP 400 错误的请求错误。


**示例请求**

下面的示例将**IsDeliveryReceiptRequested**属性设置为 true，添加注释并将消息转发。

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaLAAA=/forward
Content-Type: application/json

{
  "Message":{  
    "IsDeliveryReceiptRequested": true,
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"danas@contoso.onmicrosoft.com",
          "Name":"Dana Swope"
        }
      }
     ]
  },
  "Comment": "Dana, just want to make sure you get this." 
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

通过使用**转发**方法并 （可选） 指定注释中转发的邮件。 然后在已发送邮件文件夹中保存邮件。

或者，如果您需要修改要转发的邮件中所有[更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，您可以第一个[创建拔模转发邮件](#CreateForwardDraft)，[更新](#UpdateMessages)消息属性，然后[发送](#SendDraftMessages)答复。


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/forward
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要转发的邮件的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|ToRecipients|集合 （[收件人](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes)）|收件人列表中。|

指定在请求正文中的**注释**和**ToRecipients**参数。


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/forward
Content-Type: application/json

{
  "Comment": "FYI",
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
      }
    }
  ]
}
```

**响应示例**

```
Status code: 202
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

通过使用**转发**方法并 （可选） 指定注释中转发的邮件。 然后在已发送邮件文件夹中保存邮件。

或者，如果您需要修改要转发的邮件中所有[更新的属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)，您可以第一个[创建拔模转发邮件](#CreateForwardDraft)，[更新](#UpdateMessages)消息属性，然后[发送](#SendDraftMessages)答复。


```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/forward
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要转发的邮件的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|ToRecipients|集合 （[收件人](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes)）|收件人列表中。|

指定在请求正文中的**注释**和**ToRecipients**参数。

[!code-REST-i[mail_api_send_forward_message_by_id](./_data/mail_api_send_forward_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->





****

<a name="CreateForwardDraft"> </a>
###<a name="create-a-draft-forward-message-rest"></a>创建转发邮件草稿 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

创建转发邮件草稿包括注释或更新都在一个**CreateForward**调用任何[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)。 然后可以[将发送](#SendDraftMessages)邮件草稿。


```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createforward
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要转发的邮件的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|ToRecipients|集合 （[收件人](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes)）|收件人列表中。|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要更新答复邮件中的任何可写属性。 |

**请注意**

- 注释或**Body**属性可以指定`Message`参数。 如果同时指定将返回 HTTP 400 错误的请求错误。
- 您必须指定`ToRecipients`参数或的**ToRecipients**属性`Message`参数。 如果同时指定或指定既不会返回 HTTP 400 错误的请求错误。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkADA1MTAAAH5JaLAAA=/createforward
Content-Type: application/json

{
  "Message":{  
    "IsDeliveryReceiptRequested": true,
    "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"danas@contoso.onmicrosoft.com",
          "Name":"Dana Swope"
        }
      }
     ]
  },
  "Comment": "Dana, just want to make sure you get this; you'll need this if the project gets approved." 
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTAAAH5JKqAAA=')",
  "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DQ\"",
  "Id": "AAMkADA1MTAAAH5JKqAAA=",
  "CreatedDateTime": "2016-03-15T08:42:10Z",
  "LastModifiedDateTime": "2016-03-15T08:42:10Z",
  "ChangeKey": "CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAH5/DQ",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-15T08:42:10Z",
  "SentDateTime": "2016-03-15T08:42:10Z",
  "HasAttachments": true,
  "InternetMessageId": "<DM2PR00MB0057E0EBC90EF37FC9233941F7890@DM2PR00MB0057.namprd00.prod.outlook.com>",
  "Subject": "FW: Let's start a group",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n<body>\r\nDana, just want to make sure you get this; you'll need this if the project gets approved.\r\n<b>From:</b> Admin<br>\r\n<b>Sent:</b> Tuesday, March 15, 2016 6:47:54 AM<br>\r\n<b>To:</b> Fanny Downs; Randi Welch<br>\r\n<b>Subject:</b> RE: Let's start a group</body>\r\n</html>\r\n"
  },
  "BodyPreview": "Dana, just want to make sure you get this; you'll need this if the project gets approved.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:47:54 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubject: RE: Let's st",
  "Importance": "Normal",
  "ParentFolderId": "AQMkADA1MTAAAAIBDwAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Admin",
      "Address": "admin@contoso.onmicrosoft.com"
    }
  },
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Dana Swope",
        "Address": "danas@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkADA1MTLvWmGtIo-aFE=",
  "ConversationIndex": "AQHRdar6akFxUaMjCku9aYa0ij9oUZ9IbLr7gBGx9qGAAAMtlIAAH+3c",
  "IsDeliveryReceiptRequested": true,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkADA1MTAAAH5JKqAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "MentionedMe": null,
  "AppliedHashtagsPreview": null,
  "LikesPreview": null,
  "MentionsPreview": null,
  "Mentioned": [ ],
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" }
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

创建一个**CreateForward**调用中添加评语或收件人转发邮件的草稿。 然后可以[更新](#UpdateMessages)[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)和[发送](#SendDraftMessages)草稿。


```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/createforward
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要转发的邮件的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|ToRecipients|集合 （[收件人](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes)）|收件人列表中。|

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createforward
Content-Type: application/json

{
  "ToRecipients":[
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
   ],
  "Comment": "Dana, just want to make sure you get this." 
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k6AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG\"",
  "Id": "AAMkAGE0Mz7k6AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG",
  "Categories": [],
  "CreatedDateTime": "2016-03-15T08:42:10Z",
  "LastModifiedDateTime": "2016-03-15T08:42:10Z",
  "Subject": "FW: Let's start a group",
  "BodyPreview": "Dana, just want to make sure you get this.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:47:54 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubject: RE: Let's st",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "'alexd@contoso.onmicrosoft.com'",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [   
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2016-03-15T08:42:10Z",
  "SentDateTime": "2016-03-15T08:42:10Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

创建一个**CreateForward**调用中添加评语或收件人转发邮件的草稿。 然后可以[更新](#UpdateMessages)[消息属性](..\api\complex-types-for-mail-contacts-calendar.md#MessageProperties)和[发送](#SendDraftMessages)草稿。

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/createforward
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要转发的邮件的 ID。|
|_正文参数_|
|注释|string|要包含的注释。 可以为空字符串。|
|ToRecipients|集合 （[收件人](..\api\complex-types-for-mail-contacts-calendar.md#ComplexTypes)）|收件人列表中。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8DmAAA=/createforward
Content-Type: application/json

{
  "ToRecipients":[
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
   ],
  "Comment": "Dana, just want to make sure you get this." 
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz7k6AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG\"",
  "Id": "AAMkAGE0Mz7k6AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AhG",
  "Categories": [],
  "CreatedDateTime": "2016-03-15T08:42:10Z",
  "LastModifiedDateTime": "2016-03-15T08:42:10Z",
  "Subject": "FW: Let's start a group",
  "BodyPreview": "Dana, just want to make sure you get this.\r\n________________________________\r\nFrom: Admin\r\nSent: Tuesday, March 15, 2016 6:47:54 AM\r\nTo: Fanny Downs; Randi Welch\r\nSubject: RE: Let's st",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEPAAA=",
  "From": null,
  "Sender": {
    "EmailAddress": {
      "Address": "'alexd@contoso.onmicrosoft.com'",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [   
    {
      "EmailAddress": {
        "Address":"danas@contoso.onmicrosoft.com",
        "Name":"Dana Swope"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0M3HbTkEU=",
  "ReceivedDateTime": "2016-03-15T08:42:10Z",
  "SentDateTime": "2016-03-15T08:42:10Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": true,
  "IsRead": true
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



 **响应类型**

草案转发[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)与**IsDraft**和预先设置适当的属性。

****


<a name="ForwardDirectlyClient"></a>
###<a name="forward-a-message-directly-client"></a>转发邮件直接 （客户端）

直接通过调用**ForwardAsync**和传递在注释和收件人转发的邮件。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
List<Recipient> recipients = new List<Recipient>();
recipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com"
    }
});
await outlookClient.Me.Messages[messageId].ForwardAsync("Interested?", recipients);
```

<!-- ENDSECTION -->

<a name="CreateDraftForwardClient"> </a>
###创建转发邮件草稿 （客户端）

通过调用**CreateForwardAsync**来创建转发邮件草稿。 然后，您可以[更新该草案](#UpdateMessagesClient)并[将其发送](#SendDraftClient)。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage forwardDraft = await outlookClient.Me.Messages[messageId].CreateForwardAsync();

// Get the ID of the draft Forward message.
string forwardMessageId = forwardDraft.Id;
```

<!-- ENDSECTION -->

**CreateForward**与**IsDraft**和其他适当的预填充的属性创建邮件草稿。

****

<a name="UpdateMessages"> </a>
##<a name="update-messages"></a>更新邮件

更改邮件的可写属性并保存更改。

REST API︰[更新消息 (REST)](#UpdateAMessage)

客户端库︰[更新的消息 （客户端）](#UpdateAMessageClient)

<a name="UpdateAMessage"></a>
###<a name="update-a-message-rest"></a>更新的消息 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_


更改在草稿或现有[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)的可写属性。 您指定的属性被更改。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/messages/{message_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要更新的消息 ID。|

指定一个或多个可写[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性请求主体中。


**示例请求**

```
PATCH https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz8S-AAA=
Content-Type: application/json

{
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "IsRead": true
}
```

**响应示例**

```
Status code: 200


{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8S-AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP\"",
  "Id": "AAMkAGE0Mz8S-AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "CreatedDateTime": "2014-10-17T17:12:15Z",
  "LastModifiedDateTime": "2014-10-19T03:24:35Z",
  "Subject": "Meeting notes from today",
  "BodyPreview": "See attached",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": true,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mip-qvhs=",
  "ConversationIndex": "AQHRh5tqrkAcds2kw==",
  "ReceivedDateTime": "2014-10-17T17:12:15Z",
  "SentDateTime": "2014-10-17T17:12:12Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/messages/{message_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要更新的消息 ID。|

指定一个或多个可写[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性请求主体中。

**示例请求**

```
PATCH https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8S-AAA=
Content-Type: application/json

{
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "IsRead": true
}
```

**响应示例**

```
Status code: 200


{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8S-AAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP\"",
  "Id": "AAMkAGE0Mz8S-AAA=",
  "ChangeKey": "CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIP",
  "Categories": [
    "Orange category",
    "Green category"
  ],
  "CreatedDateTime": "2014-10-17T17:12:15Z",
  "LastModifiedDateTime": "2014-10-19T03:24:35Z",
  "Subject": "Meeting notes from today",
  "BodyPreview": "See attached",
  "Body": {
    "ContentType": "HTML",
    "Content": "<html>\r\n...</html>\r\n"
  },
  "Importance": "Normal",
  "HasAttachments": true,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGE0Mip-qvhs=",
  "ReceivedDateTime": "2014-10-17T17:12:15Z",
  "SentDateTime": "2014-10-17T17:12:12Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/messages/{message_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要更新的消息 ID。|

指定一个或多个可写[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性请求主体中。

[!code-REST-i[mail_api_update_message_by_id](./_data/mail_api_update_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

更新的[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

****

<a name="UpdateAMessageClient"> </a>
###<a name="update-a-message-client"></a>更新的消息 （客户端）

更改消息上的可写属性并调用**UpdateAsync**来保存所做的更改。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage message = await outlookClient.Me.Messages[messageId].ExecuteAsync();
message.Body = new ItemBody
{
        Content = "I'm coming out a week earlier."
};
message.ToRecipients.Add(new Recipient
{
    EmailAddress = new EmailAddress
    {
        Address = "garthf@a830edad9050849NDA1.onmicrosoft.com"
    }
});
await message.UpdateAsync();
```

<!-- ENDSECTION -->

您可以定义多个更新客户端，发送请求所有次 （批它们） 通过使用以下模式︰
1. 调用`UpdateAsync(true)`为每个您想要更新的实体。 指定`true`注册客户端在本地更新但不将其发布到服务器。
2. 调用`outlookClient.Context.SaveChangesAsync()`将本地注册的所有更新。



****


<a name="DeleteMessages"> </a>
##<a name="delete-messages"></a>删除邮件

删除邮件。

**请注意**删除邮件时要小心。 已删除的内容可能无法恢复。
若要了解详细信息，请参阅[删除项目](http://msdn.microsoft.com/library/c81e3160-e12b-47e0-b3d6-4be28537f301%28Office.15%29.aspx)。

REST API︰[删除邮件 (REST)](#DeleteAMessage)

客户端库︰[删除邮件 （客户端）](#DeleteMessagesClient)

<a name="DeleteAMessage"></a>
###<a name="delete-a-message-rest"></a>删除邮件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]



```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages/{message_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要删除的消息的 ID。|

**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz8TBAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/messages/{message_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要删除的消息的 ID。|

**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8TBAAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]


```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/messages/{message_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要删除的消息的 ID。|

[!code-REST-i[mail_api_delete_message_by_id](./_data/mail_api_delete_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->




****

<a name="DeleteMessagesClient"> </a>
###<a name="delete-a-message-client"></a>删除邮件 （客户端）

通过调用**DeleteAsync**中删除邮件。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和[获得消息 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage message = await outlookClient.Me.Messages[messageId].ExecuteAsync();
await message.DeleteAsync();
```

<!-- ENDSECTION -->

****


<a name="MoveCopyMessages"> </a>
##<a name="move-or-copy-messages"></a>移动或复制邮件

您可以移动或复制到文件夹的邮件。

REST API︰[移动消息 (REST)](#MoveMessage) | [复制邮件 (REST)](#CopyMessage)

客户端库︰[移动或复制邮件 （客户端）](#MoveMessagesClient)

<a name="MoveMessage"> </a>
###<a name="move-a-message-rest"></a>移动消息 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

将邮件移动到文件夹中。 这会在目标文件夹中创建邮件的新副本。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/move
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|若要移动消息的 ID。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGI2TIy-AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGI2AAEJAAA="
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0MGz_vSAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
  "Id": "AAMkAGI2shBhAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGI2AAEJAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGWgitxag=",
  "ConversationIndex": "AQHRh6etrkAcds2kw==",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/move
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|若要移动消息的 ID。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2TIy-AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGI2AAEJAAA="
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0MGz_vSAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP\"",
  "Id": "AAMkAGI2shBhAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGI2AAEJAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGWgitxag=",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/move
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|若要移动消息的 ID。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|

[!code-REST-i[mail_api_move_message_by_id](./_data/mail_api_move_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

已移动的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

****


<a name="CopyMessage"> </a>
###<a name="copy-a-message-rest"></a>复制邮件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

将邮件复制到一个文件夹。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/copy
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要复制的邮件的 ID。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGI2TIy-AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8TDAAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIS\"",
  "Id": "AAMkAGI2T8DtAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "InternetMessageId": "SN2PR00M@SN2.namprd00.prod.outlook.com",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQAQAKjRc0YJSUBJpofjWgitxag=",
  "ConversationIndex": "AQHRh6sdrkAcds2kw==",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/copy
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要复制的邮件的 ID。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2TIy-AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGE0Mz8TDAAA=')",
  "@odata.etag": "W/\"CQAAABYAAAAmP1Ln1wcHRariNdTMGAO9AAAS0AIS\"",
  "Id": "AAMkAGI2T8DtAAA=",
  "ChangeKey": "CQAAABYAAACd9nJ/tVysQos2hTfspaWRAAADTJqP",
  "Categories": [],
  "CreatedDateTime": "2014-10-20T00:13:21Z",
  "LastModifiedDateTime": "2014-10-20T00:13:23Z",
  "Subject": "Contract Signing",
  "BodyPreview": "There will be a detailed legal review of Project Falcon once the contract is ready.",
  "Body": {
    "ContentType": "Text",
    "Content": "There will be a detailed legal review of Project Falcon once the contract is ready."
  },
  "Importance": "Normal",
  "HasAttachments": false,
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "From": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "Sender": {
    "EmailAddress": {
      "Address": "alexd@a830edad9050849NDA1.onmicrosoft.com",
      "Name": "Alex D"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Address": "katiej@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Katie Jordan"
      }
    },
    {
      "EmailAddress": {
        "Address": "garthf@a830edad9050849NDA1.onmicrosoft.com",
        "Name": "Garth Fort"
      }
    }
  ],
  "CcRecipients": [],
  "BccRecipients": [],
  "ReplyTo": [],
  "ConversationId": "AAQkAGI2NGVhZTVlLTI1OGMtNDI4My1iZmE5LTA5OGJiZGEzMTc0YQAQAKjRc0YJSUBJpofjWgitxag=",
  "ReceivedDateTime": "2014-10-20T00:13:21Z",
  "SentDateTime": "2014-10-20T00:13:21Z",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsDraft": false,
  "IsRead": true
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/copy
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|要复制的邮件的 ID。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


[!code-REST-i[mail_api_copy_message_by_id](./_data/mail_api_copy_message_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


**响应类型**

新[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)的副本。

****

<a name="MoveMessagesClient"> </a>
### <a name="move-or-copy-a-message-client"></a>移动或复制邮件 （客户端）

移动或复制邮件通过将目标文件夹 ID 传递给**MoveAsync**或**CopyAsync**的方法。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户](..\api\use-outlook-rest-api.md#GetClient)、[获得消息 ID](#GetMessagesClient)，而且[有目的文件夹 ID](#GetFoldersClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IMessage messageToMove = await outlookClient.Me.Messages[messageId].ExecuteAsync();
await messageToMove.MoveAsync("AAMkADE3N...");
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IMessage messageToCopy = await outlookClient.Me.Messages[messageId].ExecuteAsync();
await messageToCopy.CopyAsync("Inbox");
```

<!-- ENDSECTION -->

****

<a name="ManageFocusedInbox"></a>
##<a name="manage-focused-inbox"></a>管理重点的收件箱

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

重点收件箱，您可以查看重要的消息，在`Focused`的收件箱和收件箱中的邮件的其他选项卡`Other`选项卡。 分类系统最初组织收件箱邮件中的默认方式。 您可以更正，然后随时间通过用户界面或通过编程方式训练系统。 您使用的越多，系统可以更好地推断为重要的传入消息。

级别的编程专注于收件箱 REST API，致力于指定的用户的邮件，并支持为每个消息的**InferenceClassification**属性。 可能的值为`Focused`， `Other`，它指示是否用户认为该消息一样，分别更重要的是，并不太重要。 要更正并训练邮件分类系统，使用[修补程序操作上的**InferenceClassification**属性](#UpdateMessageClassificationBeta)在消息级别。 

专注于收件箱 REST API 还允许您创建重写。 由[InferenceClassificationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassificationOverrideResource)实例，每个重写是始终将来自特定发件人的邮件指定以一致的方式 （即，始终作为"焦点"或始终为"其他"），而不考虑任何以前学习方法的分类系统的指令。 您可以[创建](#CreateOverrideBeta)、[获取](#GetAllSenderOverridesBeta)、[更新](#UpdateOverrideBeta)和[删除](#DeleteOverrideBeta)指定的用户重写。 该用户的覆盖，如果有的话，都可以访问**InferenceClassification**导航属性，它是**InferenceClassificationOverride**实例的集合中。 替代允许用户更好地控制接收的邮件，分类和生成更高信任度的分类系统。

注意分类系统学习并应用分类只对传入的邮件在收件箱中。 其他文件夹中的邮件在默认情况下，"焦点"。 重写设置会影响将来邮件到达收件箱;重写并不修改任何文件夹包括收件箱中的现有邮件中的**InferenceClassification**属性。


**邮件分类系统的培训**

[更新邮件分类](#UpdateMessageClassificationBeta)


**使用重写每个发件人以一致的方式分类**

[创建发件人重写](#CreateOverrideBeta) | [获取所有用户重写](#GetAllSenderOverridesBeta) | [更新发件人重写](#UpdateOverrideBeta) | [删除发件人重写](#DeleteOverrideBeta) 


<a name="UpdateMessageClassificationBeta"></a>
###<a name="update-message-classification"></a>更新邮件分类

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

将指定的消息的**InferenceClassification**属性的更改。 如果邮件在收件箱中，用户将看到该消息下相应的`Focused`或`Other`选项卡。 这种修正还会训练未来的分类指定用户自定义的消息分类系统。 

```no-highlight
PATCH https://outlook.office.com/api/beta/me/messages('{message_id}')

PATCH https://outlook.office.com/api/beta/Users('{user_id}')/messages('{message_id}')
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|草稿信息发送的 ID。|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

更新的[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

**示例请求**

本示例更改将**InferenceClassification**属性设为`Other`的指定消息的已登录的用户。
```
PATCH https://outlook.office.com/api/beta/me/messages('AAMkADA1MTQBAAA=')

{
    "InferenceClassification": "Other"
}
```

**响应示例**

此处所示的响应对象显示更新的**InferenceClassification**属性，并将被截断为简洁起见。 实际的修补程序请求返回消息的所有属性。
```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTQBAAA=')",
    "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAffAsD\"",
    "Id": "AAMkADA1MTQBAAA=",
    "Importance": "Normal",
    "Sender": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Admin",
                "Address": "admin@adatum.onmicrosoft.com"
            }
        }
    ],
    "InferenceClassification": "Other"
}
```


<a name="CreateOverrideBeta"></a>
###<a name="create-an-override-for-a-sender"></a>创建发件人重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

创建发件人标识 SMTP 地址重写。 未来从消息的 SMTP 地址将一直归在重写中指定。

<a name="CreateOverrideNoteBeta"></a>

**请注意**

- 如果已存在具有相同 STMP 地址重写，然后的**ClassifyAs**和重写**名称**字段将更新与提供的值。
- 重写对邮箱支持的最大数目为 1000，基于唯一发件人的 SMTP 地址。
- POST 操作支持一次创建一个重写。 若要创建多个覆盖，您可以发送多个 POST 请求或[批次](..\api\batch-outlook-rest-requests.md)它们。


```no-highlight
POST https://outlook.office.com/api/beta/me/InferenceClassification/Overrides

POST https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|user_id|string|用户的电子邮件地址。 |

**响应类型**

新创建的[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)或更新后的**InferenceClassicationOverride**实例，如果一个具有相同 SMTP 地址已存在。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/InferenceClassification/Overrides

{
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```

**响应示例**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```


<a name="GetAllSenderOverridesBeta"></a>
###<a name="get-all-user-overrides"></a>获取所有用户重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

获取用户设置始终将来自特定发件人的邮件分类以特定的方式重写。

每个替代与发件人的 SMTP 地址相对应。 最初，用户没有任何重写。

```no-highlight
GET https://outlook.office.com/api/beta/me/InferenceClassification/Overrides

GET https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)实例的集合。
如果用户没有设置任何重写，则返回一个空集合。


**示例请求**

```
GET https://outlook.office.com/api/beta/me/InferenceClassification/Overrides
```

**响应示例**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/InferenceClassification/Overrides",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
            "ClassifyAs": "Focused",
            "SenderEmailAddress": {
                "Name": "Fanny Downs",
                "Address": "fannyd@adatum.onmicrosoft.com"
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
            "ClassifyAs": "Other",
            "SenderEmailAddress": {
                "Name": "Randi Welch",
                "Address": "randiw@adatum.onmicrosoft.com"
            }
        }
    ]
}
```


<a name="UpdateOverrideBeta"></a>
###<a name="update-an-override-for-a-sender"></a>发件人的更新重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

更改为指定重写**ClassifyAs**字段。 

修补程序不能用于更改[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)实例中的任何其他字段。 

如果重写用于发件人和发件人改变他/她的显示名称，可以[使用发布来强制更新到现有的重写中字段的名称](#CreateOverrideNoteBeta)。

如果重写用于发件人和发件人改变他/她的 SMTP 地址，[删除](#DeleteOverrideBeta)现有重写和[创建](#CreateOverrideBeta)一个新新的 SMTP 地址是"更新"重写此发件人的唯一办法。


```no-highlight
PATCH https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('{override_id}')

PATCH https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|override_id|string|要更新该重写的 ID。|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

更新后的[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)实例。


**示例请求**

下面的示例更改为已登录的用户重写。 重写为发件人的 SMTP 地址randiw@adatum.onmicrosoft.com,从更改`Other`到`Focused`。
```
PATCH https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')

{
    "ClassifyAs": "Focused"
}

```

**响应示例**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@adatum.onmicrosoft.com"
    }
}
```


<a name="DeleteOverrideBeta"></a>
###<a name="delete-a-sender-override"></a>删除发件人重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

删除重写由其 id。


```no-highlight
DELETE https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('{override_id}')

DELETE https://outlook.office.com/api/beta/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|override_id|string|草稿信息发送的 ID。|
|user_id|string|用户的电子邮件地址。 |


**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')
```

**响应示例**

```
Status code: 204 No Content
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

重点收件箱，您可以查看重要的消息，在`Focused`的收件箱和收件箱中的邮件的其他选项卡`Other`选项卡。 分类系统最初组织收件箱邮件中的默认方式。 您可以更正，然后随时间通过用户界面或通过编程方式训练系统。 您使用的越多，系统可以更好地推断为重要的传入消息。

级别的编程专注于收件箱 REST API，致力于指定的用户的邮件，并支持为每个消息的**InferenceClassification**属性。 可能的值为`Focused`， `Other`，它指示是否用户认为该消息一样，分别更重要的是，并不太重要。 要更正并训练邮件分类系统，使用[修补程序操作上的**InferenceClassification**属性](#UpdateMessageClassificationV2)在消息级别。 

专注于收件箱 REST API 还允许您创建重写。 由[InferenceClassificationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassificationOverrideResource)实例，每个重写是始终将来自特定发件人的邮件指定以一致的方式 （即，始终作为"焦点"或始终为"其他"），而不考虑任何以前学习方法的分类系统的指令。 您可以[创建](#CreateOverrideV2)、[获取](#GetAllSenderOverridesV2)、[更新](#UpdateOverrideV2)和[删除](#DeleteOverrideV2)指定的用户重写。 该用户的覆盖，如果有的话，都可以访问**InferenceClassification**导航属性，它是**InferenceClassificationOverride**实例的集合中。 替代允许用户更好地控制接收的邮件，分类和生成更高信任度的分类系统。

注意分类系统学习并应用分类只对传入的邮件在收件箱中。 其他文件夹中的邮件在默认情况下，"焦点"。 重写设置会影响将来邮件到达收件箱;重写并不修改任何文件夹包括收件箱中的现有邮件中的**InferenceClassification**属性。


**邮件分类系统的培训**

[更新邮件分类](#UpdateMessageClassificationV2)


**使用重写每个发件人以一致的方式分类**

[创建发件人重写](#CreateOverrideV2) | [获取所有用户重写](#GetAllSenderOverridesV2) | [更新发件人重写](#UpdateOverrideV2) | [删除发件人重写](#DeleteOverrideV2) 


<a name="UpdateMessageClassificationV2"></a>
###<a name="update-message-classification"></a>更新邮件分类

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

将指定的消息的**InferenceClassification**属性的更改。 如果邮件在收件箱中，用户将看到该消息下相应的`Focused`或`Other`选项卡。 这种修正还会训练未来的分类指定用户自定义的消息分类系统。 

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/messages('{message_id}')

PATCH https://outlook.office.com/api/v2.0/Users('{user_id}')/messages('{message_id}')
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|草稿信息发送的 ID。|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

更新的[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

**示例请求**

本示例更改将**InferenceClassification**属性设为`Other`的指定消息的已登录的用户。
```
PATCH https://outlook.office.com/api/v2.0/me/messages('AAMkADA1MTQBAAA=')

{
    "InferenceClassification": "Other"
}
```

**响应示例**

此处所示的响应对象显示更新的**InferenceClassification**属性，并将被截断为简洁起见。 实际的修补程序请求返回消息的所有属性。
```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/Messages('AAMkADA1MTQBAAA=')",
    "@odata.etag": "W/\"CQAAABYAAADX8oL1Wa7jQbcPAHouCzswAAAffAsD\"",
    "Id": "AAMkADA1MTQBAAA=",
    "Importance": "Normal",
    "Sender": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "From": {
        "EmailAddress": {
            "Name": "Fanny Downs",
            "Address": "fannyd@adatum.onmicrosoft.com"
        }
    },
    "ToRecipients": [
        {
            "EmailAddress": {
                "Name": "Admin",
                "Address": "admin@adatum.onmicrosoft.com"
            }
        }
    ],
    "InferenceClassification": "Other"
}
```


<a name="CreateOverrideV2"></a>
###<a name="create-an-override-for-a-sender"></a>创建发件人重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

创建发件人标识 SMTP 地址重写。 未来从消息的 SMTP 地址将一直归在重写中指定。

<a name="CreateOverrideNoteV2"></a>

**请注意**

- 如果已存在具有相同 STMP 地址重写，然后的**ClassifyAs**和重写**名称**字段将更新与提供的值。
- 重写对邮箱支持的最大数目为 1000，基于唯一发件人的 SMTP 地址。
- POST 操作支持一次创建一个重写。 若要创建多个覆盖，您可以发送多个 POST 请求或[批次](..\api\batch-outlook-rest-requests.md)它们。


```no-highlight
POST https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides

POST https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

新创建的[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)或更新后的**InferenceClassicationOverride**实例，如果一个具有相同 SMTP 地址已存在。


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides

{
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```

**响应示例**

```
Status code: 201 Created

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Fanny Downs",
        "Address": "fannyd@adatum.onmicrosoft.com"
    }
}
```


<a name="GetAllSenderOverridesV2"></a>
###<a name="get-all-user-overrides"></a>获取所有用户重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

获取用户设置始终将来自特定发件人的邮件分类以特定的方式重写。

每个替代与发件人的 SMTP 地址相对应。 最初，用户没有任何重写。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides

GET https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)实例的集合。
如果用户没有设置任何重写，则返回一个空集合。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides
```

**响应示例**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/InferenceClassification/Overrides",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf11a9b9')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf11a9b9",
            "ClassifyAs": "Focused",
            "SenderEmailAddress": {
                "Name": "Fanny Downs",
                "Address": "fannyd@adatum.onmicrosoft.com"
            }
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
            "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
            "ClassifyAs": "Other",
            "SenderEmailAddress": {
                "Name": "Randi Welch",
                "Address": "randiw@adatum.onmicrosoft.com"
            }
        }
    ]
}
```


<a name="UpdateOverrideV2"></a>
###<a name="update-an-override-for-a-sender"></a>发件人的更新重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

更改为指定重写**ClassifyAs**字段。 

修补程序不能用于更改[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)实例中的任何其他字段。 

如果重写用于发件人和发件人改变他/她的显示名称，可以[使用发布来强制更新到现有的重写中字段的名称](#CreateOverrideNoteV2)。

如果重写用于发件人和发件人改变他/她的 SMTP 地址，[删除](#DeleteOverrideV2)现有重写和[创建](#CreateOverrideV2)一个新新的 SMTP 地址是"更新"重写此发件人的唯一办法。


```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('{override_id}')

PATCH https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|override_id|string|要更新该重写的 ID。|
|user_id|string|用户的电子邮件地址。 |


**响应类型**

更新后的[InferenceClassicationOverride](..\api\complex-types-for-mail-contacts-calendar.md#InferenceClassicationOverrideResource)实例。


**示例请求**

下面的示例更改为已登录的用户重写。 重写为发件人的 SMTP 地址randiw@adatum.onmicrosoft.com从`Other`到`Focused`。
```
PATCH https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')

{
    "ClassifyAs": "Focused"
}

```

**响应示例**

```
Status code: 200 OK

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/InferenceClassification/Overrides/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('86b6ceaf-57f7-4278-97c4-4da0a97f6cdb@70559e59-b378-49ea-8e53-07a3a3d27f5b')/InferenceClassificationOverrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')",
    "Id": "98f5bdef-576a-404d-a2ea-07a3cf34af4r",
    "ClassifyAs": "Focused",
    "SenderEmailAddress": {
        "Name": "Randi Welch",
        "Address": "randiw@adatum.onmicrosoft.com"
    }
}
```


<a name="DeleteOverrideV2"></a>
###<a name="delete-a-sender-override"></a>删除发件人重写

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

删除重写由其 id。


```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('{override_id}')

DELETE https://outlook.office.com/api/v2.0/Users('{user_id}')/InferenceClassification/Overrides('{override_id}')
```

|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|override_id|string|草稿信息发送的 ID。|
|user_id|string|用户的电子邮件地址。 |


**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/InferenceClassification/Overrides('98f5bdef-576a-404d-a2ea-07a3cf34af4r')
```

**响应示例**

```
Status code: 204 No Content
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前在 2.0 版和测试版。 要了解更多信息，使用文章的右上角中的控件，然后选择上述版本之一。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="ManageMentions"></a>
##<a name="manage--mentions-preview"></a>管理@-Mentions（预览）

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

调用出收件人可以在邮件中获取收件人的注意是社会的一个常见操作。
[提到](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource)资源提供了轻量机制通知另一个收件人，或在邮件发件人获得通知。 

<!-- Comment out for Mentions API
Add this sentence when support for events is back in

**Mention** is also supported by 
[Event](..\api\complex-types-for-mail-contacts-calendar.md#EventResource).

-->

应用程序可以通过用户界面，让用户在邮件中插入提及，前面提及的与`@`(通常用于在其他应用程序，因此类似的方案一词@-mention).以编程方式，应用程序可以[创建](#CreateMentionInNewMessage)提及的通过将其添加到**中提到了**在同一个属性`POST`调用来创建邮件。 

应用程序可以让用户[查找](#GetAllMessagesMentionUser)是否已在其收件箱中的所有邮件通知他们。 用户可以在每个消息中提及的[查找详细信息](#GetDetailsEachMentionInMessage)。 它们还可以[删除](#DeleteMention)邮件中提到。



<a name="CreateMentionInNewMessage"></a>
**创建一封新邮件中提及**

[创建并发送新邮件的一部分提及](#CreateSendMention) | [创建的邮件草稿一部分提及](#CreateMentionInDraft)


**在邮件中得到信息提及**

[获取所有提及已登录的用户的邮件](#GetAllMessagesMentionUser) | [获得的每个消息中提到的详细信息](#GetDetailsEachMentionInMessage)


**删除邮件中提及**

[删除记录](#DeleteMention)


<a name="CreateSendMention"></a>
###<a name="create-and-send-mentions-as-part-of-a-new-message"></a>创建并发送新邮件的一部分提及

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_

创建并发送邮件提供在请求正文中包括的一个或多个[提到](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource)的实例的集合。

这将使用相同的[SendMail](#SendMessageOnTheFly)操作[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)资源;此外，包括**提及**作为**消息**正文参数的属性。


```no-highlight
POST https://outlook.office.com/api/beta/me/sendmail
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_正文参数_|
|Message|[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)|要发送的消息。|
|SavetoSentItems|布尔|指示是否将邮件保存在已发送邮件中。 默认值为**true**。 所需的才**假**。|

指定所需的**ToRecipients**属性、**中提到了**属性和请求主体中的任何可写[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性的**消息**参数。

而且，对于每提及中**提到**的属性，您必须指定**提到我们**和**创建者**属性。


**示例请求**

```
POST https://outlook.office.com/api/beta/me/sendmail
Content-Type: application/json

{
  "Message": {
    "Subject": "Project kickoff",
    "ToRecipients":[
      {
          "EmailAddress":{
          "Name":"Fanny Downs",
          "Address":"fannyd@contoso.onmicrosoft.com"
          }
      }
    ],
    "Mentions":[
      {
        "Mentioned":{
          "Name":"Dana Swope",
          "Address":"danas@contoso.onmicrosoft.com"
         },
        "CreatedBy": {
            "Name":"Randi Welch",
            "Address":"randiw@contoso.onmicrosoft.com"
        }
      }
    ]
  }
}
```

**响应示例**

```
Status code: 202 Accepted
```


<a name="CreateMentionInDraft"></a>
###<a name="create-mentions-as-part-of-a-message-draft"></a>邮件草稿中创建引用的公告

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

创建一个新邮件，其中包含一个或多个[提到](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource)的实例的集合的草案。 您可以创建任何文件夹和 （可选）[更新](#UpdateMessages)该草案之前[发送](#SendDraftMessages)它。 

这将使用相同的[POST](#CreateNewDraft)方法上的[信息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)资源;此外，您在请求正文中包括它**提到**的属性。

```no-highlight
POST https://outlook.office.com/api/beta/me/messages
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|目标文件夹 ID，或`Inbox`或`Drafts`的已知文件夹的名称。|

指定请求主体中的**提到**属性和任何可写的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)属性。

而且，对于每提及中**提到**的属性，您必须指定**提到我们**和**创建者**属性。

**响应类型**

草案的[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。

**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages
Content-Type: application/json

{
    "Subject": "Party planning",
    "ToRecipients":[
      {
          "EmailAddress":{
          "Name":"Fanny Downs",
          "Address":"fannyd@contoso.onmicrosoft.com"
          }
      }
    ],
    "Mentions":[
      {    
        "Mentioned":{
          "Name":"Dana Swope",
          "Address":"danas@contoso.onmicrosoft.com"
         },
        "CreatedBy": {
            "Name":"Randi Welch",
            "Address":"randiw@contoso.onmicrosoft.com"
        }
      }
    ]
}
```

**响应示例**

下图显示邮件创建的草稿。 注意︰ 此处所示的响应对象将被截断为简洁起见。 从实际调用将返回的所有属性。

```
Status code: 201 Created

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAW1fsAAAAA==')",
  "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAbYj7\"",
  "Id":"AQMkADJmMTUAAAW1fsAAAAA==",
  "Body":{
    "ContentType":"Text",
    "Content":""
  },
  "BodyPreview":"",
  "Sender":null,
  "From":null,
  "ToRecipients":[
    {
      "EmailAddress":{
        "Name":"Fanny Downs",
        "Address":"fannyd@contoso.onmicrosoft.com"
      }
    }
  ],
  "MentionsPreview":{
    "IsMentioned":false
  },
  "Mentions@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages('AQMkADJmMTUAAAW1fsAAAAA%3D%3D')/Mentions",
  "Mentions":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAW1fsAAAAA==')/Mentions('4577bba4-b063-4cea-9073-6f7ca815fcec')",
      "Id":"4577bba4-b063-4cea-9073-6f7ca815fcec",
      "Mentioned":{
        "Name":"Dana Swope",
        "Address":"danas@contoso.onmicrosoft.com",
        "ExternalId":"72137a84-1a8b-4b92-aa06-cca538e8616b"
      },
      "MentionText":null,
      "ClientReference":null,
      "CreatedBy":{
        "Name":"Randi Welch",
        "Address":"randiw@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "CreatedDateTime":"2016-07-22T02:22:44Z",
      "ServerCreatedDateTime":"2016-07-22T02:22:44.201Z",
      "DeepLink":null,
      "Application":null
    }
  ]
}
```


<a name="GetAllMessagesMentionUser"></a>
###<a name="get-all-messages-that-mention-the-signed-in-user"></a>获取所有提及已登录的用户的邮件

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

在已登录的用户的邮箱，或在指定的文件夹，包含[提及](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource)此用户得到的所有消息。

这将使用同一个[GET](#GetMessageCollection)方法可用[信息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)资源;此外，包括`$filter`查询**MentionsPreview**属性的参数。 

默认情况下，`GET /me/messages`调用不返回该**表述**的属性。 使用`$expand`查询参数的每个消息中提及的[查找详细信息](#GetDetailsEachMentionInMessage)。

注意︰ 请确保您实际调用适当编码查询参数字符串中的空格字符。

```no-highlight
GET https://outlook.office.com/api/beta/me/messages?$filter=MentionsPreview/IsMentioned eq true

GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/messages?$filter=MentionsPreview/IsMentioned eq true
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|目标文件夹 ID，或`Inbox`或`Drafts`的已知文件夹的名称。|


**响应类型**

请求的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)集合中。


**示例请求**

下面的示例中为那些提及用户筛选器已登录的用户邮箱中的所有邮件。 它使用`$select`在响应中返回的每个消息的属性子集。 它还包含 URL 编码的查询参数字符串中的空格字符。

```
GET https://outlook.office.com/api/beta/me/messages?$filter=MentionsPreview/IsMentioned%20eq%20true&$select=Subject,Sender,ReceivedDateTime,MentionsPreview
```

**响应示例**

该响应包含 2 提及已登录的用户的邮件。

```
Status code: 200 OK

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages(Subject,Sender,ReceivedDateTime,MentionsPreview)",
  "value":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')",
      "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAAATI\"",
      "Id":"AQMkADJmMTUAAAgVZAAAA",
      "ReceivedDateTime":"2016-07-21T07:40:21Z",
      "Subject":"Re: Start planning soon",
      "Sender":{
        "EmailAddress":{
          "Name":"Randi Welch",
          "Address":"randiw@contoso.onmicrosoft.com"
        }
      },
      "MentionsPreview":{
        "IsMentioned":true
      }
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAjwVAAAA')",
      "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAAEGj\"",
      "Id":"AQMkADJmMTUAAAjwVAAAA",
      "ReceivedDateTime":"2016-07-21T07:40:20Z",
      "Subject":"Re: Start planning soon",
      "Sender":{
        "EmailAddress":{
          "Name":"Randi Welch",
          "Address":"randiw@contoso.onmicrosoft.com"
        }
      },
      "MentionsPreview":{
        "IsMentioned":true
      }
    }
  ]
}
```


<a name="GetDetailsEachMentionInMessage"></a>
###<a name="get-details-of-each-mention-in-a-message"></a>在邮件中获得每个记录的详细的信息

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

扩展的消息中得到一条消息，[说](..\api\complex-types-for-mail-contacts-calendar.md#MentionResource)每个细节。

这将使用同一个[GET](#GetMessage)方法可用[信息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)资源;此外，包括`$expand`查询上**提到了**导航属性的参数。

```no-highlight
GET https://outlook.office.com/api/beta/me/messages('{message_id}')?$expand=Mentions
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|请求消息的 ID。|


**响应类型**

请求的[邮件](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)。


**示例请求**

下面的示例中，在已登录的用户是 Dana Swope。 该示例演示在 Dana 的邮箱指定消息中获取所有有关记录的详细信息。

```
GET https://outlook.office.com/api/beta/me/messages('AQMkADJmMTUAAAgVZAAAA')?$expand=Mentions 
```

**响应示例**

下图显示请求的消息中**提到**的属性包括每个记录的详细信息。 此邮件包含 2 提及，一个为已登录的用户 Dana，另一个用于 Randi 图案来工作。

注意︰ 此处所示的响应对象将被截断为简洁起见，将精力集中在与支持**提及**相关的属性。

```
Status code: 200 OK

{
  "@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages/$entity",
  "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')",
  "@odata.etag":"W/\"CQAAABYAAAAPFhK2FclcRbABBJhCde8iAAAAAATI\"",
  "Id":"AQMkADJmMTUAAAgVZAAAA",
  "Subject":"Start planning soon",
  "Body":{
    "ContentType":"HTML",
    "Content":"<html><head></head><body"><p><a href=\"mailto:danas@contoso.onmicrosoft.com\">@Dana Swope</a>,<a href=\"mailto:randiw@contoso.onmicrosoft.com\">@Randi Welch</a>, forgot to mention, I will be away&nbsp;this weekend. I can start on Monday though.</p></body></html>"
  },
  "BodyPreview":"@Dana Swope<mailto:danas@contoso.onmicrosoft.com>, @Randi Welch, forgot to mention, I will be away this weekend. I can start on Monday though.",
  "Sender":{
    "EmailAddress":{
      "Name":"Fanny Downs",
      "Address":"fannyd@contoso.onmicrosoft.com"
    }
  },
  "From":{
    "EmailAddress":{
      "Name":"Fanny Downs",
      "Address":"fannyd@contoso.onmicrosoft.com"
    }
  },
  "ToRecipients":[
    {
      "EmailAddress":{
        "Name":"Dana Swope",
        "Address":"danas@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress":{
        "Name":"Randi Welch",
        "Address":"randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients":[
  ],
  "BccRecipients":[
  ],
  "MentionsPreview":{
    "IsMentioned":true
  },
  "Mentions@odata.context":"https://outlook.office.com/api/beta/$metadata#Me/Messages('AQMkADJmMTUAAAgVZAAAA')/Mentions",
  "Mentions":[
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')/Mentions('138f4c0a-1130-4776-b780-bf79d73abb3f')",
      "Id":"138f4c0a-1130-4776-b780-bf79d73abb3f",
      "Mentioned":{
        "Name":"Dana Swope",
        "Address":"danas@contoso.onmicrosoft.com",
        "ExternalId":"72137a84-1a8b-4b92-aa06-cca538e8616b"
      },
      "MentionText":null,
      "ClientReference":null,
      "CreatedBy":{
        "Name":"Fanny Downs",
        "Address":"fannyd@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "CreatedDateTime":"2016-07-21T07:40:20.152Z",
      "ServerCreatedDateTime":"2016-07-21T07:40:20.152Z",
      "DeepLink":null,
      "Application":null
    },
    {
      "@odata.id":"https://outlook.office.com/api/beta/Users('266efe5a-0fd7-4edd-877b-b2d1e561f193@ae01a323-3934-4475-a32d-af1274312bb0')/Messages('AQMkADJmMTUAAAgVZAAAA')/Mentions('7b94df1a-0086-482a-b0da-e62fae12f983')",
      "Id":"7b94df1a-0086-482a-b0da-e62fae12f983",
      "Mentioned":{
        "Name":"Randi Welch",
        "Address":"randiw@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "MentionText":null,
      "ClientReference":null,
      "CreatedBy":{
        "Name":"Fanny Downs",
        "Address":"fannyd@contoso.onmicrosoft.com",
        "ExternalId":"266efe5a-0fd7-4edd-877b-b2d1e561f193"
      },
      "CreatedDateTime":"2016-07-21T07:40:20.158Z",
      "ServerCreatedDateTime":"2016-07-21T07:40:20.158Z",
      "DeepLink":null,
      "Application":null
    }
  ]
}

```


<a name="DeleteMention"></a>
###<a name="delete-a-mention"></a>删除记录

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

删除已登录的用户邮箱中的指定消息中提及的指定。 

```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages('{message_id}')/mentions('{mention_id}')
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|mention_id|string|若要删除提及的 ID。|
|message_id|string|其中包含提及的消息的 ID。|


**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/messages('AAMkADA1MTk1ZAAAKXBQCAAA=')/mentions('7b94df1a-0086-482a-b0da-e62fae12f983')
```

**响应示例**

```
Status code: 204 No Content
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

此功能目前处于测试阶段。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前处于测试阶段。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****


<a name="Unsubscribe"></a>
##<a name="unsubscribe-preview"></a>取消订阅 （预览）

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.send_
- _wl.imap_

提交代表已登录的用户的电子邮件请求取消订阅电子邮件通讯组列表。 使用中的信息`List-Unsubscribe`头。

```no-highlight
POST https://outlook.office.com/api/beta/me/messages('{message_id}')/unsubscribe
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|草稿信息发送的 ID。|


邮件发件人可以使用邮件列表以用户友好的方式通过包括收件人的选项选择退出。 他们可以通过指定实现`List-Unsubscribe`中遵循[RFC 2369](http://www.faqs.org/rfcs/rfc2369.html)每封邮件的标头。

**请注意**要**取消订阅**操作，指定发件人必须特别要说明的是，`mailto:`和不基于 URL 的取消订阅信息。

设置该标题会设置为[消息](../api/complex-types-for-mail-contacts-calendar.md#MessageResource)实例的**UnsubscribeEnabled**属性`true`，并将**UnsubscribeData**属性为标头数据。

如果一条消息的**UnsubscribeEnabled**属性是`true`，可用于**取消订阅**操作取消类似未来邮件用户作为托管邮件发件人。 

成功**取消订阅**操作将邮件移动到已删除邮件文件夹中。 未来的邮件分发用户实际排除由发件人管理。



**示例请求**

```
POST https://outlook.office.com/api/beta/me/messages('AAMkADA1MTk1ZAAAKXBQCAAA=')/unsubscribe
```

**响应示例**

```
Status code: 202 Accepted
```
 


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

此功能目前处于测试阶段。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前处于测试阶段。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="GetAutoReplySettings"></a>
##<a name="get-auto-reply-settings"></a>获取自动答复设置

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

自动答复允许他们向您发送电子邮件时自动通知消息的人。 例如，您可以通知时不可用，无法对其进行响应。

自动答复的组成部分 （由[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta)） 的用户的邮箱设置，因为您可以通过获取所有邮箱设置，其中包括自动答复设置，或都获取专门的自动答复设置来查看自动答复设置。

您可以使用`Prefer: outlook.timezone`HTTP 标头，指定首选的时区来显示**ScheduledStartDateTime**和**ScheduledEndDateTime**的值。

REST API︰[获取所有邮箱设置](#GetAllMailboxSettingsBeta) | [都获得专门的自动答复设置](#GetOnlyAutoReplySettingsBeta)


<a name="GetAllMailboxSettingsBeta"></a>
###<a name="get-all-mailbox-settings"></a>获取所有邮箱设置

_**所需的最小范围**︰ https://outlook.office.com/mailboxsettings.readwrite_

获取已登录的用户的主邮箱的设置。


```no-highlight
GET https://outlook.office.com/api/beta/me/MailboxSettings
```

 **响应类型**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta)。


**示例请求**

```
GET https://outlook.office.com/api/beta/me/MailboxSettings
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "All",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-14T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
        "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}
```


<a name="GetOnlyAutoReplySettingsBeta"></a>
###<a name="get-automatic-reply-settings"></a>获取自动答复设置

_**所需的最小范围**︰ https://outlook.office.com/mailboxsettings.readwrite_

获取已登录的用户邮箱的自动答复设置。


```no-highlight
GET https://outlook.office.com/api/beta/me/MailboxSettings/AutomaticRepliesSetting
```

 **响应类型**

[AutomaticRepliesSetting](../api/complex-types-for-mail-contacts-calendar.md#AutomaticRepliesSettingBeta)。


**示例请求**

```
GET https://outlook.office.com/api/beta/me/MailboxSettings/AutomaticRepliesSetting
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings/AutomaticRepliesSetting",
    "Status": "AlwaysEnabled",
    "ExternalAudience": "None",
    "ScheduledStartDateTime": {
        "DateTime": "2016-03-19T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "ScheduledEndDateTime": {
        "DateTime": "2016-03-20T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

自动答复允许他们向您发送电子邮件时自动通知消息的人。 例如，您可以通知时不可用，无法对其进行响应。

自动答复的组成部分 （由[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2)） 的用户的邮箱设置，因为您可以通过获取所有邮箱设置，其中包括自动答复设置，或都获取专门的自动答复设置来查看自动答复设置。

您可以使用`Prefer: outlook.timezone`HTTP 标头，指定首选的时区来显示**ScheduledStartDateTime**和**ScheduledEndDateTime**的值。

REST API︰[获取所有邮箱设置](#GetAllMailboxSettingsV2) | [都获得专门的自动答复设置](#GetOnlyAutoReplySettingsV2)


<a name="GetAllMailboxSettingsV2"></a>
###<a name="get-all-mailbox-settings"></a>获取所有邮箱设置

_**所需的最小范围**︰ https://outlook.office.com/mailboxsettings.readwrite_

获取已登录的用户的主邮箱的设置。


```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailboxSettings
```

 **响应类型**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2)。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/MailboxSettings
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "All",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-14T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T07:00:00.0000000",
            "TimeZone": "UTC"
        },
        "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
        "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}
```


<a name="GetOnlyAutoReplySettingsV2"></a>
###<a name="get-automatic-reply-settings"></a>获取自动答复设置

_**所需的最小范围**︰ https://outlook.office.com/mailboxsettings.readwrite_

获取已登录的用户邮箱的自动答复设置。


```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailboxSettings/AutomaticRepliesSetting
```

 **响应类型**

[AutomaticRepliesSetting](../api/complex-types-for-mail-contacts-calendar.md#AutomaticRepliesSettingV2)。


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/MailboxSettings/AutomaticRepliesSetting
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings/AutomaticRepliesSetting",
    "Status": "AlwaysEnabled",
    "ExternalAudience": "None",
    "ScheduledStartDateTime": {
        "DateTime": "2016-03-19T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "ScheduledEndDateTime": {
        "DateTime": "2016-03-20T02:00:00.0000000",
        "TimeZone": "UTC"
    },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前在 2.0 版和测试版。 要了解更多信息，使用文章的右上角中的控件，然后选择上述版本之一。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****



<a name = "UpdateAutoReplySettings"></a>
##<a name="update-auto-reply-settings"></a>更新自动答复设置

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**所需的最小范围**︰ https://outlook.office.com/mailboxsettings.readwrite_


自动答复是用户的邮箱设置 （由[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta)） 的一部分。 您可以启用、 配置或通过更新相应的邮箱设置禁用自动答复。 

**请注意**您不能创建或删除邮箱中的任何设置。

```no-highlight
PATCH https://outlook.office.com/api/beta/me/MailboxSettings
```

**响应类型**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsBeta)。


**示例请求**

在获取自动答复设置的[前面的示例中](#GetOnlyAutoReplySettingsBeta)下, 一个示例将更改**状态**从`AlwaysEnabled`到`Scheduled`，并对不同的日期范围的开始和结束日期。



```
PATCH https://outlook.office.com/api/beta/me/MailboxSettings
Content-Type: application/json

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ScheduledStartDateTime": {
          "DateTime": "2016-03-20T18:00:00.0000000",
          "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
          "DateTime": "2016-03-28T18:00:00.0000000",
          "TimeZone": "UTC"
        }
    }
}
```



**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "None",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-20T02:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T02:00:00.0000000",
            "TimeZone": "UTC"
        },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}


```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

_**所需的最小范围**︰ https://outlook.office.com/mailboxsettings.readwrite_


自动答复是用户的邮箱设置 （由[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2)） 的一部分。 您可以启用、 配置或通过更新相应的邮箱设置禁用自动答复。 

**请注意**您不能创建或删除邮箱中的任何设置。

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/MailboxSettings
```

**响应类型**

[MailboxSettings](../api/complex-types-for-mail-contacts-calendar.md#MailboxSettingsV2)。


**示例请求**

在获取自动答复设置的[前面的示例中](#GetOnlyAutoReplySettingsV2)下, 一个示例将更改**状态**从`AlwaysEnabled`到`Scheduled`，并对不同的日期范围的开始和结束日期。



```
PATCH https://outlook.office.com/api/v2.0/me/MailboxSettings
Content-Type: application/json

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ScheduledStartDateTime": {
          "DateTime": "2016-03-20T18:00:00.0000000",
          "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
          "DateTime": "2016-03-28T18:00:00.0000000",
          "TimeZone": "UTC"
        }
    }
}
```



**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailboxSettings",
    "AutomaticRepliesSetting": {
        "Status": "Scheduled",
        "ExternalAudience": "None",
        "ScheduledStartDateTime": {
            "DateTime": "2016-03-20T02:00:00.0000000",
            "TimeZone": "UTC"
        },
        "ScheduledEndDateTime": {
            "DateTime": "2016-03-28T02:00:00.0000000",
            "TimeZone": "UTC"
        },
    "InternalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "ExternalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    },
    "TimeZone": "Pacific Standard Time",
    "Language":{
        "Locale":"en-US",
        "DisplayName":"English (United States)"
    }
}


```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前测试版和 2.0 版中。 要了解更多信息，使用文章的右上角中的控件，然后选择上述版本之一。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="GetMailTips"></a>
##<a name="get-mailtips-preview"></a>获取邮件提醒 （预览）

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**所需的最小作用域**_︰ 下列情况之一︰

- _https://outlook.office.com/mail.read.my_
- _https://outlook.office.com/mail.read.shared_

向已登录的用户获取可用一个或多个收件人的邮件提醒。 请注意，这作为执行**GetMailTips**操作 POST 操作。


```no-highlight
POST https://outlook.office.com/api/beta/me/GetMailTips
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_正文参数_|
|EmailAddresses|Collection(String)|收件人收到的邮件提醒的 SMTP 地址的集合。|
|MailTipsOptions|[MailTipsType](../api/complex-types-for-mail-contacts-calendar.md#MailTipsType)|获取指定的收件人的邮件提醒种类。|


**响应类型**

[邮件提醒](../api/complex-types-for-mail-contacts-calendar.md#MailTips)的集合。


**示例请求**

下面的示例获取指定的收件人，任何自动答复设置和邮箱满状态的邮件提醒。


```
POST https://outlook.office.com/api/beta/me/GetMailTips
Content-Type: application/json

{
    "EmailAddresses": [
        "danas@contoso.onmicrosoft.com", 
        "fannyd@contoso.onmicrosoft.com"
    ],
    "MailTipsOptions": "AutomaticReplies, MailboxFullStatus"
}
```



**响应示例**

```
Status code: 200 OK

{
    "@odata.context":"https://outlook.office.com/api/beta/$metadata#Collection(Microsoft.OutlookServices.MailTips)",
    "value":[
        {
            "EmailAddress":{
                "Name":"",
                "Address":"danas@contoso.onmicrosoft.com"
            },
            "AutomaticReplies":{
                "Message":"<style type=\"text/css\" style=\"\">\r\n<!--\r\np\r\n\t{margin-top:0;\r\n\tmargin-bottom:0}\r\n-->\r\n</style>\r\n<div dir=\"ltr\">\r\n<div id=\"x_divtagdefaultwrapper\" style=\"font-size:12pt; color:#000000; background-color:#FFFFFF; font-family:Calibri,Arial,Helvetica,sans-serif\">\r\n<p>Hi, I am on vacation right now. I'll get back to you after I return.<br>\r\n</p>\r\n</div>\r\n</div>",
                "MessageLanguage":{
                    "Locale":"en-US",
                    "DisplayName":"English (United States)"
                }
            },
            "MailboxFull":false
        },
        {
            "EmailAddress":{
                "Name":"",
                "Address":"fannyd@contoso.onmicrosoft.com"
            },
            "AutomaticReplies":{
                "Message":""
            },
            "MailboxFull":false
        }
    ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

此功能目前处于测试阶段。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前处于测试阶段。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****


<a name="GetAttachments"> </a>
##<a name="get-attachments"></a>获取附件

您可以获取附件集合或获取附件。 附件可以是文件 （例如， 

REST API︰[获取附件集合 (REST)](#GetAttachmentCollection) | [获取附件 (REST)](#GetAttachment)

客户端库︰[获取一个或多个消息附件 （客户端）](#GetAttachmentsClient)


<a name="GetAttachmentCollection"> </a>
###<a name="get-an-attachment-collection-rest"></a>获取附件集合 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

获得特定邮件的附件。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
GET https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|

**请注意**默认情况下，每个附件在响应中的包括其对应于该附件类型的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

**响应类型**

它可以是类型[FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)， [ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)或[ReferenceAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)的附件集合。


**示例请求和响应**

下面的示例演示如何使用**$select**来指定响应中返回每个文件附件的**名称**属性。 请参阅示例响应中[获取附件 (REST)](#GetAttachment)如果您不使用**$select**将返回附件的属性的完整列表。

**示例请求**

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGI2THVSAAA=/attachments?$select=Name
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments(Name)",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
            "Id": "AAMkAGI2j4kShdM=",
            "Name": "minutes.docx"
        }
    ]
}
```

下面的示例演示获取唯一附件即 Outlook 邮件项。 该响应包括附件 ID，它也是连接的消息的 ID。

```
GET https://outlook.office.com/api/beta/me/messages('AAMkADFiNTPAAA=')/attachments

Content-Type: application/json

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkADFiNTPAAA%3D')/Attachments",
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
      "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-20075df800e5@1717622f-1d94-4d0c-9d74-f907ad6677b4')/Messages('AAMkADFiNTPAAA=')/Attachments('AAMkADFiNTAUhhYuYi0=')",
      "Id": "AAMkADFiNTAUhhYuYi0=",
      "Name": "How to retrieve item attachment using Outlook REST API",
      "ContentType": message/rfc822,
      "Size": 71094,
      "IsInline": false,
      "LastModifiedDateTime": "2015-09-24T05:57:59Z",
    }
  ]
}
```




[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|

**请注意**默认情况下，每个附件在响应中的包括其对应于该附件类型的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

它可以是[FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)类型的附件集合。


**示例请求和响应**

下面的示例演示如何使用**$select**来指定响应中返回每个文件附件的**名称**属性。 请参阅示例响应中[获取附件 (REST)](#GetAttachment)如果您不使用**$select**将返回附件的属性的完整列表。

**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2THVSAAA=/attachments?$select=Name
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments(Name)",
    "value": [
        {
            "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
            "Id": "AAMkAGI2j4kShdM=",
            "Name": "minutes.docx"
        }
    ]
}
```

下面的示例演示获取唯一附件即 Outlook 邮件项。 该响应包括附件 ID，它也是连接的消息的 ID。

```
GET https://outlook.office.com/api/v2.0/me/messages('AAMkADFiNTPAAA=')/attachments

Content-Type: application/json

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkADFiNTPAAA%3D')/Attachments",
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
      "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-20075df800e5@1717622f-1d94-4d0c-9d74-f907ad6677b4')/Messages('AAMkADFiNTPAAA=')/Attachments('AAMkADFiNTAUhhYuYi0=')",
      "Id": "AAMkADFiNTAUhhYuYi0=",
      "Name": "How to retrieve item attachment using Outlook REST API",
      "ContentType": message/rfc822,
      "Size": 71094,
      "IsInline": false,
      "LastModifiedDateTime": "2015-09-24T05:57:59Z",
    }
  ]
}
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|

**请注意**默认情况下，每个附件在响应中的包括其对应于该附件类型的所有属性。 使用**$select**可以指定只有最佳性能所需的属性。 始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。


**响应类型**

它可以是[FileAttachment](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[ItemAttachment](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)类型的附件集合。


**示例请求和响应**

下面的示例演示如何使用**$select**来指定响应中返回每个文件附件的**名称**属性。 请参阅示例响应中[获取附件 (REST)](#GetAttachment)如果您不使用**$select**将返回附件的属性的完整列表。

[!code-REST-i[mail_api_get_attachments](./_data/mail_api_get_attachments.json)]


下面的示例演示获取唯一附件即 Outlook 邮件项。 该响应包括附件 ID，它也是连接的消息的 ID。

```
GET https://outlook.office.com/api/v1.0/me/messages('AAMkADFiNTPAAA=')/attachments

Content-Type: application/json

{
  "@odata.context": "https://outlook.office.com/api/v1.0/$metadata#Me/Messages('AAMkADFiNTPAAA%3D')/Attachments",
  "value": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
      "@odata.id": "https://outlook.office.com/api/v1.0/Users('ddfcd489-628b-40d7-b48b-20075df800e5@1717622f-1d94-4d0c-9d74-f907ad6677b4')/Messages('AAMkADFiNTPAAA=')/Attachments('AAMkADFiNTAUhhYuYi0=')",
      "Id": "AAMkADFiNTAUhhYuYi0=",
      "Name": "How to retrieve item attachment using Outlook REST API",
      "ContentType": message/rfc822,
      "Size": 71094,
      "IsInline": false,
      "DateTimeLastModified": "2015-09-24T05:57:59Z",
    }
  ]
}
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****


<a name="GetAttachment"> </a>
###<a name="get-an-attachment-rest"></a>获取附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

获得特定邮件的附件。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/messages/{message_id}/attachments/{attachment_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|attachment_id|string|附件 id。|

**请注意**默认情况下，该响应包括所有附件的属性。 使用**$select**可以指定只有最佳性能所需的属性。 有关示例，请参阅[获取附件集合 (REST)](#GetAttachmentCollection) 。  
始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

**响应类型**

请求的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)、[项附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)或[引用附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)。


**示例请求 （附件）**

下面的示例获取附加到特定邮件的文件。

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGI2THVSAAA=/attachments/AAMkAGI2j4kShdM=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
    "Id": "AAMkAGI2j4kShdM=",
    "LastModifiedDateTime": "2014-10-20T00:41:52Z",
    "Name": "minutes.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11585,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQDCAAA4KQAAAAA="
}
```

**示例请求 （参考附件）**

下面的示例获取参考附件的邮件。

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGE1Mbs88AADUv0uFAAA=/attachments/AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADUv0uFAAA%3D')/attachments/$entity",
  "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
  "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=",
  "LastModifiedDateTime": "2016-03-12T06:04:38Z",
  "Name": "Koala picture",
  "ContentType": null,
  "Size": 382,
  "IsInline": false,
  "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
  "ProviderType": "OneDriveBusiness",
  "ThumbnailUrl": null,
  "PreviewUrl": null,
  "Permission": "Edit",
  "IsFolder": false
}
```


**示例请求 ($expand 附件)**

下面的示例获取并展开所有 3 个参照附件嵌入邮件属性。

```
GET https://outlook.office.com/api/beta/me/messages/AAMkAGE1Mbs88AADUv0uFAAA=/?$expand=attachments
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages/$entity",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZsPav\"",
  "Id": "AAMkAGE1Mbs88AADUv0uFAAA=",
  "CreatedDateTime": "2016-03-08T01:01:57Z",
  "LastModifiedDateTime": "2016-03-12T06:18:54Z",
  "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZsPav",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-08T01:01:57Z",
  "SentDateTime": "2016-03-08T01:01:51Z",
  "HasAttachments": true,
  "InternetMessageId": "<SN2SR0101MB00299F0D7D22EE5D380104ED84B20@SN2SR0101MB0029.namsdf01.sdf.exchangelabs.com>",
  "Subject": "RE: New year activity",
  "Body": {
    "ContentType": "html",
    "Content": "<html>\r\n<<body>Let's gather to celebrate the new year! </body>\r\n</html>\r\n"
  },
  "BodyPreview": "What about the tulips?\r\n________________________________\r\nFrom: Dana Swope <danas@contoso.onmicrosoft.com>\r\nSent: Monday, March 7, 2016 10:51:39 PM\r\nTo: Dana Swope; Culinary Expert Group\r\nSubject: RE: New year activity\r\n\r\nLet's gather to celebrate the new year! ",
  "Importance": "Normal",
  "ParentFolderId": "AQMkAGE1MQN7j5uzzwAAAIBDAAAAA==",
  "Sender": {
    "EmailAddress": {
      "Name": "Dana Swope",
      "Address": "danas@contoso.onmicrosoft.com"
    }
  },
  "From": {
    "EmailAddress": {
      "Name": "Dana Swope",
      "Address": "danas@contoso.onmicrosoft.com"
    }
  },
  "ToRecipients": [
    {
      "EmailAddress": {
        "Name": "Dana Swope",
        "Address": "danas@contoso.onmicrosoft.com"
      }
    },
    {
      "EmailAddress": {
        "Name": "Culinary Expert Group",
        "Address": "Chefs@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkAGE1MMM2SaRFsKgx7BKVfig=",
  "ConversationIndex": "AQHRaThgdSG4wzZJpEWwqDHsEpV+KJ9OtWGUgAAkYLI=",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": false,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADUv0uFAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "InferenceClassification": "Focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "FlagStatus": "NotFlagged" },
  "Attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADUv0uFAAA%3D')/attachments",
  "Attachments": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAL53d0u3BKBJmCxKVxZKBZ8=",
      "LastModifiedDateTime": "2016-03-12T05:54:31Z",
      "Name": "Personal pictures",
      "ContentType": null,
      "Size": 362,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics",
      "ProviderType": "OneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": true
    },
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=",
      "LastModifiedDateTime": "2016-03-12T06:04:38Z",
      "Name": "Koala picture",
      "ContentType": null,
      "Size": 382,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
      "ProviderType": "OneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    },
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAO3wkFiM3KlCpn81m8qS1W0=",
      "LastModifiedDateTime": "2016-03-12T06:18:54Z",
      "Name": "Hydrangea picture",
      "ContentType": null,
      "Size": 412,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
      "ProviderType": "OneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    }
  ]
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments/{attachment_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|attachment_id|string|附件 id。|

**请注意**默认情况下，该响应包括所有附件的属性。 使用**$select**可以指定只有最佳性能所需的属性。 有关示例，请参阅[获取附件集合 (REST)](#GetAttachmentCollection) 。  
始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

 **响应类型**

请求的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)的[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/messages/AAMkAGI2THVSAAA=/attachments/AAMkAGI2j4kShdM=
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/Messages('AAMkAGI2THVSAAA%3D')/Attachments/$entity",
    "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/Messages('AAMkAGI2THVSAAA=')/Attachments('AAMkAGI2j4kShdM=')",
    "Id": "AAMkAGI2j4kShdM=",
    "LastModifiedDateTime": "2014-10-20T00:41:52Z",
    "Name": "minutes.docx",
    "ContentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
    "Size": 11585,
    "IsInline": false,
    "ContentId": null,
    "ContentLocation": null,
    "ContentBytes": "UEsDBBQABgAIAAAAIQDCAAA4KQAAAAA="
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments/{attachment_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|attachment_id|string|附件 id。|

**请注意**默认情况下，该响应包括所有附件的属性。 使用**$select**可以指定只有最佳性能所需的属性。 有关示例，请参阅[获取附件集合 (REST)](#GetAttachmentCollection) 。  
始终返回的**Id**属性。 筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

 **响应类型**

请求的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)的[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。


[!code-REST-i[mail_api_get_attachment_by_id](./_data/mail_api_get_attachment_by_id.json)]



[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****

<a name="GetAttachmentsClient"> </a>
###<a name="get-one-or-more-message-attachments-client"></a>获取一个或多个消息附件 （客户端）

通过调用**附件**属性获取邮件上的附件。 若要获得特定附件，作为**附件**的索引指定附件 ID
集合或使用**GetById**方法。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


**请注意**附件集合支持**选择**、**排序**，并**执行**查询表达式。


本示例将调用方法[创建 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。 .NET 代码假定您已[收到的邮件 ID](#GetMessagesClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Mail" -->

<!--tested-->
```cs-i
var outlookClient = await CreateOutlookClientAsync("Mail");
var messages = await outlookClient.Me.Folders["Inbox"].Messages
  .Where(m => m.HasAttachments == true)
  .Expand(m => m.Attachments)
  .Take(10)
  .ExecuteAsync();

foreach (var message in messages.CurrentPage)
{
  var attachments = message.Attachments.CurrentPage;
  System.Diagnostics.Debug.WriteLine("Message '{0}' contains '{1}' attachment(s).",
    message.Subject,
    attachments.Count);

  foreach (var attachment in attachments)
  {
    System.Diagnostics.Debug.WriteLine("*    '{0}' ({1} KB)",
      attachment.Name,
      attachment.Size);
  }
}

```
```javascript-i
outlookClient.me.folders.getFolder('Inbox').messages.getMessages().filter('HasAttachments eq true').fetchAll(10).then(function (result) {
    result.forEach(function (message) {
        message.attachments.getAttachments().fetchAll(100).then(function (attachmentResult) {
            console.log('Message "' + message.subject + '" contains ' + attachmentResult.length + ' attachment(s)');
            attachmentResult.forEach(function (attachment) {
                console.log('*    "' + attachment.name + '" (' + attachment.size + ' KB)');
            });
        });
    }, function (error) {
        console.log(error);
    });
}, function (error) {
    console.log(error);
});
```

<!-- ENDSECTION -->

****

<a name="CreateAttachments"> </a>
##<a name="create-attachments"></a>创建附件
您可以创建一个文件附件或邮件[创建项附件](#CreateItemAttachment)。

REST API︰[创建一个文件附件 (REST)](#CreateFileAttachment) | [创建一个项目附件 (REST)](#CreateItemAttachment) | 
[创建一个引用附件 (REST)](#CreateReferenceAttachment)



<a name="CreateFileAttachment"></a>
###<a name="create-a-file-attachment-rest"></a>创建一个文件附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

将添加到邮件的文件附件。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|_正文参数_|
|@odata.type|string|`#Microsoft.OutlookServices.FileAttachment`|
|名称|string|附件的名称。|
|ContentBytes|二进制文件|要附加的文件。|

在请求正文中指定的**名称**和**ContentBytes**参数和任何可写的[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)的属性。


<!--comment out until I get a working request body
[!code-REST-i[mail_api_create_file_attachment](./_data/mail_api_create_file_attachment.json)]

-->

 **响应类型**

新[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)。

****


<a name="CreateItemAttachment"></a>
###<a name="create-an-item-attachment-rest"></a>创建项附件 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

项目将附件添加到邮件。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]


```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments
```

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|_正文参数_|
|@odata.type|string|```#Microsoft.OutlookServices.ItemAttachment```|
|名称|string|附件的名称。|
|项目|一个[消息](..\api\complex-types-for-mail-contacts-calendar.md#MessageResource)或[事件](..\api\complex-types-for-mail-contacts-calendar.md#EventResource)的实体。|若要将附加项。|

指定的**名称**和**项**的参数和任何可写[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)属性请求主体中。

<!--comment out until I get a working request body
[!code-REST-i[mail_api_create_file_attachment](./_data/mail_api_create_file_attachment.json)]

-->

 **响应类型**

新[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

<!--
<a name="AddAttachments"> </a>
## Add attachments

Add a **FileAttachment** or an **ItemAttachment** to a message.

Updating attachments is not supported. Instead, delete the existing attachment and add a new one with updated values.

### Add file attachments

Add a file attachment to a message by getting the file and calling **AddAttachmentAsync**.

This example assumes you already [got the Outlook Services client](..\api\use-outlook-rest-api.md#GetClient) and [got the message ID](#GetMessages).



```cs
    FileAttachment newFileAttachment = new FileAttachment
    {
        ContentBytes = System.IO.File.ReadAllBytes(@"C:\Attachments\capture.png"),
        Name = "capture.png"
    };
    await outlookClient.Me.Messages[messageId].Attachments.AddAttachmentAsync(newFileAttachment);
```



### Add item attachments

Add message attachment to a message by getting the message and calling **AddAttachmentAsync**.

This example assumes you already [got the Outlook Services client](..\api\use-outlook-rest-api.md#GetClient) and [got the message ID](#GetMessages) of the message to add the attachment to and the message to attach.



```cs

    IMessage messageToAttach = await outlookClient.Me.Messages[messageId].ExecuteAsync();
    ItemAttachment newItemAttachment = new ItemAttachment
    {
        Item = (Message)messageToAttach
    };
    await outlookClient.Me.Messages[messageId].Attachments.AddAttachmentAsync(newItemAttachment);
```
-->

****

<a name="CreateReferenceAttachment"></a>


###<a name="create-a-reference-attachment-preview-rest"></a>创建一个引用附件 （预览） (REST)

<!-- ==================================== Start beta content ====================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

添加到邮件中引用附件。

```no-highlight
POST https://outlook.office.com/api/beta/me/messages/{message_id}/attachments
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|String|消息 id。|
|_正文参数_|
|@odata.type|String|```#Microsoft.OutlookServices.ReferenceAttachment```|
|Name|字符串|附件的显示名称。 必需。|
|SourceUrl|String | 若要获取附件内容的 URL。 如果这是一个文件夹的 URL，然后在 Outlook 或 web 上的 Outlook 中正确显示的文件夹设置**IsFolder**为 true。 必需。|

指定的**名称**和**SourceUrl**参数和任何可写的[引用附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)属性请求主体中。



**响应类型**

请[参考附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)。


**示例请求**

下面的示例将现有邮件引用附件。 附件是一个链接到 OneDrive 上的文件进行业务。

```
POST https://outlook.office.com/api/beta/me/messages/AAMkAGE1Mbs88AADUv0uFAAA=/attachments
Content-Type: application/json

{ 
    "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment", 
    "Name": "Koala picture", 
    "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg", 
    "ProviderType": "oneDriveBusiness", 
    "Permission": "Edit", 
    "IsFolder": "False" 
} 
```


**响应示例**

```
Status code: 201 Created

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADUv0uFAAA%3D')/attachments/$entity",
  "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
  "Id": "AAMkAGE1Mbs88AADUv0uFAAABEgAQAPSg72tgf7hJp0PICVGCc0g=",
  "LastModifiedDateTime": "2016-03-12T06:04:38Z",
  "Name": "Koala picture",
  "ContentType": null,
  "Size": 382,
  "IsInline": false,
  "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/koala.jpg",
  "ProviderType": "oneDriveBusiness",
  "ThumbnailUrl": null,
  "PreviewUrl": null,
  "Permission": "edit",
  "IsFolder": false
}
```


**示例请求**

下面的示例创建邮件草稿作为同一个调用中添加引用附件。 附件是一个链接到 OneDrive 上的文件进行业务。

```
POST https://outlook.office.com/api/beta/me/messages
Content-Type: application/json

{
    "Subject": "Plan for dinner",
    "Body": {
      "ContentType": "HTML",
      "Content": "Office anniversary is coming soon!"
    },
    "ToRecipients": [
      {
        "EmailAddress": {
          "Address": "randiw@contoso.onmicrosoft.com"
        }
      }
    ],
    "Attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment", 
        "Name": "Hydrangea picture", 
        "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg", 
        "ProviderType": "oneDriveBusiness", 
        "Permission": "Edit", 
        "IsFolder": "False" 
      }
    ]
}
```


**响应示例**

```
Status code: 201 Created

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages/$entity",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZ8qi1\"",
  "Id": "AAMkAGE1Mbs88AADZ0CU9AAA=",
  "CreatedDateTime": "2016-03-12T09:04:54Z",
  "LastModifiedDateTime": "2016-03-12T09:04:54Z",
  "ChangeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AADZ8qi1",
  "Categories": [ ],
  "ReceivedDateTime": "2016-03-12T09:04:54Z",
  "SentDateTime": "2016-03-12T09:04:54Z",
  "HasAttachments": true,
  "InternetMessageId": "<BL2SR0101MB00188944566BDECE6EDE57F384B60@BL2SR0101MB0018.namsdf01.sdf.exchangelabs.com>",
  "Subject": "Plan for dinner",
  "Body": {
    "ContentType": "html",
    "Content": "<html>\r\n<body>\r\nOffice anniversary is coming soon!\r\n</body>\r\n</html>\r\n"
  },
  "BodyPreview": "Office anniversary is coming soon!",
  "Importance": "normal",
  "ParentFolderId": "AQMkAGE1MQN7j5uzzwAAAIBDwAAAA==",
  "Sender": null,
  "From": null,
  "ToRecipients": [
    {
      "EmailAddress": {
      "Name": "Randi Welch",
      "address": "randiw@contoso.onmicrosoft.com"
      }
    }
  ],
  "CcRecipients": [ ],
  "BccRecipients": [ ],
  "ReplyTo": [ ],
  "ConversationId": "AAQkAGE1MMAAQAJk0cqqggzpKtIHErqyDkcU=",
  "ConversationIndex": "AQHRfD4+mTRyqqCDOkq0gcSurIORxQ==",
  "IsDeliveryReceiptRequested": false,
  "IsReadReceiptRequested": false,
  "IsRead": true,
  "IsDraft": true,
  "WebLink": "https://outlook.office.com/owa/?ItemID=AAMkAGE1Mbs88AADZ0CU9AAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "InferenceClassification": "focused",
  "UnsubscribeData": [ ],
  "UnsubscribeEnabled": false,
  "Flag": { "flagStatus": "notFlagged" },
  "Attachments@odata.context": "https://outlook.office.com/api/beta/$metadata#users('ddfcd489-628b-40d7-b48b-57002df800e5')/messages('AAMkAGE1Mbs88AADZ0CU9AAA%3D')/attachments",
  "Attachments": [
    {
      "@odata.type": "#Microsoft.OutlookServices.ReferenceAttachment",
      "Id": "AAMkAGE1Mbs88AADZ0CU9AAABEgAQAGe4H1iqXwtLsrCCLLkDxqo=",
      "LastModifiedDateTime": null,
      "Name": "Hydrangea picture",
      "ContentType": null,
      "Size": 0,
      "IsInline": false,
      "SourceUrl": "https://contoso-my.spoppe.com/personal/danas_contoso_onmicrosoft_com/Documents/Pics/hydrangea.jpg",
      "ProviderType": "oneDriveBusiness",
      "ThumbnailUrl": null,
      "PreviewUrl": null,
      "Permission": "edit",
      "IsFolder": false
    }
  ]
}
```

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End beta content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前仅是测试版。 若要了解详细信息，请在右上角的文章，选择**测试版**中使用控件。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



****


<a name="DeleteAttachments"> </a>
##<a name="delete-attachments"></a>删除附件

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

删除指定的邮件附件。 附件可以是[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)、[项附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)或[引用附件](..\api\complex-types-for-mail-contacts-calendar.md#ReferenceAttachmentResource)。

```no-highlight
DELETE https://outlook.office.com/api/beta/me/messages/{message_id}/attachments/{attachment_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|attachment_id|string|附件 id。|


**示例请求**

```
DELETE https://outlook.office.com/api/beta/me/messages/AAMkAGE0Mz8S-AAA=/attachments/AAMkAGE0Mg67gL7o=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

删除指定的邮件附件。 附件可以是[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/messages/{message_id}/attachments/{attachment_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|attachment_id|string|附件 id。|


**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/messages/AAMkAGE0Mz8S-AAA=/attachments/AAMkAGE0Mg67gL7o=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

删除指定的邮件附件。 附件可以是[文件附件](..\api\complex-types-for-mail-contacts-calendar.md#FileAttachmentResource)或[项目附件](..\api\complex-types-for-mail-contacts-calendar.md#ItemAttachmentResource)。

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/messages/{message_id}/attachments/{attachment_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|message_id|string|消息 id。|
|attachment_id|string|附件 id。|

[!code-REST-i[mail_api_delete_attachment](./_data/mail_api_delete_attachment.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->



<!--
<a name="DeleteAttachments"> </a>
## Delete attachments

You can delete an attachment by calling **DeleteAsync** on a **FileAttachment** or **ItemAttachment**.


This example assumes you already [got the Outlook Services client](..\api\use-outlook-rest-api.md#GetClient) and [got the message ID](#GetMessages).



```cs

    //No ToFileAttachment or Attachment.ExecuteAsync
    Attachment attachmentToDelete = await outlookClient.Me.Messages[messageId].
        Attachments[attachmentId].ToFileAttachment().ExecuteAsync();
    await attachmentToDelete.DeleteAsync();

    IMessage message = await outlookClient.Me.Messages[messageId].ExecuteAsync();
    IPagedCollection<IAttachment> attachmentsResults = message.Attachments;
    List<IAttachment> attachmentsPage = attachmentsResults.CurrentPage.ToList();

    // Delete the first attachment in the collection.
    Attachment attachmentToDelete = (Attachment)attachmentsPage[0];
    await attachmentToDelete.DeleteAsync();
```
-->



****


<a name="GetFolders"> </a>
##<a name="get-folders"></a>获取文件夹

您可以获取文件夹集合或获得用户的邮箱中的文件夹。

REST API︰[获取文件夹集合 (REST)](#GetFolderCollection) | [获取文件夹 (REST)](#GetFolder)

客户端库︰[获取文件夹或文件夹集合 （客户端）](#GetFoldersClient)


<a name="GetFolderCollection"> </a>
###<a name="get-a-folder-collection-rest"></a>获取文件夹集合 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_



<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

获取已登录的用户邮箱中所有邮件文件夹 (`.../me/MailFolders`)，或都获取指定文件夹下的文件夹集合。

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders
GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/childfolders
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称，如果您收到特定文件夹中的文件夹。|


**示例请求**

```
GET https://outlook.office.com/api/beta/me/MailFolders
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEKAAA=')",
            "Id": "AAMkAGI2AAEKAAA=",
            "DisplayName": "Deleted Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 1,
            "WellKnownName": "deleteditems"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEPAAA=')",
            "Id": "AAMkAGI2AAEPAAA=",
            "DisplayName": "Drafts",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0,
            "WellKnownName": "drafts"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
            "Id": "AAMkAGI2AAEMAAA=",
            "DisplayName": "Inbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 6,
            "TotalItemCount": 6,
            "WellKnownName": "inbox"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEeAAA=')",
            "Id": "AAMkAGI2AAEeAAA=",
            "DisplayName": "Junk Email",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0,
            "WellKnownName": "junkemail"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAELAAA=')",
            "Id": "AAMkAGI2AAELAAA=",
            "DisplayName": "Outbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0,
            "WellKnownName": "outbox"
        },
        {
            "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEJAAA=')",
            "Id": "AAMkAGI2AAEJAAA=",
            "DisplayName": "Sent Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 3,
            "WellKnownName": "sentitems"
        }
    ]
}

```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

获取在已登录的用户的根文件夹下的文件夹集合 (`.../me/MailFolders`)，或在指定的文件夹下。 您可以使用`.../me/MailFolders`以获取顶级文件夹集合并导航到另一个文件夹的快捷方式。

```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders
GET https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/childfolders
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称，如果您收到特定文件夹中的文件夹。|

**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/MailFolders
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders",
    "value": [
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEKAAA=')",
            "Id": "AAMkAGI2AAEKAAA=",
            "DisplayName": "Deleted Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 1
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEPAAA=')",
            "Id": "AAMkAGI2AAEPAAA=",
            "DisplayName": "Drafts",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
            "Id": "AAMkAGI2AAEMAAA=",
            "DisplayName": "Inbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 6,
            "TotalItemCount": 6
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEeAAA=')",
            "Id": "AAMkAGI2AAEeAAA=",
            "DisplayName": "Junk Email",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAELAAA=')",
            "Id": "AAMkAGI2AAELAAA=",
            "DisplayName": "Outbox",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 0
        },
        {
            "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEJAAA=')",
            "Id": "AAMkAGI2AAEJAAA=",
            "DisplayName": "Sent Items",
            "ParentFolderId": "AAMkAGI2AAEIAAA=",
            "ChildFolderCount": 0,
            "UnreadItemCount": 0,
            "TotalItemCount": 3
        }
    ]
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

获取在已登录的用户的根文件夹下的文件夹集合 (`.../me/folders`)，或在指定的文件夹下。 您可以使用`.../me/folders`以获取顶级文件夹集合并导航到另一个文件夹的快捷方式。

```no-highlight
GET https://outlook.office.com/api/v1.0/me/folders
GET https://outlook.office.com/api/v1.0/me/folders/{folder_id}/childfolders
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称，如果您收到特定文件夹中的文件夹。|

[!code-REST-i[mail_api_get_folders](./_data/mail_api_get_folders.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

请求的[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)集合中。

****


<a name="GetFolder"> </a>
###<a name="get-a-folder-rest"></a>获取文件夹 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

获取文件夹 id。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders/{folder_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
GET https://outlook.office.com/api/beta/me/MailFolders/inbox
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
    "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
    "Id": "AAMkAGI2AAEMAAA=",
    "DisplayName": "Inbox",
    "ParentFolderId": "AAMkAGI2AAEIAAA=",
    "ChildFolderCount": 0,
    "UnreadItemCount": 6,
    "TotalItemCount": 6,
    "WellKnownName": "inbox"
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
GET https://outlook.office.com/api/v2.0/me/MailFolders/inbox
```

**响应示例**

```
Status code: 200

{
    "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
    "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGI2AAEMAAA=')",
    "Id": "AAMkAGI2AAEMAAA=",
    "DisplayName": "Inbox",
    "ParentFolderId": "AAMkAGI2AAEIAAA=",
    "ChildFolderCount": 0,
    "UnreadItemCount": 6,
    "TotalItemCount": 6
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
GET https://outlook.office.com/api/v1.0/me/folders/{folder_id}
```

**请注意**筛选、 排序和分页参数请参见[OData 查询参数](..\api\complex-types-for-mail-contacts-calendar.md#OdataQueryParams)。

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|

[!code-REST-i[mail_api_get_folder_by_id](./_data/mail_api_get_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

所请求的[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)。

****

<a name="GetFoldersClient"> </a>
###<a name="get-a-folder-or-folder-collection-client"></a>获取文件夹或文件夹集合 （客户端）

通过获取邮箱中的顶级文件夹`Me.Folders`快捷键属性。 若要从特定文件夹获取文件夹，使用的**ChildFolders**属性。
可用于以下的已知文件夹名称而不是 ID 对应的文件夹︰ `Inbox`， `SentItems`， `Drafts`， `DeletedItems`。

示例︰`outlookClient.Me.Folders["Drafts"].ChildFolders.ExecuteAsync()`


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


若要获得特定的文件夹，指定为**文件夹**集合的索引的文件夹 ID，或使用**GetById**方法。

**请注意**文件夹集合支持**选择**、**排序**，并**执行**查询表达式。

本示例将调用方法[获取 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" data-resources="OutlookServices.Mail" -->

<!--tested-->
```cs-i
var outlookClient = await CreateOutlookClientAsync("Mail");
var mailFolders = await outlookClient.Me.Folders
  .Take(10)
  .ExecuteAsync();

foreach(var mailFolder in mailFolders.CurrentPage)
{
  System.Diagnostics.Debug.WriteLine("Mail folder '{0}'.", mailFolder.DisplayName);
}

```
```javascript-i
outlookClient.me.folders.getFolders().fetchAll(100).then(function (result) {
    result.forEach(function (folder) {
        console.log('Folder "' + folder.displayName + '"');
    });
}, function (error) {
    console.log(error);
});
```

<!-- ENDSECTION -->


****

<a name="SynchronizeFolders"></a>
##<a name="synchronize-folder-hierarchy"></a>同步文件夹层次结构

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

您可以获取邮箱中所有文件夹的简单表格。 同步邮件文件夹层次结构之后，请求此类别。

|**终结点**|**类别文件夹**|
|:-----|:-----|
| 我 / MailFolders | 邮件文件夹 |

您可以仅同步每个文件夹类别的最高级别。 例如，您可以请求_Me / MailFolders_但不是_Me/MailFolders('inbox')_。

检索所有的文件夹层次结构中的完全同步和增量同步，以检索所有自上次完全同步后已更改的文件夹，同步支持。 

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_

```no-highlight
GET https://outlook.office.com/api/beta/me/MailFolders
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|更喜欢|odata.trackchanges|指示请求的同步请求。|
|_正文参数_|
|odata.deltaLink|string|一个标记，它指示上一次同步文件夹层次结构。|

如果有以下查询参数- `$filter`， `$orderby`， `$search`， `$top` -包含在请求中，它们将被忽略。

**响应类型**

在请求的类别文件夹简单列表。

[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->


<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

您可以获取邮箱中所有文件夹的简单表格。 同步邮件文件夹层次结构之后，请求此类别。

|**终结点**|**类别文件夹**|
|:-----|:-----|
| 我 / MailFolders | 邮件文件夹 |

您可以仅同步每个文件夹类别的最高级别。 例如，您可以请求_Me / MailFolders_但不是_Me/MailFolders('inbox')_。

检索所有的文件夹层次结构中的完全同步和增量同步，以检索所有自上次完全同步后已更改的文件夹，同步支持。 


_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.read_
- _wl.imap_


```no-highlight
GET https://outlook.office.com/api/v2.0/me/MailFolders
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_标头参数_|
|更喜欢|odata.trackchanges|指示请求的同步请求。|
|_正文参数_|
|odata.deltaLink|string|一个标记，它指示上一次同步文件夹层次结构。|

如果有以下查询参数- `$filter`， `$orderby`， `$search`， `$top` -包含在请求中，它们将被忽略。

**响应类型**

在请求的类别文件夹简单列表。

[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->


<!-- ==================================== Start v1 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

此功能目前在 2.0 版和测试版。 要了解更多信息，使用文章的右上角中的控件，然后选择上述版本之一。

[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

****

<a name="CreateFolders"> </a>
##<a name="create-folders"></a>创建文件夹

将新文件夹添加到文件夹集合。

REST API︰[创建文件夹 (REST)](#CreateAFolder)

客户端库︰[创建文件夹 （客户端）](#CreateFoldersClient)

<a name="CreateAFolder"> </a>
###<a name="create-a-folder-rest"></a>创建一个文件夹 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

在**显示名称**中指定的名称创建一个子文件夹。 **显示名称**是[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)的只写属性。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/childfolders
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DisplayName|string|文件夹的显示名称。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/MailFolders/inbox/childfolders
Content-Type: application/json

{
  "DisplayName": "Company"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders('inbox')/ChildFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Company",
  "ChildFolderCount": 0,
  "UnreadItemCount": 2,
  "TotalItemCount": 27,
  "WellKnownName": ""
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/childfolders
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DisplayName|string|文件夹的显示名称。|

**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/MailFolders/inbox/childfolders
Content-Type: application/json

{
  "DisplayName": "Company"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders('inbox')/ChildFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Company",
  "ChildFolderCount": 0,
  "UnreadItemCount": 2,
  "TotalItemCount": 27
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/childfolders
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DisplayName|string|文件夹的显示名称。|

[!code-REST-i[mail_api_create_folder](./_data/mail_api_create_folder.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

新的[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)中。

**备注**

不能创建一个顶级文件夹。 您只能添加到文件夹`childfolders`终结点。

****

<a name="CreateFoldersClient"> </a>
###<a name="create-a-folder-client"></a>创建一个文件夹 （客户端）

创建一个**文件夹**并将其传递给**AddFolderAsync**方法对目标文件夹的**ChildFolders**集合。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[获得了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)和父文件夹的[文件夹 ID 了](#GetFolders)。


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
Folder newFolder = new Folder
{
    DisplayName = "Private"
};
await outlookClient.Me.Folders["Inbox"].ChildFolders.AddFolderAsync(newFolder);

// Get the ID of the new folder.
string folderId = newFolder.Id;
```

<!-- ENDSECTION -->


****


<a name="UpdateFolders"> </a>
##<a name="update-folders"></a>更新文件夹

更改文件夹的名称。

REST API︰[更新文件夹 (REST)](#UpdateAFolder)

客户端库︰[更新文件夹 （客户端）](#UpdateFoldersClient)

<a name="UpdateAFolder"> </a>
###<a name="update-a-folder-rest"></a>更新文件夹 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

更改为在**显示名称**中指定的文件夹名称。 名称是一个[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)的只写属性。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
PATCH https://outlook.office.com/api/beta/me/MailFolders/{folder_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DisplayName|string|文件夹的新的显示名称。|


**示例请求**

```
PATCH https://outlook.office.com/api/beta/me/MailFolders/AAMkAGE0Mz-l_AAA=
Content-Type: application/json

{
  "DisplayName": "Business"
}
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38,
  "WellKnownName": ""
}

```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DisplayName|string|文件夹的新的显示名称。|


**示例请求**

```
PATCH https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=
Content-Type: application/json

{
  "DisplayName": "Business"
}
```

**响应示例**

```
Status code: 200

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38
}

```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
PATCH https://outlook.office.com/api/v1.0/me/folders/{folder_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DisplayName|string|文件夹的新的显示名称。|

[!code-REST-i[mail_api_update_folder_by_id](./_data/mail_api_update_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

已更新的[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)中。

****

<a name="UpdateFoldersClient"> </a>
###<a name="update-a-folder-client"></a>更新文件夹 （客户端）

更改文件夹的名称。 **显示名称**是文件夹的只写属性。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户](..\api\use-outlook-rest-api.md#GetClient)，[有的文件夹 ID](#GetFoldersClient)。


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
folder.DisplayName = "Personal";
await folder.UpdateAsync();

// Get the updated property.
string updatedName = folder.DisplayName;
```

<!-- ENDSECTION -->

您可以定义多个更新客户端，发送请求所有次 （批它们） 通过使用以下模式︰
1. 调用`UpdateAsync(true)`为每个您想要更新的实体。 指定`true`注册客户端在本地更新但不将其发布到服务器。
2. 调用`outlookClient.Context.SaveChangesAsync()`将本地注册的所有更新。

****


<a name="DeleteFolders"> </a>
##<a name="delete-folders"></a>删除文件夹

删除某个文件夹及其所有内容。

**请注意**删除文件夹时，则要小心。 已删除的内容可能无法恢复。
若要了解详细信息，请参阅[删除项目](http://msdn.microsoft.com/library/c81e3160-e12b-47e0-b3d6-4be28537f301%28Office.15%29.aspx)。

REST API︰[删除文件夹 (REST)](#DeleteAFolder)

客户端库︰[删除文件夹 （客户端）](#DeleteFoldersClient)

<a name="DeleteAFolder"> </a>
###<a name="delete-a-folder-rest"></a>删除文件夹 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

在**folder_id**中指定的文件夹中删除。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
DELETE https://outlook.office.com/api/beta/me/MailFolders/{folder_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
DELETE https://outlook.office.com/api/BETA/me/MailFolders/AAMkAGE0Mz-l_AAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
DELETE https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
DELETE https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=
```

**响应示例**

```
Status code: 204
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
DELETE https://outlook.office.com/api/v1.0/me/folders/{folder_id}
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|

[!code-REST-i[mail_api_delete_folder_by_id](./_data/mail_api_delete_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


****

<a name="DeleteFoldersClient"> </a>
###<a name="delete-a-folder-client"></a>删除文件夹 （客户端）

删除由其 ID 和调用**DeleteAsync**文件夹。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


此示例假定您已经[有了 Outlook 服务客户](..\api\use-outlook-rest-api.md#GetClient)，[有的文件夹 ID](#GetFolders)。


<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
await folder.DeleteAsync();
```

<!-- ENDSECTION -->

****

<a name="MoveCopyFolders"> </a>
##<a name="move-or-copy-folders"></a>移动或复制文件夹
您可以移动或复制到其他文件夹的文件夹。

REST API︰[移动文件夹 (REST)](#MoveFolders) | [复制文件夹 (REST)](#CopyFolders)

客户端库︰[移动或复制的文件夹 （客户端）](#MoveFoldersClient)

<a name="MoveFolders"> </a>
###<a name="move-a-folder-rest"></a>移动文件夹 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

使用**Move**方法，文件夹和其内容移动到另一个文件夹。

<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/move
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/MailFolders/AAMkAGE0Mz-l_AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGE0MyxQ9AAA="
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MyxQ9AAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38,
  "WellKnownName": ""
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

```no-highlight
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/move
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=/move
Content-Type: application/json

{
  "DestinationId": "AAMkAGE0MyxQ9AAA="
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-l_AAA=')",
  "Id": "AAMkAGE0Mz-l_AAA=",
  "ParentFolderId": "AAMkAGE0MyxQ9AAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/move
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|

[!code-REST-i[mail_api_move_folder_by_id](./_data/mail_api_move_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->


 **响应类型**

移动该[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)。

****


<a name="CopyFolders"> </a>
###<a name="copy-a-folder-rest"></a>复制文件夹 (REST)

_**所需的最小作用域**︰ 下列情况之一︰_
- _https://outlook.office.com/mail.readwrite_
- _wl.imap_

通过使用**复制**方法，文件夹及其内容复制到另一个文件夹。


<!-- ==================================== Start beta content ==================================================== -->

[!INCLUDE [BEGIN Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

```no-highlight
POST https://outlook.office.com/api/beta/me/MailFolders/{folder_id}/copy
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


**示例请求**

```
POST https://outlook.office.com/api/beta/me/MailFolders/AAMkAGE0Mz-l_AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/beta/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/beta/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-mAAAA=')",
  "Id": "AAMkAGE0Mz-mAAAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38,
  "WellKnownName": ""
}
```


[!INCLUDE [END Outlook beta section](../includes/controls/outlookrestapibetasection.html)]

<!-- ==================================== End BETA content ====================================================== -->



<!-- ==================================== Start v2 content ====================================================== -->

[!INCLUDE [BEGIN Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]


**示例请求**


```no-highlight
POST https://outlook.office.com/api/v2.0/me/MailFolders/{folder_id}/copy
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|


```
POST https://outlook.office.com/api/v2.0/me/MailFolders/AAMkAGE0Mz-l_AAA=/copy
Content-Type: application/json

{
  "DestinationId": "inbox"
}
```

**响应示例**

```
Status code: 201

{
  "@odata.context": "https://outlook.office.com/api/v2.0/$metadata#Me/MailFolders/$entity",
  "@odata.id": "https://outlook.office.com/api/v2.0/Users('ddfcd489-628b-40d7-b48b-57002df800e5@1717622f-1d94-4d0c-9d74-709fad664b77')/MailFolders('AAMkAGE0Mz-mAAAA=')",
  "Id": "AAMkAGE0Mz-mAAAA=",
  "ParentFolderId": "AAMkAGE0MAAEMAAA=",
  "DisplayName": "Business",
  "ChildFolderCount": 0,
  "UnreadItemCount": 4,
  "TotalItemCount": 38
}
```


[!INCLUDE [END Outlook v2 section](../includes/controls/outlookrestapiv2section.html)]

<!-- ==================================== End v2 content ======================================================== -->



<!-- ==================================== Start v1 content ====================================================== -->


[!INCLUDE [BEGIN Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

```no-highlight
POST https://outlook.office.com/api/v1.0/me/folders/{folder_id}/copy
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|folder_id|string|文件夹 ID 或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|
|_正文参数_|
|DestinationId|string|目标文件夹 ID，或`Inbox`， `Drafts`， `SentItems`，或`DeletedItems`的已知文件夹的名称。|

[!code-REST-i[mail_api_copy_folder_by_id](./_data/mail_api_copy_folder_by_id.json)]


[!INCLUDE [END Outlook v1 section](../includes/controls/outlookrestapiv1section.html)]

<!-- ==================================== End v1 content ======================================================== -->

**响应类型**

[文件夹](..\api\complex-types-for-mail-contacts-calendar.md#FolderResource)的新副本。

****

<a name="MoveFoldersClient"> </a>
###<a name="move-or-copy-a-folder-client"></a>移动或复制的文件夹 （客户端）

移动或复制文件夹通过将目标文件夹 ID 传递给**MoveAsync**或**CopyAsync**的方法。


**关注**如果您正在访问 Outlook.com 的邮箱数据，不使用客户端库并直接调用 REST API。


本示例假定您已经[有了 Outlook 服务客户端](..\api\use-outlook-rest-api.md#GetClient)并且要移动的文件夹和目标文件夹的[文件夹 ID 了](#GetFoldersClient)。

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

<!--tested-->
```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
await folder.MoveAsync("AAMkADE3N...");
```

<!-- ENDSECTION -->

<!-- BEGINSECTION class="tabbedCodeSnippets" -->

```cs
IFolder folder = await outlookClient.Me.Folders[folderId].ExecuteAsync();
await folder.CopyAsync("Inbox");
```

<!-- ENDSECTION -->

****

<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

无论您是准备开始构建应用程序，或只是想要了解更多，我们有您的要求。

- [开始使用邮件、 日历和联系人 REST Api](http://dev.outlook.com/RestGettingStarted)。

- 探讨使用交互式[API 沙盒](http://apisandbox.msdn.microsoft.com/)Office 365 Api。

- 需要示例？ [我们已经有了](..\howto\starter-projects-and-code-samples.md)。


或者，了解有关使用 Office 365 的平台︰

- [在 Outlook 开发人员中心上的 outlook REST API，](http://dev.outlook.com/RestGettingStarted/Overview)

- [在 Office 365 的平台上开发的概述](..\howto\platform-development-overview.md)

- [Office 365 的应用程序的身份验证和资源授权](..\howto\common-app-authentication-tasks.md)

- [手动注册您的应用程序 Azure 的广告，这样它可以访问 Office 365 的 Api](..\howto\add-common-consent-manually.md)

- [日历 API 参考](..\api\calendar-rest-operations.md)

- [联系人 API 参考](..\api\contacts-rest-operations.md)

- [任务 REST API，](..\api\task-rest-operations.md)（预览）

- [OneDrive API](https://dev.onedrive.com/)

- [发现服务 REST API 操作参考](..\api\discovery-service-rest-operations.md)

- [资源引用的邮件、 日历、 联系人和任务 REST Api](..\api\complex-types-for-mail-contacts-calendar.md)


[!INCLUDE [Enable filtering functionality ](../includes/controls/enablefiltering.html)]



