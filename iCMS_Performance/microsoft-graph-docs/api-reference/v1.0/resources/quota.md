# <a name="quota-resource-type"></a>配额资源类型

**配额**资源提供有关驱动器配额的详细信息。



## <a name="properties"></a>属性

| 属性名称 | 类型   | 说明                                                                 |
|:--------------|:-------|:----------------------------------------------------------------------------|
| 总计         | Int64  | 允许的总存储空间，以字节为单位。 只读的。                           |
| 使用          | Int64  | 总空间，以字节为单位。 只读的。                                      |
| 其余     | Int64  | 达到配额限制，以字节为单位之前剩余的空间总量。 只读的。 |
| 删除       | Int64  | 以字节为单位的回收站中的文件占用的空间总量。 只读的。      |
| 状态         | string | 枚举值，该值指示存储空间的状态。 只读的。 |



## <a name="state-enumeration"></a>状态枚举

| 值      | 说明                                                                                                                                                                 |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `normal`   | 驱动器都有充足的剩余配额向左。                                                                                                                               |
| `nearing`  | 剩余的配额是少于 10%的总配额空间。                                                                                                                      |
| `critical` | 剩余的配额将少于 1%的总配额空间。                                                                                                                       |
| `exceeded` | 使用的配额已超出总配额。 直到它在总配额量或购买更多存储空间，新的文件或文件夹无法添加到该驱动器。 |


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.quota"
}-->

```json
{
  "deleted": 1024,
  "remaining": 1024,
  "state": "normal | nearing | critical | exceeded",
  "total": 1024,
  "used": 1024
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "quota resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
