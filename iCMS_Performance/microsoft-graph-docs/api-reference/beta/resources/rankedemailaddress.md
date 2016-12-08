# <a name="rankedemailaddress-resource-type"></a>rankedEmailAddress 资源类型

表示一个级别的电子邮件地址。


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|address|string|电子邮件地址。|
|排名|double|电子邮件地址的排位。 等级被用作排序关键字，相对于其他返回的结果。 更高的排名值对应于更多相关的结果。 相关性由通信、 协作和业务关系发出的信号。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.rankedemailaddress"
}-->

```json
{
  "address": "string",
  "rank": 1024
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "rankedEmailAddress resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
