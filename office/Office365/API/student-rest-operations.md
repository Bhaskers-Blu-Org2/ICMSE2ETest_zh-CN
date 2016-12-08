ms。TocTitle︰ 学生 REST API 引用标题︰ 学生 REST API 参考说明︰ 参考如何与提供给学生在 Office 365 教育租户访问学生 REST API 进行交互。
ms。ContentId: aec1e56a-081d-4214-b441-9039b8341a9e ms.topic︰ 参考 (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]



# <a name="students-rest-api-reference"></a>学生 REST API 参考
    
 _**适用于︰**Office 365 教育_
<p class="previewnote">本文档介绍当前正在预览的功能。 有关如何使用预览功能的信息，请参阅[在 Office 365 的平台上的预览开发功能](..\howto\platform-development-preview-features-overview.md)。</p>


<a name="Overview"> </a>Office 365 的教育 Api 有助于从您 Office 365 的租户，它已通过 Microsoft 学校数据同步到云同步提取数据。 这些结果包含关于学校、 分区、 教师、 学生和名单信息的信息。 学生 REST API 提供的教育租户到 Office 365 中的学生实体的访问。

该 API 依赖 Microsoft Azure Active Directory 和 OAuth 向[应用程序请求进行身份验证](..\howto\common-app-authentication-tasks.md)。
 
若要从应用程序访问学生 REST API，您将需要到[Azure Active Directory 中注册](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)。
您还需要管理身份验证令牌，以及构造正确的 URL 和查询，以满足您的需要。 下面的示例可用于构造查询的帮助。

<!-- Add Extension Properties and Data-Model-->

## <a name="all-students-rest-api-operations"></a>所有的学生 REST API 操作

<a name="StudentOperations"></a>学生表示为 Azure Active Directory 中的用户。 您可以获取当前已登录的学生的信息，还将获得学校和学生为属于部分。


[获取当前用户](#GetCurrentUser) | [获取学校的学生](#GetStudentSchool) | [获得部分的学生](#GetStudentSections) 


## <a name="use-the-students-rest-api"></a>使用学生 REST API，

要与学生 REST API 进行交互，您发送 HTTP GET 请求。

如果登录的用户是一名学生，所有学生 REST API 请求将都使用以下根 URL:

`https://graph.windows.net/me`

学生在 Azure Active Directory 中表示为用户。 对用户的扩展属性中添加学生特定的信息。  
例如，`extension_fe2174665583431c953114ff7268b7b3_Education_Grade`属性包含学生的成绩。

**请注意**所有的请求都需要指定`api-version`在 URL 查询字符串。 REST API，学生需要 1.5 或更高版本。 例如︰ `https://graph.windows.net/me?api-version=1.5`。   

## <a name="student-attributes"></a>学生端属性

帮助识别有关学生的信息处的属性的说明︰[学生端属性](education-rest-attributes.md#StudentAttributes)

****

<a name="GetCurrentUser"> </a>
##<a name="get-current-user"></a>获取当前用户

您可以获取当前登录用户并检查，如果该用户是一名学生。

```no-highlight
GET https://graph.windows.net/me?api-version=1.5
```

```REST
[!INCLUDE [students_api_get_current_user.json](./_data/students_api_get_current_user.json)]
```

 **响应类型**

当前登录用户。

###<a name="check-if-student"></a>如果请学生

当前登录的用户可能是学生，教师或非教育用户 （例如，管理人员）。 您可以检查该用户是否在您的应用程序内的一名学生。 查询`Education_ObjectType`扩展属性等于`Student`。

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Student'
```

****

<a name="GetStudentSchool"> </a>
##<a name="get-school-of-a-student"></a>获得学生的学校

学校[管理单位](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx)在 Azure Active Directory 中表示。 在这些管理单元上的扩展属性添加特定学校的信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade`属性包含为该学校的最高评分结果。

已登录的学生的学校可以获得成员资格的学生，然后筛选`extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'School'`和`objectType == 'AdministrativeUnit'`

###<a name="get-student-membership"></a>获得学生成员资格

您可以使用下面的查询已登录学生端的成员资格。


```no-highlight
GET https://graph.windows.net/me/memberOf?api-version=1.5
```


 **响应类型**

响应将包含多个组、 DirectoryRoles，和/或学生所在的 AdministrativeUnits。

###<a name="filter-for-school"></a>学校的筛选器

可以通过筛选来获得学生的校园生活`extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'School'`， `objectType == 'AdministrativeUnit'`。


**** 

<a name="GetStudentSection"> </a>
##<a name="get-section-of-a-student"></a>获取部分学生

节在 Azure Active Directory 中表现为[统一的组](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)。 统一在组上的扩展属性添加特定部分的信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_CourseName`属性包含节课程名称。

###<a name="get-student-membership"></a>获得学生成员资格

您可以使用下面的查询该学生的成员资格。


```no-highlight
GET https://graph.windows.net/me/memberOf?api-version=1.5
```

 **响应类型**

响应将包含多个组、 DirectoryRoles，和/或学生所在的 AdministrativeUnits。

###<a name="filter-for-section"></a>部分中的筛选器

可以通过筛选来获得部分学生`extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Section'`， `objectType == 'Group'`。

**** 

<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

其他教育的一些相关资源，您可能会感兴趣

- 访问学校信息使用[学校的其他操作](..\api\school-rest-operations.md)

- 使用[部分其余操作](..\api\section-rest-operations.md)访问部分信息

- 使用[教师其余操作](..\api\teacher-rest-operations.md)访问教师信息 

- 属性说明都在[教育属性](..\api\education-rest-attributes.md)


无论您是准备开始构建应用程序，或只是想要了解更多，我们有您的要求。


- 准备好开始了吗？ 启动[设置您的环境](..\howto\setup-development-environment.md)，然后签出我们[第一个应用程序演练](..\howto\getting-started-Office-365-APIs.md)。

- 探讨使用交互式[API 沙盒](http://apisandbox.msdn.microsoft.com/)Office 365 Api。
    
- 需要示例？ [我们已经有了](..\howto\starter-projects-and-code-samples.md)。
    

或者，了解有关使用 Office 365 的平台︰

- [在 Office 365 的平台上开发的概述](..\howto\platform-development-overview.md)
    
- [Office 365 的应用程序的身份验证和资源授权](..\howto\common-app-authentication-tasks.md)
    
- [手动注册您的应用程序 Azure 的广告，这样它可以访问 Office 365 的 Api](..\howto\add-common-consent-manually.md)
  
- [邮件发送 API 参考](..\api\mail-rest-operations.md)
  
- [日历 API 参考](..\api\calendar-rest-operations.md)

- [文件 API 参考](..\api\files-rest-operations.md)

- [发现服务 REST API 操作参考](..\api\discovery-service-rest-operations.md)

- [资源引用的邮件、 日历和联系人 REST Api](..\api\complex-types-for-mail-contacts-calendar.md)
    
