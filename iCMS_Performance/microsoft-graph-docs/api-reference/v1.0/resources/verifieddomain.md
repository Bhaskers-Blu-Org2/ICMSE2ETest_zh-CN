# <a name="verifieddomain-resource-type"></a>verifiedDomain 资源类型

指定域的租户。 [组织](organization.md)实体的**verifiedDomains**属性是集合的**VerifiedDomain**。


## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|功能|String|例如，"电子邮件"，"OfficeCommunicationsOnline"。|
|后|Boolean|                **如此**如果这是默认的域与租户;否则为**假**。            |
|isInitial|Boolean|**如此**如果这是初始域与租户;否则为**假**|
|name|String|域的名称;例如，"contoso.onmicrosoft.com"|
|类型|String|例如，"托管"。|


## <a name="json-representation"></a>JSON 表示形式

这里是 JSON 表示的资源

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.verifieddomain"
}-->

```json
{
  "capabilities": "string",
  "isDefault": true,
  "isInitial": true,
  "name": "string",
  "type": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "verifiedDomain resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
