---
title: CustomKeyword
description: CustomKeyword
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 776e6349-4d19-44a9-b49a-a2c73e218540
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: ea23c3bc18cf2fa4db08ec9b9797d95ad2cd5fee
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customkeyword"></a>CustomKeyword


表示配置文件的自定义关键字。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[SystemProvider](systemprovider.md)&gt;

               &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                    &lt;**CustomKeyword**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                         &lt;[SystemProvider](systemprovider.md)&gt;

                              &lt;[Keywords (in SystemProvider)](keywords--in-systemprovider-.md)&gt;

                                   &lt;**CustomKeyword**&gt;

## <a name="syntax"></a>语法


``` syntax
<CustomKeyword Value = SystemCustomKeywordAttributeType>
</CustomKeyword>
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
<td><p>十六进制格式的字符串名称的自定义事件。</p></td>
<td><p>使用下面的模式生成的字符串︰ 0x [a-fA-F0-9] {1,8}。</p></td>
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
<td><p>[关键字 （在 SystemProvider)](keywords--in-systemprovider-.md)</p></td>
<td><p>表示一组关键字和自定义关键字。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


此元素允许创建的自定义关键字的任何可能的事件跟踪 Windows (ETW) 事件。

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







