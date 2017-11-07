---
title: "自旋锁"
description: "自旋锁"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5ca2ee5f-ad3f-42ec-91e4-a044ce982650
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 9813421e0d18947e83b791d952b99b655dd38726
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="spinlock"></a>自旋锁


此操作生成一个文本文件，其中列出与自旋锁活动相关的信息。

``` syntax
-a spinlock [-summary] [-counts [n]]
```

## <a name="options"></a>Options


<a href="" id="-summary"></a>**-摘要**  
总结了自旋锁事件信息以制表符分隔的格式。

<a href="" id="-count-n-"></a>**-计数***\[n\]*  
要显示的文件的最大数目。

## <a name="remarks"></a>备注


Xperf 自旋锁分析是适用于 64 位体系结构。 自旋锁检测从开始 Windows 7，Windows Server 2008 R2，并且较新版本的操作系统支持。 Xperf 支持正常的自旋锁，排队的自旋锁。 关于自旋锁的详细信息，请参阅[自旋锁](http://go.microsoft.com/fwlink/p/?linkid=213937)。 为了减少开销，ETW 自旋锁检测是基于样本。 采样频率可以调节与`-setspinlocksample`。 有关启动采样自旋锁的详细信息，请参阅[启动](start.md)。

要进行有意义的分析，建议使用 WPA 符号的熟悉。 符号的信息，请参见[符号支持](symbol-support.md)。

如果已在运行您的测试方案，它没有必要停止收集自旋锁事件的方案。 而积极实施感兴趣的代码，您可以开始自旋锁事件收集。 也有必要在收集自旋锁事件数据时暂停您的方案。

**请注意**  
大量的自旋锁事件可能重载跟踪缓冲区并造成事件丢失。 合并和加载跟踪，如果发生这种情况时，则将出现一条消息。 为避免丢失事件的有关详细信息，请参阅[避免丢失事件](avoid-lost-events.md)。

**自旋锁**操作有关的详细信息，请参阅[自定义自旋锁参数](customizing-spinlock-parameters.md)。

 

## <a name="example"></a>示例


下面的命令示例演示如何使用自旋锁数据启动跟踪。

``` syntax
xperf -on PROC_THREAD+LOADER+SPINLOCK
```

自旋锁事件数据也可以收集使用仅"自旋锁"选项，下面的命令示例中所示。

``` syntax
xperf -on SPINLOCK
```

但是，如果"进程内\_线程 + 加载程序"选项被忽略、 符号信息不可用于解码。 关于符号的详细信息，请参见[符号支持](symbol-support.md)。

事件数据已收集到 ETL 文件后，处理 ETL 文件，下面的命令示例中所示。

``` syntax
xperf -i example.etl -symbols -o example.txt -a spinlock
```

这将产生自旋锁报告。 有关此报告的详细说明，请参阅[计算自旋锁数据](evaluating-spinlock-data.md)。

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

 

 







