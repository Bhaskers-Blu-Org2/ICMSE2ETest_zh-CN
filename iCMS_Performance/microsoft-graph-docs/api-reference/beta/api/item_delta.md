# <a name="track-changes-for-an-item-and-its-children"></a>一项及其子项的修订

检索一个项及其子项的当前状态，并跟踪随时间的变化。

您的应用程序开始调用`delta`不带任何参数。 在服务启动枚举 driveItem 的层次结构，返回页的项和任何一个`@odata.nextLink`或`@odata.deltaLink`，如下所述。 您的应用程序时，应该使用调用`@odata.nextLink`直到不能再看到`@odata.nextLink`返回，或参阅更改的一个空集的响应。

接收的所有更改后，您可能将它们应用于您的本地状态。 若要在将来检查更改，请调用`delta`再次与`@odata.deltaLink`从上面的回答。

已删除的邮件所返回的[`deleted`方面](../resources/deleted.md)。
设置了此属性的项目应从您的本地状态。 注意︰ 如果同步所有更改之后为空，只应删除一个文件夹。

## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰

  * Files.Read
  * Files.Readwrite

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/drive/root/delta
GET /me/drive/items/{item-id}/delta
GET /me/drive/root:/{item-path}:/delta
```

## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持[OData 查询参数](http://graph.microsoft.io/docs/overview/query_parameters)来帮助自定义响应。

## <a name="request-headers"></a>请求标头

| 名称          | 值  | 说明               |
|:--------------|:-------|:--------------------------|
| 授权 | string | 持有者<token>。 必需。 |


## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[driveItem](../resources/driveitem.md)集合。

除了 driveItems 集合，响应还包括以下属性之一︰

| 名称                 | 值  | 说明                                                                                                                                      |
|:---------------------|:-------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| **@odata.nextLink**  | url    | 若要检索下一可用页的更改，如果有其他更改当前集中一个 URL。                                        |
| **@odata.deltaLink** | url    | 而不是返回 URL**@odata.nextLink**毕竟当前更改已被退回。 用于在将来读取下一组更改。  |


## <a name="example-initial-request"></a>示例 （初始请求）
这里是如何调用此 API 来建立您的本地状态的示例。

##### <a name="request"></a>请求
这里是初始请求的示例。

<!-- {
  "blockType": "request",
  "name": "get_item_delta"
}-->
```http
GET /drive/root/delta
```

##### <a name="response"></a>响应
这里是响应的示例。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "0123456789abc",
            "name": "folder2",
            "folder": { }
        },
        {
            "id": "123010204abac",
            "name": "file.txt",
            "file": { }
        },
        {
            "id": "2353010204ddgg",
            "name": "file5.txt",
            "deleted": { }
        }
    ],
    "@odata.nextLink": "https://api.onedrive.com/drive/root/view.delta?token=1230919asd190410jlka"
}
```

此响应包含的更改，第一页和**@odata.nextLink**属性指示有当前的项目集中更多的项目。
您的应用程序应该继续请求的 URL 值的**@odata.nextLink**直到已检索到的项目的所有页。

## <a name="example-last-page-in-a-set"></a>示例 （集中的最后一页）
这里是如何调用此 API 来更新您的本地状态的示例。

##### <a name="request"></a>请求
初始的请求后，下面是示例请求。

<!-- {
  "blockType": "request",
  "name": "get_item_delta"
}-->
```http
GET /drive/root/delta?(token='123123901209310923!23alksjd')
```

##### <a name="response"></a>响应
这里是响应的示例。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.driveItem",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "0123456789abc",
            "name": "folder2",
            "folder": { },
            "deleted": { }
        },
        {
            "id": "123010204abac",
            "name": "file.txt",
            "file": { }
        }
    ],
    "@odata.deltaLink": "https://graph.microsoft.com/beta/me/drive/root/delta?(token='1230919asd190410jlka')"
}
```

此响应表示，此项名为`folder2`已被删除，该项目`file.txt`添加或修改初始请求，该请求可更新的本地状态之间。

项目的最后一页将包括**@odata.deltaLink**属性，它提供可以以后使用，因为当前的项集检索更改的 URL。

## <a name="remarks"></a>备注

* 增量馈送显示每个项，不是每个更改的最新状态。 如果两次被重命名的项，它将只显示一次，用它的新名称。
* 同一项可能不止一次出现在增量馈送，出于各种原因。
  您应使用最后一次看到。
* `parentReference`项的属性将不包括**路径**的值。
  出现这种情况是因为重命名文件夹不会导致任何后代从 view.delta 返回的文件夹。 在使用 view.delta 时应始终按 id 跟踪项目。

可能在某些情况下，如果服务不能提供更改列表为一个给定的标记 （例如，如果客户端尝试断开很长时间后重新使用旧的标记或如果服务器状态已更改，新的标记是必需的）。 在这些情况下此服务将返回`HTTP 410 Gone`错误时出现错误响应包含一个错误代码，和一个`Location`包含从头开始一个全新的增量枚举新 nextLink 标头。 完成完全枚举后, 比较本地状态返回的项，并按照这些说明进行操作。

| 错误类型                       | 说明                                                                                                                                                                                                                    |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ResyncChangesApplyDifferences`  | 如果您确信该服务已达日期与本地更改上一次同步时将会用服务器的版本 （包括删除） 替换任何本地项目。 上传服务器并不知道有关任何本地更改。 |
| `ResyncChangesUploadDifferences` | 任何本地项服务没有不返回，并上载任何 （如果您不确定哪一个是更多最新保持这两个副本） 的服务器的版本不同的文件上载。                                       |


在业务和 SharePoint OneDrive`delta`上才支持`root`文件夹，不是在其他文件夹。 它也不会返回以下 driveItem 属性︰

* **创建者**
* **cTag**
* **eTag**
* **fileSystemInfo**
* **lastModifiedBy**
* **parentReference**
* **大小**


<!-- {
  "type": "#page.annotation",
  "description": "Get item delta",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
