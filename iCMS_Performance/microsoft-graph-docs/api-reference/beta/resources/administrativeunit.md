# <a name="administrativeunit-resource-type"></a>administrativeUnit 资源类型

一个管理单元提供用户和组目录对象概念的容器。 使用管理单位，公司管理员现在可以委派管理职责，可以管理用户和组内包含或范围限于给地区或部门管理员的管理单位。 

让我们看一个示例。 假设 Contoso 公司由构成的两个部门的除西海岸和东海岸部。 在 Contoso 的目录角色作用于整个组织。 Lee，Contoso 公司管理员，想要委派管理职责，但其范围到西海岸划分或东海岸除。  Lee 可以创建一个*西海岸 admistrative 单元*并放入这个管理单元的西海岸的所有用户。  同样，Lee 可以创建一个*东海岸管理单位*。  现在，先生，可以开始委派管理职责给其他人，但向新管理单元**范围内**他时才创建。 Lee 将珍珍放在*帮助台管理员*角色**作用**于*西海岸管理单元*。  这使珍妮弗重置任何用户的密码，但如果这些用户位于*西海岸管理单元*。  同样，Lee 在 Dave*用户帐户管理员*角色**作用**于*东海岸管理单元*。  这样，Dave 来更新用户、 分配许可证和重置任何用户的密码，但如果这些用户是在*东海岸管理单元*中。 视频的概述，请参阅[介绍到 Azure 活动目录管理单元](https://channel9.msdn.com/Series/Windows-Azure-Active-Directory/Introduction-to-Azure-Active-Directory-Administrative-Units)。

本主题提供声明的属性和公开的 administrativeUnit 实体，以及操作和函数可以调用 administrativeUnits 资源的导航属性的说明。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[创建 administrativeUnit](../api/administrativeunit_post_administrativeunits.md) | [administrativeUnit](administrativeunit.md) | 创建一个新的管理单元。|
|[列表 administrativeUnits](../api/administrativeunit_list.md) | [administrativeUnit](administrativeunit.md)集合 |列出所有的 administrativeUnits 的属性。|
|[获得 administrativeUnit](../api/administrativeunit_get.md) | [administrativeUnit](administrativeunit.md) |读取属性和特定的 administrativeUnit 对象的关系。|
|[更新 adminstrativeUnit](../api/administrativeunit_update.md) | [administrativeUnit](administrativeunit.md)  |更新 administrativeUnit 对象。 |
|[删除 adminstrativeUnit](../api/administrativeunit_delete.md) | 无 |删除 administrativeUnit 对象。 |
|[添加成员](../api/administrativeunit_post_members.md) |[directoryObject](directoryObject.md)| 添加成员 （用户或组）。|
|[列表成员](../api/administrativeunit_list_members.md) |[directoryObject](directoryObject.md)集合| 获取列表中的成员 （用户和组） 的成员。|
|[获取成员](../api/administrativeunit_get_members.md) |[directoryObject](directoryObject.md)| 获取特定成员。|
|[删除成员](../api/administrativeunit_delete_members.md) |[directoryObject](directoryObject.md)| 删除成员。|
|[添加作用域角色管理员](../api/administrativeunit_post_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)| 添加作用域角色管理员。|
|[列表范围角色管理员](../api/administrativeunit_list_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)集合| 获取范围角色管理员列表。|
|[获取范围角色管理员](../api/administrativeunit_get_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)| 获取特定的作用域角色管理员。|
|[删除作用域角色管理器](../api/administrativeunit_delete_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)| 删除作用域角色管理器。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|description|string|管理单元可选说明。|
|显示名称|string|管理单元的显示名称。|
|id|string|管理部门的唯一标识符。 只读的。|
|visibility|string|控制是否隐藏管理单元和它的成员或公众。 可以设置为 HiddenMembership 或公共。 如果没有设置，默认行为是公众。 如果设置为 HiddenMembership，只有管理单元的成员可以列出的管理部门中的其他成员。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|成员|[directoryObject](directoryObject.md)集合|用户和组是此 Adminsitrative 单元的成员。 HTTP 方法︰ 获取 （列表中的成员），开机自检 （添加成员），删除 （删除成员）。|
|scopedAdministrators|[scopedRoleMembership](scopedrolemembership.md)集合| 此管理单元的范围的管理员。  HTTP 方法︰ 获取 (列表 scopedRoleMemberships)，开机自检 （添加 scopedRoleMembership），删除 (删除 scopedRoleMembership)。 |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.administrativeunit"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "visibility": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "administrativeUnit resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->