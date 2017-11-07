---
title: SystemProviderId
description: SystemProviderId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f5ac9900-e43b-480b-9be7-5f5f726b1635
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d27cbb2f9f41c807e0311844955060f153a135ef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemproviderid"></a>SystemProviderId


唯一地标识系统提供程序。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;**SystemProviderId**&gt;

## <a name="syntax"></a>语法


``` syntax
<SystemProviderId Value = IdType>

  <!-- Child elements -->
  Keywords,
  Stacks,
  PoolTags

</SystemProviderId>
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
<td><p><strong>值</strong></p></td>
<td><p>唯一地标识系统提供程序。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
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
<td><p>[关键字 （在 SystemProvider)](keywords--in-systemprovider-.md)</p></td>
<td><p>表示系统提供关键字的集合。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="even">
<td><p>[堆栈](stacks.md)</p></td>
<td><p>表示堆栈的集合。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="odd">
<td><p>[PoolTags](pooltags.md)</p></td>
<td><p>表示池标记的集合。</p></td>
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
<td><p>[收集器](collectors.md)</p></td>
<td><p>表示系统收集器标识符、 事件收集器标识符和可选的堆事件收集器标识符的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


创作系统提供程序定义的详细信息，请参阅[2。系统和事件提供程序定义](2-system-and-event-provider-definitions.md)和[3。配置文件定义](3-profile-definitions.md)。

## <a name="example"></a>示例


下面的代码示例演示一个包含此元素的配置文件定义的部分。

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
…
  </Collectors>
</Profile>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







