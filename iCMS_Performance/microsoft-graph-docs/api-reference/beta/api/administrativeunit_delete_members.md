# <a name="remove-a-member"></a>删除成员

使用此 API 来删除的成员 （用户或组） 从一个管理单元。

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
DELETE /administrativeUnits/<id>/members/<id>/$ref
```
## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
请不要提供此方法请求正文。

## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。 在下面的示例中，id1 为目标管理单位表示的标识符和 id2 表示要从指定的管理单元中删除的成员用户或组的唯一标识符。 

```http
DELETE https://graph.microsoft.com/beta/administrativeUnits/<id1>/members/<id2>/$ref
```

##### <a name="response"></a>响应
这里是响应的示例。
 
```http
HTTP/1.1 204 No Content
```
