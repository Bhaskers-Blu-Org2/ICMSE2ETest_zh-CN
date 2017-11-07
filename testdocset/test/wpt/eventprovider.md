---
title: EventProvider
description: EventProvider
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bf7e4e86-e837-41f8-847f-42fc12c5a98c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 17140550564b359627bff139880c85d621c36590
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventprovider"></a>EventProvider


配置跟踪 Windows 事件 (ETW) 用户模式提供程序。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**EventProvider**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                              &lt;**EventProvider**&gt;

## <a name="syntax"></a>语法


``` syntax
<EventProvider Id               = IdType
               Name             = string
               Base             = string
               NonPageMemory    = boolean
               Stack            = boolean
               SID              = boolean
               TSID             = boolean
               Level            = unsigendByte
               CaptureStateOnly = boolean>

  <!-- Child elements -->
  Keywords,
  CaptureStateOnStart,
  CaptureStateOnSave

</EventProvider>
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
<td><p>唯一地标识事件提供程序。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>名称</strong></p></td>
<td><p>表示事件提供程序的名称。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>A 注册深的提供程序，例如， &quot;Microsoft Windows 搜索核&quot;。</p></li>
<li><p>提供程序的 GUID，例如&quot;49c2c27c-fe2d-40bf-8c4e-c3fb518037e7&quot;。</p></li>
<li><p>传统提供程序名称，例如&quot;IE6&quot;。</p></li>
<li><p>特殊用例名称，如&quot;PerfTrack&quot;或&quot;DotNetProvider&quot;。</p></li>
</ul></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>ProcessExeFilter</strong></p></td>
<td><p>一个基于指定的进程.exe 名称的事件的筛选器。</p></td>
<td><p>这是可选属性添加到<strong>EventProvider ID</strong> WPR 配置文件中。 例如︰</p>
<ul>
<li><p>&quot;ProcessExeFilter =&quot;wpa.exe&quot;</p></li>
</ul>
<div class="alert">
<strong>请注意</strong>  
<p>WPR 实质上是在[EVENT_FILTER_DESCRIPTOR](https://msdn.microsoft.com/library/windows/desktop/aa363758.aspx)结构传.exe 名称上。</p>
</div>
<div>
 
</div></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>基</strong></p></td>
<td><p>表示基础提供程序。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>NonPagedMemory</strong></p></td>
<td><p>指示是否要使用的非分页内存。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="even">
<td><p><strong>Stack</strong></p></td>
<td><p>指示提供程序是否应该捕获堆栈。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="odd">
<td><p><strong>SID</strong></p></td>
<td><p>指示是否要包括日志中的事件的扩展数据的用户的安全标识符 (SID)。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="even">
<td><p><strong>TSID</strong></p></td>
<td><p>指示是否将终端会话标识符包含在扩展数据的记录的事件。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="odd">
<td><p><strong>Level</strong></p></td>
<td><p>指明级别的值。</p></td>
<td><p>unsignedByte</p></td>
<td><p>否</p></td>
<td><p>零，ETW 将视为 0xFFFFFFFFFFFFFFFF。</p></td>
</tr>
<tr class="even">
<td><p><strong>CaptureStateOnly</strong></p></td>
<td><p>指示提供程序仅在开始启用还是保存的跟踪会话。</p></td>
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
<td><p>[关键字 （在 EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>表示[关键字 （在 EventProvider)](keyword--in-eventprovider-.md)元素的集合。</p></td>
<td><p>需要 1 或更多。</p></td>
</tr>
<tr class="even">
<td><p>[CaptureStateOnStart](capturestateonstart.md)</p></td>
<td><p>表示在开始跟踪捕获事件的[关键字 （在 EventProvider)](keyword--in-eventprovider-.md)元素的集合。</p></td>
<td><p>可选，0 或 1。</p></td>
</tr>
<tr class="odd">
<td><p>[CaptureStateOnSave](capturestateonsave.md)</p></td>
<td><p>表示保存跟踪时捕获事件的[关键字 （在 EventProvider)](keyword--in-eventprovider-.md)元素的集合。</p></td>
<td><p>可选，0 或 1。</p></td>
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
<td><p>[EventProviders](eventproviders.md)</p></td>
<td><p>代表<strong>EventProvider</strong>元素的集合。</p></td>
</tr>
<tr class="even">
<td><p>[配置文件](profiles.md)</p></td>
<td><p>表示收集器、 提供程序和配置文件的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


定义提供程序的顺序很重要。 定义必须出现在.wprp 文件中的顺序如下︰

1.  收集器

2.  系统提供程序

3.  事件提供程序

可选的内部 XML 标记指定要启用哪些关键字。 与系统供应商，没有定义为事件提供程序，所以必须使用十六进制样式字符串的文本常数。 然而，语法是相同的与系统提供商。 如果未不指定任何关键字，使用 （它被视为由 ETW 字符串 0xFFFFFFFFFFFFFFFF） 默认值零。

默认情况下，派生的事件提供程序具有基提供程序的所有属性。 他们可以通过显式指定它们中派生的提供程序重写。 有关详细信息，请参阅[继承](inheritance.md)。

## <a name="example"></a>示例


下面的示例定义两个事件提供程序。

``` syntax
<EventProvider
  Id="Win32K-provider"
  Name="Microsoft-Windows-Win32K"
  NonPagedMemory="true"
  Stack="true"> 
  <Keywords>
    <Keyword
      Value="0x240000"/>
  </Keywords>
</EventProvider>

<EventProvider
  Id="Search-Core-provider"
  Name="Microsoft-Windows-Search-Core"/>
```

下面的代码示例定义捕获状态提供程序。

``` syntax
<EventProvider Id="sample-provider" Name="SampleProvider" NonPagedMemory="true" Level="5">
  <Keywords>
    <Keyword Value="0x98"/> <!-- Provider is enabled with these keywords throughout the tracing session. -->
  </Keywords>
  <CaptureStateOnStart>
    <Keyword Value="0xff4"/> <!-- Provider is enabled with these keywords when tracing is started. -->
  </CaptureStateOnStart>
  <CaptureStateOnSave>
    <Keyword Value="0x118"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>

<EventProvider Id="EventProvider_DWMWin32k_CaptureState" Name="e7ef96be-969f-414f-97d7-3ddb7b558ccc" NonPagedMemory="true" CaptureStateOnly="true" > 
  <!-- CaptureStateOnly="true" means that provider is not enabled throughout the tracing session. -->
  <CaptureStateOnSave>
    <Keyword Value="0x80000"/> <!-- Provider is enabled with these keywords when tracing is saved. -->
  </CaptureStateOnSave>
</EventProvider>
```

托管的情况下，使用下面的事件提供程序定义︰

``` syntax
<EventCollectorId Value ="WPAEventCollector">
  <EventProviders>
    <EventProviderId Value="EventProvider_DotNetProvider" />
    <EventProvider Name="Microsoft-Windows-WPA" Id="Microsoft-Windows-WPA" Stack="true">
    </EventProvider>
  </EventProviders>
</EventCollectorId>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







