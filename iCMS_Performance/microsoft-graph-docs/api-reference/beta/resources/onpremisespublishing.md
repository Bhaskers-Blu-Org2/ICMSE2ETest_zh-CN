# <a name="onpremisespublishing-resource-type"></a>onPremisesPublishing 资源类型




## <a name="properties"></a>属性
| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|customDomainCertificate|String|在使用自定义的域时，与应用程序关联的证书的详细信息。 为空时使用的默认域。|
|externalAuthenticationType|String|详细介绍了预身份验证设置，应用程序可能的值为︰ `passthru`， `aadPreAuthentication`。|
|externalUrl|String|应用程序的已发布外部 url。 例如 https://intranet-contoso.msappproxy.net/  |
|internalUrl|String|内部应用程序的 url。 例如 http://intranet/|
|isOnPremPublishingEnabled|Boolean|如果应用程序当前是否正在发布的指示。|
|isTranslateHostHeaderEnabled|Boolean|指示该应用程序应将翻译的响应标头中的 url。 这包括设置正确的站点的 cookie。|

## <a name="json-representation"></a>JSON 表示形式

这里是资源的 JSON 表示。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.onPremisesPublishing"
}-->

```json
{
  "customDomainCertificate": "String",
  "externalAuthenticationType": "String",
  "externalUrl": "String",
  "internalUrl": "String",
  "isOnPremPublishingEnabled": true,
  "isTranslateHostHeaderEnabled": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "onPremisesPublishing resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->