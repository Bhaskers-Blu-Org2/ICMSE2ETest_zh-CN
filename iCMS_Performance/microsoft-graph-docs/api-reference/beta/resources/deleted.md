# <a name="deleted-resource-type"></a>删除资源类型

**删除**资源指示该项已被删除。 在此版本的 API，存在资源值 （非空） 指示该文件已被删除。 Null 值 （或缺少） 值表示该文件未被删除。

[查看更改的项](../api/item_delta.md)的详细信息，请参阅。

## <a name="properties"></a>属性

| 属性 | 类型   | 说明                               |
|:---------|:-------|:------------------------------------------|
| 状态    | String | 表示已删除的项的状态。 |

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
  "state"
  ],
  "@odata.type": "microsoft.graph.deleted"
}-->
```json
{
  "state": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "deleted resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
