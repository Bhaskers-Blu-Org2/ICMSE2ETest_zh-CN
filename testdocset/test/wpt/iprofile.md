---
title: IProfile
description: IProfile
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 62442c73-627c-4f91-b33e-ec3e55293d70
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4b178fcafcf4eb79b0c446833419d9f0ca43f99e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="iprofile"></a>IProfile


表示客户端控件的配置文件。 该接口提供加载配置文件时，XML 格式，或者从文件或从字符串的函数。 客户端可以确定是否允许用户通过添加或移除事件跟踪 Windows (ETW) 提供程序的配置文件更新。

## <a name="syntax"></a>语法


``` syntax
{
  typedef enum
  {
    LoggingMode_Unknown,
    LoggingMode_Memory,
    LoggingMode_File,
  }
  CLoggingMode;
  typedef enum
  {
    DetailLevel_Unknown,
    DetailLevel_Light,
    DetailLevel_Verbose,
  }
  CDetailLevel;
  [propget, id(1), helpstring("IsMutable")] HRESULT IsMutable
    ([out, retval] VARIANT_BOOL* pfMutable);
  [propput, id(1), helpstring("IsMutable")] HRESULT IsMutable
    ([in] VARIANT_BOOL fMutable);  [propget, id(2), helpstring("Version")] HRESULT Version
    ([out, retval] float* pVersion);
  [propget, id(3), helpstring("Author")] HRESULT Author
    ([out, retval] BSTR* pbstrAuthor);
  [propget, id(4), helpstring("Team")] HRESULT Team
    ([out, retval] BSTR* pbstrTeam);
  [propget, id(5), helpstring("Comments")] HRESULT Comments
    ([out, retval] BSTR* pbstrComments);
  [propget, id(6), helpstring("Company")] HRESULT Company
    ([out, retval] BSTR* pbstrCompany);
  [propget, id(7), helpstring("Copyright")] HRESULT Copyright
    ([out, retval] BSTR* pbstrCopyright);
  [propget, id(8), helpstring("Tag")] HRESULT Tag
    ([out, retval] BSTR* pbstrTag);
  [propget, id(9), helpstring("Id")] HRESULT Id
    ([out, retval] BSTR* pbstrId);
  [propget, id(10), helpstring("Name")] HRESULT Name
    ([out, retval] BSTR* pbstrName);
  [propget, id(11), helpstring("Description")] HRESULT Description
    ([out, retval] BSTR* pbstrDescription);
  [propget, id(12), helpstring("LoggingMode")] HRESULT LoggingMode
    ([out, retval] CLoggingMode* pLoggingMode);
  [propget, id(13), helpstring("LoggingModeString")] HRESULT LoggingModeString
    ([out, retval] BSTR* pbstrLoggingMode);
  [propget, id(14), helpstring("DetailLevel")] HRESULT DetailLevel
    ([out, retval] CDetailLevel* pDetailLevel);
  [propget, id(15), helpstring("DetailLevelString")] HRESULT DetailLevelString
    ([out, retval] BSTR* pbstrDetailLevel);
  [propget, id(16), helpstring("IsStrict")] HRESULT IsStrict
    ([out, retval] VARIANT_BOOL* pfStrict);
  [propget, id(17), helpstring("IsDefault")] HRESULT IsDefault
    ([out, retval] VARIANT_BOOL* pfDefault);
  [propget, id(18), helpstring("ProblemCategories")] HRESULT ProblemCategories
    ([out, retval] BSTR* pbstrProblemCategories);
  [id(19), helpstring("LoadFromFile")] HRESULT LoadFromFile
    ([in] BSTR bstrProfileName,
    [in] BSTR bstrFileName);
  [id(20), helpstring("LoadFromString")] HRESULT LoadFromString
    ([in] BSTR bstrProfile);
  [id(21), helpstring("IsEqual")] HRESULT IsEqual
    ([in] IProfile* pProfile);};
```

## <a name="functions"></a>函数


下表描述了此接口提供的功能。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>函数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>propget</strong></p></td>
<td><p>返回指定属性的值。</p></td>
</tr>
<tr class="even">
<td><p><strong>propput</strong></p></td>
<td><p>设置指定的属性。</p></td>
</tr>
<tr class="odd">
<td><p>[LoadFromFile](loadfromfile.md)</p></td>
<td><p>从指定文件加载配置文件。</p></td>
</tr>
<tr class="even">
<td><p>[LoadFromString](loadfromstring.md)</p></td>
<td><p>从指定的 XML 配置文件定义字符串加载配置文件。</p></td>
</tr>
<tr class="odd">
<td><p>[IsEqual](isequal.md)</p></td>
<td><p>比较两个<strong>IProfile</strong>对象。</p></td>
</tr>
</tbody>
</table>

 

## <a name="properties"></a>属性


此接口提供下表中描述的属性。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>参数</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>IsMutable</strong></p></td>
<td><p><em>pfMutable</em></p></td>
<td><p>[out]返回一个布尔值，指示，讲座和提供程序时，可添加到现有的配置文件具有相同名称的配置文件合并在一起的<strong>IProfileCollection::Add</strong>方法。 S_OK 表示成功。</p></td>
</tr>
<tr class="even">
<td><p><strong>IsMutable</strong></p></td>
<td><p><em>fMutable</em></p></td>
<td><p>[中]一个布尔值，该值指示是否可以向配置文件添加会话和提供程序。 S_OK 表示成功。</p></td>
</tr>
<tr class="odd">
<td><p><strong>版本</strong></p></td>
<td><p><em>pVersion</em></p></td>
<td><p>[out]表示配置文件的版本。</p></td>
</tr>
<tr class="even">
<td><p><strong>作者</strong></p></td>
<td><p><em>pbstrAuthor</em></p></td>
<td><p>[out]表示配置文件的作者。</p></td>
</tr>
<tr class="odd">
<td><p><strong>工作组</strong></p></td>
<td><p><em>pbstrTeam</em></p></td>
<td><p>[out]指示团队创建配置文件。</p></td>
</tr>
<tr class="even">
<td><p><strong>Comments</strong></p></td>
<td><p><em>pbstrComments</em></p></td>
<td><p>[out]有关配置文件的可选注释。</p></td>
</tr>
<tr class="odd">
<td><p><strong>单位</strong></p></td>
<td><p><em>pbstrCompany</em></p></td>
<td><p>[out]指示创建配置文件的公司。</p></td>
</tr>
<tr class="even">
<td><p><strong>版权</strong></p></td>
<td><p><em>pbstrCopyright</em></p></td>
<td><p>[out]指示与配置文件相关的版权信息。</p></td>
</tr>
<tr class="odd">
<td><p><strong>标记</strong></p></td>
<td><p><em>pbstrTag</em></p></td>
<td><p>[out]可以用于区分配置文件的可选标记的值。</p></td>
</tr>
<tr class="even">
<td><p><strong>Id</strong></p></td>
<td><p><em>pbstrId</em></p></td>
<td><p>[out]表示配置文件的标识符。</p></td>
</tr>
<tr class="odd">
<td><p><strong>名称</strong></p></td>
<td><p><em>pbstrName</em></p></td>
<td><p>[out]表示配置文件的名称。</p></td>
</tr>
<tr class="even">
<td><p><strong>说明</strong></p></td>
<td><p><em>pbstrDescription</em></p></td>
<td><p>[out]表示配置文件的说明。</p></td>
</tr>
<tr class="odd">
<td><p><strong>LoggingMode</strong></p></td>
<td><p><em>pLoggingMode</em></p></td>
<td><p>[out]指示日志记录模式。</p></td>
</tr>
<tr class="even">
<td><p><strong>LoggingModeString</strong></p></td>
<td><p><em>pbstrLoggingMode</em></p></td>
<td><p>[out]指示日志记录模式字符串。 可能的值是&quot;内存&quot;和&quot;文件&quot;。</p></td>
</tr>
<tr class="odd">
<td><p><strong>DetailLevel</strong></p></td>
<td><p><em>pDetailLevel</em></p></td>
<td><p>[out]指示的详细程度。</p></td>
</tr>
<tr class="even">
<td><p><strong>DetailLevelString</strong></p></td>
<td><p><em>pbstrDetailLevel</em></p></td>
<td><p>[out]指明级别的详细信息的字符串。 可能的值是&quot;详细&quot;和&quot;光&quot;。</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsStrict</strong></p></td>
<td><p><em>pfStrict</em></p></td>
<td><p>[out]一个布尔值，该值指示是否录制滚回是否任何收集器或提供程序无法启动。</p></td>
</tr>
<tr class="even">
<td><p><strong>后</strong></p></td>
<td><p><em>pfDefault</em></p></td>
<td><p>[out]一个布尔值，该值指示这是否为默认配置文件。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProblemCategories</strong></p></td>
<td><p><em>pbstrProblemCategories</em></p></td>
<td><p>[out]指示问题，此配置文件用于检测。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[接口](interfaces-wprcontrol.md)

 

 







