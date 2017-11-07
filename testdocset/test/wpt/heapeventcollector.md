---
title: HeapEventCollector
description: HeapEventCollector
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e8f6e4d9-b037-49ca-b816-cc7757b98b3d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a5fd3621f8e821bd0903f69c4cd063dc4a426859
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapeventcollector"></a>HeapEventCollector


表示为堆事件收集器。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**HeapEventCollector**&gt;

## <a name="syntax"></a>语法


``` syntax
<HeapEventCollector Id       = IdType
                    Base     = string
                    Name     = string
                    FileName = string
                    Realtime = boolean
                    Secure   = boolean>

  <!-- Child elements -->
  BufferSize,
  Buffers,
  StackCaching

</HeapEventCollector>
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
<td><p>唯一地标识堆事件回收器。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>基</strong></p></td>
<td><p>表示器的基础。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>名称</strong></p></td>
<td><p>指示堆事件收集器的名称。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>指示事件应写入的文件的名称。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>实时</strong></p></td>
<td><p>指示是否事件收集器的实时操作。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>false</p></td>
</tr>
<tr class="even">
<td><p><strong>安全</strong></p></td>
<td><p>如果设置为&quot;为&quot;，表示只有具有管理权限，适当的访问权限的用户可以控制该会话。 如果设置为&quot;false&quot;，表示所有用户可以都控制该会话。</p></td>
<td><p>布尔</p></td>
<td><p>否</p></td>
<td><p>true</p></td>
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
<td><p>描述要启动的会话或会话，这<strong>PercentageOfTotalMemory</strong>属性的值取决于分配的总内存的百分比时分配的缓冲区数。</p></td>
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


默认情况下，派生的事件收集器具有基本的收集器的特性。 这些可以通过显式指定这些派生的收集器中。 有关详细信息，请参阅[继承](inheritance.md)。

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

[继承](inheritance.md)

 

 







