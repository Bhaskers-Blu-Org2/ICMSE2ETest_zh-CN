---
title: CustomEvent
description: CustomEvent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4ce7091b-4e6a-40c3-aeff-1c9434310f44
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 19c80247cddf024308c66245263210c6e1a0ec4f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customevent"></a>CustomEvent


表示一个自定义事件。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;[TraceMergeProperty](tracemergeproperty.md)&gt;

               &lt;[CustomEvents](customevents.md)&gt;

                    &lt;**CustomEvent**&gt;

## <a name="syntax"></a>语法


``` syntax
<CustomEvent Value = "None" | "ImageId" | "BuildInfo" | ...>
</CustomEvent>
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
<td><p>描述自定义事件的值。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>无</p></li>
<li><p>图像 Id</p></li>
<li><p>BuildInfo</p></li>
<li><p>VolumeMapping</p></li>
<li><p>EventMetadata</p></li>
<li><p>PerfTrackMetadata</p></li>
<li><p>WinSAT</p></li>
<li><p>NetworkInterface</p></li>
</ul></td>
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
<td><p>[CustomEvents](customevents.md)</p></td>
<td><p>表示自定义的事件的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>示例


下面的代码示例演示如何在跟踪合并属性定义中使用此元素。

``` syntax
<TraceMergeProperty
  Id="TraceMerge_Default"
  Name="TraceMerge_Default">
  <DeletePreMergedTraceFiles
    Value="true"/>
  <CustomEvents>
    <CustomEvent
      Value="ImageId"/>
    <CustomEvent
      Value="BuildInfo"/>
    <CustomEvent
      Value="VolumeMapping"/>
    <CustomEvent
      Value="EventMetadata"/>
    <CustomEvent
      Value="PerfTrackMetadata"/>
    <CustomEvent
      Value="WinSAT"/>
    <CustomEvent
      Value="NetworkInterface"/>
  </CustomEvents>
</TraceMergeProperty>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







