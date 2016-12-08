---
title: OnOffTransitionConfigurations
description: OnOffTransitionConfigurations
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7046c6c0-8e74-47a1-a4ce-47a7dc5a43c0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fa1106ba070654cd7fa4fcd407f2ff3e2f00422d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onofftransitionconfigurations"></a>OnOffTransitionConfigurations


表示关闭转换的集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;**OnOffTransitionConfigurations**&gt;

## <a name="syntax"></a>语法


``` syntax
<OnOffTransitionConfigurations>

  <!-- Child elements -->
  OnOffTransitionConfiguration

</OnOffTransitionConfigurations>
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
<td><p>[OnOffTransitionConfiguration](onofftransitionconfiguration.md)</p></td>
<td><p>表示一个打开/关闭转换配置。</p></td>
<td><p>需要，正好是 1。</p></td>
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

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







