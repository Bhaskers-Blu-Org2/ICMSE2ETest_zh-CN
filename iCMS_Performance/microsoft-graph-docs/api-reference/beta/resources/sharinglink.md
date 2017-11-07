# <a name="sharinglink-resource-type"></a>sharingLink 资源类型

提供信息的共享链接项。


## <a name="properties"></a>属性

| 属性    | 类型                    | 说明                                                                                                                                                                                             |
|:------------|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| application | [标识](identity.md) | 关联应用程序的链接。                                                                                                                                                                    |
| 类型        | String                  | 创建的链接类型。                                                                                                                                                                           |
| scope       | String                  | 由该权限表示的链接范围。 值`anonymous`表示该链接是由任何人，`organization`指示链接为仅适用于登录到同一个租户的用户。 |
| webUrl      | String                  | 在 OneDrive 网站上的浏览器中打开的项目的 URL。                                                                                                                                       |


## <a name="type-enumeration"></a>类型枚举

下表定义了该**类型**属性的可能值︰

| 值   | 角色    | 说明                                                                     |
|:--------|:--------|:--------------------------------------------------------------------------------|
| `view`  | `read`  | 仅可查看的共享链接，允许进行只读访问。                            |
| `edit`  | `write` | 编辑共享链接，允许读写访问权限。                               |

## <a name="scope-enumeration"></a>作用域枚举

| 值          | 说明                                                                                                                 |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------|
| `anonymous`    | 共享链接仅供任何人使用。                                                                            |
| `organization` | 共享链接仅供同一组织 （租户） 使用中的任何人。 OneDrive 个人不可用。 |


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "application", "scope" ],
  "@odata.type": "microsoft.graph.sharingLink"
}-->

```json
{
  "application": {"@odata.type": "microsoft.graph.identity"},
  "type": "view | edit",
  "scope": "anonymous | organization",
  "webUrl": "url"
}
```



<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharingLink resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
