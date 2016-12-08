# <a name="hashes-resource-type"></a>哈希值资源类型

**哈希值**方面，分组到项的单个结构的哈希值的不同类型。

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "sha1Hash", "crc32Hash", "quickXorHash" ],
  "@odata.type": "microsoft.graph.hashes"
}-->

```json
{
  "crc32Hash": "string",
  "sha1Hash": "string",
  "quickXorHash": "string"
}
```


## <a name="properties"></a>属性

| 属性      | 类型                   | 说明                                                       |
|:--------------|:-----------------------|:------------------------------------------------------------------|
| **sha1Hash**  | String  | 内容 （如果有） 的文件的 SHA1 哈希。 只读的。 |
| **crc32Hash** | String  | CRC32 值的文件 （如果可用）。 只读的。            |
| **quickXorHash** | String | 可用于确定文件的内容是否已更改 （是否可用） 的文件的专有哈希值。 只读的。 | 

**注意︰**在某些情况下哈希值可能不可用。 如果出现这种情况，将后将项下载更新哈希值的项。



## <a name="remarks"></a>备注

在业务的 OneDrive， **sha1Hash**和**crc32Hash**都不可用。

在 OneDrive 个人**quickXorHash**将不可用。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "hashes resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
