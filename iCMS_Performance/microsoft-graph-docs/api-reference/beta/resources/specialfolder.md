# <a name="specialfolder-resource-type"></a>specialFolder 资源类型

**SpecialFolder**方面提供了有关如何通过[特殊文件夹集合](../api/drive_special.md)访问某个文件夹的信息。

特殊文件夹提供简单可访问 OneDrive 中的已知文件夹，而无需查找按 （这将需要本地化） 的路径，该文件夹的别名或引用的文件夹 id。 如果特殊文件夹被重命名或移动到驱动器中的其他位置，将继续这种语法来查找该文件夹。

第一次应用程序试图写入，如果不存在自动创建特殊文件夹。 如果用户删除了一个，都会重新创建它时再次写入。

**注意︰**如果您的应用程序只请求了**Files.Read**范围，并请求特殊文件夹不存在，该响应将`403 Forbidden`错误。

## <a name="properties"></a>属性
| 属性  | 类型   | 说明                                                            |
|:----------|:-------|:-----------------------------------------------------------------------|
| name      | string | 在此项的唯一标识符`/drive/special`集合 |

## <a name="json-representation"></a>JSON 表示形式

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.specialFolder"
}-->
```json
{
  "name": "string"
}

```

## <a name="special-folders"></a>特殊文件夹

以下是可用 OneDrive 个人和企业的 OneDrive 中的特殊文件夹。

| 名称        | 文件夹 id    | 说明                                                              |
|:------------|:-------------|:-------------------------------------------------------------------------|
| 应用程序根目录    | `approot`    | 应用程序的个人文件夹。 通常在`/Apps/{Application Name}` |
| 照相机前滚 | `cameraroll` | 照相机将备份文件夹中。 在 OneDrive 的业务中不可用。   |
| Documents   | `documents`  | 文档文件夹中。                                                    |
| 音乐       | `music`      | 音乐文件夹中。 在 OneDrive 的业务中不可用。                |
| 照片      | `photos`     | 图片文件夹中。                                                       |


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "specialFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
