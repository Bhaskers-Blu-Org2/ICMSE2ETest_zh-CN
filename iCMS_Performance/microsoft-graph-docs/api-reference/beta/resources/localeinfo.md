# <a name="localeinfo-resource-type"></a>localeInfo 资源类型

有关区域设置，包括首选的语言和国家/地区中已登录的用户的信息。


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|区域设置|string|对于用户，包括用户的区域设置表示的首选语言和国家/地区。 例如，"en-我们"。 语言组件后面两个字母的代码在[ISO 639-1](http://www.iso.org/iso/home/standards/language_codes.htm)，和国家组件后面两个字母代码定义[字母](http://www.iso.org/iso/country_codes.htm)的 ISO 3166-1-2。|
|显示名称|string|一个表示用户的语言环境中自然语言，例如，"英语 （美国）"的名称。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.localeInfo"
}-->

```json
{
  "locale": "string",
  "displayName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "localeInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->