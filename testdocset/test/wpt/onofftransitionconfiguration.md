---
title: OnOffTransitionConfiguration
description: OnOffTransitionConfiguration
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c9b194b8-c179-49da-ac8d-aae373c9d706
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ace632678e9c04ecf5f2676d5a16d70b91976072
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="onofftransitionconfiguration"></a>OnOffTransitionConfiguration


表示一个打开/关闭转换配置。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[OnOffTransitionConfigurations](onofftransitionconfigurations.md)&gt;

          &lt;**OnOffTransitionConfiguration**&gt;

## <a name="syntax"></a>语法


``` syntax
<OnOffTransitionConfiguration Id = IdType
                              Name = string
                              Type = "On/Off - Boot" | "On/Off - HybridBoot" | "On/Off - Shutdown" | ...>

  <!-- Child elements -->
  PrepareSystem,
  NumberOfRuns,
  PostBootDelay,
  WakeupDelay,
  TransitionTag

</OnOffTransitionConfiguration>
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
<td><p>唯一地标识打开/关闭转换配置。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>名称</strong></p></td>
<td><p>表示配置的名称。</p></td>
<td><p>string</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>类型</strong></p></td>
<td><p>指示关闭转换的类型。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>开/关-启动</p></li>
<li><p>开/关-HybridBoot</p></li>
<li><p>开/关-关闭</p></li>
<li><p>开/关-RebootCycle</p></li>
<li><p>开/关-等待/继续</p></li>
<li><p>开/关-休眠/继续</p></li>
</ul></td>
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
<td><p>[PrepareSystem](preparesystem.md)</p></td>
<td><p>指示是否准备开/关转换系统。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="even">
<td><p>[NumberOfRuns](numberofruns.md)</p></td>
<td><p>指示运行中开/关切换数。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="odd">
<td><p>[PostBootDelay](postbootdelay.md)</p></td>
<td><p>指示在启动后的延迟。</p></td>
<td><p>可选，0 或 1。</p></td>
</tr>
<tr class="even">
<td><p>[WakeupDelay](wakeupdelay.md)</p></td>
<td><p>表示延迟时从休眠状态中不断涌现。</p></td>
<td><p>可选，0 或 1。</p></td>
</tr>
<tr class="odd">
<td><p>[TransitionTag](transitiontag.md)</p></td>
<td><p>指示转换标记。</p></td>
<td><p>可选，0 或 1。</p></td>
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
<td><p>[OnOffTransitionConfigurations](onofftransitionconfigurations.md)</p></td>
<td><p>表示关闭转换的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>示例


下面的代码示例演示如何配置此元素。

``` syntax
<OnOffTransitionConfiguration
  Id="OnOffTransitionConfiguration_Default_Boot"
  Name="OnOffTransitionConfiguration_Default_Boot"
  Type="On/Off - Boot">
  <PrepareSystem Value="true"/>
  <NumberOfRuns Value="3"/>
  <PostBootDelay Value="120"/>
  <WakeupDelay Value="60"/>
  <TransitionTag Value="Boot"/>
</OnOffTransitionConfiguration>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







