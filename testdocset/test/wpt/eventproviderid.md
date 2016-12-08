---
title: EventProviderId
description: EventProviderId
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b97422a9-0fa1-484b-9b2e-8fd72dcbf494
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: fb49f763705ae9ee7f5533d8c6733a3a6ca19006
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="eventproviderid"></a>EventProviderId


表示配置文件的事件提供程序标识符。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                               &lt;**EventProviderId**&gt;

## <a name="syntax"></a>语法


``` syntax
<EventProviderId Value = IdType>

  <!-- Child elements -->
  Keywords,
  CaptureStateOnStart,
  CaptureStateOnSave

</EventProviderId>
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
<td><p>唯一地标识事件提供程序。</p></td>
<td><p>必须具有至少一个字符并且不能包含冒号 （:） 或空格的字符串。</p></td>
<td><p>是</p></td>
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
<td><p>[关键字 （在 EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>表示关键字的集合。</p></td>
<td><p>需要 1 或更多。 使用<code>0x0</code>作为关键字来包含所有的事件。</p></td>
</tr>
<tr class="even">
<td><p>[CaptureStateOnStart](capturestateonstart.md)</p></td>
<td><p>表示一个描述在开始录制的捕获事件的关键字集合。</p></td>
<td><p>可选，0 或 1。</p></td>
</tr>
<tr class="odd">
<td><p>[CaptureStateOnSave](capturestateonsave.md)</p></td>
<td><p>表示一个描述保存录制时捕获事件的关键字集合。</p></td>
<td><p>可选，0 或 1。</p></td>
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
<td><p>[EventProviders](eventproviders.md)</p></td>
<td><p>表示事件提供程序和事件提供程序标识符的集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="example"></a>示例


托管的情况下，使用下面的事件提供程序定义。

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

 

 







