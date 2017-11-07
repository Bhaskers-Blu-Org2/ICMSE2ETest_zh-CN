# <a name="microsoft-graph-optional-query-parameters"></a>Microsoft Graph 可选的查询参数
## <a name="optional-odata-query-parameters"></a>可选的 OData 查询参数
Microsoft Graph 提供了一些可选的查询参数，可用于指定和控制的响应中返回的数据量。 Microsoft Graph 提供了下面的查询选项。 

|名称|值|说明|
|:---------------|:--------|:-------|
|$select|字符串|要在响应中包含的属性的逗号分隔列表。|
|$ expand|字符串|关系展开，并在响应中包含以逗号分隔的列表。  |
|$orderby|字符串|用于响应集合中的项进行排序的属性的逗号分隔列表。|
|$filter|字符串|筛选器基于一组条件的响应。|
|$top|整数|在结果集中返回的项的数目。|
|$skip|整数|结果集中要跳过的项的数目。|
|$skipToken|字符串|用于获取下一步的结果集的分页标记。|
|$count|无|一个集合，集合中的项的数目。|


**编码的查询参数**

- 如果您试用[Microsoft Graph 资源管理器](https://graphexplorer2.azurewebsites.net/)中的查询参数，您可以复制和粘贴不用任何 URL 编码的查询字符串到下面的示例。 下面的示例正常工作_的图形浏览器中_没有空格和引号字符进行编码︰
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address eq 'jon@contoso.com'
``` 
- 一般情况下，在指定查询参数_在您的应用程序_时，确保适当编码仅[供 URI 中的特殊含义](https://tools.ietf.org/html/rfc3986#section-2.2)的字符。
例如，编码在最后一个示例中，空格和引号的字符，如下所示︰
```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address%20eq%20%27jon@contoso.com%27
```

### <a name="select"></a>$select
若要指定要返回的属性的子集，请使用**$select**查询选项。 例如，当检索您的邮件，您可能想要选择的并且只有**从**和返回的邮件的**主题**属性。

```http
GET https://graph.microsoft.com/v1.0/me/messages?$select=from,subject
```

<!--For example, when retrieving the children of an item on a drive, you want to select that only the **name** and **size** properties of items are returned.

```http
GET https://graph.microsoft.com/v1.0/me/drive/root/children?$select=name,size
```

By submitting the request with the `$select=name,size` query string, the objects
in the response will only have those property values included. 


```json
{
  "value": [
    {
      "id": "13140a9sd9aba",
      "name": "Documents",
      "size": 1024
    },
    {
      "id": "123901909124a",
      "name": "Pictures",
      "size": 1012010210
    }
  ]
}
```--> 

### <a name="expand"></a>$ expand

在 Microsoft Graph API 请求中，不自动扩展导航到对象或引用的项的集合。 这是由设计因为它减少了网络流量和从服务生成响应所花费的时间。 但是，在某些情况下您可能需要在响应中包含这些结果。

**$Expand**查询字符串参数可用于指示要展开的子对象或集合，包括那些结果的 API。

例如，若要检索根驱动器信息和顶层级别的孩子项在驱动器中，您使用**$expand**参数。 本示例还使用**$select**语句仅返回子级的_id_和_名称_的属性的项。

```http
GET https://graph.microsoft.com/v1.0/me/drive/root?$expand=children($select=id,name)
```

>  **注意**︰ 扩展对象请求的最大数目为 20。 

> 此外，如果查询的[用户](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/user)资源，可用于**$expand**获取的属性只有一个子对象或集合一次。 

下面的示例获取**用户**对象，每个都有扩展**directReports**集合中的最多 20 个**directReport**对象︰
```http
GET https://graph.microsoft.com/v1.0/users?$expand=directReports
```
某些其他资源可能有限制以及，因此总是检查可能出现的错误。


<!---The following shows a sample result that is returned in the response body.-->


### <a name="orderby"></a>$orderby

若要指定从 API 返回的项的排序顺序，请使用**$orderby**查询选项。 

例如，若要返回用户订购其显示名称的组织中，语法是，如下所示︰

```http
GET https://graph.microsoft.com/v1.0/users?$orderBy=displayName
``` 

您还可以排序的复杂类型的实体。 下面的示例获取消息并对它们的**从**属性，该属性的复杂类型**电子邮件地址**的**地址**字段进行排序︰

```http
GET https://graph.microsoft.com/v1.0/me/messages?$orderBy=from/emailAddress/address
``` 

若要按升序或降序顺序对结果进行排序，追加`asc`或`desc`之间用一个空格，例如，分隔的字段名称为`?orderby=name%20desc`。

 >  **注意**︰ 不能与 $filter 表达式组合**$orderby** 。

### <a name="filter"></a>$filter
若要筛选基于一组条件的响应数据，请使用**$filter**查询选项。
例如，要返回开头"Garth"的显示名称组织筛选器中的用户，其语法是，如下所示。

```http
GET https://graph.microsoft.com/v1.0/users?$filter=startswith(displayName,'Garth')
```

您还可以按复杂类型的实体进行筛选。 下面的示例返回具有等同于**从**属性的**地址**字段的消息"jon@contoso.com". **from**属性属于复杂类型**电子邮件地址**。

```http
GET https://graph.microsoft.com/v1.0/me/messages?$filter=from/emailAddress/address eq 'jon@contoso.com'
``` 

### <a name="top"></a>$top
若要指定要在结果集中返回的最大项数，请使用**$top**查询选项。 **$Top**查询选项标识集合中的一个子集。 此子集形成通过选择只前 N 个项的设置，其中 N 是一个正整数值，指定此查询选项。 例如，若要返回用户的邮箱中的前五个消息，语法是，如下所示︰

```http
GET https://graph.microsoft.com/v1.0/me/messages?$top=5
```

### <a name="skip"></a>$skip
若要设置跳过检索集合中的项之前的项数，请使用**$skip**查询选项。 例如，若要返回按创建日期、 事件和 21 事件开始的语法是，如下所示。

```http
GET  https://graph.microsoft.com/v1.0/me/events?$orderby=createdDateTime&$skip=20
```

### <a name="skiptoken"></a>$skipToken
页并指定下一个要返回的结果集，请使用**$skipToken**查询选项。  **$SkipToken**查询选项的值是一个标记，用于标识集合中的起始点。 例如， **$skipToken**查询选项的值无法标识集合中的第一个项目或包含 20 项或在集合中的任何其他位置的集合中的第 8 项。

由于**$skipToken**查询选项的值标识索引划分成一组，在查询中使用它标识项的子集。 通过一组中的最后一项 （由**$skipToken**查询选项的值标识） 的索引处的第一项启动标识的子集。

在一些响应，您将看到`@odata.nextLink`值。 它们中的一些包括**$skipToken**值。  **$SkipToken**值就像一种标记，告诉该服务位置继续下一步的结果集。  下面是一个示例`@odata.nextLink`从响应值。

```
"@odata.nextLink": "https://graph.microsoft.com/v1.0/users?$orderby=displayName&$top=3&$skiptoken=X%2783630372100000000000000000000%27"
```

例如，要返回下一组用户在组织中，每次在结果中，限制为 3 号的语法是，如下所示。

```http
GET  https://graph.microsoft.com/v1.0/users?$orderby=displayName&$top=3&$skiptoken=X%2783630372100000000000000000000%27
```

### <a name="count"></a>$count
使用**$count**作为查询参数，如以下示例所示︰
```http
GET  https://graph.microsoft.com/v1.0/me/contacts?$count=true
```
这将在**联系人**集合中返回**联系人**集合和项的数目`@odata.id`属性。

注意︰ 这不是支持[directoryObject](http://graph.microsoft.io/en-us/docs/api-reference/v1.0/resources/directoryobject)集合。
