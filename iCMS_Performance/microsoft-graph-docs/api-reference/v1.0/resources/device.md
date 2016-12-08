# <a name="device-resource-type"></a>设备资源类型

表示目录中注册的设备。 从[directoryObject](directoryobject.md)继承。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获取设备](../api/device_get.md) | [设备](device.md) |读取属性和关系的设备对象。|
|[创建 registeredOwner](../api/device_post_registeredowners.md) |[directoryObject](directoryobject.md)| 作为该设备的新所有者的用户添加由过账到 registeredOwners 导航属性。|
|[列表 registeredOwners](../api/device_list_registeredowners.md) |[directoryObject](directoryobject.md)集合| 获取设备 registeredOwners 导航属性的注册的所有者的用户。|
|[创建 registeredUser](../api/device_post_registeredusers.md) |[directoryObject](directoryobject.md)| 设备已注册的用户添加由过账到 registeredUsers 导航属性。|
|[列表 registeredUsers](../api/device_list_registeredusers.md) |[directoryObject](directoryobject.md)集合| 从 registeredUsers 导航属性获取设备的注册的用户。|
|[更新](../api/device_update.md) | [设备](device.md)  |更新设备对象的属性。 |
|[删除](../api/device_delete.md) | 无 |删除的设备对象。 |



## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|accountEnabled|Boolean| **如此**如果启用了帐户;否则为**假**。 |
|alternativeSecurityIds|[alternativeSecurityId](alternativesecurityid.md)集合| **Any**运算符，则需要为多值属性的筛选器表达式。 不可以为 null。           |
|approximateLastSignInDateTime|方法|            时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|deviceId|Guid|            |
|deviceMetadata|String||
|操作系统|String|在设备上的操作系统的类型。|
|operatingSystemVersion|String|在设备上的操作系统版本|
|deviceVersion|Int32|            |
|physicalIds|字符串集合| 不可以为 null。            |
|trustType|String||
|onPremisesSyncEnabled|Boolean|**如此**如果此对象同步从本地目录中。**假**如果此对象最初从内部目录同步，但不会再同步;**null**如果该对象已永远不会从内部目录 （默认值） 进行同步。|
|显示名称|String|该设备为显示名称。|
|isCompliant|Boolean|**如此**如果设备符合移动设备管理 (MDM) 策略;否则为**假**。|
|isManaged|Boolean|**如此**如果设备由一个移动设备管理 (MDM) 应用程序，如 Intune;否则为**假**。|
|onPremisesLastSyncDateTime|方法|上一次的对象与内部目录同步。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|id|String|设备的唯一标识符。 从[directoryObject](directoryobject.md)继承。 键，不可以为 null。 只读的。|

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|registeredOwners|[directoryObject](directoryobject.md)集合|该设备的注册的所有者的用户。 只读的。 可以为 null。|
|registeredUsers|[directoryObject](directoryobject.md)集合|注册的用户的设备的用户。 只读的。 可以为 null。|



## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "registeredOwners",
    "registeredUsers"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.device"
}-->

```json
{
  "accountEnabled": true,
  "alternativeSecurityIds": [{"@odata.type": "microsoft.graph.alternativeSecurityId"}],
  "approximateLastSignInDateTime": "String (timestamp)",
  "deviceId": "string",
  "deviceMetadata": "string",
  "deviceVersion": 1024,
  "displayName": "string",
  "id": "string (identifier)",
  "isCompliant": true,
  "isManaged": true,
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "operatingSystem": "string",
  "operatingSystemVersion": "string",
  "physicalIds": ["string"],
  "trustType": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "device resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
