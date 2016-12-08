ms。TocTitle︰ 部分 REST API 引用标题︰ 部分 REST API 参考说明︰ 参考如何与部分 REST API 来访问 Office 365 教育租户的各部分进行交互。
ms。ContentId: 3805c218-e0c7-48e9-b458-448563ff7ae4 ms.topic︰ 参考 (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]


# <a name="sections-rest-api-reference"></a>部分 REST API 参考
    
 _**适用于︰**Office 365 教育_
<p class="previewnote">本文档介绍当前正在预览的功能。 有关如何使用预览功能的信息，请参阅[在 Office 365 的平台上的预览开发功能](..\howto\platform-development-preview-features-overview.md)。</p>



<a name="Overview"> </a>Office 365 的教育 Api 有助于从您 Office 365 租户，其中已通过 Microsoft 学校数据同步到云同步提取数据。 这些结果提供了关于学校、 分区、 教师、 学生和 rosters 的信息。 在学校的每个类都表示为一节。 部分 REST API，提供教育租户访问 Office 365 中的截面图元。

该 API 依赖 Microsoft Azure Active Directory 和 OAuth 向[应用程序请求进行身份验证](..\howto\common-app-authentication-tasks.md)。
 
若要从应用程序访问部分 REST API，您将需要到[Azure Active Directory 中注册](https://azure.microsoft.com/en-us/documentation/articles/active-directory-integrating-applications/#adding-an-application)。
您还需要管理身份验证令牌，以及构造正确的 URL 和查询，以满足您的需要。 下面的示例可用于构造查询的帮助。

<!-- Add Extension Properties and Data-Model-->

## <a name="all-sections-rest-api-operations"></a>所有节 REST API 操作

<a name="SectionOperations"></a>节表现为[统一组](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)Azure Active Directory 中。 您可以获得承租人、 学生和教师的每个部分，一部分以及部分所属学校详细信息中提供的部分。


[获取部分](#GetSections) | [获取学校的一节](#GetSectionsSchool) | [获取分区内的学生](#GetSectionStudents) | [获取一个节中的教师](#GetSectionTeachers) 


## <a name="use-the-sections-rest-api"></a>使用节 REST API，

要与部分 REST API 进行交互，您发送 HTTP GET 请求。

所有节 REST API 请求都使用以下根 URL:

`https://graph.windows.net/{tenant_id}/groups`

`{tenant_id}`是唯一的 ID 或域的 Azure Active Directory 租户。 可以通过以下方式之一来指定 tenant_id:
- 对象 ID (GUID) 的租户;例如︰ `https://graph.windows.net/95b43ae0-0554-4cc5-8c22-fe219dc31156/`。
- 已验证的域名租户;例如︰ `https://graph.windows.net/contoso.onmicrosoft.com/`。
- `myOrganization`别名。 此别名解析为已登录的用户 （根据请求中发送的持有者标记）; 租户例如， `https://graph.windows.net/myorganization/`。 

在下面的示例中，我们将使用`tenant_id = 95b43ae0-0554-4cc5-8c22-fe219dc31156`。

节在 Azure Active Directory 中表现为[统一的组](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)。 统一在组上的扩展属性中添加教育相关的信息。  
例如，`extension_fe2174665583431c953114ff7268b7b3_Education_CourseNumber`属性包含一个部分的课程数目。

**请注意**所有的请求都需要指定`api-version`在 URL 查询字符串。 部分 REST API 要求版本 1.5 或更高，除了获得学派的要求作为版本`beta`。 例如︰ `https://graph.windows.net/{tenant_id}/groups?api-version=1.5`。   

## <a name="section-attributes"></a>节属性

帮助识别部分有关的信息都是最的特性的描述︰[部分属性](education-rest-attributes.md#SectionAttributes)

****

<a name="GetSections"> </a>
##<a name="get-sections"></a>获取部分

可以获得所有的部分，通过获取单个部分的`object_id`，或获取与一组查询筛选器相匹配的部分的集合。

<a name="GetAllSections"> </a>
###<a name="get-all-sections"></a>获取所有稿件

获取在 Azure Active Directory 租户中存在的所有部分。

```no-highlight
GET https://graph.windows.net/{tenant_id}/groups?api-version=1.5&$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'Section'
```

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|

```REST
[!INCLUDE [sections_api_get_sections.json](./_data/sections_api_get_sections.json)]
```

 **响应类型**

部分实体的集合。


****


<a name="GetSection"> </a>
###<a name="get-a-section"></a>获取节

通过使用可以得到`object_id`。

```no-highlight
GET https://graph.windows.net/{tenant_id}/groups/{object_id}?api-version=1.5
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|省略 object_id|string|在 Azure Active Directory 中的节组的对象 ID。|   


```REST
[!INCLUDE [sections_api_get_section_by_id.json](./_data/sections_api_get_section_by_id.json)]
```

 **响应类型**

请求的部分的实体。


****

<a name="GetSectionsSchool"> </a>
##<a name="get-school-of-a-section"></a>获得学校的一节

学校管理单位在 Azure Active Directory 中表示。 在这些管理单元上的扩展属性添加特定学校的信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_HighestGrade`属性包含为该学校的最高评分结果。

您可以查询用于管理单位与部分学校`SchoolId`从属性获取`extension_fe2174665583431c953114ff7268b7b3_Education_SchoolId`[可以得到](#GetSection)响应。


```no-highlight
GET https://graph.windows.net/{tenant_id}/administrativeUnits?api-version=beta
        &$filter=extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType%20eq%20'School'%20
        and%20extension_fe2174665583431c953114ff7268b7b3_Education_SchoolId%20eq%20'{school_id}'
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|school_id|string|学校在学校信息系统 (SIS) 的 ID。|   


```REST
[!INCLUDE [sections_api_get_school_for_section_id.json](./_data/sections_api_get_school_for_section_id.json)]
```

 **响应类型**

一个学校的实体。

**** 

<a name="GetSectionStudents"> </a>
##<a name="get-students-within-a-section"></a>在节内使学生

学生在 Azure Active Directory 中表示为用户。 用户扩展属性添加学生特定的信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_Grade`属性包含学生的年级。  

通过获取该节的统一组的成员和过滤掉非学生用户从应用程序内生成的集合，可以在特定的部分，了解学生。

###<a name="get-section-members"></a>获取部分成员
```no-highlight
GET https://graph.windows.net/{tenant_id}/groups/{object_id}/members?api-version=1.5
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|省略 object_id|string|在 Azure Active Directory 中的节组的对象 ID。|   


```REST
[!INCLUDE [sections_api_get_students_by_section_id.json](./_data/sections_api_get_students_by_section_id.json)]
```

 **响应类型**

用户的集合。

###<a name="find-students"></a>发现学生

学生、 教师和非教育用户 （例如，管理人员使用），可能包含用户的集合。 应用程序中，您可以筛选到学生，集合。 查询`Education_ObjectType`扩展属性等于`Student`。

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Student'
```

**** 

<a name="GetSectionTeachers"> </a>
##<a name="get-teachers-within-a-section"></a>在节内获得教师

教师在 Azure Active Directory 中表示为用户。 用户扩展属性添加教师特定的信息。 例如，`extension_fe2174665583431c953114ff7268b7b3_Education_TeacherNumber`属性包含教师的教师数量。 

通过获取该节的统一组的成员并过滤掉非教师从生成的集合，您的应用程序中的用户，可以在特定的部分，获得教师。

###<a name="get-section-members"></a>获取部分成员
```no-highlight
GET https://graph.windows.net/{tenant_id}/groups/{object_id}/members?api-version=1.5
```


|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL 参数_|
|tenant_id|string|Azure Active Directory 租户 ID 或域的名称。|
|省略 object_id|string|在 Azure Active Directory 中的节组的对象 ID。|   


```REST
[!INCLUDE [sections_api_get_teachers_by_section_id.json](./_data/sections_api_get_teachers_by_section_id.json)]
```

 **响应类型**

用户的集合。

###<a name="find-teachers"></a>查找教师

学生、 教师和非教育用户 （例如，管理人员使用），可能包含用户的集合。 应用程序中，可以筛选仅教师，到集合。 查询`Education_ObjectType`扩展属性等于`Teacher`。

```no-highlight
extension_fe2174665583431c953114ff7268b7b3_Education_ObjectType == 'Teacher'
```


**** 
<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

其他教育的一些相关资源，您可能会感兴趣

- 访问学校信息使用[学校的其他操作](..\api\school-rest-operations.md)

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
    
