---
title: "关键字 （在 EventProvider)"
description: "关键字 （在 EventProvider)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f5b18ec2-8b85-40d6-ac69-91ccd7e7fad9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9c4241668d32151be21e2fe34a356e5ca4d8faae
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keyword-in-eventprovider"></a>关键字 （在 EventProvider)


描述用于用户模式提供程序跟踪 Windows 事件 (ETW) 关键字。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[EventProvider](eventprovider.md)&gt;

               &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

               &lt;[CaptureStateOnStart](capturestateonstart.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

               &lt;[CaptureStateOnSave](capturestateonsave.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

          &lt;[HeapEventProvider](heapeventprovider.md)&gt;

               &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                    &lt;**Keyword (in EventProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                              &lt;[EventProviderId](eventproviderid.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                              &lt;[EventProvider](eventprovider.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                                   &lt;[CaptureStateOnStart](capturestateonstart.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                                   &lt;[CaptureStateOnSave](capturestateonsave.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                    &lt;[HeapEventCollectorId](heapeventcollectorid.md)&gt;

                         &lt;[HeapEventProviders](heapeventproviders.md)&gt;

                              &lt;[HeapEventProviderId](heapeventproviderid.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

                              &lt;[HeapEventProvider](heapeventprovider.md)&gt;

                                   &lt;[Keywords (in EventProvider)](keywords--in-eventprovider-.md)&gt;

                                        &lt;**Keyword (in EventProvider)**&gt;

## <a name="syntax"></a>语法


``` syntax
<Keyword Value string
</Keyword>
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
<td><p>ETW 事件的名称的字符串。</p></td>
<td><p>string</p></td>
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
<td><p>[关键字 （在 EventProvider)](keywords--in-eventprovider-.md)</p></td>
<td><p>表示一个事件提供程序关键字集合。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







