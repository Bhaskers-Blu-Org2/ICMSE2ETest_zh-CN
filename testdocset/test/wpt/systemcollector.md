---
title: SystemCollector
description: SystemCollector
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e7b9b910-9fe4-4dca-a61a-2599f67caf00
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4b645f9ba7cd3a71347a20203b7005012fc240bf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemcollector"></a>SystemCollector


说明若要启用事件跟踪 Windows (ETW) 内核模式会话的配置。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**SystemCollector**&gt;

## <a name="syntax"></a>语法


``` syntax
<SystemCollector Id       = IdType
                 Base     = string
                 Name     = "NT Kernel Logger" | "Circular Kernel Context Logger"
                 Realtime = boolean>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching

</SystemCollector>
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
<td><p>唯一地标识系统收集器。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>基</strong></p></td>
<td><p>标识系统收集器的基础。 派生的收集器具有的所有属性的基收集器。 这些可以通过显式指定这些派生的收集器中。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>名称</strong></p></td>
<td><p>指示系统收集器的名称。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>NT 内核记录器</p></li>
<li><p>圆形的内核上下文记录器</p></li>
</ul></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>实时</strong></p></td>
<td><p>指示是否收集器的实时工作。</p></td>
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
<th>要求。</th>
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


系统收集器定义应在事件收集器定义之前。

## <a name="example"></a>示例


下面的代码示例定义了一个系统收集器。

``` syntax
<SystemCollector
  Id="WPRSystemCollector”
  Name="NT Kernel Logger"
  FileName="WPRKernel.etl">
  <BufferSize Value="512"/>
  <Buffers Value="3" PercentageOfTotalMemory="true"/>
</SystemCollector>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







