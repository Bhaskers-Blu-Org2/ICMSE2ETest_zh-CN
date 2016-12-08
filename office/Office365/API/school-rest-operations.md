ms。TocTitle︰ 学校 REST API 引用标题︰ 学校 REST API 参考说明︰ 参考如何与学校 REST API 来访问 Office 365 教育租户在学校进行交互。
ms。ContentId: 35003e02-c4b1-4702-9d86-b6a7718e9fa8 ms.topic︰ 参考 (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]




# <a name="schools-rest-api-reference"></a>学校的 REST API 参考
    
 _**适用于︰**Office 365 教育_
<p class="previewnote">本文档介绍当前正在预览的功能。 有关如何使用预览功能的信息，请参阅[在 Office 365 的平台上的预览开发功能](..\howto\platform-development-preview-features-overview.md)。</p>


<a name="Overview"> </a>Office 365 的教育 Api 有助于从您 Office 365 租户，其中已通过 Microsoft 学校数据同步到云同步提取数据。 这些结果提供了关于学校、 分区、 教师、 学生和 rosters 的信息。 REST API，学校提供的教育租户到 Office 365 中的学校实体的访问。

该 API 依赖 Microsoft Azure Active Directory 和 OAuth 向[应用程序请求进行身份验证](..\howto\common-app-authentication-tasks.md)。
 
若要从应用程序访问学校 REST API，您将需要到[Azure Active Directory 中注册](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)。
您还需要管理身份验证令牌，以及构造正确的 URL 和查询，以满足您的需要。 下面的示例可用于构造查询的帮助。

<!-- Add Extension Properties and Data-Model-->

## <a name="all-schools-rest-api-operations"></a>所有学校 REST API 操作

<a name="SchoolOperations"></a>学校表示为 Azure Active Directory 中的[管理单位](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx)。 可以获取这些学校所提供的租户和也得到部分、 学生，以及教师是学校的每个实体的一部分。


[获得学校](#GetSchools) | [获取一所学校内的分区](#GetSchoolSections) | [获取一所学校内的学生](#GetSchoolStudents) | [获取一所学校内的教师](#GetSchoolTeachers) 


## <a name="use-the-schools-rest-api"></a>使用 REST API 的学校

要与学校 REST API 进行交互，您发送 HTTP GET 请求。

所有学校 REST API 请求都使用以下根 URL:

`https://graph.windows.net/{tenant_id}/administrativeUnits`

`{tenant_id}`是唯一的 ID 或域的 Azure Active Directory 租户。 可以通过以下方式之一来指定 tenant_id:
- 对象 ID (GUID) 的租户;例如︰ `https://graph.windows.net/95b43ae0-0554-4cc5-8c22-fe219dc31156/`。
- 已验证的域名租户;例如︰ `https://graph.windows.net/contoso.onmicrosoft.com/`。
- `myOrganization`别名。 此别名解析为已登录的用户 （根据请求中发送的持有者标记）; 租户例如， `https://graph.windows.net/myorganization/`。 

在下面的示例中，我们将使用`tenant_id = 95b43ae0-0554-4cc5-8c22-fe219dc31156`。   

学校管理单位在 Azure Active Directory 中表示。 在管理单元的扩展属性中添加教育相关的信息。  
例如，`extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade`属性包含在学校最高年级。

**请注意**所有的请求都需要指定`api-version`在 URL 查询字符串。 学校 REST API 要求版本`beta`。 例如︰ `https://graph.windows.net/{tenant_id}/administrativeUnits?api-version=beta`。   


## <a name="school-attributes"></a>学校的属性

帮助识别有关学校的信息处的属性的说明︰[学校特性](education-rest-attributes.md#SchoolAttributes)

****

<a name="GetSchools"> </a>
##<a name="get-schools"></a>获得学校

可以获得所有的学校，通过获取单个学校的`object_id`，或获取一个标记集合的一组查询筛选器匹配的学校。

<a name="GetAllSchools"> </a>
###<a name="get-all-schools"></a>获取所有学校

获取在 Azure Active Directory 租户中存在的所有学校。

```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits?api-version=beta&$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'School'
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|

```REST
[!INCLUDE [schools_api_get_schools.json](./_data/schools_api_get_schools.json)]
```

 **响应类型**

学校实体的集合。


****


<a name="GetSchool"> </a>
###<a name="get-a-school"></a>获取一所学校

通过使用获得学校`object_id`。

```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits/{object_id}?api-version=beta
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|省略 object_id|string|学校管理部门在 Azure Active Directory 中的对象 ID。|   

```REST
[!INCLUDE [schools_api_get_school_by_id.json](./_data/schools_api_get_school_by_id.json)]
```

 **响应类型**

要求的学校的实体。


****

<a name="GetSchoolSections"> </a>
##<a name="get-sections-within-a-school"></a>获取一所学校内的分区

节在 Azure Active Directory 中表现为[统一的组](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)。 统一在组上的扩展属性中添加部分的特定信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_CourseName`属性包含节课程名称。

可以为特定学校中获得部分查询组基于他们学校的 id，用于使用`extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType`特性和`extension_fe2174665583431c953114ff7268b7b3_Education_SyncSource_SchoolId`属性在查询中组合在一起。


```no-highlight
GET https://graph.windows.net/{tenant_id}/groups?api-version=1.5
        &$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'Section'%20
        and%20extension_fe2174665583431c953114ff7268b7b3_Education_SyncSource_SchoolId%20eq%20'{school_id}'
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|school_id|string|学校在学校信息系统 (SIS) 的 ID。|   


```REST
[!INCLUDE [schools_api_get_sections_by_school_id.json](./_data/schools_api_get_sections_by_school_id.json)]
```

 **响应类型**

部分实体的集合。

**** 

<a name="GetSchoolStudents"> </a>
##<a name="get-students-within-a-school"></a>在一所学校内使学生

学生在 Azure Active Directory 中表示为用户。 对用户的扩展属性中添加学生的特定信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_Grade`属性包含学生的年级。  

通过获取学校管理单位的成员和过滤掉非学生用户从应用程序内生成的集合，可以在特定的学校，了解学生。

###<a name="get-school-members"></a>获得学校成员
```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits/{object_id}/members?api-version=beta
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|省略 object_id|string|学校管理部门在 Azure Active Directory 中的对象 ID。|   


```REST
[!INCLUDE [schools_api_get_students_by_school_id.json](./_data/schools_api_get_students_by_school_id.json)]
```

 **响应类型**

用户的集合。

###<a name="find-students"></a>发现学生

学生、 教师和非教育用户 （例如，管理人员使用），可能包含用户的集合。 在您的应用程序中，您可以筛选到学生集合。 查找`Education_ObjectType`扩展属性等于`Student`。

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Student'
```

**** 

<a name="GetSchoolTeachers"> </a>
##<a name="get-teachers-within-a-school"></a>在学校得到老师

教师在 Azure Active Directory 中表示为用户。 对用户的扩展属性中添加教师的特定信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_TeacherNumber`属性包含教师的教师数量。 

通过获取学校管理单位的成员和过滤掉非教师用户从应用程序内生成的集合，可以在特定学校获得教师。

###<a name="get-school-members"></a>获得学校成员
```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits/{object_id}/members?api-version=beta
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|省略 object_id|string|学校管理部门在 Azure Active Directory 中的对象 ID。|   


```REST
[!INCLUDE [schools_api_get_teachers_by_school_id.json](./_data/schools_api_get_teachers_by_school_id.json)]
```

 **响应类型**

用户的集合。

###<a name="find-teachers"></a>查找教师

学生、 教师和非教育用户 （例如，管理人员使用），可能包含用户的集合。 您应用程序内，您可以筛选到教师的集合。 查找`Education_ObjectType`扩展属性等于`Teacher`。

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Teacher'
```


**** 
<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

其他教育的一些相关资源，您可能会感兴趣

- 使用[部分其余操作](..\api\section-rest-operations.md)访问部分信息

- 使用[学生其余操作](..\api\student-rest-operations.md)访问学生信息

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
    
