# <a name="itemreference-resource-type"></a>itemReference 资源类型

 [DriveItem](driveitem.md)使用 API 引用所需的数据。

## <a name="properties"></a>属性

| 属性 | 类型   | 说明                                                                   |
|:---------|:-------|:------------------------------------------------------------------------------|
| 它必须引用独立  | String | 包含项的 OneDrive 实例的唯一标识符。 只读的。 |
| id       | String | 驱动器中的项的唯一标识符。 只读的。            |
| 路径     | String | 用于导航到该项目的路径。 只读的。                     |

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "path" ],
  "@odata.type": "microsoft.graph.itemReference"
}-->

```json
{
  "driveId": "string",
  "id": "string",
  "path": "string"
}
```

## <a name="remarks"></a>备注

为了解决某项从一个**itemReference**实例，构造格式的 URL:

```http
GET https://graph.microsoft.com/beta/drives/<driveId>/items/<id>
```

**路径**值是 API 路径相对于目标驱动器，例如︰ `/drive/root:/Documents/myfile.docx`。

若要检索的可读痕迹导航路径，您可以放心地忽略内容。 第一个`:`路径字符串中。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "itemReference resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
