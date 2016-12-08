# <a name="directoryrole-resource-type"></a>directoryRole 资源类型

表示一个 Azure 的广告目录角色。 Azure 的广告目录角色也称为是*管理员角色*。 有关目录 （管理员） 角色的详细信息，请参阅[在 Azure 的广告分配管理员角色](http://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/)。 使用 Microsoft Graph 中，可以将用户分配给目录角色的目标角色的权限授予他们。 若要读取目录角色或更新它的成员，它必须首先激活在租户。 默认情况下，只有公司管理员目录角色被激活。 若要激活其他可用的目录角色，您发送 POST 请求 id 为[directoryRoleTemplate](directoryroletemplate.md)的目录角色所依据。 从[directoryObject](directoryobject.md)继承。

默认情况下，目录角色的范围内，为租户范围。  但是，目录角色 （当前仅*用户帐户管理员*和*帮助台管理员*） 可能还仅限于[管理单位](administrativeunit.md)。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 directoryRole](../api/directoryrole_get.md) | [directoryRole](directoryrole.md) |读取属性和关系的 directoryRole 对象。|
|[添加成员](../api/directoryrole_post_members.md) |[directoryObject](directoryobject.md)| 由过账到成员导航属性添加到目录角色的用户。|
|[列表成员](../api/directoryrole_list_members.md) |[directoryObject](directoryobject.md)集合| 获取成员的成员导航属性中的目录角色的用户。|
|[列出指定了作用域的管理员](../api/directoryrole_list_scopedadministrators.md) |[scopedRoleMembership](scopedrolemembership.md)集合| 列出此目录角色的范围的[管理单位](administrativeunit.md)，通过 scopedRoleMembership 对象集合的成员。|
< ！-|[删除成员](../api/directoryrole_delete_members.md) |[directoryObject](directoryobject.md)| 用户从角色中删除目录按过帐到成员导航属性。|-->

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|description|字符串|对目录角色的说明。 只读的。 |
|显示名称|String|目录角色的显示名称。 只读的。 |
|id|String|目录角色的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键，不可以为 null 的只读。|
|roleTemplateId|String| 此角色基于[directoryRoleTemplate](directoryroletemplate.md) **id** 。 激活目录角色在 POST 操作与租户时，必须指定的属性。 激活目录角色后，该属性是只读属性。 |

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|成员|[directoryObject](directoryobject.md)集合|此目录角色成员的用户。 HTTP 方法︰ 获取、 发布、 删除。 只读的。 可以为 null。|
|scopedAdministrators|[scopedRoleMembership](scopedrolemembership.md)集合| 范围[管理单位](administrativeunit.md)对此目录角色的管理员。 只读的。 可以为 null。|

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "memberOf",
    "members",
    "ownedObjects",
    "owners"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.directoryRole"
}-->

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "roleTemplateId": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directoryRole resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
