---
title: start
description: start
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f99fd1e6-bcc0-443f-9f28-555a46d6c02f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 3cd2b836e8acfddd3cb747058bb0a009a2ccefa4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="start"></a>start


显示记录器启动选项。

``` syntax
xperf [-start [LoggerName] [ProfileFileName!ProfileName|SessionName]|-update [LoggerName]|[ProfileFileName!ProfileName|SessionName]] -flush [LoggerName] -save ProfileFileName!ProfileName|SessionName merged.etl -setprofint [<n>] [cached] -seteresourcesample <n1> <n2> <n3> -setspinlocksample <n1> <n2> <n3> -pooltag <P1>+<P2>+<P3>+<P4> -on (GUID|KnownProviderName)[:Flags[:Level[<:0xnnnnnnnn|’stack|[,]sid[,]tsid’]]]
```

## <a name="parameters"></a>参数


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>命令</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>-启动</strong> <em>[LoggerName] |[ProfileFileName ！ProfileName |会话名]]</em></p></td>
<td><p>启动日志记录会话的<em>LoggerName</em>、 <em>ProfileName</em>定义在<em>ProfileFileName</em>文件中，配置文件在启动记录程序或启动的记录器在<em>ProfileFileName</em>文件中定义的<em>会话名</em>。</p></td>
</tr>
<tr class="even">
<td><p><strong>-更新</strong> <em>[LoggerName] |[ProfileFileName ！ProfileName |会话名]]</em></p></td>
<td><p><em>LoggerName</em>更新的日志记录会话，则更新<em>ProfileName</em>定义在<em>ProfileFileName</em>文件中，配置文件中的记录程序或更新记录器在<em>ProfileFileName</em>文件中定义的<em>会话名</em>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-刷新</strong> <em>LoggerName</em></p></td>
<td><p><em>LoggerName</em>的刷新日志记录会话。 此参数必需的缓冲区模式跟踪保存 (请参阅<em>-缓冲</em>参数，下面)。 若要保存缓冲区模式跟踪，必须发出<em>-刷新</em>参数。</p></td>
</tr>
<tr class="even">
<td><p><strong>-capturestate</strong> <em>LoggerName 标志</em></p></td>
<td><p>捕获在<em>标记</em>中指定的提供程序从非内核日志记录会话的状态。 已接受的提供程序格式是相同的<em>-在</em>。 如果指定的标志和级别，捕获状态时启用它们。</p>
<p>这就所谓的跟踪的入门<strong>– 缓冲</strong>选项。 它的后面必须跟<strong>– 停止</strong>若要停止跟踪。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-在</strong> <em>标记 |组</em></p></td>
<td><p>对于内核日志记录会话，内核标志和组的系统的一系列由加号 （+） 分隔。 对于用户登录会话，提供程序启用，一连串以加号 （+） 分隔。 已接受的提供程序格式是<code>(GUID|KnownProviderName)[:Flags[:Level]]</code>。 [提供](providers-wpa.md)程序的有效标志的列表，请参阅。</p></td>
</tr>
<tr class="even">
<td><p><strong>-f</strong> <em>文件名</em></p></td>
<td><p>将事件记录到指定文件。 默认值为内核跟踪的 \Kernel.etl 和 \User.etl 的用户跟踪。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-buffersize</strong> <em>大小</em></p></td>
<td><p>设置跟踪到的<em>大小</em>，以 kb 为单位的缓冲区大小。 可能的值为 4 为 1024年。 默认值是 64。</p></td>
</tr>
<tr class="even">
<td><p><strong>-minbuffers</strong> <em>n</em></p></td>
<td><p>将跟踪缓冲区的最小数目设置为<em>n</em>。 默认值是 64。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-maxbuffers</strong> <em>n</em></p></td>
<td><p>将跟踪缓冲区的最大数目设置为<em>n</em>。 默认值为 320。</p></td>
</tr>
<tr class="even">
<td><p><strong>-maxfile</strong> <em>大小</em></p></td>
<td><p>设置最大文件大小为 MB 的<em>大小</em>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-flushtimer</strong> <em>n</em></p></td>
<td><p>将刷新计时器设置为<em>n</em>秒。</p></td>
</tr>
<tr class="even">
<td><p><strong>-boottrace</strong> <em>标记 |组 | 关闭</em></p></td>
<td><p>配置跟踪引导到 Windows 事件跟踪记录器。 将标志设置为&quot;关闭&quot;若要关闭启动跟踪。 所有日志记录控件可以与此配合使用。 使用<strong>-f</strong>结合非 \Perf.etl 的文件记录。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-实时</strong></p></td>
<td><p>启用实时跟踪。</p></td>
</tr>
<tr class="even">
<td><p><strong>-缓冲</strong></p></td>
<td><p>启用缓冲模式跟踪。 若要保存，使用<strong>的刷新</strong>。 <strong>-停止</strong>选项将跟踪未保存。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-filemode</strong> <em>模式</em></p></td>
<td><p>设置文件模式。 默认值是&quot;连续&quot;。 可能的模式︰&quot;连续&quot;，&quot;循环&quot;，&quot;追加&quot;，和&quot;NewFile&quot;。</p></td>
</tr>
<tr class="even">
<td><p><strong>-clocktype</strong> <em>ClockType</em></p></td>
<td><p>设置时钟类型。 默认值是&quot;PerfCounter&quot;。 可能的类型︰&quot;周期&quot;， &quot;PerfCounter&quot;，和&quot;SystemTime&quot;。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-stackwalk</strong> <em>flags|@file</em></p></td>
<td><p>启用堆栈审核事件指定为<code>Flag+...</code>，或分析<em>文件</em>的标记文件。 有关详细信息，请参阅[stackwalk](stackwalk.md)。</p></td>
</tr>
<tr class="even">
<td><p><strong>-pid</strong> <em>pid [...]</em></p></td>
<td><p>应用于进程标志<code>pid [...]</code>。 使用专用的记录器的结合使用。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-pidnewprocess</strong> <em>&lt;命令行&gt;</em></p></td>
<td><p>适用于 Xperf 将开始一个新的进程的标志&lt;<em>命令行</em>&gt;。 使用专用的记录器的结合使用。</p></td>
</tr>
<tr class="even">
<td><p><strong>-waitfornewprocess</strong></p></td>
<td><p>使用创建一个新进程等待<code>-pidNewProcess</code>在退出之前返回。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-堆</strong></p></td>
<td><p>启用指定的<em>Pid</em>和<em>PidNewProcess</em>的流程中的堆跟踪。</p></td>
</tr>
<tr class="even">
<td><p><strong>-critsec</strong></p></td>
<td><p>启用由<em>Pid</em>和<em>PidNewProcess</em>指定的流程中的关键部分跟踪。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-setprofint</strong> <em>[&lt;n&gt;] [高速缓存]</em></p></td>
<td><p>设置采样到的配置文件间隔<code>&lt;n&gt; [1221..10000000]</code>。 如果缓存指定，在 ETW 缓存和重新应用新 ETW 内核记录器与样本配置文件启动时的时间间隔。 单位是 100ns。 <em>N</em>的默认值为 10000;这就是说，1 毫秒︰ 不进行缓存。</p></td>
</tr>
<tr class="even">
<td><p><strong>-保存</strong> <em>ProfileFileName ！ProfileName |会话名 merged.etl</em></p></td>
<td><p>刷新的记录器在<em>ProfileName</em>在<em>ProfileFileName</em>文件中定义的配置文件和合并 ETL 文件复制到 merged.etl;或刷新记录器在<em>ProfileFileName</em>文件中定义的<em>会话名</em>并合并到 Merged.etl 的 ETL 文件。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-seteresourcesample</strong> <em>&lt;n1&gt; &lt;n2&gt; &lt;n3&gt;</em></p></td>
<td><p>设置 ERESOURCE 采样，其中 n1 释放采样速率大于或等于 1000年，n2 争用取样速率是大于或等于 1，和 n3 过多的超时数大于或等于 1。 争用采样率是在自旋锁事件时，会获取发生冲突的速率。 例如，如果此值为 100，每一百个旋转锁冲突购置一个自旋锁事件。</p></td>
</tr>
<tr class="even">
<td><p><strong>-setspinlocksample</strong> <em>&lt;n1&gt; &lt;n2&gt; &lt;n3&gt;</em></p></td>
<td><p>自旋锁钮阈值设置为<code>&lt;n1&gt; [ &gt;=1]</code>。 集自旋锁获取采样速率为<code>&lt;n2&gt; [ &gt;= 1000]</code>。 自旋锁争用采样速率设置为<code>&lt;n3&gt; [ &gt;= 1]</code>。 只有 64 位 Windows 7，Windows Server 2008 R2，较新版本的操作系统支持自旋锁检测。</p></td>
</tr>
<tr class="odd">
<td><p><strong>-pooltag</strong> <em>&lt;P1&gt;+&lt;P2&gt;+&lt;P3&gt;+&lt;P4&gt;</em></p></td>
<td><p>设置池标记筛选器 (<em>Pn</em>) 由加号 （+） 或分号 （;） 分隔。 单字符通配符或多字符通配符星号 （*） 中使用问号 （？）。 可以指定最多四个筛选器。</p></td>
</tr>
</tbody>
</table>

 

## <a name="remarks"></a>备注


可以使用多个启动选项启动多个记录器，每一个后跟要应用于该记录器的选项。 如果*LoggerName*或`-start LoggerName`内核记录器所隐含的省略。 任何时候，只能运行一个内核记录器实例可以存在。 如果一个记录器无法启动，则停止已启动的所有记录器。

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 







