---
title: PrepareSystem
description: PrepareSystem
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7ec136bc-f59a-4b36-9ae5-1e25c6fe06c4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2f09d96351df9ec8387146eab670401251cdf386
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="preparesystem"></a>PrepareSystem


指示是否准备系统的[OnOffTransitionConfiguration](onofftransitionconfiguration.md)元素。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[OnOffTransitionConfigurations](onofftransitionconfigurations.md)&gt;

          &lt;[OnOffTransitionConfiguration](onofftransitionconfiguration.md)&gt;

               &lt;**PrepareSystem**&gt;

## <a name="syntax"></a>语法


``` syntax
<PrepareSystem Value = boolean>
</PrepareSystem>
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
<td><p>指示是否准备系统。</p></td>
<td><p>布尔</p></td>
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
<td><p>[OnOffTransitionConfiguration](onofftransitionconfiguration.md)</p></td>
<td><p>表示一个打开/关闭转换配置。</p></td>
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

 

 







