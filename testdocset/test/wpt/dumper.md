---
title: "转储程序"
description: "转储程序"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e5fec87c-6945-4611-8e50-52d279357004
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f29ff89ba1ac9204ac118851c54379274d126990
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dumper"></a>转储程序


此操作将生成 ANSI 文本文件的 ETL 跟踪日志。

``` syntax
-a dumper [-range T1 T2] [-stacktimeshifting] [exc_dpcisr] [-provider id1 id2 …] [-add_rawdata] [-add_pgodata] [-add_inline]
```

## <a name="options"></a>Options


<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
转储数据之间时间*T1*和*T2*，以微秒为单位的这两只。

<a href="" id="-stacktimeshifting"></a>**-stacktimeshifting**  
结合用户和内核堆栈碎片，并将它们放在触发事件后。

<a href="" id="-exc-dpcisr"></a>**-执行\_dpcisr**  
不包括 Dpc 或 Isr 中花费的时间。 DPC 和中断跟踪必须启用此选项产生任何作用。 目前，这会影响只有**cswitch**事件。

<a href="" id="-providerid1-id2--"></a>**-提供商***id1...id2*  
转储为指定的提供程序的事件。 接受的输入任意数量的提供程序的 Guid。

<a href="" id="-add-rawdata"></a>**-添加\_rawdata**  
添加在每个事件之前的原始信息行。

<a href="" id="-add-pgodata"></a>**-添加\_pgodata**  
将 PGO 培训信息添加到每个堆栈帧。

<a href="" id="-add-inline"></a>**-添加\_内联**  
每个堆栈帧的结尾追加内联函数名。

## <a name="remarks"></a>备注


以文本形式转储跟踪内的事件。

## <a name="example"></a>示例


以下是此操作具有指定的提供程序的示例。

``` syntax
xperf -i trace.etl -o trace.etl.csv -a dumper -provider {315a8872-923e-4ea2-9889-33cd4754bf64} {7dd42a49-5329-4832-8dfd-43d979153a88}
```

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







