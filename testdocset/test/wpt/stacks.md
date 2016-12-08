---
title: "堆栈"
description: "堆栈"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5ea2e972-ca03-460a-9fed-8eb7670221ac
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c890a7e658a6a57d592ed44867b3197491fe46f4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stacks"></a>堆栈


表示堆栈的集合。 如果指定了**操作**属性，可以设置**堆栈**元素，或添加到集合中。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;**Stacks**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;**Stacks**&gt;

                         &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;**Stacks**&gt;

## <a name="syntax"></a>语法


``` syntax
<Stacks Operation = OperationEnumeration>

  <!-- Child elements -->
  Stack

</Stacks>
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
<td><p>指示是否应设置或添加<strong>堆栈</strong>元素。</p></td>
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
<td><p>[堆栈](stack-wpa.md)</p></td>
<td><p>表示系统堆栈。</p></td>
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
<td><p>[SystemProvider](systemprovider.md)</p></td>
<td><p>表示系统提供。</p></td>
</tr>
<tr class="even">
<td><p>[SystemProviderId](systemproviderid.md)</p></td>
<td><p>表示系统的提供程序标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







