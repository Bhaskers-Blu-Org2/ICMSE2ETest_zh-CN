---
title: "故障诊断评估"
description: "故障诊断评估"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: c0ab73ed-ba51-45f7-b498-916f2492154f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: b4a85e0463bd1a0f8b2985ef9cc231824c0672a0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="troubleshooting-assessments"></a>故障诊断评估


以下信息可以帮助您诊断评估失败的原因。

## <a name="assessment-didnt-produce-any-results"></a>评估没有产生任何结果


如果您收到一条错误消息，并且评估没有产生任何结果，请使用此方法来查看日志文件︰

-   在 Windows 评估控制台中，在**查看结果**页中，选择**错误总数**，然后再展开右侧详细信息窗格中显示的错误。

-   选择下**进一步分析**，以打开存储日志文件的文件夹的链接。 该文件夹包含 AxeLog.etl 跟踪文件，您可以打开 Windows 性能分析器 (WPA)。 该文件夹还包含 ErrorWarnings.xml 文件和 AXELog.txt 文件。 文本文件是所有作业完成后所生成的事件跟踪日志 (ETL) 文件的编译。

## <a name="the-assessment-fails-to-complete"></a>评估未完成


作业完成，但不能运行评估。 通过评估可能报告以下错误代码之一︰

-   0x80050006

-   0x80004005

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    **rundll32.exe advapi32.dll,ProcessIdleTasks**

2.  禁用定期和空闲状态维护任务，并停止所有的维护任务，然后运行评估

## <a name="related-topics"></a>相关的主题


[Windows 评估 Toolkit](windows-assessment-toolkit-technical-reference.md)

 

 







