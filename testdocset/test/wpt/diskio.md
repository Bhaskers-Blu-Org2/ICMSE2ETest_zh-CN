---
title: diskio
description: diskio
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 7df30160-5a77-40f9-a03f-f21fec9cbafb
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 89f6722a7631b92b2377e582032158fa6c52cdbf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="diskio"></a>diskio


此操作将生成文本报告，其中总结了磁盘 I/O 的指标。

``` syntax
-a diskio [-util <n>] [-summary] [-counts] [-detail] [-overlap] [-range T1 T2]
```

## <a name="options"></a>Options


<a href="" id="-util-n-"></a>**实用工具-***\[n\]*  
显示磁盘使用率为 n 秒为间隔。 默认值为 1 秒。

<a href="" id="-summary"></a>**-摘要**  
显示每个文件 I/O 摘要报告。

<a href="" id="-detail"></a>**-详细信息**  
显示每个 I/O 事件的详细信息。

<a href="" id="-overlap"></a>**-重叠**  
显示重叠的 I/O 事件。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
显示的数据之间时间*T1*和时间*T2*，同时以微秒为单位。

## <a name="remarks"></a>备注


如果选择了未指定报表类型，默认值是显示磁盘利用率报告。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







