---
title: "进程"
description: "进程"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 349abd2d-5708-4438-8448-3e9d49618ac5
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5e4f03f0201d509d58d10719c0d5c5054f389afa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="process"></a>进程


此操作会产生一个文本文件，其中概述了与流程相关的度量标准。

``` syntax
-a process [[-thread] [-image] [-vm]]|[-tree] [-range T1 T2] [-withsids] [-withcmdline]
```

## <a name="options"></a>Options


<a href="" id="-thread"></a>**-线程**  
显示线程。

<a href="" id="-image"></a>**-图像**  
显示图像。

<a href="" id="-vm"></a>**的虚拟机**  
显示分配的虚拟内存范围。

<a href="" id="-tree"></a>**-树**  
显示进程的树状结构。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
显示数据之间时间*T1*和*T2*，同时以微秒为单位。

<a href="" id="-withsid"></a>**-withsid**  
显示进程报告中的安全标识符 (Sid)。

<a href="" id="-withcmdline"></a>**-withcmdline**  
显示命令行进程报告中。

## <a name="remarks"></a>备注


默认情况下，将显示只过程。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







