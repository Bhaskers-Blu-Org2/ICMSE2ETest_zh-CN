---
title: dpcisr
description: dpcisr
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8bab6760-0aa9-403b-b552-eabe21f780dd
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c75dfb97509785e1676afd7927b1b51421b58885
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dpcisr"></a>dpcisr


此操作会生成报告汇总了有关延迟过程的各种统计数据调用 (Dpc) 和中断服务例程 (Isr)。

``` syntax
-a dpcisr [-dpc | -isr] [-summary] [-interval [n]] [-bucket [n]] [-range T1 T2 ]
```

## <a name="options"></a>Options


<a href="" id="-dpc"></a>**-dpc**  
仅显示 Dpc 的统计信息。

<a href="" id="-isr"></a>**-isr**  
对于 Isr 中只显示统计信息。

<a href="" id="-summary"></a>**-摘要**  
显示摘要报告。

<a href="" id="-interval-dt-"></a>**-间隔***\[dt\]*  
*Dt*秒为间隔显示使用情况报告。 默认值为 1。

<a href="" id="-bucket-dt-"></a>**-存储桶***\[dt\]*  
*Dt*秒为间隔显示直方图。 默认值为 2。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
显示*T1*和*T2*之间的延迟。

## <a name="remarks"></a>备注


如果指定没有数据类型，则该操作显示 Dpc 和 Isr 的报告。 如果未指定报表类型未指定，默认设置是打印所有三个报告︰ Dcp、 Isr 和摘要。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







