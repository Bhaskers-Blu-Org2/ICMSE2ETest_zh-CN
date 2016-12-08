---
title: "本地视频播放评估结果"
description: "本地视频播放评估结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 4b4198f1-99bd-4858-a933-5e194ed3367f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 02c609cafdfa18036b32a16e358dfcadb1b66ff2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-local-video-playback-assessment"></a>本地视频播放评估结果


本地视频回放评估结果显示指标和能源效率问题突出显示的问题。 如果可能，请标识能源效率问题的原因。 例如，它可能是驱动程序、 进程或服务。 提供了有关这些问题的建议的解决方案。

此主题帮助您理解使用的本地视频播放评估的电池运行下作业所产生的结果。 有关如何使用结果来识别并解决常见的问题，对计算机的电池寿命造成负面影响，它还提供指导。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-metrics)

-   [问题](#bkmk-idleissues)

有关电池运行下作业的详细信息，请参阅[连接备用能源效率](connected-standby-energy-efficiency.md)。

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>目标文件


您可以创建自定义的目标来衡量结果视图中的您改进。 目标文件是会审的工具，可帮助您了解 PC 的性能如何，比较 Pc 业务中。

例如，基本的便携式计算机目标可能不同于为高端桌面计算机设置的目标或者市场预期可能会更改所需的灵活性，可以定义不同类型的目标和时间的推移和技术的关键要求提高的方式中。

度量值是与该指标的目标相比，状态都用颜色编码在结果视图中，如下所示︰

-   浅紫色意味着系统具有出色的用户体验，有没有感觉到的问题。

-   紫色的中等意味着用户体验是容许，可以优化系统。 检查以查看可对系统进行何种改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。

-   深紫色意味着系统有很差的用户体验，并且有重大改进的空间。 检查以查看可对系统进行改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。 您可能需要考虑进行权衡，以便提供 Windows 遇到的高质量。

-   没有颜色的含义有没有定义为度量的目标。

**请注意**  
在 Windows 评估 Toolkit 针对 Windows 8，某些评估包括默认目标文件。 查看使用此版本的工具，结果在第一次使用该默认目标文件。 但是，您还可以定义自定义目标针对 Windows 8 相同的方式，可以为 Windows 8.1 和 Windows 10。

 

您可以设置文件位置的目标并将目标文件添加到该位置之前可用于用户界面应用的自定义目标。 选择目标文件后，它将继续是目标文件，用于打开的任何结果。

可每次只能有一个目标文件。 所有的评估的目标是单个目标文件中设置的。 评估工具将搜索顺序如下目标︰

1.  自定义的目标文件

2.  在结果文件中定义的目标

3.  评估清单中定义的目标

您可以在 %PROGRAMFILES%使用提供了该示例的目标文件\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\SDK\\样本\\目标来创建目标文件。

**请注意**  
不能包装作业的目标文件，但可以将其存储在供其他用户使用共享。

 

## <a name="a-href-idbkmk-metricsametrics"></a><a href="" id="bkmk-metrics"></a>指标


以下度量值是特定于本地视频播放评估︰

### <a name="diagnostic-mode-metrics"></a>诊断模式指标

### <a name="system-timer-resolution"></a>系统计时器分辨率

该指标表示的分辨率，以毫秒为单位的系统计时器。

### <a name="processes-changing-system-timer-resolution"></a>流程更改系统计时器分辨率

该指标表示请求更改系统分辨率的进程数。

### <a name="a-href-idprocesses-using--1--cpu-during-idle-periodaprocesses-using-gt1-cpu-during-idle-period"></a><a href="" id="processes-using--1--cpu-during-idle-period"></a>处理使用&gt;1 %cpu 在空闲期间

该指标表示的进程，但不包括视频播放应用程序中，至少 1%的 CPU 利用率。

### <a name="storage-read-count"></a>读取计数存储

该指标表示运行评估期间存储读取总次数。 这可以通过视频播放应用程序排除存储读取。

### <a name="data-read-from-storage"></a>从存储中读取数据

该指标表示的总大小，以千字节为单位，评估运行期间从存储区读取的数据。 这不包括视频播放应用程序已读取的数据。

### <a name="storage-write-count"></a>存储写入计数

该指标表示存储运行评估过程的写操作的总数。

### <a name="data-written-to-storage"></a>数据写入到存储

该指标表示的总的大小，以千字节为单位，评估运行中写入到存储的数据。

### <a name="storage-flush-count"></a>存储刷新计数

该指标表示运行评估期间存储刷新的总数。

### <a name="a-href-idprocesses-reading---50-timesaprocesses-reading-gt-50-times"></a><a href="" id="processes-reading---50-times"></a>处理读取&gt;50 倍

该指标表示从存储中读取超过 50 次运行评估过程的进程的数。 这不包括视频播放应用程序。

### <a name="a-href-idprocesses-reading---1-mbaprocesses-reading-gt-1-mb"></a><a href="" id="processes-reading---1-mb"></a>处理读取&gt;1 MB

该指标表示运行评估过程从存储中读取超过 1 兆的进程数。 这不包括视频播放应用程序。

### <a name="processes-writing-to-storage"></a>写入存储过程

该指标表示写入存储过程评估运行中的进程数。 这不包括视频播放应用程序。

### <a name="other-metrics"></a>其他指标

### <a name="dflip-used-by-playback"></a>DFlip 使用的播放

该指标表示是否播放媒体文件的全屏模式时启用 DirectFlip。

## <a name="a-href-idbkmk-idleissuesaissues"></a><a href="" id="bkmk-idleissues"></a>问题


本地视频播放评估执行高级的问题分析，并提供到 Windows 性能分析器 (WPA) 标识问题进行故障排除的链接。 WPA 可能存在磁盘活动或根据发现的问题类型的 CPU 活动有关的其他详细信息。 详细信息深入分析有关问题和建议请参阅， [In-Depth 分析的常见问题](common-in-depth-analysis-issues.md)。

下面是运行的本地视频回放评估时可能遇到的问题的列表。

### <a name="directflip-is-not-enabled"></a>未启用 DirectFlip

如果未启用 DirectFlip，生成，重点介绍了在使用 DirectFlip 时可以获得能源效率改进问题。

### <a name="directflip-is-not-supported"></a>不支持 DirectFlip

当显示驱动程序不支持 DirectFlip 时，生成，重点介绍了在使用 DirectFlip 时可以获得能源效率改进的问题。

### <a name="total-storage-write-count"></a>总存储写入计数

问题始终生成用于突出显示的写入存储，以及阈值的总数。 将数据写入到存储增加了能源消耗。

### <a name="total-writes-to-storage"></a>到存储的写入总数

问题始终生成，重点介绍了运行此评估过程中写入到存储的数据的总大小。 将数据写入到存储增加了能源消耗。

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

## <a name="related-topics"></a>相关的主题


[Windows 评估 Toolkit](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

[连接备用能源效率](connected-standby-energy-efficiency.md)

 

 







