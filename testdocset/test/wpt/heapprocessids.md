---
title: HeapProcessIds
description: HeapProcessIds
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bc7619b5-11f7-48d1-93f3-5103fbfc52ce
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e50cb7e5c0fa7ad5f6a983332615582101114730
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapprocessids"></a>HeapProcessIds


表示一个堆进程标识符的集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[HeapEventProvider](heapeventprovider.md)&gt;

           &lt;**HeapProcessIds**&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;[HeapEventProviderId](heapeventproviderid.md)&gt;

                                   &lt;**HeapProcessIds**&gt;

                              &lt;[HeapEventProvider](heapeventprovider.md)&gt;

                                   &lt;**HeapProcessIds**&gt;

## <a name="syntax"></a>语法


``` syntax
<HeapProcessIds Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  HeapProcessId

</HeapProcessIds>
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
<td><p>指示是否应设置或添加<strong>HeapProcessId</strong>元素。</p></td>
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
<td><p>[HeapProcessId](heapprocessid.md)</p></td>
<td><p>唯一地标识一个堆的过程。</p></td>
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
<td><p>[HeapEventProvider](heapeventprovider.md)</p></td>
<td><p>表示一个堆事件提供程序。</p></td>
</tr>
<tr class="even">
<td><p>[HeapEventProviderId](heapeventproviderid.md)</p></td>
<td><p>表示一个堆事件提供程序的标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







