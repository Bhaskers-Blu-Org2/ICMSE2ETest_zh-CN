# <a name="create-application"></a>创建应用程序

使用此 API 来创建新的应用程序。
## <a name="prerequisites"></a>先决条件
要执行此 API 需要以下**范围**︰ 

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /applications
```

## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| 授权  | string  | 载体 {标记}。 必需。 |

## <a name="request-body"></a>请求正文
在请求正文中，提供[应用程序](../resources/application.md)对象的 JSON 表示。


## <a name="response"></a>响应
如果成功，此方法返回`201, Created`在响应正文中的响应代码和[应用程序](../resources/application.md)对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "create_application_from_applications"
}-->
```http
POST https://graph.microsoft.com/beta/applications
Content-type: application/json
Content-length: 717

{
  "addIns": [
      {
        "id": "id-value",
        "type": "type-value",
        "properties": [
          {
            "key": "key-value",
            "value": "value-value"
          }
        ]
      }
    ],
    "appRoles": [
      {
        "allowedMemberTypes": [
          "allowedMemberTypes-value"
        ],
        "description": "description-value",
        "displayName": "displayName-value",
        "id": "id-value",
        "isEnabled": true,
        "origin": "origin-value",
        "value": "value-value"
      }
    ],
    "availableToOtherOrganizations": true,
    "displayName": "displayName-value",
    "errorUrl": "errorUrl-value"
}
```
在请求正文中，提供[应用程序](../resources/application.md)对象的 JSON 表示。
##### <a name="response"></a>响应
这里是响应的示例。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.application"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 717

{
  "application": {
    "addIns": [
      {
        "id": "id-value",
        "type": "type-value",
        "properties": [
          {
            "key": "key-value",
            "value": "value-value"
          }
        ]
      }
    ],
    "appId": "appId-value",
    "appRoles": [
      {
        "allowedMemberTypes": [
          "allowedMemberTypes-value"
        ],
        "description": "description-value",
        "displayName": "displayName-value",
        "id": "id-value",
        "isEnabled": true,
        "origin": "origin-value",
        "value": "value-value"
      }
    ],
    "availableToOtherOrganizations": true,
    "displayName": "displayName-value",
    "errorUrl": "errorUrl-value"
  }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create Application",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
