---
title: "配置文件"
description: "配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b0b4c89c-70e7-4fe8-986d-e057b8074c9e
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d35f424d336707825d8a7dcf22ce16c4e8a7412b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="profile"></a>配置文件


此操作生成一个文本文件，其中总结了配置文件为度量值。

``` syntax
-a profile [-util [n]] [-detail] [-range T1 [T2]]
```

## <a name="options"></a>Options


<a href="" id="-util-n-"></a>**实用工具-***\[n\]*  
第二个时间间隔显示*n*的 CPU 利用率。 默认值为 1 秒。

<a href="" id="-detail"></a>**-详细信息**  
如果启用了符号进行解码，显示 CPU 样本 bucketed 通过流程和模块如果未启用符号进行解码，以及过程和函数名。

<a href="" id="-ranget1--t2-"></a>**-范围***T1 \[T2\]*  
显示数据之间时间*T1*和*T2*，同时以微秒为单位。 如果*T2*不存在，将使用跟踪的结束。

<a href="" id="-freq"></a>**-频率**  
显示跟踪中固定采样频率区域。

## <a name="remarks"></a>备注


如果没有`-util`， `-detail`，或`-freq`指定，则默认情况下显示 CPU 使用率报告。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







