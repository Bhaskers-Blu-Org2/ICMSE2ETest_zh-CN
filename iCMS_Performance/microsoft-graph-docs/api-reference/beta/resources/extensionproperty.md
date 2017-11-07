# <a name="extensionproperty-resource-type"></a>extensionProperty 资源类型

允许应用程序来定义和使用一套可以不需要外部数据存储区的应用程序将添加到目录对象 （用户、 组、 组织详细信息、 设备、 应用程序和服务主体） 的附加属性。 有关扩展属性的详细信息，请参阅[Azure 广告图形 API 目录架构扩展](https://msdn.microsoft.com/en-us/library/azure/dn720459.aspx)。 从[directoryObject](directoryobject.md)继承。


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.extensionproperty"
}-->

```json
{
  "appDisplayName": "string",
  "dataType": "string",
  "id": "string (identifier)",
  "isSyncedFromOnPremises": true,
  "name": "string",
  "targetObjects": ["string"]
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|appDisplayName|String|            |
|数据类型|String|指定要添加的目录扩展属性的类型。   支持的类型包括︰ 整数、 LargeInteger、 （必须在指定 ISO 8601-存储在 UTC 日期时间） 的日期时间、 二进制文件、 布尔和字符串。|
|isSyncedFromOnPremises|Boolean|指示是否在的内部部署目录中同步的扩展属性。                            **备注**︰ 不可以为 null。            |
|name|String|指定的目录扩展属性显示名称。                            **备注**︰ 不可以为 null。            |
|id|String|该权限范围的唯一标识符。 从[directoryObject](directoryobject.md)继承。                            **备注**︰**键**，永恒的、 不可为空的唯一。             只读的。|
|targetObjects|字符串集合|要向其添加目录扩展属性的目录对象。  可以扩展的支持的目录实体是:"用户"、"组"、"组织"、"设备"、"应用程序"和"ServicePrincipal"的**注释**︰ 不可以为 null。            |

## <a name="relationships"></a>Relationships
无


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 extensionProperty](../api/extensionproperty_get.md) | [extensionProperty](extensionproperty.md) |读取属性和关系的 extensionProperty 对象。|
|[更新](../api/extensionproperty_update.md) | [extensionProperty](extensionproperty.md)   |更新 extensionProperty 对象。 |
|[删除](../api/extensionproperty_delete.md) | 无 |删除 extensionProperty 对象。 |
|[checkMemberGroups](../api/extensionproperty_checkmembergroups.md)|字符串集合||
|[getMemberGroups](../api/extensionproperty_getmembergroups.md)|字符串集合||
|[getMemberObjects](../api/extensionproperty_getmemberobjects.md)|字符串集合||

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "extensionProperty resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
