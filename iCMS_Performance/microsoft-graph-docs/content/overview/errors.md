# <a name="microsoft-graph-error-responses-and-resource-types"></a>Microsoft Graph 错误响应和资源类型

<!--In this article:
  
-   [Status code](#msg_status_code)
-   [Error resource type](#msg_error_resource_type)
-   [Code property](#msg_code_property)

<a name="msg_error_response"> </a> -->

##<a name="status-code"></a>状态代码
使用标准的 HTTP 状态代码，以及错误响应一个 JSON 返回 Microsoft Graph API 服务中的错误。 应具有以下 HTTP 状态代码。

| 状态代码 | 状态消息                  | 说明                                                                                                                            |
|:------------|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| 400         | 错误的请求                     | 因为它是不正确或不正确，无法处理此请求。                                                                       |
| 401         | 未经授权                    | 所需的身份验证信息已丢失或无效的资源。                                                   |
| 403         | 禁止访问                       | 拒绝访问请求的资源。 用户可能没有足够的权限。                                                 |
| 404         | 找不到                       | 所请求的资源不存在。                                                                                                  |
| 405         | 不允许的方法              | 在资源上不允许在请求的 HTTP 方法。                                                                         |
| 406         | 不接受                  | 此服务不支持要求在 Accept 标头的格式。                                                                |
| 409         | Conflict                        | 与请求的预期的当前状态冲突。 例如，指定的父文件夹可能不存在。                   |
| 410         | 离开                            | 所请求的资源已在服务器不可用。                                               |
| 411         | 所需的长度                 | 该请求需要的内容长度标头。                                                                                    |
| 412         | 不满足前提条件             | （例如，如果匹配标题） 请求中提供的前提条件与资源的当前状态不匹配。                       |
| 413         | 请求实体太大        | 请求的大小超出最大限制。                                                                                            |
| 415         | 不支持的媒体类型          | 请求的内容类型是服务不支持的格式。                                                      |
| 416         | 请求的范围无法满足 | 指定的字节范围为无效或不可用。                                                                                    |
| 422         | 无法处理的实体            | 因为它是在语义上不正确，无法处理此请求。                                                                       |
| 429         | 请求太多               | 客户端应用程序已被阻止，不应尝试重复请求，直至经过一段时间。                |
| 500         | 内部服务器错误           | 处理请求时出现内部服务器错误。                                                                       |
| 501         | 未实现                 | 所请求的功能未实现。                                                                                               |
| 503         | 服务不可用             | 该服务当前不可用。 片刻后，可能会重复请求。 可能会有重试之后头。                   |
| 507         | 存储不足，            | 已达到最大存储配额。                                                                                            |
| 509         | 超出带宽限制        | 您的应用程序已被阻止因超出最大带宽上限。 更多的时间过去后，您的应用程序可以再次重试请求。 |

错误响应是单个的 JSON 对象，包含一个名为**错误**的单个属性。 此对象包括所有错误的详细信息。 您可以使用此处返回，而不是，或返回的 HTTP 状态代码的信息。 下面是完整的 JSON 错误体的一个示例。

<!-- { "blockType": "example", "@odata.type": "sample.error", "expectError": true, "name": "example-error-response"} -->
```json
{
  "error": {
    "code": "invalidRange",
    "message": "Uploaded fragment overlaps with existing data.",
    "innerError": {
      "requestId": "request-id",
      "date": "date-time"
    }
  }
}
```

<!--<a name="msg_error_resource_type"> </a> -->

# <a name="error-resource-type"></a>错误的资源类型

每当请求的处理过程中出现错误，则返回错误资源。

错误响应执行中的错误响应的[OData v4](http://docs.oasis-open.org/odata/odata-json-format/v4.0/os/odata-json-format-v4.0-os.html#_Toc372793091)规范的定义。

## <a name="json-representation"></a>JSON 表示形式

这些资源包括错误资源︰

<!-- { "blockType": "resource", "@odata.type": "sample.error" } -->
```json
{
  "error": { "@odata.type": "odata.error" }  
}
```

#### <a name="odataerror-resource-type"></a>odata.error 资源类型

内部错误响应是错误的资源包括以下属性︰

<!-- { "blockType": "resource", "@odata.type": "odata.error", "optionalProperties": [ "target", "details", "innererror"] } -->
```json
{
  "code": "string",
  "message": "string",
  "innererror": { "@odata.type": "odata.error" }
}
```

| 属性名称  | 值                  | Description\                                                                                               |
|:---------------|:-----------------------|:-----------------------------------------------------------------------------------------------------------|
| **代码**       | string                 | 发生的错误的错误代码字符串                                                            |
| **消息**    | string                 | 开发人员可以随时有关出现的错误消息。 这不应显示给用户直接。 |
| **innererror** | 错误对象           | 可选项。 额外的错误可能比顶级错误更具体的对象。                     |
<!-- {
  "type": "#page.annotation",
  "description": "Understand the error format for the API and error codes.",
  "keywords": "error response, error, error codes, innererror, message, code",
  "section": "documentation",
  "tocPath": "Misc/Error Responses"
} -->

<!--<a name="msg_code_property"> </a> -->

##<a name="code-property"></a>代码属性

`code`属性包含下列可能值之一。 您的应用程序应准备好处理这些错误中的任何一个。

| 代码                      | 说明
|:--------------------------|:--------------
| **accessDenied**          | 调用方不具有执行该操作的权限。 
| **activityLimitReached**  | 应用程序或用户已被阻止。
| **generalException**      | 发生未指定的错误。
| **invalidRange**          | 指定的字节范围为无效或不可用。
| **invalidRequest**        | 该请求是不正确或不正确。
| **itemNotFound**          | 找不到该资源。
| **malwareDetected**       | 所请求的资源时，检测到的恶意软件。
| **nameAlreadyExists**     | 指定的项名已存在。
| **notAllowed**            | 系统不允许此操作。
| **notSupported**          | 系统不支持该请求。
| **resourceModified**      | 由于调用方上次读取它，也就是通常的 eTag 不匹配，正在更新的资源已更改。
| **resyncRequired**        | 三角形标记将不再有效，并且该应用程序必须重置同步状态。
| **serviceNotAvailable**   | 服务不可用。 片刻后再次重试请求。 可能会有重试之后头。 
| **quotaLimitReached**     | 用户已达到其配额限制。
| **未经身份验证的**       | 调用方未通过身份验证。

`innererror`对象可能会以递归方式包含更多`innererror`对象具有更多、 更具体的错误代码。 处理时出现错误，应用程序应遍历所有可用的错误代码，并使用最详细他们了解。 在本页底部列出了一些更详细的代码。

若要验证一个 error 对象是希望出现错误，您必须遍历`innererror`对象，错误代码为您寻找希望。 例如︰

```csharp
public bool IsError(string expectedErrorCode)
{
    OneDriveInnerError errorCode = this.Error;
    while (null != errorCode)
    {
        if (errorCode.Code == expectedErrorCode)
            return true;
        errorCode = errorCode.InnerError;
    }
    return false;
}
```

要正确处理错误的完整示例，看一下[错误代码处理](https://gist.github.com/rgregg/a1866be15e685983b441)。

`message`的根本属性包含适用于开发人员阅读一条错误消息。 错误消息没有本地化，并且不应直接向用户显示。 时处理错误，您的代码不应关闭的关键`message`值，因为他们可以更改在任何时候，而且通常包含特定于失败请求的动态信息。 只应将针对中返回的错误代码`code`属性。

### <a name="detailed-error-codes"></a>详细的错误代码
下面是一些其他的错误，您的应用程序可能会遇到内嵌套`innererror`对象。 应用程序不需要处理这些数据，但如果他们选择可能会。 该服务可以添加新错误代码或停止返回在任何时候，旧的因此非常重要，所有的应用程序能够处理前面的 section](#code-property) 中的基本的错误代码。

| 代码                               | 说明
|:-----------------------------------|:----------------------------------------------------------
| **accessRestricted**               | 访问仅限于该项目的负责人。
| **cannotSnapshotTree**             | 未能获取一致的增量快照。 稍后再试。
| **childItemCountExceeded**         | 已达到最大值的子项目数限制。
| **entityTagDoesNotMatch**          | ETag 与当前项的值不匹配。
| **fragmentLengthMismatch**         | 声明为此片段的总大小是不同的在上载会话。
| **fragmentOutOfOrder**             | 已上载的片段是无序。
| **fragmentOverlap**                | 与现有的数据重叠上载的片段。
| **invalidAcceptType**              | 无效的接受类型。
| **invalidParameterFormat**         | 无效的参数格式。
| **invalidPath**                    | 名称包含无效字符。
| **invalidQueryOption**             | 无效的查询选项。
| **invalidStartIndex**              | 无效的开始索引。
| **lockMismatch**                   | 锁定标记不匹配现有的锁定。
| **lockNotFoundOrAlreadyExpired**   | 在该项目上目前没有未过期的锁定。
| **lockOwnerMismatch**              | 锁的所有者 ID 不匹配提供 id。
| **malformedEntityTag**             | ETag 标头格式不正确。 Etag 必须被括起来的字符串。
| **maxDocumentCountExceeded**       | 达到最大值限制的文档数。
| **maxFileSizeExceeded**            | 已超出最大文件大小。
| **maxFolderCountExceeded**         | 已达到最大文件夹数限制。
| **maxFragmentLengthExceeded**      | 已超出最大文件大小。
| **maxItemCountExceeded**           | 达到最大值限制的项数。
| **maxQueryLengthExceeded**         | 超出了最大查询长度。
| **maxStreamSizeExceeded**          | 超出了最大流大小。
| **parameterIsTooLong**             | 参数超出最大长度。
| **parameterIsTooSmall**            | 参数是较小则最小值。
| **pathIsTooLong**                  | 路径超过了最大长度。
| **pathTooDeep**                    | 达到文件夹层次结构的深度限制。
| **propertyNotUpdateable**          | 属性不可更新。
| **resyncApplyDifferences**         | 需要重新同步。 如果您确信该服务已达日期与本地更改上一次同步时将会用服务器的版本 （包括删除） 替换任何本地项目。 上传服务器并不知道有关任何本地更改。
| **resyncRequired**                 | 重新同步是必需的。
| **resyncUploadDifferences**        | 需要重新同步。 任何本地项服务没有不返回，并上载任何 （如果您不确定哪一个是更多最新保持这两个副本） 的服务器的版本不同的文件上载。
| **serviceNotAvailable**            | 服务器不能处理的当前请求。
| **serviceReadOnly**                | 资源是暂时是只读的。
| **throttledRequest**               | 请求太多。
| **tooManyResultsRequested**        | 请求的结果太多。
| **tooManyTermsInQuery**            | 在查询词过多。
| **totalAffectedItemCountExceeded** | 因为受影响的项的数目超过了阈值，不允许操作。
| **truncationNotAllowed**           | 不允许数据截断。
| **uploadSessionFailed**            | 上载失败的会话。
| **uploadSessionIncomplete**        | 上传完整会话。
| **uploadSessionNotFound**          | 上载中找不到会话。
| **virusSuspicious**                | 此文档是可疑，可能有病毒。
| **zeroOrFewerResultsRequested**    | 请求的结果为零或更少。

<!-- ##Additional Resources##

- [Microsoft Graph API release notes and known issues](microsoft-graph-api-release-notes-known-issues.md )
- [Hands on lab: Deep dive into the Microsoft Graph API](http://dev.office.com/hands-on-labs/4585) -->
