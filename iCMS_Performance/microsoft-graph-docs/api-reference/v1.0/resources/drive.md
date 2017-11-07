# <a name="drive-resource-type"></a>驱动器资源类型

该驱动器资源是用户的 OneDrive 中的顶级对象。
用户必须始终至少一个可用的驱动器-默认驱动器。
驱动器资源也代表一个文档库中的 SharePoint 站点或 Office 365 组。

## <a name="methods"></a>方法

下列方法都可用于驱动器资源。


| 方法                                                    | 返回类型                          | 说明                                             |
|:----------------------------------------------------------|:-------------------------------------|:--------------------------------------------------------|
| [获取用户的默认驱动器](../api/drive_get.md)           | [驱动器](drive.md)                    | 读取驱动器资源的属性。                      |
| [获得另一个用户的驱动器](../api/drive_get.md)           | [驱动器](drive.md)                    | 读取驱动器资源的属性。                      |
| [获取驱动器的根文件夹](../api/item_get.md)    | [driveItem](driveitem.md)            | 读取驱动器的根文件夹的属性。        |
| [在驱动器中的列表项](../api/item_list_children.md)     | [driveItem](driveitem.md)集合 | 获取一个项的对象集合。                           |
| [在驱动器列表更改](../api/item_delta.md)           | [driveItem](driveitem.md)集合 | 跟踪更改某个驱动器中的项目。                      |
| [在驱动器中搜索项目](../api/item_search.md)          | [driveItem](driveitem.md)集合 | 搜索项匹配的驱动器中的关键字。          |


## <a name="properties"></a>属性

| 属性  | 类型                          | 说明                                                                                          |
|:----------|:------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| id        | String                        | 驱动器的唯一标识符。 只读的。                                                                                                           |
| driveType | String                        | 介绍了由该资源表示的驱动器的类型。 OneDrive 个人驱动器将返回`personal`。 业务的 OneDrive 将返回`business`。 只读的。 |
| 所有者     | [identitySet](identityset.md) | 拥有此驱动器的用户帐户。                                                                                                                    |
| 配额     | [配额](quota.md)             | 驱动器的存储空间配额有关的信息。                                                                                                       |

## <a name="relationships"></a>Relationships

| 关系 | 类型 |说明 |
|:--------|:---------------------------|:-------------------------------------------------------------------------|
| Items   | [driveitem](driveitem.md)集合 | 在驱动器中包含的所有项。 只读的。 可以为 null。                   |
| 根    | [driveitem](driveitem.md)            | 驱动器的根文件夹。 只读的。                                 |
| 特别 | [driveitem](driveitem.md)集合 | 在 OneDrive 中可用的公用文件夹的集合。 只读的。 可以为 null。 |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "items", "root", "special" ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.drive"
}-->

```json
{
  "id": "string (identifier)",
  "driveType": "string",
  "owner": {"@odata.type": "microsoft.graph.identitySet"},
  "quota": {"@odata.type": "microsoft.graph.quota"},
  "root": {"@odata.type": "microsoft.graph.driveItem" },
  "items": [ {"@odata.type": "microsoft.graph.driveItem" }],
  "special": [ {"@odata.type": "microsoft.graph.driveItem" }]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "drive resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": "OneDrive/Drive"
}-->
