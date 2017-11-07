# <a name="approleassignment-resource-type"></a>appRoleAssignment 资源类型

用于记录当用户或组分配给应用程序。 在这种情况下，角色分配将导致应用程序图块中显示了用户的应用程序访问面板上。 此实体还可能用于授予另一个应用程序 （即主体服务建模） 访问资源应用程序处于特定的角色。 您可以创建、 读取、 更新和删除角色分配。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.approleassignment"
}-->

```json
{
  "creationTimestamp": "String (timestamp)",
  "id": "guid (identifier)",
  "principalDisplayName": "string",
  "principalId": "guid",
  "principalType": "string",
  "resourceDisplayName": "string",
  "resourceId": "guid"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|creationTimestamp|方法|授予创建时的时间。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|id|Guid|已分配给该主体角色 id。  此角色必须声明通过其**appRoles**属性在目标资源应用程序**资源 Id** 。 其中资源没有声明任何权限，必须指定一个默认 id (零 GUID)。 键。 不可以为 null。 |
|principalDisplayName|String|被授予访问权的主体显示名称。|
|principalId|Guid|唯一标识符 (**id**) 被授予访问权限的主体。 需要创建。            |
|principalType|String|主体的类型。  这可以是"用户"、"组"或"ServicePrincipal"。|
|resourceDisplayName|String|对其进行分配的资源显示名称。|
|资源 Id|Guid|目标资源 （服务主体） 对其进行分配唯一标识符 (**id**)。|

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 appRoleAssignment](../api/approleassignment_get.md) | [appRoleAssignment](approleassignment.md) |读取属性和关系的 appRoleAssignment 对象。|
|[更新](../api/approleassignment_update.md) | [appRoleAssignment](approleassignment.md)   |更新 appRoleAssignment 对象。 |
|[删除](../api/approleassignment_delete.md) | 无 |删除 appRoleAssignment 对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "appRoleAssignment resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->