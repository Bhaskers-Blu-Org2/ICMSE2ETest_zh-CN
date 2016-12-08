---
title: "计算自旋锁数据"
description: "计算自旋锁数据"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9e5e4ffa-5fb7-401e-bfc3-760cbb7955d9
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: a4e1663b0a13d76a35d0657fdb5b29011b687909
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="evaluating-spinlock-data"></a>计算自旋锁数据


自旋锁报表提供以下有关锁的信息︰

-   获取采样速率。

-   争用采样速率。

-   数值调节钮的阈值。

-   Cpu 的数目。

-   CPU 速度，单位为兆赫。

-   跟踪长度，在十亿分之一秒内。

-   在周期中跟踪长度。

报告下一节显示过程配置文件时间段使用自旋锁。 分别显示了每个自旋锁。 自旋锁进行排序与显示第一个"最热门"自旋锁。 通常是可以通过观察顶几个自旋锁确定了自旋锁的瓶颈效应。

每个自旋锁提供以下信息︰

-   锁的类型。

-   锁定的内核地址。

-   锁定的符号。 动态创建的锁没有符号。

摘要报告提供以下信息如下所示︰

-   锁购置用的 CPU 时间的百分比。

-   锁争用花费的 CPU 时间的百分比。

-   锁采集速率。

-   冲突率。

-   旋转速率。

-   争用率同时采样和规范化。

报告在最后两个部分是由于中断和释放函数跳过事件。

自旋锁时，会发生中断。 在这种情况中自旋锁持续时间，, 包括中断处理时间和自旋锁持续时间显示需要长。 Xperf 不包括计算自旋锁持有时间时处理中断时保持的自旋锁事件。 "事件中断由于跳过"行显示未包括在计算中的事件数。 这个数字是通常很小。

自旋锁可以被获取或释放从不同的代码路径。 发行的自旋锁的函数的列表将显示在报表的末尾。 列表被按自旋锁的持续时间。 此外介绍了关于特定版本功能，例如购置或争用，附加信息。

## <a name="example"></a>示例


下面的示例演示如何获取自旋锁数据的汇总。

``` syntax
xperf -i example.etl -symbols -o example.txt -a spinlock -summary
```

下面的示例演示如何限制返回的记录数为 5 个最活跃的自旋锁。

``` syntax
xperf -i example.etl -symbols -o example.txt -a spinlock -summary -counts 5
```

## <a name="related-topics"></a>相关的主题


[自旋锁](spinlock.md)

 

 







