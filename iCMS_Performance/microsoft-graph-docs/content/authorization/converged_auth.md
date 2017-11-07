# <a name="authenticate-microsoft-graph-endpoints-using-the-v2-authentication-endpoint"></a>对 Microsoft Graph 终结点使用的 v2 身份验证终结点进行身份验证


<!--
### Preview documentation
There are features and functionality of the converged authentication model that are not yet supported in the public preview period. You should be aware of them if you are building applications during the public preview. For more information, see [Limitations and restrictions of the converged authentication model preview](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/).
-->

## <a name="signing-in-microsoft-account-and-azure-ad-users-with-a-single-authentication-model"></a>在 Microsoft 客户并与单一身份验证模型的 Azure AD 用户登录

通过使用 v2 身份验证终结点，您可以创建接受学校 (Azure AD)、 工作以及个人 （Microsoft 帐户） 标识的应用程序。

在过去，如果想要开发的应用程序以支持 Microsoft 帐户和 Azure Active Directory，您必须与两个完全独立的系统集成。 使用 v2 身份验证终结点，您可以现在支持两种类型的帐户具有单一的集成。 一个简单的过程立即到达跨越数以百万计的个人和工作/学校帐户的用户群体。   

将您的应用程序集成与 v2 身份验证终结点后，他们可以立即访问 Microsoft Graph 端点可供个人和工作/学校的科目，如︰ 

| Data              | 终结点                                       |
|:------------------|:-----------------------------------------------|
| 用户配置文件      | `https://graph.microsoft.com/v1.0/me`          |
| Outlook 邮件      | `https://graph.microsoft.com/v1.0/me/messages` |
| Outlook 联系人  | `https://graph.microsoft.com/v1.0/me/contacts` |
| Outlook 日历 | `https://graph.microsoft.com/v1.0/me/events`   |
| OneDrive          | `https://graph.microsoft.com/v1.0/me/drive`    |

 >**注意︰**某些 Microsoft Graph 终结点如组和任务不是适用于个人帐户。  

## <a name="microsoft-graph-api-authentication-scopes"></a>Microsoft Graph API 身份验证作用域

V2 身份验证终结点支持所有使用 Azure AD 身份验证[Microsoft Graph 权限范围](permission_scopes.md)主题中列出的权限范围。 不过，v2 身份验证端点当前不支持仅限应用程序的范围。

>**注意︰**目前，您需要将资源 URL https://graph.microsoft.com 作为范围字符串的前缀传递。 例如，若要使用`Files.Read`范围，指定的作用域为`https://graph.microsoft.com/Files.Read`。

V2 身份验证终结点，和它不同于在 Azure AD 中使用资源的方式与使用作用域的详细信息，请参阅[范围，不是资源](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-compare/#scopes-not-resources)。

<!--
The table below lists the authentication scopes to use with the converged authentication model preview. For more information about using scopes with the converged authentication model, and how it differs from using resources in Azure AD, see [Scopes, not resources](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-compare/#scopes-not-resources).


| **Scope**             | **Permission**                        | **Description**                                                                                                                                         |
|:----------------------|:--------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `User.Read`           | Enable sign-in and read user profile  | Allows users to sign-in to the app, and allows the app to read the profile. It also allow the app to read basic company information of signed-in users. |
| `User.ReadWrite`      | Read and write access to user profile | Allows the app to read the profile of signed-in users, and to update profile information on behalf of signed-in users.                                  |
| `Mail.Read`           | Read user mail                        | Allows this app to read messages in user mailboxes.                                                                                                     |
| `Mail.ReadWrite`      | Read and write access to user mail    | Allows the app to read, update, create, and delete messages in user mailboxes.                                                                          |
| `Mail.Send`           | Send mail as a user                   | Allows the app to send messages as users in the organization.                                                                                           |
| `Contacts.Read`       | Read user contacts                    | Allows the app to read user contacts.                                                                                                                   |
| `Contacts.ReadWrite`  | Have full access to user contacts     | Allows the app to read, update, create and delete user contacts.                                                                                        |
| `Calendars.Read`      | Read user calendars                   | Allows the app to read events in user calendars.                                                                                                        |
| `Calendars.ReadWrite` | Have full access to user calendars    | Allows the app to read, update, create, and delete events in user calendars.                                                                            |
| `Files.Read`          | Read users' files                     | Allows the application to read the current user's files.                                                                                                |
| `Files.ReadWrite`     | Edit or delete users' files           | Allows the app to edit or delete the current user's files.                                                                                              |
| `openid`              | Sign users in                         | Allows users to sign in to the app and allows the app to see basic user profile information.                                                            |
| `offline_access`      | Read and write user's information     | Allows the app to see and update user's data, even when the user is not actively using the app.                                                         |

**Note**: currently it is required to pass the resource url of 'https://graph.microsoft.com' as prefix for the scope string. For example, to use the `Files.Read` scope you would specify the scope as `https://graph.microsoft.com/Files.Read`.
-->


## <a name="next-steps"></a>下一步行动

[注册应用程序以使用 v2 身份验证终结点](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-app-registration/)

## <a name="learn-more"></a>了解更多信息

[V2 身份验证模式有关的新增功能](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-compare)

[限制和 v2 身份验证模型中的限制](https://azure.microsoft.com/en-us/documentation/articles/active-directory-v2-limitations/)

[Microsoft Azure v2 身份验证终结点文档](https://azure.microsoft.com/en-us/documentation/articles/?service=active-directory&term=app+model+v2.0)
