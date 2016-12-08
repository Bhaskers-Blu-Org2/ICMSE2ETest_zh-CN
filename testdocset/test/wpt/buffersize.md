---
title: BufferSize
description: BufferSize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2ff38035-21a6-4081-b8e7-37b6fd3b6f4e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 0dcbd5908105ed9064dac518bb61ca637aec2aef
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="buffersize"></a>BufferSize


描述每个缓冲区，以 kb 为单位的大小。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemCollector](systemcollector.md)&gt;

               &lt;**BufferSize**&gt;

          &lt;[EventCollector](eventcollector.md)&gt;

               &lt;**BufferSize**&gt;

          &lt;[HeapEventCollector](heapeventcollector.md)

               &lt;**BufferSize**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;**BufferSize**&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;**BufferSize**&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;**BufferSize**&gt;

## <a name="syntax"></a>语法


``` syntax
<BufferSize Operation = "Set" | "Add" | “Remove”
            Value     = unsignedLong>
</BufferSize>
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
<td><p>指示是否应设置或添加元素。</p></td>
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
<td><p>指示缓冲区，以 kb 为单位的大小。</p></td>
<td><p>unsignedLong</p></td>
<td><p>是</p></td>
<td><p></p></td>
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


下面的代码示例显示如何在系统收集和事件收集器定义中使用此元素。

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

[缓冲区](buffers.md)

[SystemCollector](systemcollector.md)

[EventCollector](eventcollector.md)

[HeapEventCollector](heapeventcollector.md)

 

 







