# <a name="create-section"></a>创建分区

指定的节组中创建一个新[节](../resources/section.md)。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰   
Notes.Create、 Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite 或 Notes.ReadWrite.All
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/sectionGroups/<id>/sections
POST /users/<id | userPrincipalName>/notes/sectionGroups/<id>/sections
POST /groups/<id>/notes/sectionGroups/<id>/sections
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |
| 内容类型 | string | `application/json` |

## <a name="request-body"></a>请求正文
在请求正文中，提供该节的名称。

在相同的层次结构级别，节名称必须唯一。 名称不能包含超过 50 个字符或包含下列字符︰ ? *\/: <> | & # %~


## <a name="response"></a>响应
如果成功，此方法返回`201 Created`响应代码和[部分](../resources/section.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_section_from_sectiongroup"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/sectionGroups/<id>/sections
Content-type: application/json
Content-length: 27

{
  "name": "Section name"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 此处所示的响应对象将被截断为简洁起见。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.section"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 272

{
  "isDefault": true,
  "pagesUrl": "pagesUrl-value",
  "name": "name-value",
  "createdBy": "createdBy-value",
  "createdByIdentity": {
    "user": {
      "id": "id-value",
      "displayName": "displayName-value"
    }
  },
  "lastModifiedBy": "lastModifiedBy-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Section",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->