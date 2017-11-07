# <a name="notes-resource-type"></a>备注的资源类型

OneNote 资源的入口点。

所有到 OneNote 服务通过 Microsoft Graph API 调用使用此服务根 URL:

```
https://graph.microsoft.com/<version>/<location>/notes/ 
```

OneNote 支持是在预览中，因此始终是版本`beta`。 

只有用户和组笔记本在 Office 365 提供支持。 当前不支持访问 OneDrive 或 SharePoint 网站宿主的笔记本电脑使用者笔记本。 

**用户的笔记本电脑**若要访问个人笔记本业务的 OneDrive，请使用以下 Url 之一︰

```
https://graph.microsoft.com/beta/me/notes/<notebooks | sections | sectionGroups | pages> 
https://graph.microsoft.com/beta/users/<userPrincipalName>/notes/<notebooks | sections | sectionGroups | pages> 
https://graph.microsoft.com/beta/users/<id>/notes/<notebooks | sections | sectionGroups | pages> 
```

**组的笔记本**若要访问笔记本所拥有的组，请使用以下服务根 URL:

```
https://graph.microsoft.com/beta/groups/<id>/notes/<notebooks | sections | sectionGroups | pages> 
```

以下权限范围提供的 OneNote 笔记本的访问级别。 同时选择权限范围取决于您目标笔记本和应用程序的功能的位置上。 

**OneDrive 为企业所拥有的当前用户的个人笔记本的作用域**

| 作用域 （企业） | 在 Azure 门户的权限 | 说明 |
|:-------|:------|:------|
| Notes.Create | 创建网页，用户的笔记本电脑 （预览） | 可以查看对您的笔记本和分区; 职务在任何位置创建新页。 不能查看或编辑现有的网页。 |
| Notes.ReadWrite.CreatedByApp | 有限的笔记本电脑访问 （预览） | 可以查看对您的笔记本和分区; 职务创建新的页面; 例如︰查看和修改所创建的应用程序页。 不能查看或修改由其他应用程序或密码保护的分区中创建的页。 |
| Notes.Read | 读取用户的笔记本电脑 （预览） | 可以查看您的笔记本和分区的内容。 无法创建新的页面; 例如︰修改现有的页面; 例如︰访问密码保护的部分。 |
| Notes.ReadWrite | 读取和写入用户笔记本 （预览） | 可以查看对您的笔记本和分区; 职务查看和修改所有页面;创建新页。 不能访问受密码保护的分区。 |

**由其他用户和组笔记本的当前用户可以访问共享的个人笔记本的作用域**

| 作用域 （企业） | 在 Azure 门户的权限 | 说明 |
|:-------|:------|:------|
| Notes.Read.All | 读取用户可以访问的所有笔记本 （预览） | 可以在已登录的用户有权访问的所有笔记本电脑查看笔记本和分区的内容。 无法创建新的页面; 例如︰修改现有的页面; 例如︰访问密码保护的部分。 |
| Notes.ReadWrite.All | 读取和写入笔记本用户都可以访问 （预览） | 可以查看标题的笔记本和分区;查看和修改所有页面; 例如︰在已登录的用户有权访问的所有笔记本中创建新页。 不能访问受密码保护的分区。 |

**注意︰**目前不支持通过图形 API 访问 SharePoint 站点的笔记本。

**作用域的组**

如果您正在访问组笔记本，您将需要组的权限范围内，获取组 id。 目前，这些权限需要管理员权限。

| 作用域 （企业） | 在 Azure 门户的权限 | 说明 |
|:-------|:------|:------|
| Group.Read.All | 读取所有组 | 可以读取所有组属性和成员身份;读取组日历和公用组和登录的用户组的成员的对话。 |
| Group.ReadWrite.All | 读取和写入的所有组 | 可以创建代表已登录的用户的组和读取所有组属性和成员身份;更新组属性和组成员身份中已登录的用户拥有;读取和写入公用组和已登录的用户是其成员的组的组日历和对话。 |

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "notebooks",
    "pages",
    "resources",
    "sectionGroups",
    "sections"
  ],
  "@odata.type": "microsoft.graph.notes"
}-->

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|笔记本|[笔记本](notebook.md)集合|OneNote 笔记本所负责的用户或组的集合。 只读的。 可以为 null。|
|操作|[操作](notesoperation.md)集合 |OneNote 操作的状态。 不支持获取操作集合，但您可以获取长时间运行操作的状态，如果`Operation-Location`在响应中返回的文件头。 只读的。 可以为 null。|
|页面|[页](page.md)集合|由该用户或组拥有的所有 OneNote 笔记本中的页面。  只读的。 可以为 null。|
|资源|[资源](resource.md)集合 |该图像并在 OneNote 页中其他文件的资源。 不支持获取资源集合，但您可以[获得特定资源的二进制内容](resource.md)。 只读的。 可以为 null。|
|sectionGroups|[SectionGroup](sectiongroup.md)集合|在所有 OneNote 笔记本中所拥有的用户或组的节组。  只读的。 可以为 null。|
|Sections|[部分](section.md)集合|由该用户或组拥有的所有 OneNote 笔记本中的部分。  只读的。 可以为 null。|


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[创建笔记本](../api/notes_post_notebooks.md) |[笔记本](notebook.md)| 由过账到笔记本集合创建一个笔记本。|
|[列表的笔记本](../api/notes_list_notebooks.md) |[笔记本](notebook.md)集合| 获取一个标记集合的笔记本。|
|[创建页](../api/notes_post_pages.md) |[页面](page.md)| 由过账到 pages 集合中创建的页。|
|[列表页](../api/notes_list_pages.md) |[页](page.md)集合| 获取页面的集合。|
|[列表中的节组](../api/notes_list_sectiongroups.md) |[SectionGroup](sectiongroup.md)集合| 获取集合中的节组。|
|[列表中的节](../api/notes_list_sections.md) |[部分](section.md)集合| 获得的部分的集合。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "notes resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
