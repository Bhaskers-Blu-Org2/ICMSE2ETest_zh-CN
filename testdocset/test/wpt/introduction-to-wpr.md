---
title: "WPR 简介"
description: "WPR 简介"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f2d73e54-da70-42d6-80c6-6ff22983ea9f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: b48705a3de80347234fea16d7b2b1d28af593338
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="introduction-to-wpr"></a>WPR 简介


Windows 性能记录器 (WPR) 是一个工具，扩大了事件跟踪 Windows (ETW) 也提供了系统和应用程序行为和资源使用情况的详细的记录。 您可以使用 WPR 以及 Windows 性能分析器 (WPA) 调查特定方面的性能和资源消耗的总体理解。 WPR 和 WPA 实现开发和 IT 专业人员能够主动识别并解决性能问题。 WPR 要求 Windows 7 或更高版本的操作系统。

## <a name="wpr-user-interface"></a>WPR 用户界面


WPR 用户界面 (UI) 还能轻松地生成录制使用内置录音配置文件分析 CPU 使用率、 电源问题、 很差的系统或应用程序性能或其他性能问题。

## <a name="authoring-custom-recording-profiles"></a>创作自定义录制配置文件


可以创作自定义配置文件的 XML 并将其添加到 WPR。 单独或与内置的配置文件或使专门的录制的任何用法方案设计时，可以使用自定义配置文件。

## <a name="logging-to-file-or-memory"></a>文件或内存中的日志记录


WPR 可以记录事件到一个文件或内存中的循环缓冲区。 我们建议您记录到文件，以便可以预测，如应用程序启动或电源的使用当计算机从休眠状态中出现的有限的事件。 文件记录是唯一可用来测量开/关切换至事件的日志记录模式。

我们建议您登录到内存不可预知的事件。 而无需占用有限的内存资源，可以很长一段时间的运行这些唱片。

## <a name="detail-level"></a>详细信息级别


您可以选择适合该方案的详细级别︰ 浅或详细。 浅录制执行开销更少，且干扰就越 （有时称它们为"排练时间"录制） 系统。 详细的录制很透彻的分析更有用。

## <a name="related-topics"></a>相关的主题


[Windows 性能记录器](windows-performance-recorder.md)

[WPR 快速入门](wpr-quick-start.md)

 

 







