# <a name="delete-connectorgroup"></a>删除 connectorGroup

删除 connectorGroup。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.ReadWrite.All 或 Directory.AccessAsUser.All*

> **注意︰**连接器组不能有与之相关联的任何连接器。

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
DELETE /connectorGroups/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| 授权  | 持有者。 是否必需|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。


## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "delete_connectorgroup"
}-->
```http
DELETE https://graph.microsoft.com/{ver}/connectorGroups/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Delete connectorGroup",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
