---
title: "关键字 （在 EventProvider)"
description: "关键字 （在 EventProvider)"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9ecdbe0a-7635-416a-a690-cf18c63d429f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 187c025472fb5a704f3e32c0d98ad60e0f57ad84
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="keywords-in-eventprovider"></a>关键字 （在 EventProvider)


表示一个事件关键字集合。

## <a name="element-hierarchy"></a>元素层次结构


&lt;[WindowsPerformanceRecorder](windowsperformancerecorder.md)&gt;

     &lt;[Profiles](profiles.md)&gt;

          &lt;[EventProvider](eventprovider.md)&gt;

               &lt;**Keywords (in EventProvider)**&gt;

          &lt;[Profile](profile-wpr.md)&gt;

               &lt;[Collectors](collectors.md)&gt;

                    &lt;[EventCollectorId](eventcollectorid.md)&gt;

                         &lt;[EventProviders](eventproviders.md)&gt;

                              &lt;[EventProviderId](eventproviderid.md)&gt;

                                   &lt;**Keywords (in EventProvider)**&gt;****

                              &lt;[EventProvider](eventprovider.md)&gt;

                                   &lt;**Keywords (in EventProvider)**&gt;

## <a name="syntax"></a>语法


``` syntax
<Keywords Operation = "Set" | "Add" | “Remove” >

  <!-- Child elements -->
  Keyword

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
<td><p>[关键字 （在 EventProvider)](keyword--in-eventprovider-.md)</p></td>
<td><p>描述用于用户模式提供程序跟踪 Windows 事件 (ETW) 关键字。</p></td>
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
<td><p>[EventProvider](eventprovider.md)</p></td>
<td><p>表示事件提供程序的配置文件。</p></td>
</tr>
<tr class="even">
<td><p>[EventProviderId](eventproviderid.md)</p></td>
<td><p>表示事件提供程序标识符。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[元素](elements.md)

 

 







