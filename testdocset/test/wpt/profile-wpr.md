---
title: "配置文件"
description: "配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 92a5d494-cd6f-4a9b-942b-f1318ab48b00
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 75c0558f8dc3925f60c94848662f7956908b5925
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="profile"></a>配置文件


代表的问题类别和收集器元素的集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**Profile**&gt;

## <a name="syntax"></a>语法


``` syntax
<Profile Id          = IdType
         Name        = string
         Description = string
         Base        = string
         LoggingMode = "File" | "Memory"
         DetailLevel = "Verbose" | "Light"
         Strict      = boolean
         Internal    = boolean
         Default     = boolean>

  <!-- Child elements -->
  ProblemCategories,
  Collectors

</Profile>
```

## <a name="attributes-and-elements"></a>特性和元素


### <a name="attributes"></a>属性

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>说明</th>
<th>数据类型</th>
<th>是否必需</th>
<th>默认值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Id</strong></p></td>
<td><p>唯一地标识的配置文件。</p></td>
<td><p>必须具有至少一个字符，并且不能包含冒号或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>名称</strong></p></td>
<td><p>表示配置文件的名称。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>说明</strong></p></td>
<td><p>表示配置文件的说明。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>基</strong></p></td>
<td><p>表示配置文件的基础。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>LoggingMode</strong></p></td>
<td><p>指示 WPR 将写入内存或写入顺序文件。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>对象。</p></li>
<li><p>Memory</p></li>
</ul></td>
<td><p>是</p></td>
<td><p>对象。</p></td>
</tr>
<tr class="even">
<td><p><strong>DetailLevel</strong></p></td>
<td><p>指定是否为定时跟踪使用配置文件定义 (&quot;光&quot;) 或分析跟踪 (&quot;详细&quot;)。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>详细</p></li>
<li><p>淡</p></li>
</ul></td>
<td><p>是</p></td>
<td><p>详细</p></td>
</tr>
<tr class="odd">
<td><p><strong>严格</strong></p></td>
<td><p>指示提供程序或收集器故障是否导致启动操作失败。 如果将此属性设置为&quot;false&quot;、 启动操作成功即使一些收集或提供程序失败。 至少一个收集器和一个提供程序都必须成功才能继续操作。 如果将此属性设置为&quot;为&quot;，提供或收集器启动失败的信息作为警告，而不是错误。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="even">
<td><p><strong>内部</strong></p></td>
<td><p>指示该配置文件是内部。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="odd">
<td><p><strong>默认值</strong></p></td>
<td><p>指示该配置文件是否为默认配置文件。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>子元素

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
<th>要求</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[ProblemCategories](problemcategories.md)</p></td>
<td><p>表示问题类别的集合。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="even">
<td><p>[收集器](collectors.md)</p></td>
<td><p>表示配置文件的收集器的集合。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
</tbody>
</table>

 

### <a name="parent-elements"></a>父元素

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[配置文件](profiles.md)</p></td>
<td><p>表示收集器、 提供程序和配置文件的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


每个.wprp 文件通常包含至少两个配置文件定义︰ 一个用于每种日志记录模式。 例外情况是，开/关切换配置文件可以只记录到文件，这些配置文件的.wprp 文件可以包含只能有一个配置文件定义。 每个.wprp 文件可以包含最多四个配置文件︰ 一个用于每个日志记录模式和明细数据级别组合。 一个.wprp 文件中的所有配置文件必须具有**名称**属性的值相同。

通过组合的**名称**、 **DetailLevel**和**LoggingMode**的特性，用句点分隔，如下面的示例中所示的值构建的**Id**属性值。

默认情况下，派生的配置文件都具有基本配置文件的所有的属性。 这些可以通过显式指定它们派生的配置文件中重写。 有关详细信息，请参阅[继承](inheritance.md)。

## <a name="example"></a>示例


下面的代码示例演示一个配置文件定义。

``` syntax
<Profile
  Id="Example.Light.File"
  Name="Example"
  DetailLevel="Light"
  LoggingMode="File"
  Description="Example profile">
  <ProblemCategories>
    <ProblemCategory
      Value="First Level Triage"/>
  </ProblemCategories>
  <Collectors>
    <SystemCollectorId
      Value="WPRSystemCollector">
    <SystemProviderId
      Value="system-provider"/>
    </SystemCollectorId>
    <EventCollectorId
      Value="WPREventCollector">
      <EventProviders>
        <EventProviderId
          Value="Win32K-provider"/>
        <EventProviderId
          Value="Search-Core-provider"/>
      </EventProviders>
    </EventCollectorId>
  </Collectors>
</Profile>
```

收集器和提供程序还可以在配置文件定义中的位置，定义。

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







