# <a name="update-group"></a>更新组

更新组对象的属性。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Group.ReadWrite.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /groups/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|allowExternalSenders|Boolean|默认值为**false**。 指示外部成员可以向组发送电子邮件。|
|autoSubscribeNewMembers|Boolean|默认值为**false**。 指示将自动订阅接收电子邮件通知将新成员添加到组中。|
|description|字符串|组的可选说明。 |
|显示名称|String|组的显示名称。 将创建一个组并在更新过程中不能清除时，该属性是必需的。 $Filter 和 $orderby 的支持。|
|groupTypes|字符串集合|指定要创建组的类型。 可能的值为动态组**统一**创建 Office 365 组或**DynamicMembership** 。  对于所有其他组类型，如已启用安全性的组，并启用了电子邮件的安全组，不设置此属性。|
|visibility|Boolean|指定 Office 365 组的可见性。 可能的值有︰**私有**、**公共**、 或空 （这将被解释为**公用**）。|
|mailEnabled|Boolean|指定是否已启用邮件的组。 组的**securityEnabled**属性也是**如此**，如果是已启用邮件的安全组;否则，组是 Microsoft Exchange 通讯组。|
|mailNickname|String|组中的邮件别名。 在创建组时，必须指定此属性。 支持 $filter。|
|securityEnabled|Boolean|指定组是否是一个安全组。 组的**mailEnabled**属性也是如此，如果是已启用邮件的安全组;否则，它是一个安全组。 必须为**false**的 Office 365 组。 支持 $filter.|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[组](../resources/group.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_group"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/groups/<id>
Content-type: application/json
Content-length: 211

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.group"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 211

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "groupTypes-value"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->