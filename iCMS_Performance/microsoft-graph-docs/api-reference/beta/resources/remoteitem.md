# <a name="remoteitem-resource-type"></a>remoteItem 资源类型

**RemoteItem**资源类型指示[driveItem](driveitem.md)引用的项目，在另一个驱动器中存在提供一个指针，指向该驱动器。

它位于`remoteItem`的已共享并添加到驱动器中，例如，通过使用"添加到 OneDrive"功能的[driveItem](driveitem.md)资源的属性。

**注意︰**与使用相同的驱动器，文件夹移动到远程项目项可能具有其`id`更改。

## <a name="json-representation"></a>JSON 表示形式

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.remoteItem", optionalProperties: ["name", "fileSystemInfo", "file", "folder"] } -->
```json
{
  "id": "string",
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "timestamp",
  "file": { "@odata.type": "microsoft.graph.file" },
  "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" },
  "folder": { "@odata.type": "microsoft.graph.folder" },
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "timestamp",
  "name": "string",
  "package": { "@odata.type": "microsoft.graph.package" },
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "sharepointIds": { "@odata.type": "microsoft.graph.sharepointIds" },
  "size": 1024,
  "specialFolder": { "@odata.type": "microsoft.graph.specialFolder" },
  "webDavUrl": "url",
  "webUrl": "url"
}
```

## <a name="properties"></a>属性

| 属性名称   | 类型                                           | 说明                                                              |
|:----------------|:-----------------------------------------------|:-------------------------------------------------------------------------|
| 创建者       | [IdentitySet](identityset.md)            | 用户、 设备和应用程序创建的项的标识。 只读的。   |
| createdDateTime | Timestamp                                | 日期和时间创建项。 只读的。 |
| 文件            | [文件](file.md)                          | 指示远程项目文件。 只读的。                     |
| fileSystemInfo  | [FileSystemInfo](filesysteminfo.md)      | 本地文件系统中的远程项目有关的信息。 只读的。 |
| 文件夹          | [文件夹](folder.md)                      | 指示远程项目是文件夹。 只读的。                   |
| id              | String                                         | 在其驱动器内远程项目的唯一标识符。 只读的。           |
| lastModifiedBy  | [IdentitySet](identityset,md)           | 标识用户、 设备和应用程序的最后修改该项目。 只读的。 |
| lastModifiedDateTime | Timestamp                           | 日期和上次修改项目的时间。 只读的。  | 
| name            | String                                         | 可选项。 远程项目的文件名。 只读的。                        |
| 包         | [包](package.md)                    | （如果存在） 表示，此项是包而不是一个文件夹或文件。 包可以看作是在某些上下文中的文件和文件夹的其他人。 只读的。 |
| parentReference | [ItemReference](itemreference.md) | 远程的项的父项的属性。 只读的。                  |
| sharepointIds   | [SharepointIds](sharepointids.md) | OneDrive 为企业中的项目与 SharePoint 之间的互操作提供了全套的项标识符。 只读的。  |
| size            | Int64                                          | 远程项目的大小。 只读的。                                      |
| specialFolder   | [SpecialFolder](specialfolder.md) | 如果当前项同时也是一个特殊的文件夹，则返回此方面。 只读的。 |
| webDavUrl       | Url | 该项目的 DAV 兼容的 URL。 |
| webUrl          | Url | 在浏览器中显示的资源的 URL。 只读的。 | 


<!-- {
  "type": "#page.annotation",
  "description": "remoteItem resource type provides a link to an item in another drive.",
  "keywords": "remoteitem symlink remote drive shared with me add to onedrive",
  "section": "documentation"
} -->
