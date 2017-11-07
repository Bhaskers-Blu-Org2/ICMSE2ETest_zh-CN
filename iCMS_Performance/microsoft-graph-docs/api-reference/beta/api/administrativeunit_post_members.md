# <a name="add-a-member"></a>添加成员

使用此 API 成员 （用户或组） 添加到一个管理单元。

`NOTE: Currently it's only possible to add one member at a time to an administrative unit.`

## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /administrativeUnits/<id>/members/$ref
```
## <a name="request-headers"></a>请求标头
| 名称      |说明|
|:----------|:----------|
| 授权  | 持有者<token>。 必需。|

## <a name="request-body"></a>请求正文
在请求正文中，提供[用户](../resources/user.md)、[组](../resources/group.md)或添加[directoryObject](../resources/directoryObject.md)的 JSON 表示。

## <a name="response"></a>响应
如果成功，此方法返回`204, No Content`响应代码。 它不返回任何响应正文中。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。

```http
POST https://graph.microsoft.com/beta/administrativeUnits/<id>/members/$ref
Content-type: application/json
Content-length: 109

{
  "@odata.id":"https://graph.microsoft.com/beta/groups/<id>"
}

```
在请求正文中，提供的 JSON 表示`id`您想要添加的[用户](../resources/user.md)或[组](../resources/group.md)对象。

##### <a name="response"></a>响应
这里是响应的示例。
 
```http
HTTP/1.1 204 No Content
```
