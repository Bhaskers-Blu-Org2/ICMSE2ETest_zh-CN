---
title: "调试与备用电源问题"
description: "您在中制定了现代备用系统使用正确的电源管理指南后，您需要测试并验证优化电源平面布置，以提供延长电池寿命，待机。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5A43DECA-DF16-4CE2-BE21-4077D362C8D7
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: dec20d9d8766cf88392796b7234c4eac9d17a6b8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="debugging-power-problems-with-standby"></a>调试与备用电源问题


您在中制定了现代备用系统使用正确的电源管理指南后，您需要测试并验证优化电源平面布置，以提供延长电池寿命，待机。 您可能需要将分解系统隔离电源罪犯。

此实验室提供非常有用的工具，如**SleepStudy**和**WPA**，更深入的了解，并将引导您完成各种案例研究，说明了常见的问题。 包括以下主题︰

-   USB 设备的影响

-   固件问题和缺少约束

-   驱动程序问题

-   识别虚假的唤醒源

## <a name="goals"></a>目标


本指南将向您展示如何执行以下任务︰

-   解释数据从**SleepStudy**报告和**WPA DRIPS**插件

-   识别可能会影响电源平面布置的常见问题

## <a name="terminology"></a>术语


-   **内心最深处的运行时平台空闲状态 (DRIPS)**: 说系统是在系统消耗的电源可能，最低量受系统的电源平面布置时，可**DRIPS** 。 当屏幕被关闭时，在现代的待机状态会话启动和系统经历多个阶段，以进入低功耗状态。 当系统处于低电量状态时，系统将处于**DRIPS**。 系统没有**DRIPS**中时它正在执行任务，例如，接收电子邮件，更新动态图块新鲜的内容，收到 VoIP 呼叫或任何其他需要系统资源的后台任务。 系统处于**DRIPS**屏幕之前更多的时间重新启动，时间越长的电池寿命。

    ``` syntax
    Total standby session time = DRIPS time + non-DRIPS time
    ```

-   **激活器**︰ 软件组件，它们允许执行工作在现代待机状态时的背景。

## <a name="tools"></a>工具


**Windows 性能 Toolkit**包含两个独立的工具︰ **Windows 性能记录器 (WPR)**和**Windows 性能分析器 (WPA)**。 **WPR**是一个功能强大的记录工具，创建跟踪 Windows 事件 (ETW) 录制。 您可以从用户界面 (UI) 或命令行 (CL) 运行**WPR** 。 **WPR**提供内置的配置文件，可以用来选择您想要记录的事件。 **WPA**是一种功能强大的分析工具，结合丰富的图形功能灵活的用户界面和数据表格来可以透视并具有全文搜索功能。

**SleepStudy**是一种 Windows 诊断工具，支持现代待机 （连接或断开连接）。 它监视现代备用电脑行为并提供现代的备用电池寿命可操作诊断。 它是只在现代待机功能电脑上可用。 **SleepStudy**生成摘要会导致较差的现代备用电池寿命的热门问题。

要获得**SleepStudy**报告，请键入下面的命令到管理员命令提示符︰

``` syntax
powercfg.exe /SleepStudy
```

内置的**powercfg.exe**实用程序将创建一个名为 sleepstudy-report.html 的当前工作目录中的 HTML 文件。

**请注意**  
本指南使用预生成**SleepStudy**的报告，使您无需为本指南生成任何**SleepStudy**报告中的所有练习。

 

## <a name="exercises"></a>练习


本指南包括以下练习。

-   [练习 1-识别虚假的唤醒的问题](debugging-problems-with-standby-exercise-1.md)

-   [练习 2-识别缺少驱动程序的问题](debugging-problems-with-standby-exercise-2.md)

-   [练习 3-识别缺少约束的问题](debugging-problems-with-standby-exercise-3.md)

-   [练习 4-识别 USB 设备的问题](debugging-problems-with-standby-exercise-4.md)

 

 






