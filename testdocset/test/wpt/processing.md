---
title: "处理"
description: "处理"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: effacd2f-9804-434e-bbd9-128cddd7f940
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 2ab4f11a0148c9903cbad92af73db2a0db687590
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="processing"></a>处理


显示跟踪后期处理选项。

``` syntax
xperf -i <trace file>… [-o output] [-symbols …] [-target {human|machine}] [-a action …[-a action …] …]
```

## <a name="parameters"></a>参数


<a href="" id="-itrace-file"></a>**-i***跟踪文件*  
要处理的跟踪文件。

<a href="" id="-ooutput-file"></a>**-o***输出文件*  
输出文件的名称。 如果不指定，使用**标准输出**。

<a href="" id="-symbols-options-"></a>**-符号***\[选项\]*  
启用并配置符号解码支持。 有关详细信息，请参见[符号](symbols.md)。

<a href="" id="-target-human-machine-"></a>**的目标***{人 | 机}*  
选择输出的目标听众。 默认值是"人"。

<a href="" id="-quiet"></a>**-安静**  
不打印进度信息。

<a href="" id="-tle"></a>**-tle**  
处理跟踪甚至存在丢失的事件。 首字母缩写词*TLE*代表*承受丢失的事件*。

<a href="" id="-tti"></a>**-tti**  
处理跟踪甚至存在时间 inversions。 首字母缩写词*TTI*代表*容忍时间 inversions*。

<a href="" id="-aaction----"></a>**-a***操作...*  
要采取的操作。 默认操作是转储文本窗体中的事件。

## <a name="remarks"></a>备注


下表描述了可用的操作。

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
<td><p>显示启动和关机的统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[bootprefetch](bootprefetch.md)</p></td>
<td><p>显示启动时预取信息。</p></td>
</tr>
<tr class="odd">
<td><p>[cpudisk](cpudisk.md)</p></td>
<td><p>显示 CPU/磁盘活动报告。</p></td>
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
<td><p>在直方图格式显示所有磁盘活动和空闲的时间。</p></td>
</tr>
<tr class="odd">
<td><p>[dpcisr](dpcisr.md)</p></td>
<td><p>显示 DPC/ISR 统计信息。</p></td>
</tr>
<tr class="even">
<td><p>[drvdelay](drvdelay.md)</p></td>
<td><p>显示驱动程序延迟。</p></td>
</tr>
<tr class="odd">
<td><p>[转储程序](dumper.md)</p></td>
<td><p>转储文本形式跟踪内的事件。</p></td>
</tr>
<tr class="even">
<td><p>[文件名](filename-wpa.md)</p></td>
<td><p>在跟踪中显示文件的名称。</p></td>
</tr>
<tr class="odd">
<td><p>[focuschange](focuschange.md)</p></td>
<td><p>在跟踪中显示 Windows 线程焦点更改事件。</p></td>
</tr>
<tr class="even">
<td><p>[hardfault](hardfault.md)</p></td>
<td><p>显示由进程和文件的硬错误统计信息。</p></td>
</tr>
<tr class="odd">
<td><p>[堆](heap.md)</p></td>
<td><p>显示堆信息。</p></td>
</tr>
<tr class="even">
<td><p>[标记](marks.md)</p></td>
<td><p>显示标记的信息。</p></td>
</tr>
<tr class="odd">
<td><p>[pagefault](pagefault.md)</p></td>
<td><p>在跟踪中显示页故障信息。</p></td>
</tr>
<tr class="even">
<td><p>[perfctrs](perfctrs.md)</p></td>
<td><p>显示流程性能计数器。</p></td>
</tr>
<tr class="odd">
<td><p>[即插即用](pnp.md)</p></td>
<td><p>显示插跟踪内的事件。</p></td>
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
<td><p>显示与自旋锁活动相关的信息。</p></td>
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
<td><p>在跟踪中显示 Windows 登录事件。</p></td>
</tr>
</tbody>
</table>

 

如果存在任何操作，不则**转储程序**将被调用。

## <a name="example"></a>示例


下表显示了**处理**的示例。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><code>xperf -i trace.etl -o out.csv</code></p></td>
<td><p>转储 trace.etl 到 Out.csv 文件中的事件。</p></td>
</tr>
<tr class="even">
<td><p><code>xperf -help registry</code></p></td>
<td><p>打印<strong>注册表</strong>操作帮助。</p></td>
</tr>
<tr class="odd">
<td><p><code>xperf -i trace.etl -a registry</code></p></td>
<td><p>打印到<strong>标准输出</strong>的注册表访问统计信息。</p></td>
</tr>
<tr class="even">
<td><p><code>xperf -i trace32.etl trace64.etl -o out.csv</code></p></td>
<td><p>转储到 Out.csv 文件中 Trace32.etl 和 Trace64.etl 的事件。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 







