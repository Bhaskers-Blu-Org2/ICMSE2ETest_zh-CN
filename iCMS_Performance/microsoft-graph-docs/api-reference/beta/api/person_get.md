# <a name="get-person"></a>获得某人

检索的属性和一个 person 对象的关系。
## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *People.Read*;*User.ReadBasic.All*
 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /me/people/<id>
GET /users/<id>/people/<id>
```
## <a name="optional-query-parameters"></a>可选的查询参数
|名称|值|说明|
|:---------------|:--------|:-------|
|$filter|字符串|限制对其记录包含指定的条件的那些人的响应。|
|$orderby|字符串|默认情况下按其与查询的相关性排序响应中的人。 您可以更改使用*$orderby*参数的响应中人员的顺序。|
|$search|string|搜索人员按名称或别名。 支持模糊匹配|
|$select|字符串|要在响应中包含的属性的逗号分隔列表。 为获得最佳性能，仅选择所需的属性的子集。|
|$skip|整数|跳过第一个 n 结果用于分页。 仅在使用*$search*时，不支持这样做。|
|$top|整数|要返回的结果数。|

## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<code>|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。
## <a name="response"></a>响应
如果成功，此方法返回`200 OK`在响应正文中的响应代码和[用户](../resources/person.md)对象。
## <a name="examples"></a>示例
#### <a name="browse"></a>浏览
以下请求获取用户与用户，基于通信、 协作和业务关系密切相关。 默认情况下，每个响应返回 10 条记录，但您可以更改此使用*$top*参数。 该请求需要*People.Read*范围。

<!-- {
  "blockType": "request",
  "name": "get_person"
}-->
```http
GET https://graph.microsoft.com/beta/me/people/
```

这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.person"
} -->

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 196

{
  "displayName": "displayName-value",
  "givenName": "givenName-value",
  "surname": "surname-value",
  "birthday": "birthday-value",
  "personNotes": "personNotes-value",
  "isFavorite": true
}
```

##### <a name="requesting-a-subsequent-page-of-people"></a>请求人后续页
如果第一个响应中不包含的相关人员的完整列表，您可以使用*$top*和*$skip*请求信息的其他页面的第二个请求。 如果前一个请求有更多的信息，以下请求从服务器上获取下一个页面的人。

```http
GET https://graph.microsoft.com/beta/me/people/?$top=10&$skip=10
```

##### <a name="sort-the-response"></a>对响应进行排序
默认情况下按其与查询的相关性排序响应中的人。 您可以更改使用*$orderby*参数的响应中人员的顺序。 此查询选择与您最相关的人员，按其显示名称，进行排序然后对已排序列表中返回的前 10 人。

```http
GET https://graph.microsoft.com/beta/me/people/?$orderby=DisplayName
```
##### <a name="changing-the-number-of-people-returned-and-the-fields-returned"></a>更改人员返回和返回的字段的数
您可以更改通过将*$top*参数设置响应中返回的人数。 

下面的示例请求 1000 最相关的人。 该请求还限制请求仅人显示名称重新从服务器发送的数据量。


```http
GET https://graph.microsoft.com/beta/me/people/?$top=1000&$Select=DisplayName
```
##### <a name="selecting-the-fields-to-return"></a>选择要返回的字段
您可以限制通过使用*$select*参数来选择一个或多个字段从服务器返回的数据量。 *@odata.id*字段始终返回。

下面的示例将限制响应的*显示名称*和*电子邮件地址*的 10 个最相关的人员。

```http
GET https://graph.microsoft.com/beta/me/people/?$select=DisplayName,EmailAddresses
```
##### <a name="using-a-filter-to-limit-the-response"></a>使用筛选器来限制响应
您可以使用*$filter*参数来限制对其记录包含指定的条件的那些人的响应。 

下面的查询限制的响应人士源"目录。


```http
GET https://graph.microsoft.com/beta/me/people/?$Filter=Sources/Any (source: source/Type  eq 'Directory')
```

##### <a name="selecting-the-fields-to-return-in-a-filtered-response"></a>选择要筛选的响应中返回的字段

您可以结合使用*$select*和*$filter*参数创建与用户相关的用户的自定义列表和获取相应应用程序需要的字段。 

下面的示例获取*显示名称*和*电子邮件地址*的人员其显示名称等于指定的名称。 在此示例中，将返回其显示名称等于"Nestor Kellum"的人。 


```http
GET https://graph.microsoft.com/beta/me/people/?$select=DisplayName,EmailAddresses&$Filter=DisplayName eq 'Nestor Kellum'
```

#### <a name="search-people"></a>搜索用户
搜索请求需要*People.Read*范围。

##### <a name="using-search-to-select-people"></a>使用搜索来选择的人

*$Search*参数用于选择满足一组特定条件的人。 

以下搜索查询返回的 GivenName 或姓以字母"j"开头的相关人员。

```http
GET https://graph.microsoft.com/beta/me/people/?$search=j
```
##### <a name="using-search-to-specify-a-relevant-topic"></a>使用搜索可以指定相关主题

以下请求返回相关人员名称中包含"ma"，谁具有关联"规划功能。"

```http
GET https://graph.microsoft.com/beta/me/people/?$search="ma topic: feature planning"
```
##### <a name="performing-a-fuzzy-search"></a>执行模糊搜索

以下请求 does 搜索人名"Hermaini 大厅"。 由于没有名为"Herminia 轮廓"的相关人员，则返回"Herminia 轮廓"的信息。

```http
GET https://graph.microsoft.com/beta/me/people/?$search="hermaini hall"
```
#### <a name="related-people"></a>相关的人员

以下请求用户的组织中获取人们与他人密切相关。 该请求需要*User.ReadBasic.All*范围。 在此示例中，显示 Nestor Kellum 相关人员。

```http
GET https://graph.microsoft.com/beta/users('nestork@contoso.com')/people/
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get person",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
