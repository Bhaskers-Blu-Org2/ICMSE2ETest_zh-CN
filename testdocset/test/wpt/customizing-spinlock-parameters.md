---
title: "自定义自旋锁参数"
description: "自定义自旋锁参数"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 16e6e317-659b-4797-a447-db4dcdb3c9c0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 5173d4a941737a54f5b16d633f8b9f61dc775c8b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customizing-spinlock-parameters"></a>自定义自旋锁参数


默认情况下，系统记录一个自旋锁事件每隔 1000年非激烈收购和每一个激烈的购置一个自旋锁事件。 自旋锁数据集合支持使您能够自定义数据收集的三个参数。 若要设置自旋锁集合参数，请使用下面的命令。

``` syntax
xperf -setspinlocksample [spin_threshold] [acquire_sample_rate] [contention_sample_rate]
```

## <a name="parameters"></a>参数


<a href="" id="spin-threshold"></a>*数值调节钮\_阈值*  
自旋锁检测提供了能力，以跟踪大量激烈的锁。 这被通过设置高的数值调节钮阈值。 如果一个锁旋转低于这个阈值时，将记录没有自旋锁事件。 例如，如果此值为 1，一个自旋锁事件获取的每次尝试获取锁。 如果此值为 10，一个自旋锁事件只记录每十个尝试获取锁。 默认值为 1。

<a href="" id="acquire-sample-rate"></a>*获得\_示例\_速率*  
在哪个自旋锁事件都记录在跟踪过程中的采样率。 例如，如果此值为 1000年，每个 1000年-冲突事件购买记录一个自旋锁事件。 默认值为 1000年。

<a href="" id="contention-sample-rate"></a>*争用\_示例\_速率*  
在哪个自旋锁会记录事件，在冲突发生时的速率。 例如，如果此值为 100，一个自旋锁事件只记录每 100 的自旋锁冲突。 默认值为 1。

## <a name="remarks"></a>备注


当系统重新启动时，自旋锁集合参数返回为默认值。 以确保有效的数据收集、 总查询或在开始收集事件数据之前设置自旋锁参数。

## <a name="example"></a>示例


下面的示例演示如何查询的当前值。

``` syntax
xperf -spinlock
```

下面的示例将旋转阈值设置为 1，1000，采集采样率以及自旋锁争用采样速率为 100。

``` syntax
xperf -setspinlocksample 1 1000 100
```

此查询会返回以下结果在前面的示例中设置的值。

``` syntax
Current Spinlock Spin Threshold = 1
Current Spinlock Acquire Sample Rate = 1000
Current Spinlock Contention Sample Rate = 100
```

## <a name="related-topics"></a>相关的主题


[自旋锁](spinlock.md)

 

 







