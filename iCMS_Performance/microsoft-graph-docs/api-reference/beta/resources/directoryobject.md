# <a name="directoryobject-resource-type"></a>directoryObject 资源类型

表示一个 Azure Active Directory 对象。 **DirectoryObject**类型是许多其他目录实体类型的基类型。


## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 directoryObject](../api/directoryobject_get.md) | [directoryObject](directoryobject.md) |读取的目录对象的属性。|
|[删除](../api/directoryobject_delete.md) | 无 |删除目录对象。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|String|Guid 的对象; 父对象的唯一标识符例如，12345678-9abc-def0-1234年-56789abcde。 键。 不可以为 null。 只读的。|

## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.directoryObject"
}-->

```json
{
  "id": "string (identifier)"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "directoryObject resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
