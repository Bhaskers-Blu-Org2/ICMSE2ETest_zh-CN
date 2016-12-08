# <a name="orgcontact-resource-type"></a>orgContact 资源类型



## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "directReports",
    "manager",
    "memberOf"
  ],
  "@odata.type": "microsoft.graph.orgcontact"
}-->

```json
{
  "businessPhones": ["string"],
  "city": "string",
  "companyName": "string",
  "country": "string",
  "department": "string",
  "displayName": "string",
  "givenName": "string",
  "id": "string (identifier)",
  "jobTitle": "string",
  "mail": "string",
  "mailNickname": "string",
  "mobilePhone": "string",
  "officeLocation": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "postalCode": "string",
  "proxyAddresses": ["string"],
  "state": "string",
  "streetAddress": "string",
  "surname": "string"
}

```
## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|市/县|String||
|国家/地区|String||
|部门|String||
|onPremisesSyncEnabled|Boolean||
|显示名称|String||
|givenName|String||
|职务|String||
|onPremisesLastSyncDateTime|方法|时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。 例如，午夜 UTC 在 2014 年 1 月 1，如下所示︰`'2014-01-01T00:00:00Z'`|
|邮件|String||
|mailNickname|String||
|mobilePhone|String||
|id|String| 只读的。|
|办公室|String||
|邮政编码|String||
|代理地址|字符串集合||
|状态|String||
|街道地址|String||
|姓氏|String||
|businessPhones|String||

## <a name="relationships"></a>Relationships
| 关系 | 类型   |说明|
|:---------------|:--------|:----------|
|directReports|[directoryObject](directoryobject.md)集合| 只读的。 可以为 null。|
|经理|[directoryObject](directoryobject.md)| 只读的。|
|memberOf|[directoryObject](directoryobject.md)集合| 只读的。 可以为 null。|

## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获得 orgContact](../api/orgcontact_get.md) | [orgContact](orgcontact.md) |读取属性和关系的 orgContact 对象。|
|[创建 directReport](../api/orgcontact_post_directreports.md) |[directoryObject](directoryobject.md)| 由过账到 directReports 集合中创建新的 directReport。|
|[列表 directReports](../api/orgcontact_list_directreports.md) |[directoryObject](directoryobject.md)集合| 获得 directReport 对象集合。|
|[创建 memberOf](../api/orgcontact_post_memberof.md) |[directoryObject](directoryobject.md)| 创建新的 memberOf 由过账到 memberOf 集合。|
|[列表 memberOf](../api/orgcontact_list_memberof.md) |[directoryObject](directoryobject.md)集合| 获取 memberOf 对象集合。|
|[更新](../api/orgcontact_update.md) | [orgContact](orgcontact.md)    |更新 orgContact 对象。 |
|[删除](../api/orgcontact_delete.md) | 无 |删除 orgContact 对象。 |
|[checkMemberGroups](../api/orgcontact_checkmembergroups.md)|字符串集合||
|[getMemberGroups](../api/orgcontact_getmembergroups.md)|字符串集合||
|[getMemberObjects](../api/orgcontact_getmemberobjects.md)|字符串集合||

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "orgContact resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->