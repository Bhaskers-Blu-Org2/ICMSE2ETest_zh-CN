# <a name="list-directorysettingtemplates"></a>列表 directorySettingTemplates

设置模板的目录表示一组目录的设置，从哪个目录设置可能创建并在组织内使用的模板。  此操作将检索可用 directorySettingTemplates 对象的列表。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.Read.All*或*Directory.ReadWrite.All*或*Directory.AccessAsUser.All*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /directorySettingTemplates
```
## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和响应正文中的[directorySettingTemplate](../resources/directorysettingtemplate.md)对象的集合。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_directorysettingtemplates"
}-->
```http
GET https://graph.microsoft.com/beta/directorySettingTemplates
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.directorySettingTemplate",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 343

{
  "value": [
    {
      "id": "id-value",
      "displayName": "displayName-value",
      "description": "description-value",
      "values": [
        {
          "name": "name-value",
          "type": "type-value",
          "defaultValue": "defaultValue-value",
          "description": "description-value"
        }
      ]
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List directorySettingTemplates",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->