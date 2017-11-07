# <a name="file-resource-type"></a>文件资源类型

**文件**资源与文件相关的数据项分组到一个单一的结构。


## <a name="properties"></a>属性

| 属性 | 类型                    | 说明                                                                                                                                      |
|:---------|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| 哈希值   | [HashesType](hashes.md) | 该文件的二进制内容，如果可用的哈希值。 只读的。                                                                                    |
| mimeType | string                  | 文件的 MIME 类型。 这由服务器上的逻辑，可能不能提供的值时上载文件。 只读的。 |


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ ],
  "@odata.type": "microsoft.graph.file"
}-->

```json
{
  "hashes": {"@odata.type": "microsoft.graph.hashes"},
  "mimeType": "string"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "file resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
