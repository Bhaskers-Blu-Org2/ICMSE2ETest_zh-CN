---
title: "缓冲区"
description: "缓冲区"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8f60d3e3-cb32-4879-8ac2-80ceaea945d3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9e190119bf8837b2e00539970c69d605b7227c8f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="buffers"></a>缓冲区


描述要启动的会话或会话，这**PercentageOfTotalMemory**属性的值取决于分配的总内存的百分比时分配的缓冲区数。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemCollector](systemcollector.md)&gt;

               &lt;**Buffers**&gt;

          &lt;[EventCollector](eventcollector.md)&gt;

               &lt;**Buffers**&gt;

          &lt;[HeapEventCollector](heapeventcollector.md)

               &lt;**Buffers**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;**Buffers**&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;**Buffers**&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;**Buffers**&gt;

## <a name="syntax"></a>语法


``` syntax
<Buffers Operation               = "Set" | "Add" | “Remove”
         Value                   = unsignedLong
         PercentageOfTotalMemory = boolean>
</Buffers>
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
<td><p><strong>操作</strong></p></td>
<td><p>指示是否应设置或添加缓冲区。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>设置</p></li>
<li><p>Add</p></li>
<li><p>删除</p></li>
</ul></td>
<td><p>否</p></td>
<td><p>设置</p></td>
</tr>
<tr class="even">
<td><p><strong>值</strong></p></td>
<td><p>指示数的缓冲区，或者如果<strong>PercentageOfTotalMemory</strong>设置为&quot;为&quot;，缓冲区的内存的百分比。</p></td>
<td><p>unsignedLong</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>PercentageOfTotalMemory</strong></p></td>
<td><p>当设置为&quot;为&quot;，限制可以对<strong>值</strong>的消耗的内存总量。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>子元素

无。

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
<td><p>[EventCollector](eventcollector.md)</p></td>
<td><p>表示事件回收器。</p></td>
</tr>
<tr class="even">
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>表示事件收集器标识符。</p></td>
</tr>
<tr class="odd">
<td><p>[HeapEventCollector](heapeventcollector.md)</p></td>
<td><p>表示堆事件回收器。</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventCollectorId](heapeventcollectorid.md)</p></td>
<td><p>表示一个堆事件收集器的标识符。</p></td>
</tr>
<tr class="odd">
<td><p>[SystemCollector](systemcollector.md)</p></td>
<td><p>表示一个系统收集器。</p></td>
</tr>
<tr class="even">
<td><p>[SystemCollectorId](systemcollectorid.md)</p></td>
<td><p>表示系统收集器标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


此元素仅用于内存中捕获。

## <a name="example"></a>示例


下面的示例演示如何在系统收集和事件收集器定义中使用此元素。

第一个示例将缓冲区大小设置为 512 KB 并限制占用的内存总量的 3%的总金额。 第二个示例设置为 128 KB 64 缓冲区。

``` syntax
<SystemCollector
  Id="WPRSystemCollector"
  Name="NT Kernel Logger"
  FileName="WPRKernel.etl">
  <BufferSize
    Value="512"/> 
  <Buffers
    Value="3"
    PercentageOfTotalMemory="true"/>
</SystemCollector>

<EventCollector
  Id="WPREventCollector"
  Name="WPR Event Collector"
  FileName="somefilename.etl">
  <BufferSize
    Value="128"/>
  <Buffers
    Value="64"/>
</EventCollector>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

[BufferSize](buffersize.md)

[SystemCollector](systemcollector.md)

[EventCollector](eventcollector.md)

[HeapEventCollector](heapeventcollector.md)

 

 







