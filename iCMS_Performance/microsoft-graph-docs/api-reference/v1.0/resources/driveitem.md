# <a name="driveitem-resource-type"></a>driveItem 资源类型

**DriveItem**资源表示驱动器中的项。 在 OneDrive 中的所有顶级文件系统对象将返回作为项目资源。 可以使用其**id**访问`/items/{item-id}`的语法，或通过其文件系统路径使用`/drive/root:/path/to/file`语法。

项目有小平面建模为属性提供有关该项目的身份和能力的数据。 文件夹都有一个[**文件夹**方面](folder.md)和[**文件方面**](file.md)的文件。 图像有[**图像方面**](image.md)除了其文件方面。

项目**文件夹**方面用作容器的项，因此有`children`引用指向的文件夹下的项的集合。

## <a name="methods"></a>方法

| 方法                                                 | 返回类型                                | 说明                                                                                                                             |
|:-------------------------------------------------------|:-------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| [获取项](../api/item_get.md)                         | [driveitem](driveitem.md)                  | 读取属性和项对象的关系。                                                                                       |
| [列表中的孩子](../api/item_list_children.md)          | [driveitem](driveitem.md)集合       | 获取子对象集合。                                                                                                       |
| [创建项目](../api/item_post_children.md)            | [driveitem](driveitem.md)                  | 由过账到子集合中创建新项。                                                                                |
| [更新项目](../api/item_update.md)                   | [driveitem](driveitem.md)                  | 更新项目对象。                                                                                                                     |
| [上载内容](../api/item_uploadcontent.md)         | 有关详细信息，请参阅 API                        | 简单上载 API 允许您提供一个新的文件的内容或更新一个 API 调用中的现有文件的内容。 |
| [下载内容](../api/item_downloadcontent.md)     | 有关详细信息，请参阅 API                        | 下载项目内容。                                                                                                      |
| [删除项目](../api/item_delete.md)                   | 无                                       | 删除项的对象。                                                                                                                     |
| [移动项目](../api/item_move.md)                       | [driveitem](driveitem.md)                  | 更新按 ID 或路径项的父文件夹。 若要移动项，您可以更新其 parentReference 属性。                           |
| [复制项目](../api/item_copy.md)                       | [driveitem](driveitem.md)                  | 用新名称或父项创建一个项目及其内容的副本。                                                                |
| [搜索项目](../api/item_search.md)                  | [driveitem](driveitem.md)集合       | 搜索与查询的匹配项。                                                                                                      |
| [查找更改](../api/item_delta.md)                   | [driveItem](driveitem.md)集合       | 查看更改的项及其子项。                                                                                              |
| [缩略图列表](../api/item_list_thumbnails.md)      | [thumbnailSet](thumbnailset.md)集合 | 获得 thumbnailSet 对象集合。                                                                                                   |
| [创建共享链接](../api/item_createlink.md)       | [权限](permission.md)                | 创建要与其他用户共享该文件的共享链接。                                                                               |
| [添加权限](../api/item_invite.md)               | [权限](permission.md)                | 通过发送共享邀请来创建一个新的权限。                                                                                |
| [列表权限](../api/item_list_permissions.md)    | [权限](permission.md)集     | 获取权限对象集合。                                                                                                     |
| [删除权限](../api/permission_delete.md) | 无                                       | 从项目中删除权限。                                                                                                       |

## <a name="properties"></a>属性

| 属性             | 类型                                | 说明                                                                                                                                                               |
|:---------------------|:------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 音频                | [音频](audio.md)                   | 音频元数据，如果该项目是一个音频文件。 只读的。                                                                                                                  |
| 内容              | Stream                              | 内容的流中，如果此项表示一个文件。                                                                                                                        |
| 创建者            | [identitySet](identityset.md)       | 用户、 设备和应用程序创建的项的标识。 只读的。                                                                                          |
| createdDateTime      | 方法                      | 日期和时间创建项。 只读的。                                                                                                                                |
| cTag                 | String                              | ETag 的项的内容。 如果只更改了元数据，则不会更改该 eTag。 **请注意**如果项目是文件夹，则不会返回此属性。 只读的。 |
| 删除              | [删除](deleted.md)               | 已删除的项的状态有关的信息。 只读的。                                                                                                               |
| eTag                 | String                              | 整个项目 （元数据和内容） 的 eTag。 只读的。                                                                                                                 |
| 文件                 | [文件](file.md)                     | 如果项是一个文件，则文件元数据。 只读的。                                                                                                                          |
| fileSystemInfo       | [fileSystemInfo](filesysteminfo.md) | 在客户端上的文件系统信息。 读写。                                                                                                                            |
| 文件夹               | [文件夹](folder.md)                 | 文件夹元数据，如果项目是文件夹。 只读的。                                                                                                                      |
| id                   | String                              | 驱动器中的项的唯一标识符。 只读的。                                                                                                            |
| image                | [图像](image.md)                   | 图像元数据，如果该项是图像。 只读的。                                                                                                                       |
| lastModifiedBy       | [identitySet](identityset.md)       | 标识用户、 设备和应用程序的最后修改该项目。 只读的。                                                                                    |
| lastModifiedDateTime | 方法                      | 日期和上次修改项目的时间。 只读的。                                                                                                                      |
| 位置             | [geoCoordinates](geoCoordinates.md) | 位置的元数据，如果该项的位置数据。 只读的。                                                                                                              |
| name                 | String                              | （文件名和扩展名） 的项的名称。 读写。                                                                                                                |
| 包              | [包](package.md)               | （如果存在） 表示，此项是包而不是一个文件夹或文件。 包可以看作是在某些上下文中的文件和文件夹的其他人。 只读的。         |
| parentReference      | [itemReference](itemreference.md)   | 父级信息，如果该项目有父级。 读写。                                                                                                                 |
| 照片                | [照片](photo.md)                   | 照片的元数据，如果该项是一张照片。 只读的。                                                                                                                        |
| remoteItem           | [remoteItem](remoteitem.md)         | 远程项目数据，如果该项从驱动器而不是被访问共享。 只读的。                                                                        |
| searchResult         | [searchResult](searchresult.md)     | 如果该项是从搜索结果中搜索元数据。 只读的。                                                                                                          |
| 共享               | [共享](shared.md)                 | 指示该项已与其他人共享，并提供有关该项目的共享状态信息。 只读的。                                               |
| size                 | Int64                               | 以字节为单位的项的大小。 只读的。                                                                                                                                     |
| specialFolder        | [specialFolder](specialfolder.md)   | 如果当前项同时也是一个特殊的文件夹，则返回此方面。 只读的。                                                                             |
| 视频                | [视频](video.md)                   | 视频元数据，如果该项是视频。 只读的。                                                                                                                        |
| webUrl               | String                              | 在浏览器中显示的资源的 URL。 只读的。                                                                                                                 |

                                                                                                                |

**注意︰**ETag 和 cTag 属性以不同的方式处理容器 （文件夹）。 CTag 值被修改时更改内容或元数据的文件夹的任何后代。 ETag 值仅修改文件夹的属性发生更改时，属性除外，均源自 （如**childCount**或**lastModifiedDateTime**） 的后代。

## <a name="instance-attributes"></a>实例属性

实例属性是具有特殊行为的属性。 此属性是临时的要么 a） 定义行为服务应执行或 b） 提供短期的属性值，如过期项的下载 URL。

| 属性名称                     | 类型   | 说明                                                                                                                                                         |
|:----------------------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @microsoft.graph.conflictBehavior | string | 创建新项的操作冲突解决行为。 一项绝不会返回与该批注。 只写的。                               |
| @microsoft.graph.downloadUrl      | string | 一个可用于下载此文件的内容的 URL。 身份验证不需要使用此 URL。 只读的。                                                    |
| @microsoft.graph.sourceUrl        | string | 当发出 PUT 请求，此实例批注可用于指示服务下载内容的 URL，并将其存储为文件。 只写的。 |

**注意︰**@microsoft.graph.downloadUrl值是生存期较短的 URL，并且不能被缓存。 URL 只可短时间内失效之前的时间。

## <a name="relationships"></a>Relationships

| 关系       | 类型                                       | 说明                                                                                                                                                                       |
|:-------------------|:-------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 儿童           | [driveitem](driveitem.md)集合       | 包含项的对象的直接子项的项的集合。 表示文件夹的项包含子项。 只读的。 可以为 null。                                        |
| createdByUser      | [用户](user.md)                            | 用户、 设备和应用程序创建的项的标识。 只读的。                                                                                                  |
| lastModifiedByUser | [用户](user.md)                            | 标识用户、 设备和应用程序的最后修改该项目。 只读的。                                                                                            |
| 权限        | [权限](permission.md)集     | 该项目的权限集。 只读的。 可以为 null。                                                                                                                         |
| 缩略图         | [thumbnailSet](thumbnailset.md)集合 | 集合，其中包含与该项目相关联的[ThumbnailSet](thumbnailSet.md)对象。 有关更多信息，请参见[获取缩略图](../api/thumbnailset_get.md)。 只读的。 可以为 null。 |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "children", "createdByUser", "lastModifiedByUser", "permissions", "thumbnails"],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.driveItem"
}-->

```json
{
  "audio": {"@odata.type": "microsoft.graph.audio"},
  "cTag": "string",
  "content": "stream",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "deleted": {"@odata.type": "microsoft.graph.deleted"},
  "eTag": "string",
  "file": {"@odata.type": "microsoft.graph.file"},
  "fileSystemInfo": {"@odata.type": "microsoft.graph.fileSystemInfo"},
  "folder": {"@odata.type": "microsoft.graph.folder"},
  "id": "string (identifier)",
  "image": {"@odata.type": "microsoft.graph.image"},
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.geoCoordinates"},
  "name": "string",
  "package": {"@odata.type": "microsoft.graph.package"},
  "parentReference": {"@odata.type": "microsoft.graph.itemReference"},
  "photo": {"@odata.type": "microsoft.graph.photo"},
  "remoteItem": {"@odata.type": "microsoft.graph.remoteItem"},
  "searchResult": {"@odata.type": "microsoft.graph.searchResult"},
  "shared": {"@odata.type": "microsoft.graph.shared"},
  "size": 1024,
  "specialFolder": {"@odata.type": "microsoft.graph.specialFolder"},
  "video": {"@odata.type": "microsoft.graph.video"},
  "webDavUrl": "string",
  "webUrl": "string",

  "createdByUser": { "@odata.type": "microsoft.graph.user" },
  "lastModifiedByUser": { "@odata.type": "microsoft.graph.user" },
  "children": [ { "@odata.type": "microsoft.graph.driveItem" }],
  "thumbnails": [ {"@odata.type": "microsoft.graph.thumbnailSet"}],
  "permissions": [ {"@odata.type": "microsoft.graph.permission"} ]
}

```

## <a name="remarks"></a>备注

在业务的 OneDrive， **cTag**属性不返回，如果项目是[文件夹](folder.md)。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
