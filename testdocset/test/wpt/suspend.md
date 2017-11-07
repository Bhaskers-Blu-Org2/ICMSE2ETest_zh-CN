---
title: "挂起"
description: "挂起"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 76df9308-9496-43a7-90cb-113ff5f672a8
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5077eff78b9e01a3b32fae9cff7f5a1ab5337eda
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="suspend"></a>挂起


此操作将生成 XML 文件，其中总结了挂起序列的指标。

``` syntax
-a suspend [-summary] [-timeout <unit> [<precision>]] [-min <duration>]
```

## <a name="options"></a>Options


<a href="" id="-summary"></a>**-摘要**  
显示此跟踪中的挂起转换。

<a href="" id="-timeunit-unit----precision--"></a>**-于***&lt;单元&gt; \[&lt;精度&gt;\]*  
配置时间演示文稿使用时间单位&lt;*单元*&gt;和 （可选） 时间精度&lt;*精度*&gt;。 可能单位是时间的"ns"（毫微秒）、"us"（微秒）、"ms"（毫秒为单位） 或"s"（秒）。

<a href="" id="-min-duration-"></a>**最小值-***&lt;持续时间&gt;*  
显示单个计时长度大于或等于&lt;*持续时间*&gt;。

## <a name="remarks"></a>备注


如果您不指定选项， **-摘要**默认情况下使用。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







