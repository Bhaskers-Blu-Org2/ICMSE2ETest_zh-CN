# <a name="checklistitemcollection-resource-type"></a>checklistItemCollection 资源类型

ChecklistItemCollection * 资源代表的任务的核对清单项的集合。 它是一部分的[任务详细信息](taskdetails.md)的对象。 属性-值对中的值是[checklistItem](checklistitem.md)对象。

* 请注意，这是开放类型。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.checklistItemCollection"
}-->

```json
{
  "String-value":
  {
    "isChecked": true,
    "lastModifiedBy": "String-value",
    "lastModifiedByDateTime": "String(timestamp)",
    "orderHint": "String-value",
    "title": "String-value"
  }
}
```
示例

```json
{
  "3a73c9dd-fb47-4230-9c0f-b80788fb0f9b": // client-generated GUID
  {
    "@odata.type": "microsoft.graph.checklistItem", // required in PATCH requests to edit the checklist on a task
    "isChecked": true,
    "lastModifiedBy": "4e971521-101a-4311-94f4-0917d7218b4e",
    "lastModifiedByDateTime": "2015-09-21T17:45:12.039Z",
    "orderHint": "0009005756397228702",
    "title": "Get stamps"
  },
  "5f36f5b2-1ec0-4c48-9c75-ed59429516c5":
  {
     "@odata.type": "microsoft.graph.checklistItem",
    "isChecked": false,
    "lastModifiedBy": "4e971521-101a-4311-94f4-0917d7218b4e",
    "lastModifiedByDateTime": "2015-09-21T17:45:12.039Z",
    "orderHint": "0004105723397228784",
    "title": "Mail card at UPS"
  }
}

```


## <a name="properties"></a>属性
开放类型的属性可以由客户端定义。 在这种情况下，客户端应为属性提供**的 Guid**和它们的值必须是[checklistItem](checklistitem.md)对象。 上面显示了示例。 核对清单中移除项，设置为属性的值`null`。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "checklistItemCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->