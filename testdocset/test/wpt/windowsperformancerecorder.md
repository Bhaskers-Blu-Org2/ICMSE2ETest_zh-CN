---
title: WindowsPerformanceRecorder
description: WindowsPerformanceRecorder
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e17ce0a4-9621-4611-a781-2750fba3b0cd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 430c6d9f58d1e3775c4b771461a303edc0c95d28
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windowsperformancerecorder"></a>WindowsPerformanceRecorder


此元素是根元素的架构。 它表示有关创作的配置文件的元数据。

## <a name="element-hierarchy"></a>元素层次结构


&lt;**WindowsPerformanceRecorder**&gt;

## <a name="syntax"></a>语法


``` syntax
<WindowsPerformanceRecorder Version   = float
                            Author    = string
                            Team      = string
                            Copyright = string
                            Company   = string
                            Comments  = string
                            Tag       = string>

  <!-- Child elements -->
  Profiles,
  TraceMergeProperties,
  OnOffTransitionConfigurations

</WindowsPerformanceRecorder>
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
<td><p><strong>版本</strong></p></td>
<td><p>表示配置文件的版本。</p></td>
<td><p>float</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>作者</strong></p></td>
<td><p>表示配置文件的作者。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>工作组</strong></p></td>
<td><p>指示创建该配置文件的团队。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>版权</strong></p></td>
<td><p>表示的版权信息。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>公司</strong></p></td>
<td><p>指示创建该配置文件的公司。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Comments</strong></p></td>
<td><p>表示配置文件的可选描述性注释。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>标记</strong></p></td>
<td><p>表示一个标记的值，可用于区分不同的配置文件。</p></td>
<td><p>string</p></td>
<td><p>否</p></td>
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
<td><p>[配置文件](profiles.md)</p></td>
<td><p>表示收集器、 提供程序和配置文件的集合。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="even">
<td><p>[TraceMergeProperties](tracemergeproperties.md)</p></td>
<td><p>表示跟踪合并属性的集合。</p></td>
<td><p>可选，0 或 1。</p></td>
</tr>
<tr class="odd">
<td><p>[OnOffTransitionConfigurations](onofftransitionconfigurations.md)</p></td>
<td><p>表示关闭转换配置的集合。</p></td>
<td><p>可选，0 或 1。</p></td>
</tr>
</tbody>
</table>

 

### <a name="parent-elements"></a>父元素

无。

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







