---
title: tracestats
description: tracestats
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 875ee44a-765d-44e4-b303-867b6c766251
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 400a1b8976be5a324c2504434d48eecd73025800
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="tracestats"></a>tracestats


此操作会生成一个文本文件，其中总结了跟踪统计。

``` syntax
-a tracestats [-timespan [actual]] [-detail] [-timezone {utc | local}]
```

## <a name="options"></a>Options


<a href="" id="-timespan-actual-"></a>**-时间跨度***\[实际\]*  
显示有关会话和跟踪信息。 默认情况下，*时间的跨度*要求检查跟踪头只;没有传递是通过跟踪会话中执行的。 指定"实际"，则会话中的第一个事件和最后一个事件的实际时间添加到报表中。 在这种情况下，通过跟踪会话中是必需的。

<a href="" id="-detail--stack-"></a>**-详细信息*\[堆栈\]***  
显示详细信息在会话中，提供程序和操作代码好记的名称和提供商、 标识符、 任务、 操作码、 版本、 通道和级别的事件。 在会话中需要跟踪一个完整传递。

指定*堆栈*参数，堆栈的每种类型的事件计数添加到报表中。 在这种情况下，第二个会话中的跟踪通过是必需的。

<a href="" id="-timezone-utc-local-"></a>**-时区***{utc | 本地}*  
显示指定的时区中的时间戳。 如果未不指定任何时区，则默认使用本地时区。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







