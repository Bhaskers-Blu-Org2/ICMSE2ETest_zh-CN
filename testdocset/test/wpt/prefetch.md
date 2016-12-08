---
title: "预取"
description: "预取"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8769558a-7749-4696-82b3-50e237d846d7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8ae48dc04ea49fbfc81be8ee24754a21755aa6fa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="prefetch"></a>预取


此操作生成一个文本文件，其中总结了预取有关的指标。

``` syntax
-a prefetch [-summary] [-timeunit <unit> [<precision>]] [-min <duration>]
```

## <a name="options"></a>Options


<a href="" id="-summary"></a>**-摘要**  
显示跟踪中的预回迁方案。

<a href="" id="-timeunit-unit----precision--"></a>**-于***&lt;单元&gt; \[&lt;精度&gt;\]*  
配置时间演示文稿使用时间单位&lt;*单元*&gt;和 （可选） 时间精度&lt;*精度*&gt;。 单位可以"ns"（纳秒），"us"（微秒）、"ms"（毫秒为单位） 或"s"（秒）。

<a href="" id="-min-duration-"></a>**最小值-***&lt;持续时间&gt;*  
显示仅单独排练时间，单位为微秒，长度大于或等于&lt;*持续时间*&gt;。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







