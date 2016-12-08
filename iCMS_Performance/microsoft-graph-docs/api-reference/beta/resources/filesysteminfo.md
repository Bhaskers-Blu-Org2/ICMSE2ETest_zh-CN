# <a name="filesysteminfo-resource-type"></a>fileSystemInfo 资源类型

**FileSystemInfo**资源包含属性所报告的设备的本地文件系统的本地版本的项目。 此方面可以用于指定上次修改日期或创建日期的项目，在本地设备上的样子。


## <a name="properties"></a>属性

| 属性                 | 类型           | 说明                                                   |
|:-------------------------|:---------------|:--------------------------------------------------------------|
| **createdDateTime**      | 方法 | UTC 日期和时间在客户端上创建文件。       |
| **lastModifiedDateTime** | 方法 | UTC 日期和时间在客户端上上次修改该文件。 |

## <a name="notes"></a>注释

CreatedDateTime 和 lastModifiedDateTime 的值不同于在[driveitem](driveitem.md)资源相同的属性。 对项目资源的值是创建和修改日期和时间像从该服务。
由客户端提供了存储在**fileSystemInfo**方面的值。

例如，如果文件是在星期一，在设备上创建，但直到星期二不上载到该服务，将文件上载的客户端应编写`fileSystemInfo`方面包括在周一的创建的日期。 项元数据检索时，创建日期的物料将反映 （星期二），但`fileSystemInfo`方面将显示原始创建在星期一的日期。

这些属性是可读写。 如果文件上载，并且知道这些字段的值的本地客户端，您应该将它们包括在请求中。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.fileSystemInfo"
}-->

```json
{
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}

```

## <a name="remarks"></a>备注

**FileSystemInfo**属性不可用于 SharePoint 或业务的 OneDrive 中的项目。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "fileSystemInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
