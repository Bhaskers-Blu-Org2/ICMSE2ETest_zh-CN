---
title: TraceMergeProperties
description: TraceMergeProperties
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7771cdc2-3573-4a3b-a52b-70ef77f706dc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 24eb13751ef5965d605df6efba20873355abb35d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="tracemergeproperties"></a>TraceMergeProperties


表示[TraceMergeProperty](tracemergeproperty.md)元素的集合。 此元素是仅供内部使用。

## <a name="element-syntax"></a>元素语法


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;**TraceMergeProperties**&gt;

## <a name="syntax"></a>语法


``` syntax
<TraceMergeProperties>

  <!-- Child elements -->
  TraceMergeProperty

</TraceMergeProperties>
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
<th>Requirment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[TraceMergeProperty](tracemergeproperty.md)</p></td>
<td><p>包含多个配置文件中的事件跟踪日志 (ETL) 文件进行合并时，将应用的配置。</p></td>
<td><p>需要 1 或更多。</p></td>
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

 

## <a name="example"></a>示例


下面的代码示例演示如何定义此元素。

``` syntax
<TraceMergeProperties>
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
</TraceMergeProperties>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

[继承](inheritance.md)

 

 







