---
title: "开始录制"
description: "开始录制"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a873691c-d198-4131-aa5d-849b4c6159d7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: c5fc78b926e184cf0bf189ee9bec9264fa7e41f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="start-a-recording"></a>开始录制


本过程描述了如何从用户界面 (UI) 启动 Windows 性能记录器 (WPR) 录制。 有关如何从命令行启动录制的信息，请参阅[WPR 命令行选项](wpr-command-line-options.md)。

WPR 要求 Windows 7 或更高版本的操作系统。

**若要开始录制**

1.  在**启动**屏幕上，单击**Windows 性能记录器**。

2.  要运行的默认配置文件，请单击**开始**。 或者，要查看和使用其他配置文件，请单击**多个选项**。

    1.  在**选择性能录制的配置文件**框中，选择至少一个配置文件。

    2.  您可以选择添加自定义配置文件。 若要执行此操作，单击**添加配置文件**，导航到所需的配置文件，然后单击**打开**。 在**自定义度量值**，选择配置文件。

    3.  从**性能情况**下拉列表中，选择所需的方案。 除非录制开/关方案中，选择**常规**。

    4.  （可选） 可以记录在浅的明细数据级别。 （**详细**是 default.level）。若要执行此操作，选择**详细级别**下拉列表中的**光**。

    5.  若要录制记录到一个文件中，请**登录模式**下拉列表中选择**文件**。 **内存**是默认日志记录模式中，除关闭事务日志，必须记录到文件中。

        **警告︰**  
        更长的时间录制，请选择**内存**。 选择**文件**时，文件可以增长非常大，因为唯一的文件大小限制为可用的磁盘空间。 Windows 性能分析器 (WPA) 无法分析极大的文件。

         

3.  单击**开始**以开始录制，或单击**取消**以结束不录制。

**请注意**  
如果在另一个应用程序记录 （如 Xperf 或使用 NT 内核记录器，如 logman 或 PerfTrace 的应用程序） 启动 WPR，WPR 将无法立即检测到录制正在进行，它最初将显示一条消息记录尚未启动。 但是，如果您尝试启动另一个应用程序正在录制期间 WPR 录制，WPR 会检测到冲突并提示您使用以下查询︰

`An existing session is already running. Click OK to stop the running session and start the selected profile(s) or Cancel to abort the operation.`

若要停止当前会话，请单击**确定**。 WPR 将开始记录。 请注意，此操作可能会影响启动取消的会话的应用程序。 要允许当前会话永久地继续，请单击**取消**。 在这种情况下，WPR 不开始录制和其他应用程序不受影响。

 

## <a name="related-topics"></a>相关的主题


[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

[对于基本系统诊断的录制](recording-for-basic-system-diagnosis.md)

 

 







