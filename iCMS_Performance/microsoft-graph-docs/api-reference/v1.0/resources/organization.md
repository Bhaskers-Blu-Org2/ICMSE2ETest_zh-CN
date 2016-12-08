# <a name="organization-resource-type"></a>组织资源类型

表示 Azure Active Directory 租户。 只读取和更新操作支持的承租人;创建和删除不受支持。 从[directoryObject](directoryobject.md)继承。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获取组织](../api/organization_get.md) | [组织](organization.md) |读取属性和关系的组织对象。|
|[更新](../api/organization_update.md) | [组织](organization.md)  |更新组织对象。 （可以更新只有**marketingNotificationMails**和**technicalNotificationMails**的属性）。 |

## <a name="properties"></a>属性

| 属性                             | 类型                                                              | 说明                                                                                                                                                                                                                                                                          |
|:-------------------------------------|:------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| assignedPlans                        | [assignedPlan](assignedplan.md)集合                        | 与租户相关的服务计划的集合。 不可以为 null。                                                                                                                                                                                                            |
| 市/县                                 | String                                                            |                                                                                                                                                                                                                                                                                      |
| companyLastDirSyncTime               | 方法                                                    | 在租户最后一次与后端目录同步的日期和时间。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'` |
| 国家/地区                              | String                                                            |                                                                                                                                                                                                                                                                                      |
| countryLetterCode                    | String                                                            |                                                                                                                                                                                                                                                                                      |
| deletionTimestamp                    | 方法                                                    | 时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`                                                                                     |
| dirSyncEnabled                       | Boolean                                                           | **如此**如果此对象同步从本地目录中。**假**如果此对象最初从内部目录同步，但不会再同步;**null**如果该对象已永远不会从内部目录 （默认值） 进行同步。                        |
| 显示名称                          | String                                                            | 对于组织显示名称。                                                                                                                                                                                                                                                     |
| id                                   | String                                                            | 组织的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键。 不可以为 null。 只读的。                                                                                                                                                            |
| marketingNotificationEmails          | 字符串集合                                                 | 不可以为 null。                                                                                                                                                                                                                                                                        |
| 对象类型                           | String                                                            | 一个字符串，标识对象类型。 承租人的值始终为"公司"。                                                                                                                                                                                                 |
| 邮政编码                           | String                                                            |                                                                                                                                                                                                                                                                                      |
| preferredLanguage                    | String                                                            |                                                                                                                                                                                                                                                                                      |
| provisionedPlans                     | [ProvisionedPlan](provisionedplan.md)集合                  | 不可以为 null。                                                                                                                                                                                                                                                                        |
| provisioningErrors                   | ProvisioningError 集合 | 不可以为 null。                                                                                                                                                                                                                                                                        |
| securityComplianceNotificationMails  | 字符串集合                                                 |                                                                                                                                                                                                                                                                                      |
| securityComplianceNotificationPhones | 字符串集合                                                 |                                                                                                                                                                                                                                                                                      |
| 状态                                | String                                                            |                                                                                                                                                                                                                                                                                      |
| 街道                               | String                                                            |                                                                                                                                                                                                                                                                                      |
| technicalNotificationMails           | 字符串集合                                                 | 不可以为 null。                                                                                                                                                                                                                                                                        |
| telephoneNumber                      | String                                                            |                                                                                                                                                                                                                                                                                      |
| verifiedDomains                      | [VerifiedDomain](verifieddomain.md)集合                    | 与该组织相关联的域的集合。 不可以为 null。                                                                                                                                                                                                                 |

## <a name="relationships"></a>Relationships
无

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.organization"
}-->

```json
{
  "assignedPlans": [{"@odata.type": "microsoft.graph.assignedPlan"}],
  "businessPhones": ["string"],
  "city": "string",
  "country": "string",
  "countryLetterCode": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "marketingNotificationEmails": ["string"],
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "postalCode": "string",
  "preferredLanguage": "string",
  "provisionedPlans": [{"@odata.type": "microsoft.graph.provisionedPlan"}],
  "securityComplianceNotificationMails": ["string"],
  "securityComplianceNotificationPhones": ["string"],
  "state": "string",
  "street": "string",
  "technicalNotificationMails": ["string"],
  "verifiedDomains": [{"@odata.type": "microsoft.graph.verifiedDomain"}]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "organization resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
