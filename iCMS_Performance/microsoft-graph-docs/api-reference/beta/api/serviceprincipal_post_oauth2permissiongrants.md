# <a name="create-oauth2permissiongrant"></a>创建 oAuth2Permissiongrant

使用此 API 来创建新的 oAuth2Permissiongrant。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /servicePrincipals/<id>/oAuth2Permissiongrants

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文，提供[oAuth2Permissiongrant](../resources/oAuth2Permissiongrant.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[oAuth2Permissiongrant](../resources/oAuth2Permissiongrant.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_oAuth2Permissiongrant_from_serviceprincipal"
}-->
```http
POST https://graph.microsoft.com/beta/servicePrincipals/<id>/oAuth2Permissiongrants
Content-type: application/json
Content-length: 180

{
  "clientId": "clientId-value",
  "consentType": "consentType-value",
  "expiryTime": "datetime-value",
  "principalId": "principalId-value",
  "resourceId": "resourceId-value"
}
```
在请求正文，提供[oAuth2Permissiongrant](../resources/oAuth2Permissiongrant.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.oAuth2Permissiongrant"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 200

{
  "clientId": "clientId-value",
  "consentType": "consentType-value",
  "expiryTime": "datetime-value",
  "id": "id-value",
  "principalId": "principalId-value",
  "resourceId": "resourceId-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create oAuth2Permissiongrant",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->