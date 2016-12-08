---
title: HeapEventProviders
description: HeapEventProviders
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b4582698-fb7f-4158-b41c-d2f1c53f3f87
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a9813df77a7bdb7a89cd344270acc90dc0acfd8c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapeventproviders"></a>HeapEventProviders


表示堆事件提供程序标识符和堆事件提供程序的集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;**HeapEventProviders**&gt;

## <a name="syntax"></a>语法


``` syntax
<HeapEventProviders Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  HeapEventProviderId,
  HeapEventProvider

</HeapEventProviders>
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
<td><p><strong>操作</strong></p></td>
<td><p>指示是否应设置或添加提供程序。</p></td>
<td><p>此属性可以具有下列值之一︰</p>
<ul>
<li><p>设置</p></li>
<li><p>Add</p></li>
<li><p>删除</p></li>
</ul></td>
<td><p>否</p></td>
<td><p>设置</p></td>
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
<td><p>[HeapEventProviderId](heapeventproviderid.md)</p></td>
<td><p>表示一个堆事件提供程序的标识符。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProvider](heapeventprovider.md)</p></td>
<td><p>表示一个堆事件提供程序。</p></td>
<td><p>零个或多个可选。</p></td>
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
<td><p>[HeapEventCollectorId](heapeventcollectorid.md)</p></td>
<td><p>表示一个堆事件收集器的标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







