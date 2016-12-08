ms。TocTitle︰ 教育属性标题︰ 教育属性描述︰ 引用属性需要从教育 REST Api 来访问学校、 节、 学生和教师在 Office 365 教育租户。
ms。ContentId: 1f51d3a9-0ab7-4654-a15d-689e0880ebfb ms.topic︰ 参考 (API)

[!INCLUDE [Add the O365API repo styles](../includes/controls/addo365apistyles.html)]

# <a name="education-attributes"></a>教育属性
    
 _**适用于︰**Office 365 教育_
<p class="previewnote">本文档介绍当前正在预览的功能。 有关如何使用预览功能的信息，请参阅[在 Office 365 的平台上的预览开发功能](..\howto\platform-development-preview-features-overview.md)。</p>


<a name="Overview"> </a>Office 365 的教育 Api 有助于从您 Office 365 租户，其中已通过 Microsoft 学校数据同步到云同步提取数据。 这些结果提供了关于学校、 分区、 教师、 学生和 rosters 的信息。

[学校的属性](#SchoolAttributes) | [节属性](#SectionAttributes) | [学生特性](#StudentAttributes) | [教师属性](#TeacherAttributes)

## <a name="school-attributes"></a>学校的属性

<a name="SchoolAttributes"></a>学校表示为 Azure Active Directory 中的[管理单位](https://msdn.microsoft.com/en-us/library/azure/dn832057.aspx)。 可以获取这些学校所提供的租户和也得到部分、 学生，以及教师是学校的每个实体的一部分。
本机上管理单元的扩展属性以及属性提供了有关学校的所有必要信息。 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**属性**|**类型**|**说明**|
|:-----|:-----|:-----|
|`displayName`|是否必需|学校的名称|
|`{prefix}_SyncSource_SchoolId`|是否必需|学校由 SIS 分配唯一 ID|
|`{prefix}_SchoolNumber`|可选|通常显示在报表中的 ID|
|`{prefix}_SchoolNationalCenterFor EducationStatisticsId`|可选|由 NCES 分配的 ID|
|`{prefix}_StateId`|可选|学校的状态分配的 ID|
|`{prefix}_LowestGrade`|可选|最低等级的学校 {1-12，Pre-K，K，其他}|
|`{prefix}_HighestGrade`|可选|学校的高年级 {1-12，Pre-K，K，其他}|
|`{prefix}_SchoolPrincipalSyncSourceId`|可选|学校主体 SIS ID|
|`{prefix}_SchoolPrincipalName`|可选|学校主体的名称|
|`{prefix}_SchoolPrincipalEmail`|可选|学校主体的电子邮件|
|`{prefix}_Address`|可选|学校的街道地址|
|`{prefix}_City`|可选|学校的城市|
|`{prefix}_State`|可选|学校的状态|
|`{prefix}_Country`|可选|国家/地区的学校|
|`{prefix}_Zip`|可选|学校的地址邮编|
|`{prefix}_Phone`|可选|学校的联系电话|
|`{prefix}_SchoolZone`|可选|地区/区域的学校|
|`{prefix}_AnchorId`|内部|定位标记 ID 内部使用，用于唯一地标识每个学校|
|`{prefix}_ObjectType`|内部|对象类型的一所学校是学校|
|`{prefix}_SyncSource`|内部|学校该信息的来源|


**** 


## <a name="section-attributes"></a>节属性

<a name="SectionAttributes"></a>节表现为[统一组](https://msdn.microsoft.com/en-us/office/office365/howto/groups-rest-operations)Azure Active Directory 中。 您可以获得承租人、 学生和教师的每个部分，一部分以及部分所属学校详细信息中提供的部分。 本机上统一组的扩展属性以及属性提供有关部分的所有必需信息。 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**属性**|**类型**|**说明**|
|:-----|:-----|:-----|
|`displayName`|是否必需|部分的好记的名称|
|`{prefix}_SectionId`|是否必需|本节由 SIS 分配唯一 ID|
|`{prefix}_SectionNumber`|可选|本节由学区学校分配编号|
|`{prefix}_SectionName`|是否必需|节的名称|
|`{prefix}_TermId`|可选|部分的术语 SIS ID|
|`{prefix}_TermName`|可选|这一节 （秋季、 冬季、 春季、 夏季等） 相关联的术语名称|
|`{prefix}_TermStartDate`|可选|期限的部分中的开始日期|
|`{prefix}_TermEndDate`|可选|结束日期部分的术语|
|`{prefix}_SchoolId`|是否必需|学校的部分的 SIS ID|
|`{prefix}_CourseId`|可选|本课程由 SIS 分配的 ID|
|`{prefix}_CourseName`|可选|课程的名称|
|`{prefix}_CourseDescription`|可选|本课程的说明|
|`{prefix}_CourseNumber`|可选|地区学校分配给课程编号|
|`{prefix}_CourseSubject`|可选|本部分的主题|
|`{prefix}_Period`|可选|所有期间的部分组合的字符串。|
|`{prefix}_AnchorId`|内部|定位标记 ID 内部使用，用于唯一地标识每个部分|
|`{prefix}_ObjectType`|内部|对象类型的一所学校是节|
|`{prefix}_SyncSource`|内部|此部分信息的来源|


**** 


## <a name="student-attributes"></a>学生端属性

<a name="StudentAttributes"></a>学生表示为 Azure Active Directory 中的用户。 您可以获取当前已登录的学生的信息，还将获得学校和学生为属于部分。 本机用户的扩展属性以及属性提供有关该学生的所有必要信息。 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**属性**|**类型**|**说明**|
|:-----|:-----|:-----|
|`mailNickname`|是否必需|在目录中的学生的唯一别名|
|`userPrincipalName`|是否必需|学生正式的电子邮件地址|
|`givenName`|是否必需|学生的名字|
|`surName`|是否必需|最后一个学生的名字|
|`{prefix}_MiddleName`|可选|学生的中间名|
|`{prefix}_SyncSource_StudentId`|是否必需|学生由 SIS 分配唯一 ID|
|`{prefix}_SyncSource_SchoolId`|是否必需|学校的学生的 ID|
|`{prefix}_Email`|可选|学生的个人电子邮件地址|
|`{prefix}_StateId`|可选|学生为指定的状态|
|`{prefix}_StudentNumber`|可选|Disctrict/学校给学生分配编号|
|`{prefix}_MailingAddress`|可选|学生的邮寄地址|
|`{prefix}_MailingCity`|可选|学生的邮寄城市|
|`{prefix}_MailingState`|可选|邮寄省的学生|
|`{prefix}_MailingZip`|可选|邮寄 Zip 的学生|
|`{prefix}_MailingLatitude`|可选|所在的邮寄地址的纬度|
|`{prefix}_MailingLongitude`|可选|Longiture 的邮寄地址|
|`{prefix}_MailingCountry`|可选|邮寄国家/地区的学生|
|`{prefix}_ResidenceAddress`|可选|学生的居住地址|
|`{prefix}_ResidenceCity`|可选|学生的居住城市|
|`{prefix}_ResidenceState`|可选|学生的居住状态|
|`{prefix}_ResidenceZip`|可选|居住 Zip 进行学生|
|`{prefix}_ResidenceLatitude`|可选|所在的居住地址的纬度|
|`{prefix}_ResidenceLongitude`|可选|Longiture 的居住地址|
|`{prefix}_ResidenceCountry`|可选|学生的居住国家/地区|
|`{prefix}_Gender`|可选|学生的性别|
|`{prefix}_DateOfBirth`|可选|学生的出生日期|
|`{prefix}_Grade`|可选|学生的成绩等级|
|`{prefix}_EnglishLanguageLearnersStatus`|可选|英语语言学员状态|
|`{prefix}_FederalRace`|可选|联邦学生角逐|
|`{prefix}_GraduationYear`|可选|学生的毕业年份|
|`{prefix}_StudentStatus`|可选|学生的状态。 {预先登记活动，已转移出、 挂起、 渐变、 历史、 处于非活动状态，等等。。|
|`{prefix}_AnchorId`|内部|定位标记 ID 内部使用，用于唯一地标识每个学生|
|`{prefix}_ObjectType`|内部|对象类型的一所学校是学生|


**** 


## <a name="teacher-attributes"></a>教师属性

<a name="TeacherAttributes"></a>教师表示为 Azure Active Directory 中的用户。 您可以获取属性的当前已登录的教师和学校和部分教师是的成员。 本机用户的扩展属性以及属性提供有关教师的所有必要信息。 

```no-highlight
{prefix} is 'extension_fe2174665583431c953114ff7268b7b3_Education'
```

|**属性**|**类型**|**说明**|
|:-----|:-----|:-----|
|`mailNickname`|是否必需|在目录中教师的唯一别名|
|`userPrincipalName`|是否必需|教师的正式的电子邮件地址|
|`givenName`|是否必需|教师的名字|
|`surName`|是否必需|教师的姓氏|
|`{prefix}_MiddleName`|可选|教师的中间名|
|`{prefix}_SyncSource_TeacherId`|是否必需|教师由 SIS 分配唯一 ID|
|`{prefix}_SyncSource_SchoolId`|是否必需|学校的教师的 ID|
|`{prefix}_StateId`|可选|教师的每个证书状态 ID 数|
|`{prefix}_TeacherNumber`|可选|地区学校分配给教师的数量|
|`{prefix}_TeacherStatus`|可选|教师状态 {活动、 上离开，这里不再等。 }|
|`{prefix}_Email`|可选|教师个人的电子邮件|
|`{prefix}_Title`|可选|教师的标题|
|`{prefix}_TeacherQualification`|可选|教师的资格认证|
|`{prefix}_AnchorId`|内部|定位标记 ID 内部使用，用于唯一地标识每个教师|
|`{prefix}_ObjectType`|内部|对象类型的一所学校是教师|


**** 
<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

其他教育的一些相关资源，您可能会感兴趣

- 访问学校信息使用[学校的其他操作](..\api\school-rest-operations.md)

- 使用[部分其余操作](..\api\section-rest-operations.md)访问部分信息

- 使用[学生其余操作](..\api\student-rest-operations.md)访问学生信息

- 使用[教师其余操作](..\api\teacher-rest-operations.md)访问教师信息 


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
    
