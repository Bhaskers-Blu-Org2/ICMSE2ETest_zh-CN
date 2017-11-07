# <a name="helpers-examples-that-arent-included-in-the-docs"></a>帮助程序 （未包含在文档中的示例）

这些是我不得不在这些文档，以确保减价扫描仪工具无法正确处理这些关系图文档中添加的内容。


## <a name="define-the-me-as-singleton"></a>作为单一实例定义 /me

<!-- {"blockType": "request", "name": "get_current_user" } -->
```http
GET https://graph.microsoft.com/v1.0/me
```

<!-- {"blockType": "response", "@odata.type": "microsoft.graph.user", truncated: true } -->
```http
HTTP/1.1 200 OK

{
}
```


## <a name="define-drives-as-an-queryable-entityset"></a>根据可查询实体定义驱动器
<!-- {"blockType": "request", "name": "get_drive_from_id" } -->
```http
GET https://graph.microsoft.com/v1.0/drives/{drive-id}
```

<!-- {"blockType": "response", "@odata.type": "microsoft.graph.drive", truncated: true } -->
```http
HTTP/1.1 200 OK

{
}
```


## <a name="define-users-as-an-queryable-entityset"></a>将用户定义为可查询实体

<!-- {"blockType": "request", "name": "get_users" } -->
```http
GET https://graph.microsoft.com/v1.0/users/{user-id}
```

<!-- {"blockType": "response", "@odata.type": "microsoft.graph.user", truncated: true } -->
```http
HTTP/1.1 200 OK

{
}
```
