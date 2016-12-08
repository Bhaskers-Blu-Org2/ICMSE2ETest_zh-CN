---
title: SystemCollectorId
description: SystemCollectorId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bbaa7eb7-a7be-4b1d-a72c-087c7bf2fbef
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 63c05055167b846b5830fbf661a342a73b212bcd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemcollectorid"></a>SystemCollectorId


表示一个系统收集器的标识符。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;**SystemCollectorId**&gt;

## <a name="syntax"></a>语法


``` syntax
<SystemCollectorId Value = IdType>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching,
  SystemProviderId,
  SystemProvider

</SystemCollectorId>
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
<td><p>介绍了该标识符。</p></td>
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
<td><p>[BufferSize](buffersize.md)</p></td>
<td><p>描述每个缓冲区，以 kb 为单位的大小。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="even">
<td><p>[缓冲区](buffers.md)</p></td>
<td><p>描述启动会话时分配的缓冲区数。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="odd">
<td><p>[StackCaching](stackcaching.md)</p></td>
<td><p>介绍了堆栈缓存的收集器的特性。</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>[SystemProviderId](systemproviderid.md)</p></td>
<td><p>表示系统的提供程序标识符。</p></td>
<td><p>一个或多个可选。</p></td>
</tr>
<tr class="odd">
<td><p>[SystemProvider](systemprovider.md)</p></td>
<td><p>表示系统提供。</p></td>
<td><p>一个或多个可选。</p></td>
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
<td><p>表示收集器标识符的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







