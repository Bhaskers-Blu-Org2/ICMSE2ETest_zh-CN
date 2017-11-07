# <a name="update-administrativeunit"></a>更新 administrativeunit

更新[administrativeUnit](../resources/administrativeunit.md)对象的属性。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /administrativeUnits/<id>
```
## <a name="optional-request-headers"></a>可选的请求标头
## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|description|string|描述管理单元。|
|显示名称|string|管理单元的显示名称。|
|visibility|string|管理部门的可见性。 如果，未设置默认值为"公用"。 可以设置为"HiddenMembership"，隐藏来自非成员的成员资格。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[administrativeUnit](../resources/administrativeunit.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_administrativeunit"
}-->
```http
PATCH https://graph.microsoft.com/beta/administrativeUnits/<id>
Content-type: application/json
Content-length: 114

{
  "displayName": "displayName-value",
  "description": "description-value",
  "visibility": "visibility-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.administrativeunit"
} -->
```http
HTTP/1.1 204 No content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update administrativeunit",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->