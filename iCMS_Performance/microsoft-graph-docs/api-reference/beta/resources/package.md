# <a name="package-resource-type"></a>包资源类型

**包**方面表示，一项是"包"或被视为而不是单个项的数据集合的项的集合中的顶级项。

包的一个示例是 OneNote 笔记本。 虽然笔记本文件和文件夹表示的笔记本的内容组成，表示该笔记本的最高级别项将有**包**方面向客户端指明这是应被视为特殊的数据的集合。

**封装**方面的项目不包括的**文件夹**或**文件**方面，但在概念上类似于**文件夹**方面的商品。

## <a name="json-representation"></a>JSON 表示形式

<!-- { "blockType": "resource", "@odata.type": "microsoft.graph.package" } -->
```json
{
  "type": "oneNote"
}
```

| 属性名称 | 类型   | 说明                                                                                                                                                                      |
|:--------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **类型**      | string | 一个字符串，表示包的类型。 虽然`oneNote`是唯一当前定义的值，可以预见，其他程序包类型返回，并采取相应处理措施。 |

<!-- {
  "type": "#page.annotation",
  "description": "The Package facet indicates that an item is the root of a special collection of items that should be treated as a single unit.",
  "keywords": "package, facet, onenote",
  "section": "documentation"
} -->
