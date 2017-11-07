# <a name="user-resource-type"></a>用户资源类型

表示一个 Azure AD 用户帐户。 从[directoryObject](directoryobject.md)继承。


## <a name="methods"></a>方法
| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获取用户](../api/user_get.md) | [用户](user.md) |读取属性和用户对象的关系。|
|[更新用户](../api/user_update.md) | [用户](user.md) |更新用户对象。 |
|[删除用户](../api/user_delete.md) | 无 |删除用户对象。 |
|[列表中的邮件](../api/user_list_messages.md) |[消息](message.md)集合| 获取已登录的用户邮箱中的所有邮件。|
|[创建邮件](../api/user_post_messages.md) |[消息](message.md)| 由过账到消息集合创建一封新邮件。|
|[列表 mailFolders](../api/user_list_mailfolders.md) |[MailFolder](mailfolder.md)集合| 在已登录的用户的根文件夹下获取邮件文件夹集合。 |
|[创建 mailFolder](../api/user_post_mailfolders.md) |[MailFolder](mailfolder.md)| 由过账到 mailFolders 集合中创建新的 MailFolder。|
|[sendMail](../api/user_sendmail.md)|无|发送请求正文中指定的消息。|
|[获取自动答复设置](../api/user_get_mailboxsettings.md) |[automaticRepliesSetting](../resources/automaticRepliesSetting.md) | 获得通知此人在收到电子邮件时自动设置。 |
|[更新自动答复设置](../api/user_update_mailboxsettings.md) |[mailboxSettings](../resources/mailboxSettings.md) | 通知此人在收到电子邮件时自动更新的设置。 |
|[事件列表](../api/user_list_events.md) |[事件](event.md)集合| 在该用户的邮箱中获取事件对象的列表。 该列表包含单个实例会议和系列的主控形状。|
|[创建事件](../api/user_post_events.md) |[事件](event.md)| 由过账到的事件集合中创建新的事件。|
|[列表中的日历](../api/user_list_calendars.md) |[日历](calendar.md)的集合| 获取日历的对象集合。|
|[创建日历](../api/user_post_calendars.md) |[日历](calendar.md)| 由过账到日历集合中创建新日历。|
|[列表 calendarGroups](../api/user_list_calendargroups.md) |[CalendarGroup](calendargroup.md)集合| 获得 CalendarGroup 对象集合。|
|[创建 calendarGroup](../api/user_post_calendargroups.md) |[CalendarGroup](calendargroup.md)| 由过账到 calendarGroups 集合中创建新的 CalendarGroup。|
|[日历视图列表](../api/user_list_calendarview.md) |[事件](event.md)集合| 获取一个事件对象集合。|
|[联系人列表](../api/user_list_contacts.md) |[联系人](contact.md)集合| 从默认的联系人文件夹的已登录的用户获取联系人的集合。|
|[创建联系人](../api/user_post_contacts.md) |[联系人](contact.md)| 由过账到联系人集合中创建新的联系人。|
|[列表 contactFolders](../api/user_list_contactfolders.md) |[ContactFolder](contactfolder.md)集合| 获取已登录的用户的默认联系人文件夹中的联系人文件夹集合。|
|[创建 ContactFolder](../api/user_post_contactfolders.md) |[ContactFolder](contactfolder.md)| 由过账到 contactFolders 集合中创建新的 ContactFolder。|
|[列表 directReports](../api/user_list_directreports.md) |[directoryObject](directoryobject.md)集合| 获得用户和联系人报告给用户 directReports 导航属性。|
|[列表管理器](../api/user_list_manager.md) |[directoryObject](directoryobject.md) | 获取用户或联系，它是从管理器的导航属性的此用户的经理。|
|[列表 memberOf](../api/user_list_memberof.md) |[directoryObject](directoryobject.md)集合| 获取组、 目录角色和用户是直接从 memberOf 导航属性成员的管理单位。|
|[列表 ownedDevices](../api/user_list_owneddevices.md) |[directoryObject](directoryobject.md)集合| 获取用户从 ownedDevices 导航属性所拥有的设备。|
|[列表 ownedObjects](../api/user_list_ownedobjects.md) |[directoryObject](directoryobject.md)集合| 获取由 ownedObjects 导航属性从用户拥有的目录对象。|
|[列表 registeredDevices](../api/user_list_registereddevices.md) |[directoryObject](directoryobject.md)集合| 获得 retistered registeredDevices 导航属性从用户的设备。|
|[列表 scopedAdministratorOf](../api/user_list_scopedadministratorof.md) |[scopedRoleMembership](scopedrolemembership.md)集合| 获取此用户范围角色管理单位成员身份。|
|[列表 createdObjects](../api/user_list_createdobjects.md) |[directoryObject](directoryobject.md)集合| 获取由 createdObjects 导航属性从用户创建的目录对象。|
|[assignLicense](../api/user_assignlicense.md)|[用户](user.md)|添加或删除用户的订阅。 您还可以启用和禁用与订阅相关的特定计划。|
|[checkMemberGroups](../api/user_checkmembergroups.md)|字符串集合|检查有列表中的组成员资格。 检查是可传递的。|
|[findmeetingtimes](../api/user_findmeetingtimes.md)|[meetingTimeCandidate](meetingtimecandidate.md)|查找时间和位置，以满足根据与会者在可用性、 位置或时间限制。|
|[getMemberGroups](../api/user_getmembergroups.md)|字符串集合|返回所有组成员的用户。 检查是可传递的。|
|[getMemberObjects](../api/user_getmemberobjects.md)|字符串集合| 返回所有组、 目录角色和用户所在的管理单位。 检查是可传递的。 |
|[reminderView](../api/user_reminderview.md)|[提醒](reminder.md)的集合|返回在指定的开始和结束时间的日历提醒列表。|



## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|aboutMe|String|用户描述自己一个自由形式的文本输入字段。|
|accountEnabled|Boolean| **如此**如果启用了帐户;否则为**假**。 在创建用户时，此属性是必需的。 支持 $filter。    |
|assignedLicenses|[assignedLicense](assignedlicense.md)集合|分配给该用户的许可证。 不可以为 null。            |
|assignedPlans|[assignedPlan](assignedplan.md)集合|分配给用户的计划。 只读的。 不可以为 null。 |
|生日|方法|用户的生日。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|市/县|String|用户所在的城市。 支持 $filter。|
|国家/地区|String|国家/地区用户所在;例如，"美国"或"英国"。 支持 $filter。|
|部门|String|用户的工作部门的名称。 支持 $filter。|
|显示名称|String|显示在通讯簿中的用户的名称。 这通常是名字的用户，中间初始和最后一个名称的组合。 创建用户并在更新过程中不能清除时，该属性是必需的。 $Filter 和 $orderby 的支持。|
|givenName|String|给定名称 （名字） 的用户。 支持 $filter。|
|hiredate|方法|雇佣日期是在用户。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|id|String|用户的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键。 不可以为 null。 只读的。|
|兴趣爱好|字符串集合|要描述他们的兴趣的用户列表。|
|职务|String|用户的职务。 支持 $filter。|
|邮件|String|例如，用户的 SMTP 地址"jeff@contoso.onmicrosoft.com".只读的。 支持 $filter。|
|mailboxSettings|[mailboxSettings](mailboxsettings.md)|已登录的用户的主邮箱的设置。 它们包括设置用于发送自动答复收到的邮件。|
|mailNickname|String|用户邮件别名。 在创建用户时，必须指定此属性。 支持 $filter。|
|mobilePhone|String|主要的移动电话用户数。|
|mySite|String|用户的个人站点的 URL。|
|办公室|String|在用户的位置业务的办公地点。|
|onPremisesImmutableId|String|此属性用于将 Azure AD 用户对象为内部部署 Active Directory 用户帐户相关联。 在关系图中创建新的用户帐户，如果您使用的联盟的域用户的**范围内**(UPN) 属性时，必须指定此属性。 **重要︰****$** ，并指定此属性时，不能使用**_**字符。 支持 $filter。                            |
|onPremisesLastSyncDateTime|方法|该值指示上一次的对象同步与内部目录;例如:"2013年-02-16T03:04:54Z"。 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰ `'2014-01-01T00:00:00Z'`。 只读的。|
|onPremisesSecurityIdentifier|String|从内部同步到云中的用户包含内部安全标识符 (SID)。 只读的。|
|onPremisesSyncEnabled|Boolean| **如此**如果此对象同步从本地目录中。**假**如果此对象最初从内部目录同步，但不会再同步;**null**如果该对象已永远不会从内部目录 （默认值） 进行同步。 只读的 |
|passwordPolicies|String|指定用户的密码策略。 此值是一个可能的值为"DisableStrongPassword"，使较弱的密码比默认策略来指定一个枚举。 此外可以指定"DisablePasswordExpiration"。 可以指定两个在一起;例如:"DisablePasswordExpiration，DisableStrongPassword"。|
|passwordProfile|[PasswordProfile](passwordprofile.md)|指定用户的密码配置文件。 配置文件包含用户的密码。 在创建用户时，此属性是必需的。 在配置文件中的密码必须满足最低要求为**passwordPolicies**属性指定的。 默认情况下，使用强密码是必需的。|
|pastProjects|字符串集合|若要枚举其过去的项目的用户列表。|
|邮政编码|String|用户的邮政地址的邮政编码。 邮政编码是特定于用户的国家/地区。 在美国，此属性包含邮政编码。|
|preferredLanguage|String|用户的首选的语言。 应遵循 ISO 639-1 代码;如"EN-US"。|
|preferredName|String|用户首选的名称。|
|provisionedPlans|[ProvisionedPlan](provisionedplan.md)集合|为用户设置的计划。 只读的。 不可以为 null。 |
|代理地址|字符串集合|例如︰ `["SMTP: bob@contoso.com", "smtp: bob@sales.contoso.com"]` **any**运算符，则需要为多值属性的筛选器表达式。 只读的不可以为 null。 支持 $filter。          |
|责任|字符串集合|要枚举其职责的用户列表。|
|学校|字符串集合|枚举它们已参加学校的用户列表。|
|技能|字符串集合|若要枚举其技能的用户列表。|
|状态|String|状态或用户的地址中的省。 支持 $filter。|
|街道地址|String|用户的业务地点的街道地址。|
|姓氏|String|用户的姓 （系列名称或姓氏）。 支持 $filter。|
|usageLocation|String|两个字母的国家代码 (ISO 3166 标准)。 所需的将由于法律要求在国家和地区的服务的可用性检查许可证分配的用户。  例如:"美国"、"JP"和"GB"。 不可以为 null。 支持 $filter。|
|范围内|String|用户主要名称 (UPN) 的用户。 UPN 是基于互联网标准 RFC 822 用户互联网式登录名。 按照惯例，这应映射到用户的电子邮件名称。 常规格式是alias@domain,域必须是现租户的集合的已验证的域中。 在创建用户时，此属性是必需的。 从[组织](organization.md)的**verifiedDomains**属性可以访问租户的验证的域。 $Filter 和 $orderby 的支持。
|用户类型|String|一个字符串值，可以用于分类目录，例如"成员"和"访客"中的用户类型。 支持 $filter。          |

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|calendar|[日历](calendar.md)|用户的主日历。 只读的。|
|calendarGroups|[CalendarGroup](calendargroup.md)集合|用户的日历组。 只读的。 可以为 null。|
|日历视图|[事件](event.md)集合|日历的日历视图中。 只读的。 可以为 null。|
|日历|[日历](calendar.md)的集合|用户的日历。 只读的。 可以为 null。|
|contactFolders|[ContactFolder](contactfolder.md)集合|用户的联系人文件夹。 只读的。 可以为 null。|
|联系人|[联系人](contact.md)集合|用户的联系人。 只读的。 可以为 null。|
|createdObjects|[directoryObject](directoryobject.md)集合|由用户创建的目录对象。 只读的。 可以为 null。|
|directReports|[directoryObject](directoryobject.md)集合|用户和联系人的报告给用户。 （用户和具有的管理器属性设置为该用户的联系人。）只读的。 可以为 null。 |
|驱动器|[驱动器](drive.md)|用户的 OneDrive。 只读的。|
|事件|[事件](event.md)集合|用户的事件。 默认值是显示在默认日历下的事件。 只读的。 可以为 null。|
|inferenceClassification|[inferenceClassification](inferenceclassification.md)| 相关用户的邮件分类基于显式指定哪些覆盖推断相关性和重要性。 |
|joinedGroups|[组](group.md)集合| 只读的。 可以为 null。|
|mailFolders|[MailFolder](mailfolder.md)集合| 将用户的邮件文件夹。 只读的。 可以为 null。|
|经理|[directoryObject](directoryobject.md)|用户或联系人，则此用户的经理。 只读的。 (HTTP 方法︰ 获取，放，删除。)|
|memberOf|[directoryObject](directoryobject.md)集合|组、 目录角色和用户所在的管理单位。 只读的。 可以为 null。|
|消息|[消息](message.md)集合|在邮箱或文件夹中的邮件。 只读的。 可以为 null。|
|备注|[备注](notes.md)| 只读的。|
|ownedDevices|[directoryObject](directoryobject.md)集合|由用户拥有的设备。 只读的。 可以为 null。|
|ownedObjects|[directoryObject](directoryobject.md)集合|由用户拥有的目录对象。 只读的。 可以为 null。|
|人员|[人员](person.md)集合| 只读的。 对用户最相关的人员。 通过给用户，由用户的通信、 协作和业务关系确定其相关性排序集合。 一个人是信息的通过邮件、 联系人和社交网络中聚合。|
|照片|[profilePhoto](profilephoto.md)| 用户的个人资料照片。 只读的。|
|照片|[照片](photo.md)集| 只读的。 可以为 null。|
|计划|[计划](plan.md)集合| 只读的。 可以为 null。 与该用户共享的计划。 |
|scopedAdministratorOf|[scopedRoleMembership](scopedrolemembership.md)集合| 此用户范围角色管理单位成员身份。 只读的。 可以为 null。|
|任务|[任务](task.md)集合| 只读的。 可以为 null。 分配给用户的任务。 |
|trendingAround|[driveItem](driveitem.md)集合| 只读的。 可以为 null。|
|workingWith|[用户](user.md)集合| 只读的。 可以为 null。|
|registeredDevices|[directoryObject](directoryobject.md)集合|设备已注册的用户。 只读的。 可以为 null。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "appRoleAssignments",
    "calendar",
    "calendarGroups",
    "calendarView",
    "calendars",
    "contactFolders",
    "contacts",
    "createdObjects",
    "directReports",
    "drive",
    "events",
    "joinedGroups",
    "mailFolders",
    "manager",
    "memberOf",
    "messages",
    "oauth2PermissionGrants",
    "ownedDevices",
    "ownedObjects",
    "photo",
    "registeredDevices"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.user"
}-->

```json
{
  "aboutMe": "string",
  "accountEnabled": true,
  "assignedLicenses": [{"@odata.type": "microsoft.graph.assignedLicense"}],
  "assignedPlans": [{"@odata.type": "microsoft.graph.assignedPlan"}],
  "birthday": "String (timestamp)",
  "businessPhones": ["string"],
  "city": "string",
  "companyName": "string",
  "country": "string",
  "department": "string",
  "displayName": "string",
  "givenName": "string",
  "hireDate": "String (timestamp)",
  "id": "string (identifier)",
  "interests": ["string"],
  "jobTitle": "string",
  "mail": "string",
  "mailboxSettings": {"@odata.type": "microsoft.graph.mailboxSettings"},
  "mailNickname": "string",
  "mobilePhone": "string",
  "mySite": "string",
  "officeLocation": "string",
  "onPremisesImmutableId": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSecurityIdentifier": "string",
  "onPremisesSyncEnabled": true,
  "passwordPolicies": "string",
  "passwordProfile": {"@odata.type": "microsoft.graph.passwordProfile"},
  "pastProjects": ["string"],
  "postalCode": "string",
  "preferredLanguage": "string",
  "preferredName": "string",
  "provisionedPlans": [{"@odata.type": "microsoft.graph.provisionedPlan"}],
  "proxyAddresses": ["string"],
  "responsibilities": ["string"],
  "schools": ["string"],
  "skills": ["string"],
  "state": "string",
  "streetAddress": "string",
  "surname": "string",
  "usageLocation": "string",
  "userPrincipalName": "string",
  "userType": "string",

  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "calendarGroups": [{ "@odata.type": "microsoft.graph.calendarGroup" }],
  "calendarView": [{ "@odata.type": "microsoft.graph.event" }],
  "calendars": [ {"@odata.type": "microsoft.graph.calendar"} ],
  "contacts": [ { "@odata.type": "microsoft.graph.contact" } ],
  "contactFolders": [ { "@odata.type": "microsoft.graph.contactFolder" } ],
  "createdObjects": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "directReports": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "events": [ { "@odata.type": "microsoft.graph.event" } ],
  "inferenceClassification": { "@odata.type": "microsoft.graph.inferenceClassification" },
  "mailFolders": [ { "@odata.type": "microsoft.graph.mailFolder" } ],
  "manager": { "@odata.type": "microsoft.graph.directoryObject" },
  "memberOf": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "messages": [ { "@odata.type": "microsoft.graph.message" } ],
  "ownedDevices": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "registeredDevices": [ { "@odata.type": "microsoft.graph.directoryObject" } ]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
