# <a name="privilegedoperationevent-resource-type"></a>privilegedOperationEvent 资源类型

表示由特权身份管理对于角色的操作，例如，管理员可以管理特权的角色、 用户激活他的角色，和用户停用他的职责的审核事件。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[列表 privilegedOperationEvent](../api/privilegedoperationevent_list.md) | [privilegedOperationEvent](privilegedoperationevent.md)集合。 |获得 privilegedOperationEvent 对象的集合。|

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|additionalInformation|string|该事件的详细人类可读信息。|
|creationDateTime|方法|指示事件在创建时的时间。|
|expirationDateTime|方法|RequestType 是"提升"，并指明角色激活过期时间时才使用此选项。|
|id|string|PrivilegedOperationEvent 的唯一标识符。 只读的。|
|referenceKey|string|在角色激活事件中的请求票证编号。 只有当角色激活期间提供的票据号码显示值。|
|referenceSystem|string|事故/请求票证系统 tole 激活期间提供。 角色在激活期间提供票证系统时，才显示值。|
|requestType|string|请求的操作类型。 示例类型可以是︰ 分配 (角色分配)、 提升 （角色激活）、 取消分配 (删除角色分配) 和 Unelevate （角色停用）。|
|requestorId|string|请求程序启动该操作的用户的 id。|
|requestorName|string|请求程序启动该操作的用户名。|
|roleId|string|与此操作相关联的角色的 id。|
|角色名|string|角色的名称。|
|tenantId|string|（组织） 租户 id。|
|用户 Id|string|与操作关联的用户 id。|
|userMail|string|用户的电子邮件。|
|用户名|string|用户的显示名称。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.privilegedOperationEvent"
}-->

```json
{
  "additionalInformation": "string",
  "creationDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "requestType": "string",
  "requestorId": "string",
  "requestorName": "string",
  "roleId": "string",
  "roleName": "string",
  "tenantId": "string",
  "userId": "string",
  "userMail": "string",
  "userName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "privilegedOperationEvent resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
