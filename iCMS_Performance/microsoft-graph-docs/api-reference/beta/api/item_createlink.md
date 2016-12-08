# <a name="create-a-sharing-link-for-a-driveitem"></a>创建 driveItem 的共享链接

您可以使用**createLink**操作共享通过链接项。

如果调用应用程序指定的链接类型尚不存在， **createLink**操作将创建新的共享链接。 如果应用程序已存在指定的类型的共享链接，则返回现有的共享链接。

项目从其祖先继承权限。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.ReadWrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/drive/items/{item-id}/createLink
POST /me/drive/root:/{item-path}:/createLink
POST /groups/<id>/drive/items/<item-id>/createLink
```

## <a name="request-headers"></a>请求标头

| 名称          | 类型   | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
请求的正文定义共享正在寻找您的应用程序的链接的类型。 该请求应具有此属性的 JSON 对象。

| 名称   | 类型   | 说明                                                          |
|:-------|:-------|:---------------------------------------------------------------------|
| **类型** | string | 共享链接创建的类型。 Either `view`, `edit`, or `embed`. |
| **作用域** | string | 要创建的链接范围。 无论是`anonymous`或`organization`。 可选项。 |

## <a name="link-types"></a>链接类型
**类型**参数可以为下列的值。

| 类型值 | 说明                                                                                  |
|:-----------|:---------------------------------------------------------------------------------------------|
| `view`     | 创建只读的链接到项目。                                                        |
| `edit`     | 创建指向项目的读写。                                                       |
| `embed`    | 创建指向项目的嵌入链接。 此选项才可用的 OneDrive 个人。 |

## <a name="scope-types"></a>作用域类型
为**作用域**参数允许下列值。 这是一个可选参数。 如果不指定**scope**参数，则将创建的最大权限的链接。

| 类型值     | 说明                                                                                                                   |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------|
| `anonymous`    | 创建指向该项目的任何用户都可以访问。 租户管理员可能禁用了匿名的链接。                 |
| `organization` | 创建该项的链接可以访问组织内。 组织链路作用域不可用于 OneDrive 个人。 |

## <a name="response"></a>响应

如果成功，此方法将返回一个[权限](../resources/permission.md)资源请求的共享链接权限表示响应正文中。

服务将首先看看当前的权限，并检查是否已经存在具有相同的**类型**调用应用程序。

响应将是`201 Created`的物料如果新的共享创建链接或`200 OK`如果返回现有的链接。

## <a name="example"></a>示例
这里是如何调用此 API 的示例。

##### <a name="request"></a>请求
下面是示例请求。

<!-- {
  "blockType": "request",
  "name": "item_createlink"
}-->
```http
POST /drive/root:/{item-path}:/createLink
Content-type: application/json

{
  "type": "view",
  "scope": "anonymous"
}
```

##### <a name="response"></a>响应

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.permission" } -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "123ABC",
  "roles": ["write"],
  "link": {
    "type": "view",
    "scope": "anonymous",
    "webUrl": "https://onedrive.live.com/redir?resid=5D33DD65C6932946!70859&authkey=!AL7N1QAfSWcjNU8&ithint=folder%2cgif",
    "application": {
      "id": "1234",
      "displayName": "Sample Application"
    },
  }
}
```

## <a name="creating-company-sharable-links"></a>创建公司共享链接

业务和 SharePoint OneDrive 支持公司共享链接。 但它们仅适用于所属的成员，这些都是组织的类似于匿名的链接。 若要创建公司共享链接，请使用**scope**参数值为`organization`。

## <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "request", "name": "create-link-scoped", "scopes": "files.readwrite service.sharepoint" } -->
```http
POST /drive/items/{item-id}/action.createLink
Content-Type: application/json

{
  "type": "edit",
  "scope": "organization"
}
```

## <a name="http-response"></a>HTTP 响应

响应将是`201 Created`的物料如果新的共享创建链接或`200 OK`如果返回现有的链接。

<!-- { "blockType": "response", "@odata.type": "microsoft.graph.permission" } -->
```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "123ABC",
  "roles": ["write"],
  "link": {
    "type": "view",
    "scope": "organization",
    "webUrl": "https://contoso-my.sharepoint.com/personal/ellen_contoso_com/...",
    "application": {
      "id": "1234",
      "displayName": "Sample Application"
    },
  }
}
```

## <a name="embeddable-links"></a>可嵌入的链接

当使用`embed`链接类型，返回 webUrl 可以嵌入在`<iframe>`HTML 元素。 当创建嵌入链接`webHtml`属性包含的 HTML 代码`<iframe>`来承载的内容。

**注意︰**嵌入链接仅供 OneDrive 个人支持。

## <a name="programming-notes"></a>编程注意事项

使用此操作创建的共享链接不会过期。 他们在该项目的共享权限中可见，可通过该项目的负责人。
共享链接始终指向当前版本的一个项目，除非该项目签出 (仅适用于 SharePoint)。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item: createLink",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Item/Create sharing link"
} -->
