---
title: "练习 2-手动收集媒体方案使用 WPR ETW 日志"
description: "自动化的测试是验证对于一个特定的自动化方案; 设备的音频或临时视频质量很好但是，如果手动测试期间出现音频或视频的小故障，然后 Windows 性能记录器 (WPR) 工具可用来手动过程再现此问题收集跟踪 Windows 事件 (ETW) 跟踪。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 89203B18-8C1F-40ED-9DF5-B68F2995BFD9
ms.openlocfilehash: e706f5b2a8de0ebd36c6f0f55549fda35d5bd022
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-2---manually-collect-etw-logs-for-media-scenarios-using-wpr"></a>练习 2-手动收集媒体方案使用 WPR ETW 日志


自动化的测试是验证对于一个特定的自动化方案; 设备的音频或临时视频质量很好但是，如果手动测试期间出现音频或视频的小故障，然后**Windows 性能记录器 (WPR)**工具可用来手动过程再现此问题收集跟踪 Windows 事件 (ETW) 跟踪。

## <a name="step-1-collect-an-etw-trace-using-wpr"></a>步骤 1︰ 收集使用 WPR ETW 跟踪


1.  用鼠标右键单击**开始**菜单，然后单击**命令提示符 （管理员）**。

2.  导航到您有**WPR**安装的文件夹。

3.  运行以下命令︰

    ``` syntax
    wpr -cancel
    ```

4.  运行以下命令︰

    ``` syntax
    wpr -start Media.wprp -filemode
    ```

5.  运行的工作负荷，如视频播放或实时通信方案。

6.  运行以下命令︰

    ``` syntax
    wpr -stop Media.etl
    ```

## <a name="step-2-visualize-the-etw-trace-in-mxa"></a>步骤 2︰ 可视化在 MXA ETW 跟踪


1.  安装**媒体体验分析器 (MXA)**可以下载[这里](https://go.microsoft.com/fwlink/?linkid=525711)。

2.  用鼠标右键单击**开始**菜单，然后单击**命令提示符 （管理员）**。

3.  导航到安装**MXA**位置的文件夹。

4.  运行以下命令︰

    ``` syntax
    xa -i <Media.etl location>\Media.etl
    ```

    例如，如果位于 c: Media.etl\\性能\\介质，可键入下面的命令︰

    ``` syntax
    xa -i C:\Performance\Media\Media.etl
    ```

5.  按**关闭符号**按钮以关闭查找符号。

6.  探索各种媒体相关的数据集和启用跟踪提供程序。

 

 






