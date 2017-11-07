# <a name="update-plandetails"></a>更新 plandetails

更新 plandetails 对象的属性。
## <a name="prerequisites"></a>先决条件
以下**范围**之一是执行此 API 所需的︰
 
Group.ReadWrite.All

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /plans/<id>/details

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| 授权  | string  | 值应该设置为"载体 （访问令牌）" |
| 如果匹配 | string | 应设置对象的 ETag 值 |
| 更喜欢 | string | 值应该设置为"返回 = 表示"以便在响应中返回更新后的对象。 这被建议，以便客户端可以获得新的 ETag 值的更新后的对象而无需进行更多的获取 |

## <a name="request-body"></a>请求正文
在请求正文中，提供相关应更新的字段的值。 不包括在请求正文中的现有属性将保留其以前的值或重新计算基于的更改其他属性值。 为了获得最佳性能不应包括尚未更改的现有值。

| 属性     | 类型   |说明|
|:---------------|:--------|:----------|
|category0Description|String|可应用于任务的说明的类别 （或标签）。|
|category1Description|String|可应用于任务的说明的类别 （或标签）。|
|category2Description|String|可应用于任务的说明的类别 （或标签）。|
|category3Description|String|可应用于任务的说明的类别 （或标签）。|
|category4Description|String|可应用于任务的说明的类别 （或标签）。|
|category5Description|String|可应用于任务的说明的类别 （或标签）。|
|sharedWith|[userIdCollection](../resources/useridcollection.md)| 此计划与共享的用户 id 的列表。 如果您将充分利用 Office 365 组，使用组 API 管理组成员共享组的计划。 但不是必需为其访问组拥有的计划，还可以向此集合添加组的现有成员。|

## <a name="response"></a>响应
如果成功，此方法返回`204 No Content`响应代码。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "update_plandetails"
}-->
```http
PATCH https://graph.microsoft.com/beta/plans/<id>/details
Content-type: application/json
Content-length: 381
If-Match: W/"JzEtMDAwMDAwMDAwMDAwMDAwOC8yMDE1LTEwLTIyVDE4OjExOjU2LjExMzU1NDYrMDA6MDAn"

{
  "sharedWith": {
  },
  "category0Description": "category0Description-value",
  "category1Description": "category1Description-value",
  "category2Description": "category2Description-value",
  "category3Description": "category3Description-value",
  "category4Description": "category4Description-value",
  "category5Description": "category5Description-value"
}
```
##### <a name="response"></a>响应
这里是响应的示例。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.plandetails"
} -->
```http
HTTP/1.1 204 No Content
```
若要获取已更新的对象，请使用`Prefer`头。 请参阅上面的请求标头。
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update plandetails",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->