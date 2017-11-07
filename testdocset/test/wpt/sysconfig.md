---
title: sysconfig
description: sysconfig
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bd020833-a2fe-4619-8d9d-d049fd4e543c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c30eb4f8b356d434613acea101e0f912108b143a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysconfig"></a>sysconfig


此操作会生成一个文本文件，其中提供了详细信息系统对其跟踪拍摄。

``` syntax
-a sysconfig [-xml] [-netidentity] [-cpu] [-memory] [-build] [-etw] [-power] [-disk] [-idechannel] [-video] [-nic] [-irq] [-services] [-pnp]
```

## <a name="options"></a>Options


<a href="" id="-xml"></a>**xml**  
输出为 XML 格式。

<a href="" id="-netidentity"></a>**-netidentity**  
显示网络标识信息。

<a href="" id="-cpu"></a>**cpu**  
显示 CPU 配置。

<a href="" id="-memory"></a>**-内存**  
显示内存配置。

<a href="" id="-build"></a>**-生成**  
显示生成的信息。

<a href="" id="-etw"></a>**-etw**  
显示 ETW 版本信息。

<a href="" id="-power"></a>**-电源**  
显示电源状态支持信息。

<a href="" id="-disk"></a>**-磁盘**  
显示磁盘配置。

<a href="" id="-idechannel"></a>**-idechannel**  
显示集成驱动器电子 (IDE) 信道配置。

<a href="" id="-video"></a>**-视频**  
显示视频配置。

<a href="" id="-nic"></a>**nic**  
显示网络接口控制器配置。

<a href="" id="-irq"></a>**-irq**  
显示中断请求 (IRQ) 配置。

<a href="" id="-services"></a>**-服务**  
显示服务的信息。

<a href="" id="-pnp"></a>**-即插即用**  
显示即插即用和运行配置。

## <a name="remarks"></a>备注


如果选择不活动，则默认情况下选中的所有活动。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







