---
title: HeapEventProvider
description: HeapEventProvider
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0f2fe538-bfd6-490b-b1c8-8f151153b8ef
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 661e82aba10d7558a4651f7fe05770fe3c67c32d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heapeventprovider"></a>HeapEventProvider


表示提供程序的配置文件堆事件。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**HeapEventProvider**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;**HeapEventProvider**&gt;

## <a name="syntax"></a>语法


``` syntax
<HeapEventProvider Id   = IdType
                   Base = string>

  <!-- Child elements -->
  HeapProcessIds

</HeapEventProvider>
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
<td><p>唯一地标识堆事件提供程序。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>基</strong></p></td>
<td><p>表示基堆事件提供程序。</p></td>
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
<td><p>[HeapProcessIds](heapprocessids.md)</p></td>
<td><p>表示一个堆进程标识符的集合。</p></td>
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
<td><p>[HeapEventProviders](heapeventproviders.md)</p></td>
<td><p>表示堆事件提供程序标识符和堆事件提供程序的集合。</p></td>
</tr>
<tr class="even">
<td><p>[配置文件](profiles.md)</p></td>
<td><p>表示收集器、 提供程序和配置文件的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


默认情况下，派生的堆事件提供程序具有基提供程序的所有属性。 这些可以通过显式指定它们中派生的提供程序重写。 有关详细信息，请参阅[继承](inheritance.md)。

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







