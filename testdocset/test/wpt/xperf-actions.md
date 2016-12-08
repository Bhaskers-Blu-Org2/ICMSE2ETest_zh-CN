---
title: "Xperf 操作"
description: "Xperf 操作"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 14ea91eb-eb7b-4dd7-a09d-da4743dc3805
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e584abcb254175dbe0cc3d51320786304bfde1e8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="xperf-actions"></a>Xperf 操作


Xperf 操作是处理逐份打印事件信息以生成文本报告的组件的跟踪。 操作生成特定于的一组事件如注册表访问、 上下文切换、 文件访问或系统配置的摘要的报告。

使用下面的命令行模式调用所有操作︰

``` syntax
xperf -i input.etl -o output.txt -a <action_name> [action_parameters]
```

*Output.txt* *input.etl*为跟踪文件的名称，其中是的报告文件的名称和*&lt;操作\_名称&gt;*是操作的名称。 操作名称始终跟在`-a`命令行开关。 操作名称后面可以跟一个或多个特定于操作的参数。

## <a name="in-this-section"></a>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>操作</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[启动](boot.md)</p></td>
<td><p>显示启动和关闭的统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[bootprefetch](bootprefetch.md)</p></td>
<td><p>显示启动预先获取事件。</p></td>
</tr>
<tr class="odd">
<td><p>[cpudisk](cpudisk.md)</p></td>
<td><p>显示 CPU 或磁盘活动。</p></td>
</tr>
<tr class="even">
<td><p>[cswitch](cswitch.md)</p></td>
<td><p>显示上下文切换的数据。</p></td>
</tr>
<tr class="odd">
<td><p>[diskio](diskio.md)</p></td>
<td><p>显示磁盘 I/O 统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[diskidlehistogram](diskidlehistogram.md)</p></td>
<td><p>显示磁盘活动和空闲时间的直方图。</p></td>
</tr>
<tr class="odd">
<td><p>[dpcisr](dpcisr.md)</p></td>
<td><p>显示延迟过程调用和中断服务例程的统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[drvdelay](drvdelay.md)</p></td>
<td><p>显示驱动程序延迟。</p></td>
</tr>
<tr class="odd">
<td><p>[转储程序](dumper.md)</p></td>
<td><p>转储的事件在窗体中的文本。</p></td>
</tr>
<tr class="even">
<td><p>[文件名](filename-wpa.md)</p></td>
<td><p>显示文件名称。</p></td>
</tr>
<tr class="odd">
<td><p>[focuschange](focuschange.md)</p></td>
<td><p>显示 Windows 线程焦点更改事件。</p></td>
</tr>
<tr class="even">
<td><p>[hardfault](hardfault.md)</p></td>
<td><p>显示由进程和文件的硬错误统计信息。</p></td>
</tr>
<tr class="odd">
<td><p>[堆](heap.md)</p></td>
<td><p>显示流程堆信息。</p></td>
</tr>
<tr class="even">
<td><p>[标记](marks.md)</p></td>
<td><p>显示标记的信息。</p></td>
</tr>
<tr class="odd">
<td><p>[pagefault](pagefault.md)</p></td>
<td><p>显示页面故障信息。</p></td>
</tr>
<tr class="even">
<td><p>[perfctrs](perfctrs.md)</p></td>
<td><p>显示流程性能计数器。</p></td>
</tr>
<tr class="odd">
<td><p>[即插即用](pnp.md)</p></td>
<td><p>显示即插即用和运行的事件。</p></td>
</tr>
<tr class="even">
<td><p>[预取](prefetch.md)</p></td>
<td><p>显示预回迁信息。</p></td>
</tr>
<tr class="odd">
<td><p>[进程](process.md)</p></td>
<td><p>显示进程、 线程和图像信息。</p></td>
</tr>
<tr class="even">
<td><p>[配置文件](profile-wta.md)</p></td>
<td><p>显示取样探查器数据。</p></td>
</tr>
<tr class="odd">
<td><p>[注册表](registry.md)</p></td>
<td><p>显示注册表访问统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[服务](services.md)</p></td>
<td><p>显示服务的状态信息。</p></td>
</tr>
<tr class="odd">
<td><p>[关机](shutdown.md)</p></td>
<td><p>显示关机统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[自旋锁](spinlock.md)</p></td>
<td><p>显示了自旋锁的信息。</p></td>
</tr>
<tr class="odd">
<td><p>[堆栈](stack.md)</p></td>
<td><p>显示堆栈信息。</p></td>
</tr>
<tr class="even">
<td><p>[挂起](suspend.md)</p></td>
<td><p>显示挂起的转换信息。</p></td>
</tr>
<tr class="odd">
<td><p>[sysconfig](sysconfig.md)</p></td>
<td><p>显示系统配置信息。</p></td>
</tr>
<tr class="even">
<td><p>[tracestats](tracestats.md)</p></td>
<td><p>显示跟踪统计信息。</p></td>
</tr>
<tr class="odd">
<td><p>[winlogon](winlogon.md)</p></td>
<td><p>显示 Winlogon 事件。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[Xperf 命令行参考](xperf-command-line-reference.md)

 

 







