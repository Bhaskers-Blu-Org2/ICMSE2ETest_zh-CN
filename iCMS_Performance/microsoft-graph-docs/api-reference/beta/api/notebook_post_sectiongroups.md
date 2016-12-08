# <a name="create-sectiongroup"></a>创建 sectionGroup

在指定的笔记本中创建新的[分区组](../resources/sectiongroup.md)。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰   
Notes.Create、 Notes.ReadWrite.CreatedByApp、 Notes.ReadWrite 或 Notes.ReadWrite.All
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/notes/notebooks/<id>/sectionGroups
POST /users/<id | userPrincipalName>/notes/notebooks/<id>/sectionGroups
POST /groups/<id>/notes/notebooks/<id>/sectionGroups
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | `Bearer <token>`对基于用户凭据并无授权访问用户的应用程序提供一个有效 OAuth 标记。 |
| 内容类型 | string | `application/json` |

## <a name="request-body"></a>请求正文
在请求正文中，提供的节组的名称。

在同一个层次结构级别，节组的名称必须是唯一的。 名称不能包含超过 50 个字符或包含下列字符︰ ? *\/: <> | & # %~

## <a name="response"></a>响应
如果成功，此方法返回`201 Created`响应代码和一个[sectionGroup](../resources/sectiongroup.md)对象在响应正文中的。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_sectiongroup_from_notebook"
}-->
```http
POST https://graph.microsoft.com/beta/me/notes/notebooks/<id>/sectionGroups
Content-type: application/json
Content-length: 30

{
  "name": "Section group name"
}
```

##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 此处所示的响应对象将被截断为简洁起见。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.sectiongroup"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 305

{
  "sectionsUrl": "sectionsUrl-value",
  "sectionGroupsUrl": "sectionGroupsUrl-value",
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
  "description": "Create SectionGroup",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->