---
title: "停止"
description: "停止"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ebde3a43-c6c9-47d4-b6f1-8b1dae313af3
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 118752f3c606b4e87667a437c241ab893a4ab14c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stop"></a>停止


显示跟踪停止选项。

``` syntax
xperf [-stop [LoggerNames]|[ProfileFileName!ProfileName|SessionName merged.etl]]|[-stopall]|[-cancel rofileFileName!ProfileName|SessionName [NoDelete]] [-d merged.etl] [-heap|-critsec]
```

## <a name="parameters"></a>参数


<a href="" id="-stoploggernames-profilefilename-profilename-sessionname-merged-etl"></a>**-停止***LoggerNames |ProfileFileName ！ProfileName |会话名 merged.etl*  
关闭在*LoggerNames*中指定的记录器、 关闭记录器在*ProfileName*的*ProfileFileName*文件中定义的配置文件和合并 ETL 文件复制到 merged.etl，或关闭记录器在*ProfileFileName*文件中定义的*会话名*并合并到 Merged.etl 的 ETL 文件。

<a href="" id="-stopall"></a>**-stopall**  
关闭所有的日志记录会话。

<a href="" id="-cancelprofilefilename-profilename-sessionname--nodelete-"></a>**-取消***ProfileFileName ！ProfileName |会话名\[NoDelete\] *  
关闭记录器在配置文件中的*ProfileFileName*文件中定义的*ProfileName*和删除跟踪文件中，或关闭记录器*会话名*定义在*ProfileFileName*文件中，并将合并到 Merged.etl 的 ETL 文件。 如果指定*NoDelete* ，则不会删除跟踪文件。

<a href="" id="-dmerged-etl"></a>**-d***merged.etl*  
合并已停止日志记录会话 merged.etl 的 ETL 文件。 如果显式停止没有会话，则将隐式停止 NT 内核记录器。

<a href="" id="-boottraceoff"></a>**-boottrace***关闭*  
关闭启动跟踪。

<a href="" id="-heap"></a>**-堆**  
停止的堆跟踪。

<a href="" id="-critsec"></a>**-critsec**  
停止临界区跟踪。

## <a name="remarks"></a>备注


目前，只有一堆跟踪或临界区跟踪可以活动一次。 因此， **-堆**和**-critsec**是互相排斥的。 如果没有指定*LoggerNames*或使用既不指定**-d** **-停止** **-stopall** ，内核记录器已停止，也不。

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 







