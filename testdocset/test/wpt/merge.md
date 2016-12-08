---
title: merge
description: merge
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: d450807c-ad86-4d1d-a089-0b3cfa86219c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4a87bf2fb40b24b76ce1cde4238393b7e3a94fd8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="merge"></a>merge


显示跟踪合并选项。

``` syntax
xperf -merge trace1.etl trace2.etl … merged.etl
```

## <a name="example"></a>示例


下面的示例将各个跟踪文件合并到 merged.etl 并添加图像识别信息和事件的清单信息所需的安全符号进行解码。

``` syntax
-merge trace1.etl trace2.etl … merged.etl
```

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 







