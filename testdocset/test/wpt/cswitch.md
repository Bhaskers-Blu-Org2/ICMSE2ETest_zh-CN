---
title: cswitch
description: cswitch
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bb976f48-b804-4de3-bbd1-108cbad6e922
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c174c46e5e0744f1cf5ccf89aace7cabe744dcf1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="cswitch"></a>cswitch


此操作将生成报告文件，其中总结了上下文切换的指标。

``` syntax
-a cswitch [-avail [n]] [-util [n]] [-process] [-thread] [-exc_dpcisr] [-range T1 T2]
```

## <a name="options"></a>Options


<a href="" id="-avail-n-"></a>**-获得***\[n\]*  
第二个时间间隔显示*n*可用的 CPU 资源。 默认值为 1。

<a href="" id="-util-n-"></a>**实用工具-***\[n\]*  
第二个时间间隔显示*n*的 CPU 利用率。 默认值为 1。

<a href="" id="-process"></a>**-过程**  
从上下文切换数据推导显示每个进程的 CPU 使用率。

<a href="" id="-thread"></a>**-线程**  
从上下文切换数据推导显示每个线程的 CPU 使用率。

<a href="" id="-exc-dpcisr"></a>**-执行\_dpcisr**  
不包括所用 DPC/ISR 在可用性、 利用率进程和线程报告的时间。 此选项产生任何作用，必须启用 DPC/中断跟踪。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
显示数据之间时间*T1*和*T2*，同时以微秒为单位。

## <a name="remarks"></a>备注


如果选择了未指定报表类型，默认值是显示 CPU 可用性报告。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







