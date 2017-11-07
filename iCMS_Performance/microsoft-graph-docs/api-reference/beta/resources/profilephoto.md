# <a name="profilephoto-resource-type"></a>profilePhoto 资源类型
用户、 组或从 Exchange 联机或 Azure 活动目录 (AAD) 访问 Outlook 联系人的个人资料照片。 它是不以 base-64 编码的二进制数据。

支持的 Exchange Online 上的高清晰度照片的大小如下所示:"48 x 48"、 'x64 的 64'、"96 96 倍"、"x 120 120"、"240 x 240"、"360 x 360，432 x 432'、 '504 x 504' 和 ' 648 x 648。 在 AAD，照片可以是任何尺寸。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获得 profilePhoto](../api/profilephoto_get.md) | [profilePhoto](profilephoto.md) |获取指定的**profilePhoto**或其元数据 （**profilePhoto**属性）。 |
|[更新](../api/profilephoto_update.md) | [profilePhoto](profilephoto.md)  |分配给指定的用户、 组或联系人的照片。 照片应该是二进制文件中。 它将替换现有的照片，如果有的话。 |


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|id|string|只读的。|
|height|int32|图片的高度。 只读的。|
|width|int32|图片的宽度。 只读的。|


## <a name="relationships"></a>Relationships
无


## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.profilePhoto"
}-->

```json
{
  "id": "240X240",
  "height": 240,
  "width": 240
}

```
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "profilePhoto resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
