# <a name="update-extensionproperty"></a>更新 extensionproperty

更新 extensionproperty 对象的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /applications/<id>/extensionProperties/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|appDisplayName|String|            |
|数据类型|String|指定要添加的目录扩展属性的类型。   支持的类型包括︰ 整数、 LargeInteger、 （必须在指定 ISO 8601-存储在 UTC 日期时间） 的日期时间、 二进制文件、 布尔和字符串。|
|isSyncedFromOnPremises|Boolean|指示是否在的内部部署目录中同步的扩展属性。                            **备注**︰ 不可以为 null。            |
|name|String|指定的目录扩展属性显示名称。                            **备注**︰ 不可以为 null。            |
|targetObjects|String|要向其添加目录扩展属性的目录对象。  可以扩展的支持的目录实体是:"用户"、"组"、"组织"、"设备"、"应用程序"和"ServicePrincipal"的**注释**︰ 不可以为 null。            |

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[extensionProperty](../resources/extensionproperty.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_extensionproperty"
}-->
```http
PATCH https://graph.microsoft.com/beta/applications/<id>/extensionProperties/<id>
Content-type: application/json
Content-length: 188

{
  "appDisplayName": "appDisplayName-value",
  "name": "name-value",
  "dataType": "dataType-value",
  "isSyncedFromOnPremises": true,
  "targetObjects": [
    "targetObjects-value"
  ]
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.extensionproperty"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 208

{
  "appDisplayName": "appDisplayName-value",
  "name": "name-value",
  "dataType": "dataType-value",
  "isSyncedFromOnPremises": true,
  "targetObjects": [
    "targetObjects-value"
  ],
  "id": "id-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update extensionproperty",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->