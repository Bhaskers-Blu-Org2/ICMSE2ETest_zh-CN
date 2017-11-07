# <a name="create-a-directory-setting"></a>创建目录设置

使用此 API 来创建新的设置，根据 directorySettingTemplates 中可用的模板。 这些设置可以在组织级别也可以在对象级别 (目前只能针对组)。 创建请求必须提供 settingValues 模板中定义的所有设置。 对于特定组的设置，仅设置控制是否邀请来宾用户组的成员可以进行设置。 向组中添加来宾用户的能力一旦上市，这将控制此行为。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.ReadWrite.All*或*Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /settings
POST /groups/<id>/settings
```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
在请求正文，提供[directorySetting](../resources/directorysetting.md)对象的 JSON 表示。  但是，设置为显示名称将基于在引用的设置模板名称。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`响应代码和[directorySetting](../resources/directorysetting.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_directorysetting_from_settings"
}-->
```http
POST https://graph.microsoft.com/beta/settings
Content-type: application/json
Content-length: 222

{
  "templateId": "templateId-value",
  "values": [
    {
      "name": "name-value",
      "value": "value-value"
    }
  ]
}
```
在请求正文，提供[directorySetting](../resources/directorysetting.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directorySetting"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 244

{
    "@odata.context": "https://graph.microsoft.com/stagingbeta/$metadata#settings/$entity",
    "id": "id-value",
    "displayName": "displayName-value",
    "templateId": "templateId-value",
    "values": [
      {
        "name": "name-value",
        "value": "value-value"
      }
    ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create directorySetting",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->