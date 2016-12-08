# <a name="sharepointids-resource-type"></a>SharePointIds 资源类型

**SharepointIds**资源组的各种 SharePoint 网站或到一个单一的结构业务的 OneDrive 中所存储的项的标识符。

### <a name="properties"></a>属性

| 属性          | 类型    | 说明                                                          |
|:------------------|:--------|:---------------------------------------------------------------------|
| listId            | string  | 在 SharePoint 中的项的列表的唯一标识符。                          |
| listItemId        | string  | 包含的列表中的项的整数标识符。                    |
| listItemUniqueId  | string  | OneDrive 蒸蒸日上或者 SharePoint 网站中的项的唯一标识符。 |
| 站点 Id            | string  | 该项目的站点集合的唯一标识符。 |
| webId             | string  | 该项目的站点的唯一标识符。                          |

### <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.sharepointIds"
}-->
```json
{
    "listId": "string",
    "listItemId": "string",
    "listItemUniqueId": "string",
    "siteId": "string",
    "webId": "string"
}

```


<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "sharepointIds resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->