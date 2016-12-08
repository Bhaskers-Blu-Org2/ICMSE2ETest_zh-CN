---
title: bootprefetch
description: bootprefetch
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 482e724b-bf10-4181-a77f-40e5fdc8db7e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 18e149dd2865c29ae2fa04e9c8009f862330cdbd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bootprefetch"></a>bootprefetch


此操作逐份打印，并总结了使用**开/关跟踪捕获**工具时，将启动相关的事件。

``` syntax
bootprefetch [-summary | -events [-pattern [-type name]] [-range T1 T2] | disktime]
```

## <a name="options"></a>Options


<a href="" id="-xml"></a>**xml**  
以 XML 格式显示输出。 这当前仅适用于**-摘要**。

<a href="" id="-summary"></a>**-摘要**  
显示启动预取的摘要。

<a href="" id="-events"></a>**-事件**  
转储的 ReadyBoot 与 earliness 的信息的事件。

<a href="" id="-pattern"></a>**-模式**  
只能在结合**-事件**。 转储的事件时, 还转储的重叠的事件。

<a href="" id="-typename"></a>**-类型***名称*  
只能在结合**-模式**。 转储只指定时转储模式视图中的事件的事件类型。 *名称*可以是下列值之一:"命中"、"预取"、"遗漏"，"挂起"写入"。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
只能在结合**-事件**。 处理 ReadyBoot 事件时间*T1*和*T2*之间完成。

<a href="" id="-disktime"></a>**-disktime**  
预启动期间显示磁盘时间分解。

## <a name="remarks"></a>备注


如果选择了未指定报表类型，默认值是显示的摘要。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







