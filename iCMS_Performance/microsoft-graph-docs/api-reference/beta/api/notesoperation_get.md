# <a name="get-notesoperation"></a>获得 notesOperation


获取长时间运行 OneNote 操作的状态。 这适用于如在响应中，返回的**操作位置**标头的操作`CopyNotebook`， `CopyToNotebook`， `CopyToSectionGroup`， `and CopyToSection`。   

可以轮询操作位置直到终点`status`属性返回`completed`或`failed`。 

如果状态是`completed`，`resourceLocation`属性包含资源端点的 URI。 

如果状态是`failed`，错误和`@api.diagnostics`属性提供错误的信息。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰  
Notes.Read、 Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite、 Notes.Read.All 或 Notes.ReadWrite.All  
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/notes/operations/<id>
GET /users/<id | userPrincipalName>/notes/operations/<id>
GET /groups/<id>/notes/operations/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
无。

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |
| 接受 | string | `application/json` | 

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和[notesOperation](../resources/notesoperation.md)对象在响应正文中的。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "get_notesoperation"
}-->
```http
GET https://graph.microsoft.com/beta/me/notes/operations/<id>
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.notesoperation"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 215

{
  "id": "id-value",
  "status": "status-value",
  "createdDateTime": "datetime-value",
  "lastActionDateTime": "datetime-value",
  "resourceLocation": "resourceLocation-value",
  "resourceId": "resourceId-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get notesOperation",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->