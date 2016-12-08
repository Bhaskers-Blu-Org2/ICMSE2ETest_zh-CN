---
title: SystemProvider
description: SystemProvider
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 20262ec7-6b20-42cb-903f-1db57a9f1e58
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9cd04d5cc683ae5545f19e3876c6b245e6cf703f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="systemprovider"></a>SystemProvider


介绍了配置，可以启用内核模式提供程序。 系统提供程序定义指定哪些系统关键字、 堆栈和池标记，以启用。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;**SystemProvider**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[SystemCollectorId](systemcollectorid.md)&gt;

                            &lt;**SystemProvider**&gt;

## <a name="syntax"></a>语法


``` syntax
<SystemProvider Id   = IdType
                Base = string>

  <!-- Child elements -->
  Keywords,
  Stacks,
  PoolTags

</SystemProvider>
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
<td><p>唯一地标识系统提供程序。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>基</strong></p></td>
<td><p>指示系统提供程序的基类。 默认情况下，派生的提供程序具有基提供程序的所有属性。 这些可以通过显式指定它们中派生的提供程序重写。</p></td>
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
<td><p>[关键字 （在 SystemProvider)](keywords--in-systemprovider-.md)</p></td>
<td><p>表示一组关键字和自定义关键字。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="even">
<td><p>[堆栈](stacks.md)</p></td>
<td><p>表示堆栈的集合。</p></td>
<td><p>需要，正好是 1。</p></td>
</tr>
<tr class="odd">
<td><p>[PoolTags](pooltags.md)</p></td>
<td><p>表示池标记的集合。</p></td>
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
<td><p>[配置文件](profiles.md)</p></td>
<td><p>表示收集器、 提供程序和配置文件的集合。</p></td>
</tr>
<tr class="even">
<td><p>[SystemCollectorId](systemcollectorid.md)</p></td>
<td><p>表示系统收集器标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


有关如何定义池标记的信息，请参阅[PoolTag](pooltag.md)。

## <a name="example"></a>示例


``` syntax
<SystemProvider Id="system-provider">
  <Keywords>
    <Keyword Value="ProcessThread"/>
    <Keyword Value="Loader"/>
    <Keyword Value="CSwitch"/>
  </Keywords>
  <Stacks>
    <Stack Value="ThreadCreate"/>
    <Stack Value="ReadyThread"/>
    <Stack Value="CSwitch"/>
  </Stacks>
  <PoolTags>
    <PoolTag Value="a*"/>
    <PoolTag Value="b*"/> 
    <PoolTag Value="c*"/> 
    <PoolTag Value="d*"/> 
  </PoolTags>
</SystemProvider>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







