# <a name="calling-microsoft-graph"></a>调用 Microsoft Graph

###<a name="call-microsoft-graph-api-service-via-rest"></a>其余部分通过 Microsoft Graph API 服务调用
用于访问和操作 Microsoft Graph API 资源，请调用，并指定在资源允许的资源 Url 使用以下操作之一。   

- 获取
- 发布
- 修补
- 放置
- 删除 

Microsoft Graph API 的所有请求都使用以下基本 URL 模式︰

```
    https://graph.microsoft.com/{version}/{resource}?[odata_query_parameters]
```

此 URL:

- `https://graph.microsoft.com`是 Microsoft Graph API 端点
- `{version}`是目标服务版本，例如，`v1.0`或`beta`。
- `{resource}`是资源段或路径如
  - `users`, `groups`, `devices`, `organization`
  - 该别名`me`，它将解析为已登录的用户
   - 如属于用户的资源`me/events`，`me/drive`或`me/messages`
  - 该别名`myOrganization`，它解析为组织中已登录的用户的组织
- `[odata_query_parameters]`表示附加 OData 查询参数如`$filter`和`$select` 

此外您可以指定组织作为您的请求，是可选的并不是必需的一部分。 当使用`me`，请不要指定租户。 常见的请求摘要[概述](overview.md)中不可用。

###<a name="microsoft-graph-api-metadata"></a>Microsoft Graph API 元数据
服务文档 ($metadata) 发布的服务的根本。 例如，您可以查看服务文档的 1.0 版和测试版的版本，通过下面的 Url。

Microsoft Graph API`v1.0`元数据。
```
    https://graph.microsoft.com/v1.0/$metadata
```
Microsoft Graph API`beta`元数据。
```
    https://graph.microsoft.com/beta/$metadata
```

元数据允许您查看实体、 实体类型和集、 复杂类型和枚举的 Microsoft Graph REST API。 使用元数据并随时可供使用的第三方工具，可以创建序列化的对象，并生成简化使用 REST API 的客户端库。  

由 Microsoft Graph 实体数据模型确定资源 URL。 实体元数据架构 ($metadata) 概述了处方。 

路径的 URL 资源名称、 查询参数和操作参数和值是区分大小写。 但是，您指定的值、 实体 Id 和其他 base64 编码的值是区分大小写。

下一节中显示一些基本编程模式调用 API。

###<a name="navigation-from-a-set-to-a-member"></a>从一组成员的导航

若要查看有关用户的信息，您可以获得`User`实体从`users`向特定用户标识其标识符，通过使用 HTTPS GET 请求的集合。 对于`User`实体，或者`id`或`userPrincipalName`属性可以用作标识符。 下面的示例请求使用`userPrincipalName`作为该用户 id 的值。 

```no-highlight 
GET https://graph.microsoft.com/v1.0/users/john.doe@contoso.onmicrosoft.com HTTP/1.1
Authorization : Bearer <access_token>
```

如果成功，将得到的用户资源表示的有效负载中包含一个 200 OK 响应，如下所示︰

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
content-length: 982

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "id": "c95e3b3a-c33b-48da-a6e9-eb101e8a4205",
    "city": "Redmond",
    "country": "USA",
    "department": "Help Center",
    "displayName": "John Doe",
    "givenName": "John",
    "userPrincipalName": "Johndoe@contoso.onmicrosoft.com",

    ... 
}
```


###<a name="projection-from-an-entity-to-properties"></a>从实体属性的投影
若要检索用户的个人数据，如用户提供_关于我_的描述和他们的技术水平仅设置，可以将 $select 查询选项添加到前一个请求。 例如，

```no-highlight 
GET https://graph.microsoft.com/v1.0/users/john.doe@contoso.onmicrosoft.com?$select=displayName,aboutMe,skills HTTP/1.1
Authorization : Bearer <access_token>
```

成功的响应将返回 200 OK 状态和有效负载的格式如下︰

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
content-length: 169

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "aboutMe": "A cool and nice guy.",
    "displayName": "John Doe",
    "skills": [
        "n-Lingual",
        "public speaking",
        "doodling"
    ]
}
```

在这里，而不是整个属性上设置`user`实体，仅`aboutMe`， `displayName` ，`skills`属性，将返回。

###<a name="traversal-to-another-resource-via-relationship"></a>遍历关系通过的其他资源
管理器保存`directReports`与其他用户的报告他 / 她的关系。 要查询用户的直接下属的列表，可以使用下面的 HTTPS GET 请求来导航到所需目标通过关系遍历。 

```no-highlight 
GET https://graph.microsoft.com/v1.0/users/john.doe@contoso.onmicrosoft.com/directReports HTTP/1.1
Authorization : Bearer <access_token>
```

成功的响应将返回 200 OK 状态和有效负载的格式如下︰

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
content-length: 152
    
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects/$entity",
    "@odata.type": "#microsoft.graph.user",
    "id": "c37b074d-fe9d-4e68-83ad-b4401d3be174",
    "department": "Sales & Marketing",
    "displayName": "Bonnie Kearney",

    ...
}
```

同样，您可以按照以导航到相关资源的关系。 例如，`user => messages`关系使图形遍历从 Azure AD 节点到 Exchange 联机的节点。 下面的示例显示如何执行此操作的 REST API 调用︰


```no-highlight 
GET https://graph.microsoft.com/v1.0/me/messages HTTP/1.1
Authorization : Bearer <access_token>
```

    
成功的响应将返回 200 OK 状态和有效负载的格式如下︰


```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal
odata-version: 4.0
content-length: 147
    
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('john.doe%40contoso.onmicrosoft.com')/Messages",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/me/messages?$top=1&$skip=1",
  "value": [
    {
      "@odata.etag": "W/\"FwAAABYAAABMR67yw0CmT4x0kVgQUH/3AAJL+Kej\"",
      "id": "<id-value>",
      "createdDateTime": "2015-11-14T00:24:42Z",
      "lastModifiedDateTime": "2015-11-14T00:24:42Z",
      "changeKey": "FwAAABYAAABMR67yw0CmT4x0kVgQUH/3AAJL+Kej",
      "categories": [],
      "receivedDateTime": "2015-11-14T00:24:42Z",
      "sentDateTime": "2015-11-14T00:24:28Z",
      "hasAttachments": false,
      "subject": "Did you see last night's game?",
      "body": {
        "ContentType": "HTML",
        "Content": "<content>"
      },
      "BodyPreview": "it was great!",
      "Importance": "Normal",
            
       ...
    }
  ]
}
```

###<a name="projection-from-entities-to-properties"></a>从实体属性的投影
除了对其属性从一个实体投影，您还可以应用类似`$select`查询到一个实体集合的选项，这些项目对它们的某些属性的集合。 例如，要查询驱动器项已登录的用户的名称，您可以提交以下获得 HTTPS 请求︰

```no-highlight 
GET https://graph.microsoft.com/v1.0/me/drive/root/children?$select=name HTTP/1.1
Authorization : Bearer <access_token>
```

成功的响应将返回 200 OK 状态代码和有效负载包含名称和类型的共享文件，如下面的示例所示︰

```no-highlight 
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('john.doe%40contoso.onmicrosoft.com')/drive/root/children(name,type)",
  "value": [
    {
      "@odata.etag": "\"{896A8E4D-27BF-424B-A0DA-F073AE6570E2},2\"",
      "name": "Shared with Everyone"
    },
    {
      "@odata.etag": "\"{B39D5D2E-E968-491A-B0EB-D5D0431CB423},1\"",
      "name": "Documents"
    },
    {
      "@odata.etag": "\"{9B51EA38-3EE6-4DC1-96A6-230E325EF054},2\"",
      "name": "newFile.txt"
    }
  ]
}
```

###<a name="query-a-subset-of-users-with-the-filtering-query-option"></a>查询与筛选的查询选项的用户的子集
若要查找的特定职务，在组织内的员工，可以从 users 集合定位，然后指定 $filter 查询选项。 示例如下所示︰

    
```no-highlight 
GET https://graph.microsoft.com/v1.0/users/?$filter=jobTitle+eq+%27Helper%27 HTTP/1.1
Authorization : Bearer <access_token>
```

成功的响应将返回 200 OK 状态代码和列表的用户指定的职务 (`'Helper'`)，如以下示例所示︰

```no-highlight 
HTTP/1.1 200 OK
content-type: application/json;odata.metadata=minimal;odata.streaming=true;IEEE754Compatible=false;charset=utf-8
odata-version: 4.0
content-length: 986

{
    "@odata.context": "https://graph.microsoft.com/v1.0/contoso.onmicrosoft.com/$metadata#users",
    "value": [
        {
            "id": "c95e3b3a-c33b-48da-a6e9-eb101e8a4205",
            "city": "Redmond",
            "country": "USA",
            "department": "Help Center",
            "displayName": "Jane Doe",
            "givenName": "Jane",
            "jobTitle": "Helper",
            ......
            "mailNickname": "Jane",
            "mobile": null,
            "otherMails": [
                "jane.doe@contoso.onmicrosoft.com"
            ],
            ......
            "surname": "Doe",
            "usageLocation": "US",
            "userPrincipalName": "help@contoso.onmicrosoft.com",
            "userType": "Member"
        },
        
        ...
    ]
}
```

###<a name="calling-odata-actions-or-functions"></a>OData 操作或函数调用
Microsoft Graph API 还支持 OData 操作和函数可用于操作资源。 例如，下面的 HTTPS POST 请求允许已登录的用户 (`me`) 发送一封电子邮件︰
```no-highlight 
POST https://graph.microsoft.com/v1.0/me/microsoft.graph.sendMail HTTP/1.1
authorization: bearer <access_token>
content-type: application/json
content-length: 96

{
  "message": {
    "subject": "Meet for lunch?",
    "body": {
      "contentType": "Text",
      "content": "The new cafeteria is open."
    },
    "toRecipients": [
      {
        "emailAddress": {
          "address": "garthf@a830edad9050849NDA1.onmicrosoft.com"
        }
      }
    ],
    "attachments": [
      {
        "@odata.type": "#Microsoft.OutlookServices.FileAttachment",
        "name": "menu.txt",
        "contentBytes": "bWFjIGFuZCBjaGVlc2UgdG9kYXk="
      }
    ]
  },
  "saveToSentItems": "false"
}
```

请求负载包含的输入`microsoft.graph.sendMail`也在 $metadata 中定义的操作。

与一个单一的统一端点，Microsoft Graph 简化了 Microsoft 云中的服务应用程序编程接口。 因此，否则为思教育服务的界限将会消失。 作为应用程序开发人员，您将不再需要跟踪的数据源，并实现各种数据源之间的自定义接口。 


