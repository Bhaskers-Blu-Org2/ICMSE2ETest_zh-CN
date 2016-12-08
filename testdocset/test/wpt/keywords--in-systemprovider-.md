---
title: "关键字 （在 SystemProvider)"
description: "关键字 （在 SystemProvider)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bf98056c-7863-4430-9522-ac2f74048481
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8a03fcc10d4499bcca1df8f09b8d6ad362de1c92
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keywords-in-systemprovider"></a>关键字 （在 SystemProvider)


表示关键字的集合。 如果指定了**操作**属性，可以设置**关键字**元素，或添加到集合中。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;**Keywords (in SystemProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProviderId](systemproviderid.md)&gt;

                                &lt;**Keywords (in SystemProvider)**&gt;

                         &lt;[SystemProvider](systemprovider.md)&gt;

                                &lt;**Keywords (in SystemProvider)**&gt;****

## <a name="syntax"></a>语法


``` syntax
<Keywords Operation = OperationEnumeration = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  Keyword,
  CustomKeyword

</Keywords>
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
<td><p>指示是否应设置或添加关键字。</p></td>
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
<td><p>[关键字 （在 SystemProvider)](keyword--in-systemprovider-.md)</p></td>
<td><p>描述可用于内核模式会话的核心标志。</p></td>
<td><p>需要 1 或更多。</p></td>
</tr>
<tr class="even">
<td><p>[CustomKeyword](customkeyword.md)</p></td>
<td><p>描述自定义关键字。</p></td>
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

 

 







