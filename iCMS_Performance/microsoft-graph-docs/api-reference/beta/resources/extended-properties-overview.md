# <a name="outlook-extended-properties-overview"></a>Outlook 的扩展属性概述

扩展的属性允许将自定义的数据存储和专门用作回退机制使应用程序访问 Outlook 的 MAPI 属性的自定义数据时，这些属性是_在 Microsoft Graph API 元数据中未被公开_。 可以使用扩展的属性 REST API 来存储或以下的用户资源中获取这种自定义的数据︰

- [消息](../resources/message.md)
- [mailFolder](../resources/mailfolder.md)
- [事件](../resources/event.md)
- [日历](../resources/calendar.md)
- [联系人](../resources/contact.md)
- [contactFolder](../resources/contactfolder.md) 

或者，下面的 Office 365 中对资源进行分组︰

- 组[事件](../resources/event.md)
- 组[日历](../resources/calendar.md)
- 组[过帐](../resources/post.md) 

## <a name="use-extended-properties-or-office-365-data-extensions"></a>使用扩展的属性或 Office 365 的数据扩展？

在大多数情况下，应该可以使用 Office 365 数据扩展插件 （由[openTypeExtension](../resources/opentypeextension.md)） 来存储和访问用户的邮箱中的资源实例的自定义数据。 仅当您需要访问自定义用于 Outlook 的 MAPI 属性不在[Microsoft Graph API 的元数据](http://graph.microsoft.io/en-us/docs/overview/call_api)中已经公开的数据，请使用扩展的属性。

## <a name="types-of-extended-properties"></a>扩展属性的类型

这取决于您是否打算将 （具有相同的类型） 的单个或多个值存储在一个扩展属性，您可以创建扩展的属性为[singleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md)或[multiValueLegacyExtendedProperty](../resources/multiValueLegacyExtendedProperty.md)。

每种类型由其**id**标识的属性和**值**中存储的数据。 

可以使用**id**来获取扩展属性，以及一个特定的资源实例或筛选扩展属性获取该属性的所有实例的单个值。 

**请注意**不能使用 REST API 来在一个调用中获取的特定实例的所有扩展的属性。
  

## <a name="id-formats"></a>id 格式

当创建一个单值或多值的扩展的属性，您可以根据字符串名称或数字标识符和属性的值或值的实际类型的两种格式之一指定**id** 。 因为扩展的属性是用 Microsoft Graph API 元数据中，为了简单起见，在不公开的定义 MAPI 属性间操作的大多数情况下您选择的格式应反映相应的 MAPI 属性是否使用[MAPI 属性标识符](https://msdn.microsoft.com/en-us/library/office/cc815528.aspx)中的字符的字符串或数字值。

**请注意**在选择一种格式的**id**后，您应只该格式访问扩展的属性。


**单值扩展属性的有效的 id 格式**

|**格式**|**示例**|**说明**|
|:---------|:----------|:--------------|
| "*{_type_} {_guid_} **Name** {_name_}*" | ```"String {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | 标识由其所属的命名空间 (GUID) 和名称属性。         |
| "*{_type_} {_guid_} **Id** {_id_}*"     | ```"Integer {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8012"```        | 标识由其所属的命名空间 (GUID) 和标识符的属性。  |


**多值扩展属性的有效的 id 格式**

|**格式**|**示例**|**说明**|
|:---------|:----------|:--------------|
| "*{_type_} {_guid_} **Name** {_name_}*" | ```"StringArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | 标识 (GUID) 的命名空间和名称属性。         |
| "*{_type_} {_guid_} **Id** {_id_}*"     | ```"IntegerArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8013"```        | 标识由命名空间 (GUID) 和标识符的属性。   |


## <a name="rest-api-operations"></a>REST API 操作
 
单值扩展属性操作︰
- [在新的或现有的资源实例中创建扩展的属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md)
- [得到一个值或使用扩展的属性的资源实例的集合`$expand`或`$filter`](../api/singlevaluelegacyextendedproperty_get.md)

扩展的多值属性的操作︰
- [在新的或现有的资源实例中创建扩展的属性](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md)
- [获取扩展的属性使用的资源实例`$expand`](../api/multivaluelegacyextendedproperty_get.md)

