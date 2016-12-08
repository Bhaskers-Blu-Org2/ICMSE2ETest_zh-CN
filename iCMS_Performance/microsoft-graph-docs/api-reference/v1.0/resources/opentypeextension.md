# <a name="opentypeextension-resource-type"></a>openTypeExtension 资源类型

**OpenTypeExtension**是的 OData v4 打开以便您可以在运行时自定义数据的实体数据模型中定义的资源实例中指定的类型。 这样可以节省时间仅仅为此目的定义新的实体类型。

组织组日历中，您可以创建[消息](message.md)、[事件](event.md)或[与](contact.md)已登录的用户的邮箱中，或在**事件**中的**openTypeExtension**类型的数据扩展插件。 在个人用户的上下文中，用户帐户可以在 Office 365 或 Microsoft 帐户 （Hotmail.com，Live.com，MSN.com、 Outlook.com 和 Passport.com）。

此资源从[扩展](extension.md)抽象类型派生的并且具有附加**extensionName**属性。
**ExtensionName**属性是预定义的、 可写属性对于所有扩展。 若要帮助确保扩展名称都是唯一的一种方法是使用的反向域名名称系统 (DNS) 方法取决于_您自己的域_，例如， `Com.Contoso.Contact`。 不要使用 Microsoft 域中扩展名称。

## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.opentypeextension"
}-->

```json
{
  "extensionName": "string",
  "id": "string (identifier)"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|extensionName|String|开放式类型数据扩展唯一文本标识符。 必需。|
|id|String| 连接具有**extensionName**扩展名类型是完全限定的标识符。 只读的。|

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[发布](../api/opentypeextension_post_opentypeextension.md) | [openTypeExtension](opentypeextension.md)，或[消息](../resources/message.md)、[事件](../resources/event.md)或[与](../resources/contact.md)包含一个 openTypeExtension 对象。 | 现有的或新资源实例中创建一个 openTypeExtension 对象。| 
|[获取](../api/opentypeextension_get.md) | [openTypeExtension](opentypeextension.md) |读取属性和关系的 openTypeExtension 对象。|
|[更新](../api/opentypeextension_update.md) | [openTypeExtension](opentypeextension.md)   |更新 openTypeExtension 对象。 |
|[删除](../api/opentypeextension_delete.md) | 无 |删除 openTypeExtension 对象。 |

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "openTypeExtension resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->