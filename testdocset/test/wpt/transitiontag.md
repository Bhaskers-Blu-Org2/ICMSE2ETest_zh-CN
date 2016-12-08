---
title: TransitionTag
description: TransitionTag
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ead6001f-02f3-4a85-a207-7af8e558a8f2
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: bd0a8f0ccbf6609448d32cd47304498867da8203
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="transitiontag"></a>TransitionTag


表示一个[OnOffTransitionConfiguration](onofftransitionconfiguration.md)元素的转换标记。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[OnOffTransitionConfigurations](onofftransitionconfigurations.md)&gt;

          &lt;[OnOffTransitionConfiguration](onofftransitionconfiguration.md)&gt;

               &lt;**TransitionTag**&gt;

## <a name="syntax"></a>语法


``` syntax
<TransitionTag Value = TransitionTagType>
</TransitionTag>
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
<td><p>插入的文件的名称的字符串。</p></td>
<td><p>不包含任何下列字符的字符串︰</p>
<ul>
<li><p>正斜杠 （/）</p></li>
<li><p>反斜杠 （)</p></li>
<li><p>冒号 （:）</p></li>
<li><p>星号 （*）</p></li>
<li><p>问号 （？）</p></li>
<li><p>管道符 (|)</p></li>
<li><p>右尖括号 (&gt;)</p></li>
<li><p>双引号 (&quot;)</p></li>
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

 

 







