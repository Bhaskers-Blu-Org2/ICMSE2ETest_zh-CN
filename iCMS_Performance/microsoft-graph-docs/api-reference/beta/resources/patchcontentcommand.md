# <a name="patchcontentcommand-resource-type"></a>patchContentCommand 资源类型

对一个修补程序在 OneNote 页进行的更改请求。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示形式的资源，在正文中发送[修补程序页 /<id>](../api/page_update.md)请求。 

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.patchcontentcommand"
}-->

```json
{
  "action": "String",
  "content": "string",
  "position": "String",
  "target": "string"
}

```

## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|操作|String|要在目标元素上执行的操作。 可能的值为︰ `replace`， `append`， `insert`，或`prepend`。|
|内容|String|一个格式良好的 html，将添加到页面以及任何图像或文件的二进制数据的字符串。 如果内容包含二进制数据，必须使用发送请求`multipart/form-data`内容类型与"命令"部分。 |
|position|String|要添加的提供的内容，与目标元素的位置。 可能的值为︰ `after` （默认值） 或`before`。|
|target|字符串|要更新的元素。 必须是`#<data-id>`或生成`<id>`的元素，或`body`或`title`关键字。|

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "patchContentCommand resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->