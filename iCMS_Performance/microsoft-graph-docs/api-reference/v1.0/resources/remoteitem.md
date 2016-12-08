# <a name="remoteitem-resource-type"></a>remoteItem 资源类型

**RemoteItem**资源类型指示[driveItem](driveitem.md)引用的项目，在另一个驱动器中存在提供一个指针，指向该驱动器。

它位于`remoteItem`的已共享并添加到驱动器中，例如，通过使用"添加到 OneDrive"功能的[driveItem](driveitem.md)资源的属性。

**注意︰**与使用相同的驱动器，文件夹移动到远程项目项可能具有其`id`更改。


## <a name="properties"></a>属性

| 属性名称   | 类型                                           | 说明                                                              |
|:----------------|:-----------------------------------------------|:-------------------------------------------------------------------------|
| 文件            | [文件](file.md)                          | 指示远程项目文件。 只读的。                     |
| fileSystemInfo  | [FileSystemInfo](filesysteminfo.md)      | 本地文件系统中的远程项目有关的信息。 只读的。 |
| 文件夹          | [文件夹](folder.md)                      | 指示远程项目是文件夹。 只读的。                   |
| id              | String                                         | 在其驱动器内远程项目的唯一标识符。 只读的。           |
| name            | String                                         | 可选项。 远程项目的文件名。 只读的。                        |
| parentReference | [ItemReference](itemreference.md) | 远程的项的父项的属性。 只读的。                  |
| size            | Int64                                          | 远程项目的大小。 只读的。                                      |


## <a name="json-representation"></a>JSON 表示形式

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.remoteItem", optionalProperties: ["name", "fileSystemInfo", "file", "folder"] } -->
```json
{
  "id": "string",
  "file": { "@odata.type": "microsoft.graph.file" },
  "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" },
  "folder": { "@odata.type": "microsoft.graph.folder" },
  "name": "string",
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "size": 1024
}
```
<!-- {
  "type": "#page.annotation",
  "description": "remoteItem resource type provides a link to an item in another drive.",
  "keywords": "remoteitem symlink remote drive shared with me add to onedrive",
  "section": "documentation"
} -->
