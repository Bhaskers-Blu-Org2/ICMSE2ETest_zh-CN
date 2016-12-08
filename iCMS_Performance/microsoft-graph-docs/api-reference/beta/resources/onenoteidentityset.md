# <a name="onenoteidentityset-resource-type"></a>oneNoteIdentitySet 资源类型

**即将推出的支持**

OneNoteIdentitySet 类型是[OneNoteIdentity](onenoteidentity.md)对象的键控的集合。
它用来表示一组关联的标识各种事件的_笔记本_、_节_或_页面_，例如 _通过创建_或_上次修改者_。 
 
目前，它包含单个密钥，_**用户**_。  在将来，可能会添加如设备或应用程序更改的项的键。

在将来，这种类型将与[IdentitySet](identityset.md)合并

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.onenoteidentityset"
}-->

```json
{
  "user": {"@odata.type": "microsoft.graph.oneNoteIdentity"}
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|user|[oneNoteIdentity](onenoteidentity.md)|OneNoteIdentity 资源，代表用户。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "oneNoteIdentitySet resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
