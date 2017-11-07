# <a name="microsoft-graph-permission-scopes"></a>Microsoft Graph 权限范围

Microsoft Graph 提供用于控制对数据的应用程序具有访问权限的 OAuth 2.0 的权限范围。 作为开发人员，您可以使用适合其需要的访问权限范围配置您的应用程序。 通常您执行此操作通过 Azure 的门户。 在签入期间用户或系统管理员提供的机会同意允许您的应用程序访问其数据与您配置的权限范围。 由于这个原因，您应选择提供最少的权限范围的您的应用程序所需的权限级别。 有关如何配置您的应用程序的权限和许可流程上的详细信息，请参阅[使用 Azure Active Directory 集成应用程序](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/)。


##<a name="permission-scope-concepts"></a>权限范围的概念

###<a name="app-only-vs-delegated-scopes"></a>只有应用程序与委派作用域
权限范围可以只包含应用程序的或委派。 仅限应用程序的作用域 （也称为应用程序角色） 授予应用程序的完整权限集提供的范围。 仅限应用程序作用域通常由没有中已登录的用户不在场的情况下，作为服务运行的应用程序使用。 委派的权限范围是用于用户登录的应用程序。 这些作用域委派已登录的用户对该应用程序，使应用程序作为登录用户的权限。 授予应用程序的实际权限将最小特权的组合 （交叉） 的权限授予的范围和那些已登录的用户拥有。 例如，如果权限范围内授予委派的权限写入目录的所有对象，但已登录的用户没有权限仅更新自己的用户配置文件，应用程序将只能编写中已登录的用户的配置文件，但没有其他对象。

###<a name="full-and-basic-profiles-for-users-and-groups"></a>为用户和组的完整和基本配置文件
完整配置文件的配置文件） 的用户或组将包括所有的实体声明属性。 因为该配置文件可能包含敏感的目录信息或个人身份信息 (PII)，几个范围限制到一组有限的属性称为基本配置文件应用程序访问。 基本配置文件的用户，包括仅有以下属性︰ 显示名称，第一个和最后一个名称，照片，和电子邮件地址。 对于组，基本配置文件中包含仅显示名称。 

<!---   <a name="msg_perm_details"> </a>  -->

##<a name="permission-scope-details"></a>许可范围详细信息
您必须配置您的应用程序具有必要的权限来访问 Microsoft Graph API 资源。 对单个资源的权限来读取、 写入或这两种情况下，权限的范围内。 

下表列出的 Microsoft Graph API 权限范围，并解释了每个授予的访问权限。 
- **作用域**列中列出的范围名称。 作用域名称花窗体 resource.operation.constraint 中;例如，Group.ReadWrite.All。 如果约束为"全部"，范围授予该应用程序的所有在目录; 指定资源 （组） 上执行的操作 （读写） 的能力否则，范围只允许已登录的用户配置文件的操作。 作用域可能授予有限的权限为指定的操作，请参阅**说明**列以了解详细信息。
- **权限**列中显示范围在 Azure 的门户网站上的显示方式。 
- **说明**列描述完整的范围由授予的权限集。 委派作用域，授予该应用程序的实际访问将范围和已登录的用户的权限授予访问权限的最小特权的组合 （交点）。 
- 根据是否需要管理员的许可权限，作用域进行分组。

  > **注**︰ 请参阅[发行说明](http://graph.microsoft.io/docs/overview/release_notes)，了解`v1.0`和`beta`权限范围的限制。
  
###<a name="permissions-requiring-administrators-consent"></a>要求管理员的许可权限

|   **作用域**                  |  **在 Azure 管理门户网站上的权限**                          |  **说明** |
|:-----------------------------|:-----------------------------------------|:-----------------|
| _User.Read.All_                |     `Read all user's full profiles`           | User.ReadBasic.All，区别是前者允许应用程序读取及组织中的所有用户的完整配置文件读取导航属性时一样喜欢经理和直接下属。 完整的配置文件将包括所有**用户**实体的声明属性。 若要读取用户所在的组，应用程序也需要 Group.Read.All 或 Group.ReadWrite.All。 |
| _User.ReadWrite.All_           |     `Read and write all user's full profiles` | 允许应用程序读取和写入完整的配置文件属性、 报表和其他用户的经理集代表已登录的用户，您的组织中。 |
| _Directory.Read.All_           |     `Read directory data`                     | 允许应用程序读取您的组织的目录，如用户、 组和应用程序中的数据。 |
| _Directory.ReadWrite.All_      |     `Read and write directory data`           | 允许应用程序读取和写入数据在您的组织的目录中，如用户和用户组。  不允许删除用户或组。 它不允许应用程序若要删除用户或组，或重新设置用户密码。 |
| _Directory.AccessAsUser.All_   |     `Access directory as the signed-in user`  | 允许应用程序与已登录的用户目录中具有相同访问权限的信息。|
| _Group.Read.All_ |    `Read all groups` | 允许应用程序到列表中的组，并读取它们的属性和所有代表已登录的用户的组成员身份。  此外允许应用程序读取已登录的用户可以访问的所有组的日历、 对话、 文件和组中的其他内容。 |
| _Group.ReadWrite.All_ |    `Read and write all groups`| 使应用程序能够创建组并读取所有组属性和代表已登录的用户的成员身份。  此外允许组所有者来管理它们的组并允许该组的成员能够更新内容分组。 |


###<a name="permissions-not-requiring-administrators-consent"></a>不需要管理员的许可权限

|   **作用域**    |  **在 Azure 管理门户网站上的权限**   |  **说明** |
|:---------------|:------------------|:-----------------|
| _User.Read_       |    `Sign-in and read user profile` | 允许用户登录到该应用程序，并允许应用程序读取已登录的用户的配置文件。 完整的配置文件将包括所有用户实体的声明属性。 应用程序无法读取导航属性，例如，经理或直接下属。 此外允许应用程序读取 （通过**TenantDetail**对象） 中已登录的用户的以下基本的公司信息︰ 租户 ID、 租户显示名称和已验证的域。|
| _User.ReadWrite_ |    `Read and write access to user profile` | 允许应用程序读取您的配置文件。 它还允许应用程序来更新您的配置文件信息，以您的名义。 |
| _User.ReadBasic.All_ |    `Read all user's basic profiles` | 允许应用程序读取代表已登录的用户的组织中的所有用户的基本配置文件。 以下属性构成了基本的用户配置文件︰ 显示名称，第一个和最后一个名称，照片，和电子邮件地址。 若要读取用户所在的组，应用程序也需要 Group.Read.All 或 Group.ReadWrite.All。| 
| _Mail.Read_ |    `Read user mail` | 允许应用程序读取用户邮箱中的电子邮件。 |
| _Mail.ReadWrite_ |    `Read and write access to user mail` | 允许应用程序创建、 读取、 更新和删除用户邮箱中的电子邮件。 不包括发送邮件的权限。|
| _Mail.Send_ |    `Send mail as a user` | 允许应用程序充当组织中的用户发送邮件。 |
| _Calendars.Read_ |    `Read user calendars`  | 允许应用程序读取用户日历中的事件。|
| _Calendars.ReadWrite_ |    `Have full access to user calendars`  | 允许应用程序创建、 读取、 更新和删除在用户的日历中的事件。 |
| _Contacts.Read_ |    `Read user contacts`  | 允许应用程序读取用户联系人。 |
| _Contacts.ReadWrite_ |    `Have full access to user contacts`  | 允许应用程序创建、 读取、 更新和删除用户的联系人。 |
| _Files.Read_ |    `Read user files and files shared with user` | 允许应用程序读取已登录的用户文件和与该用户共享的文件。| 
| _Files.ReadWrite_ |   `Have full access to user files and files shared with user` | 允许应用程序读取、 创建、 更新和删除已登录的用户的文件和与该用户共享的文件。 |
| _Files.ReadWrite.Selected_ |    `Read and write files that the user selects` | 允许读取和写入文件，用户选择的应用程序。 几个小时在用户选择一个文件后，应用程序具有访问权限。 |
| _Files.Read.Selected_ |    `Read files that the user selects`  | 允许应用程序读取文件的用户选择。 几个小时在用户选择一个文件后，应用程序具有访问权限。 |
| _Sites.Read.All_ |    `Read items in all site collections` | 允许应用程序读取文档和列表项中代表已登录的用户的所有网站集。 |
| _openid_ |    `Sign users in`（预览） | 允许用户登录到该应用程序与他们的工作或学校帐户，并允许应用程序基本的用户配置文件信息，请参阅。|
| _offline_access_ |    `Access user's data anytime`（预览） | 允许应用程序读取和更新用户的数据，即使他们目前没有使用该应用程序。|

###<a name="app-only-permissions-requiring-administrators-consent"></a>仅限应用程序的权限需要管理员的许可

|   **作用域**    |  **在 Azure 管理门户网站上的权限**   |  **说明** |
|:---------------|:------------------|:-----------------|
| _Mail.Read_       |    `Read mail in all mailboxes` | 允许应用程序读取所有已登录的用户没有邮箱中的邮件。|
| _Mail.ReadWrite_ |    `Read and write mail in all mailboxes` | 允许应用程序创建、 读取、 更新和删除所有已登录的用户没有邮箱中的邮件。 不包括发送邮件的权限。 |
| _Mail.Send_ |    `Send mail as any user` | 允许应用程序与已登录的用户的情况下任何用户发送邮件。 | 
| _Calendars.Read_ |    `Read calendars in all mailboxes` | 允许应用程序读取的事件的所有日历中已登录的用户的情况下。 |
| _Calendars.ReadWrite_ |    `Read and write calendars in all mailboxes` | 允许应用程序创建、 读取、 更新和删除的已登录的用户的情况下所有日历事件。|
| _Contacts.Read_ |    `Read contacts in all mailboxes` | 允许应用程序读取所有已登录的用户没有邮箱中的所有联系人。 |
| _Contacts.ReadWrite_ |    `Read and write contacts in all mailboxes`  |允许应用程序创建、 读取、 更新和删除所有已登录的用户没有邮箱中的所有联系人。|
| _User.ReadBasic.All_ |    `Read all users' basic profiles`  | 允许应用程序读取一组基本已登录的用户的情况下组织中其他用户的配置文件属性。 包括显示名称，第一个和最后一个名称，照片，和外出消息。|
| _User.Read.All_ |    `Read all users' full profiles` | 允许应用程序读取完整的配置文件属性、 组成员身份、 报告和其他用户已登录的用户的情况下，您的组织中的经理集。| 
| _User.ReadWrite.All_ |   `Read and write all users' full profiles` | 允许应用程序读取和写入完整的配置文件属性、 组成员身份、 报告和其他用户的经理集已登录的用户的情况下，您的组织中。|


##<a name="preview"></a>预览
###<a name="permissions-not-requiring-administrators-consent-preview"></a>不需要管理员的同意 （预览） 的权限

|   **作用域**    |  **在 Azure 管理门户网站上的权限**   |  **说明** |
|:---------------|:------------------|:-----------------|
| _Tasks.ReadWrite_ |    `Create, read, update and delete user tasks and plans`（预览） | 允许应用程序创建、 读取、 更新和删除任务和计划 （以及它们的任务），分配给网站或与已登录的用户共享。|
| _People.Read_ |    `Read users' relevant people lists`（预览） | 允许应用程序读取排名表中已登录的用户的相关人员。 该列表包括当地联系人、 来自社交网络的联系人、 您所在组织的目录和最新通信 （例如电子邮件和 Skype） 的人员。|
| _People.ReadWrite_ |    `Read and write users' relevant people lists`（预览） | 允许应用程序创建、 读取和写入相关人员已登录的用户的排名表。 该列表包括当地联系人、 来自社交网络的联系人、 您所在组织的目录和最新通信 （例如电子邮件和 Skype） 的人员。|
| _Notes.Create_ |    `Create pages in users' notebooks`（预览） | 允许应用程序读取的笔记本和分区标题和创建新的网页、 笔记本和分区代表已登录的用户。|
| _Notes.ReadWrite.CreatedByApp_ |    `Limited notebook access`（预览） | 允许应用程序读取的笔记本和分区标题、 创建新页面代表已登录的用户。 此外允许应用程序读取和更新所创建的应用程序页。 |
| _Notes.Read_ |    `Read user notebooks`（预览） | 允许应用程序以查看 OneNote 笔记本和分区的标题并读取代表已登录的用户的所有页面。 它不能查看密码保护的分区。 |
| _Notes.ReadWrite_ |    `Read and write user notebooks`（预览） | 允许应用程序读取的笔记本和分区标题、 读取所有页、 编写所有页面和创建新页面代表已登录的用户。  它不能访问密码保护的分区。 |
| _Notes.Read.All_ |    `Read all notebooks that the user can access`（预览） | 允许应用程序读取的所有笔记本和分区中已登录的用户可以访问的内容。   无法读取密码保护的分区。 |
| _Notes.ReadWrite.All_ |    `Read and write notebooks that the user can access`（预览） | 允许应用程序读取和写入的所有笔记本和分区中已登录的用户可以访问的内容。  它不能访问密码保护的分区。|


<!-- -->

##<a name="permission-scope-scenarios"></a>权限范围内的方案
以下是使用一些应用程序方案`User`和`Group`的资源和其相应的所需的范围。 下表显示了所需的应用程序，以便能够执行特定操作的权限范围。 请注意，在某些情况下，应用程序能够执行某些操作将取决于权限范围是仅限应用程序还是委派，并且当委派的权限范围，在已登录的用户的权限。 

###<a name="access-scenarios-using-the-user-resource-and-the-required-scopes"></a>使用的用户资源和所需的范围的访问方案

| **涉及用户的应用程序任务**   |  **所需的范围** | **在 Azure 管理门户网站上的权限** |
|:-------------------------------|:---------------------|:---------------|
| 应用程序想要读取其他用户的基本信息 （仅限显示名称和图片） 例如显示领料经验的人员中   | _User.ReadBasic.All_  |  `Read all user's basic profiles` |
| 应用程序想要阅读完整的用户配置文件的登录用户 （请参见直接下属，和管理器等）  | _User.Read_ | `Enable sign-in and read user profile`|
| 应用程序想要阅读完整的用户配置文件的所有用户  | _User.Read.All_ |  `Read all user's full profiles`   |
| 应用程序想要读取的文件，登录的用户的邮件和日历信息  | _User.Read_， _Files.Read_， _Mail.Read_ _Calendar.Read_ | `Enable sign-in and read user profile`, `Read users' files`,  `Read user mail`,  `Read user calendars` |
| 应用程序想要读取已登录的用户 （我） 的文件，并将其他用户具有与已登录的用户 (me) 共享的文件。 | _User.Read_， _Files.Read_， _Sites.Read.All_ | `Enable sign-in and read user profile`, `Read users' files`,  `Read items in all site collections` |
| 应用程序想要读取和写入登录的用户的用户配置文件   | _User.ReadWrite_ | `Read and write access to user profile` |
| 应用程序想要读取和写入的所有用户的用户配置文件    | _User.ReadWrite.All_ | `Read and write all user's full profiles` |
| 应用程序想要读取和写入文件，登录的用户的邮件和日历信息    | _User.ReadWrite_， _Files.ReadWrite_， _Mail.ReadWrite_ _Calendar.ReadWrite_  |  `Read and write access to user profile`,  `Read and write access to user profile`,  `Read and write access to user mail`, `Have full access to user calendars` |
   

###<a name="access-scenarios-using-the-group-resource-and-the-required-scopes"></a>使用组资源和所需的范围的访问方案
    
| **应用程序任务都涉及到组**  |  **所需的范围** |  **在 Azure 管理门户网站上的权限** |
|:-------------------------------|:---------------------|:---------------|
| 应用程序想要读取基本组信息 （仅限显示名称和图片），例如，要显示在选取体验组  | _Group.Read.All_  | `Read all groups`|
| 应用程序想要阅读所有的统一组，包括文件、 对话中的所有内容。  它还需要显示组成员身份，将无法更新组成员身份 (如果所有者)。  |  _Group.Read.All_ | `Read items in all site collections`, `Read all groups`|
| 应用程序想要读取和写入所有统一组，包括文件、 对话中的所有内容。  它还需要显示组成员身份，将无法更新组成员身份 (如果所有者)。  |  _Group.ReadWrite.All_ _Sites.ReadWrite.All_ |  `Read and write all groups`, `Edit or delete items in all site collections` |
| 应用程序想要发现 （找到） 统一的组。 它允许用户搜索特定的组，然后选择从枚举列表以允许该用户要加入的组。     | _Group.ReadWrite.All_ | `Read and write all groups`|
| 应用程序想要创建一个组通过 AAD 图形 |   _Group.ReadWrite.All_ | `Read and write all groups`|
 

<!---   ##Additional Resources##


- [Authenticate Microsoft Graph endpoints using the v2.0 app model preview](authenticate-MSGraph-using-v2.md )
- [Hands on lab: Deep dive into the Office 365 unified API](http://dev.office.com/hands-on-labs/4585) -->

