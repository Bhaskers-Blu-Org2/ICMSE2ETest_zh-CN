---
title: "堆"
description: "堆"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5a8b4c32-9a36-4668-831a-8dc6fa9e2c5d
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 8af99f93f0afed3fb960a70f4911319b044c5948
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="heap"></a>堆


写入一个文本文件，包含以下信息以表格的形式，根据所指定的输出文件`-o`:

-   分配数

-   分配大小，以 kb 为单位

-   出数

-   出大小，以 kb 为单位

-   重新分配数

-   扩展盘区的大小，以 kb 为单位

-   扩展大小，以 kb 为单位出

-   堆句柄

``` syntax
-a heap [-pid <processId>] [-stacks] [-frames] [-images] [-range T1 T2] [-lifetime T1 T2] [-size S1 S2] [-cullframes Frame1 Frame2 ... FrameN] [-requireframes Frame1 Frame2 ... FrameN] [-cullLists cullfuncs.txt] [-top <n>] [-totals]
```

## <a name="options"></a>Options


<a href="" id="-pid-processid-"></a>**-pid***&lt;流程 Id&gt;*  
显示统计信息仅用于指定的进程标识符。 如果未指定，则显示所有进程的统计数据。

<a href="" id="-stacks-s--o-oc-t-tc-rc--"></a>**-叠***\[s \[o | oc | t | tc | rc\]\]*  
显示分配，按堆栈聚合。 这是默认行为。

按未完成大小 （*因此*） 未完成计数 (*soc*，总大小 (*st*)，重新分配计数 （*src*，而总数 (*stc*)。 *因此*，默认值为。

<a href="" id="-frames-s--o-oc-t-tc-rc--"></a>**-框架***\[s \[o | oc | t | tc | rc\]\]*  
类似于`-stacks`，但聚合顶部堆栈帧，而不是通过整个堆栈。

<a href="" id="-images"></a>**-图像**  
类似于`-stacks`， `-frames`，但聚合通过顶部堆栈帧的图像名称。

<a href="" id="-ranget1-t2"></a>**-范围***T1 T2*  
使用事件数据来自时间*T1*到*T2*，同时以微秒为单位。

<a href="" id="-lifetimet1-t2"></a>**-生存期***T1 T2*  
包括只分配的生存期，以微秒为单位，大于或等于*T1*和*T2*比少。

<a href="" id="-sizes1-s2"></a>**-大小***S1 S2*  
包括分配大小大于或等于*S1*和*S2*，小于以字节为单位。

<a href="" id="-cullframesframe1-frame2---framen"></a>**-cullframes***Frame1 Frame2...FrameN*  
匹配任何指定的框架的报告中删除任何顶部堆栈帧。 参数格式为`[image!][symbol]`。 名称是不区分大小写。

<a href="" id="-requireframesframe1-frame2---framen"></a>**-requireframes***Frame1 Frame2...FrameN*  
要求每个堆栈有至少一个匹配至少一个指定框架的框架。 此测试发生之前与剔除任何显式框架`-cullframes`。

<a href="" id="-culllists-filename-"></a>**-cullLists***&lt;文件名&gt;*  
指定文件中的帧将从结果中排除。 如果堆栈中不包含此类框架，堆栈将被排除。 框架具有相同的格式为`-cullFrames`。 名称是不区分大小写。

<a href="" id="-top-n-"></a>**-top***&lt;n&gt;*  
限制显示的分配的数量。

<a href="" id="-totals"></a>**-合计**  
显示仅分配事件的总计。

## <a name="remarks"></a>备注


此操作可能需要几分钟才能完成在大跟踪由于粗分类和匹配执行。

有关如何捕获堆数据的信息，请参阅[启用堆数据捕获](enabling-heap-data-capture.md)

## <a name="related-topics"></a>相关的主题


[Xperf 操作](xperf-actions.md)

[时间和时间戳的格式](time-and-timestamp-formats.md)

 

 







