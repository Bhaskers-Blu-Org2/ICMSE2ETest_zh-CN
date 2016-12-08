---
title: EventProviders
description: EventProviders
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a486a6e7-56b9-4458-8b7d-23024b3b7762
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6c54b12e55cb52f88dc69276205632153a6f0adf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventproviders"></a>EventProviders


表示事件提供程序标识符和事件提供程序的集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;**EventProviders**&gt;

## <a name="syntax"></a>语法


``` syntax
<EventProviders Operation = "Set" | "Add" | “Remove”>

  <!-- Child elements -->
  EventProviderId,
  EventProvider

</EventProviders>
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
<td><p>指示是否应设置或添加事件提供程序。</p></td>
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
<td><p>[EventProviderId](eventproviderid.md)</p></td>
<td><p>表示事件提供程序标识符。</p></td>
<td><p>零个或多个可选。</p></td>
</tr>
<tr class="even">
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>表示事件提供程序。</p></td>
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
<td><p>[EventCollectorId](eventcollectorid.md)</p></td>
<td><p>表示事件收集器标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>示例


托管的情况下，使用下面的事件提供程序定义︰

``` syntax
<EventCollectorId Value ="WPAEventCollector">
  <EventProviders>
    <EventProviderId Value="EventProvider_DotNetProvider" />
    <EventProvider Name="Microsoft-Windows-WPA" Id="Microsoft-Windows-WPA" Stack="true">
    </EventProvider>
  </EventProviders>
</EventCollectorId>
```

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







