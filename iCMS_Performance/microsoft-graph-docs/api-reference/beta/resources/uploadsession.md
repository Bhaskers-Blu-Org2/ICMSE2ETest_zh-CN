# <a name="uploadsession-resource-type"></a>uploadSession 资源类型

在上载会话提供了有关如何上载大文件复制到 OneDrive，OneDrive 为企业或 SharePoint 文档库。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "uploadUrl", "nextExpectedRanges" ],
  "@odata.type": "microsoft.graph.uploadSession"
}-->

```json
{
  "expirationDateTime": "String (timestamp)",
  "nextExpectedRanges": ["string"],
  "uploadUrl": "url"
}

```
## <a name="properties"></a>属性


| 属性           | 类型              |说明|
|:-------------------|:------------------|:----------|
| expirationDateTime | DateTime          | 日期和时间以 UTC 上载会话将到期。 完整的文件必须上载文件之前达到此到期时间。 |
| nextExpectedRanges | 字符串集合 | 服务器缺少该文件的字节范围的集合。 这些区域均为零索引和格式"开始端"的 (例如"0-26 页"以指示该文件的第 27 个字节)。 |
| uploadUrl          | String            | 接受该文件的字节范围的 PUT 请求 URL 端点。 |

## <a name="additional-resources"></a>其他资源

有关如何上载文件使用上载会话的详细信息，请参阅[上载大文件上载会话](../api/item_createUploadSession.md)。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "uploadSession resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->