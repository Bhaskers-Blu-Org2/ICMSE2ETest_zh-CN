---
title: "配置文件"
description: "配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 00b0d6dc-d14a-4c70-ab7b-4aa2250c2395
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c8338f3b8c12bb0a2412b8e4dcec84ea4fa418d7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="profiles"></a>配置文件


表示收集器、 提供程序和配置文件的集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;**Profiles**&gt;

## <a name="syntax"></a>语法


``` syntax
<Profiles>

  <!-- Child elements -->
  SystemCollector,
  EventCollector,
  HeapEventCollector,
  SystemProvider,
  EventProvider,
  HeapEventProvider,
  Profile

</Profiles>
```

## <a name="attributes-and-elements"></a>特性和元素


### <a name="attributes"></a>属性

无。

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
<td><p>[SystemCollector](systemcollector.md)</p></td>
<td><p>表示一个系统收集器。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="even">
<td><p>[EventCollector](eventcollector.md)</p></td>
<td><p>表示事件回收器。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventCollector](heapeventcollector.md)</p></td>
<td><p>表示堆事件回收器。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="even">
<td><p>[SystemProvider](systemprovider.md)</p></td>
<td><p>表示系统提供。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="odd">
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>表示事件提供程序。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProvider](heapeventprovider.md)</p></td>
<td><p>表示一个堆事件提供程序。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="odd">
<td><p>[配置文件](profile-wpr.md)</p></td>
<td><p>表示集合的问题类别和收集器。</p></td>
<td><p>所需，1 到 4。</p></td>
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
<td><p>[WindowsPerformanceRecorder](windowsperformancerecorder.md)</p></td>
<td><p>表示配置文件的编写有关的元数据。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


**WindowsPerformanceRecorder**元素中，可以定义只能包含单个**配置文件**元素。

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







