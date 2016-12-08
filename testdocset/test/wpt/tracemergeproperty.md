---
title: TraceMergeProperty
description: TraceMergeProperty
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b3640f46-7bf4-4ee3-8094-ace27f275bd8
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 28c2e1e57024550e063c2f3ec73787fe32a8fef1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="tracemergeproperty"></a>TraceMergeProperty


包含多个配置文件中的记录进行合并时，将应用的配置。 此元素是仅供内部使用。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[TraceMergeProperties](tracemergeproperties.md)&gt;

          &lt;**TraceMergeProperty**&gt;

## <a name="syntax"></a>语法


``` syntax
<TraceMergeProperty Id   = IdType
                    Name = string
                    Base = string>

  <!-- Child elements -->
  DeletePreMergedTraceFiles,
  FileCompression
  CustomEvents
</TraceMergeProperty>
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
<td><p><strong>ID</strong></p></td>
<td><p>唯一地标识此元素。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>名称</strong></p></td>
<td><p>表示此元素的名称。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>基</strong></p></td>
<td><p>表示此元素的基础。 默认情况下，派生的元素具有基类的所有属性。 通过显式指定它们的派生元素中，可以重写这些属性。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

 

### <a name="child-elements"></a>子元素

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
<th>要求</th>
<th>可能的值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[DeletePreMergedTraceFiles](deletepremergedtracefiles.md)</p></td>
<td><p>指示是否删除 premerged 的事件跟踪日志 (ETL) 文件。</p></td>
<td><p>可选</p></td>
<td><p>为 true，假</p></td>
</tr>
<tr class="even">
<td><p>[FileCompression](filecompression.md)</p></td>
<td><p>指示是否压缩 ETL 文件。</p></td>
<td><p>可选</p></td>
<td><p>为 true，假</p></td>
</tr>
<tr class="odd">
<td><p>[CustomEvents](customevents.md)</p></td>
<td><p>表示自定义的事件的集合。</p></td>
<td><p>可选</p></td>
<td><p>为 true，假</p></td>
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
<td><p>[TraceMergeProperties](tracemergeproperties.md)</p></td>
<td><p>表示跟踪合并属性的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>示例


下面的代码示例显示一个跟踪合并属性定义。

``` syntax
<TraceMergeProperty
  Id="TraceMerge_Default"
  Name="TraceMerge_Default">
  <DeletePreMergedTraceFiles
    Value="true"/>
  <FileCompression
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

 

 







