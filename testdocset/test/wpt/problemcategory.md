---
title: ProblemCategory
description: ProblemCategory
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 93db9658-1b8a-4713-8cac-702034d017d3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 455036a267e2e8e4ba6352fcad6d82d4dbceea20
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="problemcategory"></a>ProblemCategory


表示配置文件的问题类别。 此元素是仅供内部使用。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[ProblemCategories](problemcategories.md)&gt;

                    &lt;**ProblemCategory**&gt;-

## <a name="syntax"></a>语法


``` syntax
<ProblemCategory Value = "First Level Triage" | "CPU" | "Storage" ...>
</ProblemCategory>
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
<td><p>描述问题的类型。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>第一级别会审</p></li>
<li><p>CPU</p></li>
<li><p>Storage</p></li>
<li><p>网络</p></li>
<li><p>Memory</p></li>
<li><p>多媒体</p></li>
<li><p>能量</p></li>
<li><p>开/关切换</p></li>
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
<td><p>[ProblemCategories](problemcategories.md)</p></td>
<td><p>表示问题类别的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







