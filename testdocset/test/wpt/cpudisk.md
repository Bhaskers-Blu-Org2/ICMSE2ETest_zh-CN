---
title: cpudisk
description: cpudisk
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2332140d-cc89-4896-b877-d0478af890a8
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 6ca386a9e5f8b9e654b9686763a7f0852ec16656
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cpudisk"></a>cpudisk


此操作将生成文本报告，其中总结了 CPU 和磁盘方面的各种统计数据。

``` syntax
-a cpudisk [-thread] [-exc_dpcisr] [-pids ...] [-exes ..] [-marks ..] [-times ..]
```

## <a name="options"></a>Options


<a href="" id="-thread"></a>**-线程**  
线程级别的报告。

<a href="" id="-exc-dpcisr"></a>**-执行\_dpcisr**  
如果 DPC/ISR 事件跟踪中存在从进程/线程时不包括 DPC/ISR 时间。

<a href="" id="-pids-pid-"></a>**-pid***&lt;pid&gt;*  
若要在报表中包括的进程标识符。

<a href="" id="-exes-name-"></a>**-exe***&lt;名称&gt;*  
若要在报表中包括的进程名称。

<a href="" id="-marks-mark-"></a>**-标记***&lt;标记&gt;*  
确定的时间间隔报告中的标记。

<a href="" id="-timest1-t2"></a>**-时间***T1 T2*  
确定报告中的时间间隔的时间戳。

## <a name="remarks"></a>备注


如果没有**-pid**或**-exe**指定，都包括在报表中的所有进程。

如果没有**-标记**或**-时间**将指定，标记中跟踪信息，或跟踪的开始和结束时间，如果少于两个标记都在跟踪，用于确定报表的时间间隔。

若要禁用跟踪中的标记，指定一个空**– 标记**选项。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







