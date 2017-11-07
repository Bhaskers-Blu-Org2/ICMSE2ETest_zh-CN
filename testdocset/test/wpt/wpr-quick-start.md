---
title: "WPR 快速入门"
description: "WPR 快速入门"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bb93222f-a938-45a9-8fd7-0a1eb254537c
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 67c403094110d8cd858a7c36812600670662fc3d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpr-quick-start"></a>WPR 快速入门


本文总结了在 Windows 性能记录器 (WPR) 用户界面 (UI) 中可用的功能。

**请注意**  
您还可以运行 WPR 从命令行;有关该选项的信息，请参阅[WPR 命令行选项](http://go.microsoft.com/fwlink/p/?linkid=223233)。

 

**在这篇文章︰**

-   [通过使用 WPR 默认设置录制](#default)

-   [使用配置文件记录](#profiles)

-   [使用性能的方案](#perf)

-   [使用明细级别](#detail)

-   [使用日志记录模式](#logmode)

## <a name="a-href-iddefaultarecording-by-using-the-wpr-default-settings"></a><a href="" id="default"></a>通过使用 WPR 默认设置录制


在**启动**屏幕上，单击**Windows 性能记录器**打开 WPR 用户界面。 在 WPR，单击**开始**使用**通用**配置文件的默认设置录制系统的性能。

有关此功能的详细信息，请参阅[开始录制](http://go.microsoft.com/fwlink/?LinkId=249060)和[记录进行基本的系统诊断](http://go.microsoft.com/fwlink/?LinkId=249061)。

## <a name="a-href-idprofilesausing-recording-profiles"></a><a href="" id="profiles"></a>使用配置文件记录


WPR 录制配置文件包含所有需要启用记录特定方案的性能的信息。 您可以在单个记录中包含多个配置文件。

关于 WPR 配置文件的一般信息，请参阅[记录配置文件](http://go.microsoft.com/fwlink/?LinkId=249062)。

WPR 提供各种可供选择的内置录制按功能分类到组的配置文件。 关于 WPR 内置配置文件的详细信息，请参阅[内置录音配置文件](http://go.microsoft.com/fwlink/?LinkId=249063)和[选择内置的配置文件](http://go.microsoft.com/fwlink/?LinkId=249064)。

您还可以创作，并将自定义配置文件 （.wprp 文件） 添加到记录集的事件。 有关自定义配置文件的详细信息，请参阅[创作录制配置文件](http://go.microsoft.com/fwlink/p/?linkid=223238)和[添加或删除自定义录制配置文件](http://go.microsoft.com/fwlink/?LinkId=249068)。

## <a name="a-href-idperfausing-performance-scenarios"></a><a href="" id="perf"></a>使用性能的方案


可以使用性能方案记录如开/关切换或堆分析的常见方案。 您可以选择录制的只有一个方案。 有关性能的方案的详细信息，请参阅[WPR 方案](http://go.microsoft.com/fwlink/p/?linkid=223244)和[更改性能的方案](http://go.microsoft.com/fwlink/?LinkId=249066)。

## <a name="a-href-iddetailausing-detail-levels"></a><a href="" id="detail"></a>使用明细级别


您可以选择每个记录的明细数据级别。 可用的级别是**光**和**详细**。 **光**详细程度主要用于计时的录制。 **详细**详细程度提供了进行分析所需的详细的信息。 有关的详细信息级别的详细信息，请参阅[详细信息级别](http://go.microsoft.com/fwlink/?LinkId=249070)，[更改详细信息级别](http://go.microsoft.com/fwlink/?LinkId=249069)。

## <a name="a-href-idlogmodeaselecting-a-logging-mode"></a><a href="" id="logmode"></a>选择一种日志记录模式


WPR 可以记录事件到顺序文件或内存中的循环缓冲区。 日志记录到一个文件用于短的跟踪，当您知道预期要跟踪的事件。 日志记录到内存用于连续跟踪，当您想要记录可以在任何时间发生的事件。 一般情况下可以使用这两种类型的日志记录。 但是，关闭过渡只能使用文件记录。

有关日志记录模式的详细信息，请参阅[模式的日志记录](http://go.microsoft.com/fwlink/?LinkId=249071)和[更改日志记录模式](http://go.microsoft.com/fwlink/?LinkId=249072)。

## <a name="related-topics"></a>相关的主题


[WPR 简介](introduction-to-wpr.md)

[WPR 功能](http://go.microsoft.com/fwlink/p/?linkid=223236)

[WPR 帮助主题](http://go.microsoft.com/fwlink/p/?linkid=223237)

[WPR 引用](http://go.microsoft.com/fwlink/p/?linkid=223245)

 

 







