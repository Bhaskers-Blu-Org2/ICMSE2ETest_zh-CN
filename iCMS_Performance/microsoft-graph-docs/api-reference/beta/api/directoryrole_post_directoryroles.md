# <a name="activate-directoryrole"></a>激活 directoryRole

激活目录角色。 若要读取目录角色或更新它的成员，它必须首先激活在租户。 只有公司的管理员和隐式的用户目录角色会激活默认情况下。 若要将成员分配到另一个目录角色访问，您必须首先激活它用其相应的目录角色模板 ([directoryRoleTemplate](../resources/directoryroletemplate.md))。

## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Directory.ReadWrite.All*或*Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /directoryRoles

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文，提供[directoryRole](../resources/directoryrole.md)对象的 JSON 表示。

下表显示当您激活目录角色时所需的属性。

|必选的参数 | 类型 | 说明|
|:---------|:---------|:---------|
|roleTemplateId | string | [DirectoryRoleTemplate](../resources/directoryroletemplate.md)基于角色的 ID。 这是唯一可能请求中指定的属性。|


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[directoryRole](../resources/directoryrole.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_directoryrole_from_directoryroles"
}-->
```http
POST https://graph.microsoft.com/beta/directoryRoles
Content-type: application/json
Content-length: 153

{
  "description": "description-value",
  "displayName": "displayName-value",
  "roleTemplateId": "roleTemplateId-value"
}
```
在请求正文，提供[directoryRole](../resources/directoryrole.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directoryRole"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 175

{
  "description": "description-value",
  "displayName": "displayName-value",
  "roleTemplateId": "roleTemplateId-value",
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create directoryRole",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
