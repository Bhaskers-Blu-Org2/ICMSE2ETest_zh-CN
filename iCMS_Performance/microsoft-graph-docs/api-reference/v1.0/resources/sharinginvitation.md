# <a name="sharinginvitation-resource-type"></a>sharingInvitation 资源类型

表示一组权限的共享邀请有关的信息。 该对象是只读的。


## <a name="properties"></a>属性

| 属性名称  | 类型                          | 说明                                                                                                                   |
|:---------------|:------------------------------|:------------------------------------------------------------------------------------------------------------------------------|
| 电子邮件          | String                        | 提供有关共享邀请的收件人电子邮件地址。 只读的。                                          |
| invitedBy      | [identitySet](identityset.md) | 提供了有关发件人创建此权限，邀请该信息是否可用的信息。 只读的。 |
| signInRequired | Boolean                       | 如果`true`邀请的收件人需要登录才能访问共享的项目。 只读的。                     |

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.sharingInvitation"
}-->

```json
{
  "email": "string",
  "redeemedBy": "string",
  "signInRequired": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharingInvitation resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
