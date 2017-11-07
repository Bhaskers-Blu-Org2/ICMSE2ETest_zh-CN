# <a name="create-group"></a>创建组

使用此 API 来创建新的组指定请求主体中。 您可以创建一个 3 种类型的组︰
* Office 365 组 （也称为统一组）
* 动态组
* 安全组

至少，您必须指定要创建的组类型所需的属性。 这包括︰

| 组类型 | **groupTypes**属性 | **securityEnabled**属性 | **mailEnabled**属性 |
|:--------------|:------------------------|:-----------------------------|:-------------------------|
| Office 365 | "统一" | false | true |
| 动态 | "DynamicMembership" | true | false |
| 安全性 | 未设置。 | true | false |

有关详细信息，请参阅[组](../resources/group.md)资源的属性。
### <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ _Group.ReadWrite.All_ 
### <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups
```
### <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

### <a name="request-body"></a>请求正文
在请求正文中，提供[组](../resources/group.md)对象的 JSON 的表示。

下表显示当您创建一个组时所需的属性。

| 参数 | 类型 | 说明|
|:---------------|:--------|:----------|
| 显示名称 | string | 要在通讯簿的组中显示的名称。 |
| mailEnabled | 布尔 | 设置为**true**的已启用邮件的组。 |
| mailNickname | string | 组中的邮件别名。 |
| securityEnabled | 布尔 | 设置为**true**已启用安全性的组。 如果创建一个 Office 365 的组，则设置为**false** 。 |

### <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[组](../resources/group.md)对象。

### <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_group_from_groups"
}-->
```http
POST https://graph.microsoft.com/beta/groups
Content-type: application/json
Content-length: 244

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "Unified"
  ],
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "securityEnabled": false
}
```
在请求正文中，提供[组](../resources/group.md)对象的 JSON 的表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.group"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 244

{
  "description": "description-value",
  "displayName": "displayName-value",
  "groupTypes": [
    "Unified"
  ],
  "mail": "mail-value",
  "mailEnabled": true,
  "mailNickname": "mailNickname-value",
  "securityEnabled": false
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
