# <a name="update-device"></a>更新设备

更新设备的属性。
## <a name="prerequisites"></a>先决条件
需执行此 API 之一以下**范围**︰ *Device.ReadWrite.All*或*Directory.ReadWrite.All*或*Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /devices/<id>
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 持有者<token>。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|accountEnabled|Boolean| **如此**如果启用了帐户;否则为**假**。 |
|alternativeSecurityIds|[alternativeSecurityId](../resources/alternativesecurityid.md)集合| **Any**运算符，则需要为多值属性的筛选器表达式。 不可以为 null。           |
|approximateLastSignInDateTime|方法|            时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|deviceId|Guid|            |
|deviceMetadata|String||
|操作系统|String|在设备上的操作系统的类型。|
|operatingSystemVersion|String|在设备上的操作系统版本|
|deviceVersion|Int32|            |
|physicalIds|字符串集合| 不可以为 null。            |
|trustType|String||
|显示名称|String|该设备为显示名称。|
|isCompliant|Boolean|**如此**如果设备符合移动设备管理 (MDM) 策略;否则为**假**。|
|isManaged|Boolean|**如此**如果设备由一个移动设备管理 (MDM) 应用程序，如 Intune;否则为**假**。|

## <a name="response"></a>响应
如果成功，此方法返回`200 OK`响应代码和更新的[设备](../resources/device.md)对象在响应正文中。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_device"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/devices/<id>
Content-type: application/json
Content-length: 322

{
  "accountEnabled": true,
  "alternativeSecurityIds": [
    {
      "type": 99,
      "identityProvider": "identityProvider-value",
      "key": "key-value"
    }
  ],
  "approximateLastSignInDateTime": "datetime-value",
  "deviceId": "deviceId-value",
  "deviceMetadata": "deviceMetadata-value",
  "deviceVersion": 99
}
```
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.device"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 322

{
  "accountEnabled": true,
  "alternativeSecurityIds": [
    {
      "type": 99,
      "identityProvider": "identityProvider-value",
      "key": "key-value"
    }
  ],
  "approximateLastSignInDateTime": "datetime-value",
  "deviceId": "deviceId-value",
  "deviceMetadata": "deviceMetadata-value",
  "deviceVersion": 99
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update device",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
