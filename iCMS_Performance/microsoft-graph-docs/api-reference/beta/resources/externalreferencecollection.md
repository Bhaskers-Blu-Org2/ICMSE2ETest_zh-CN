# <a name="externalreferencecollection-resource-type"></a>externalReferenceCollection 资源类型

ExternalReferenceCollection * 资源表示的任务的引用的集合。 它是一部分的[任务详细信息](taskdetails.md)的对象。 属性-值对中的值是[externalReference](externalreference.md)对象。

* 请注意，这是开放类型。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.externalReferenceCollection"
}-->


```json
{
  "String-value":
  {
    "alias": "String-value",
    "lastModifiedBy": "String-value",
    "lastModifiedDateTime": "String(timestamp)",
    "previewPriority": "String-value",
    "type": "String-value"
  }
}
```

示例

```json
{
  "https%3A//contoso%2Esharepoint%2Ecom/teams/agile/documents/AnnualReport%2Epptx":
  {
    "@odata.type": "microsoft.graph.externalReference", // required in PATCH requests to edit the references on a task
    "alias": "Agile Team Annual Report",
    "lastModifiedBy": "1e9955d2-6acd-45bf-86d3-b546fdc795eb",
    "lastModifiedDateTime": "2015-09-21T17:45:12.039Z",
    "previewPriority": "0009005756397228702",
    "type": "PowerPoint"
  }
}

```

## <a name="properties"></a>属性
开放类型的属性可以由客户端定义。 在这种情况下，客户端必须提供**有效 Url**基于**HTTP/HTTPS**协议作为属性和它们的值必须是[externalReference](externalreference.md)对象。 根据 OData，打开类型中的属性名称不能包含下列字符︰ `.`， `:`，`%`因此，他们需要进行编码。 上面显示了示例。 若要删除的引用，设置为属性的值`null`

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "externalReferenceCollection resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->