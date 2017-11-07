---
title: "练习 1-评估设备的音频延迟性能对于通信方案"
description: "在本练习中，我们将运行生成延迟方面的各种支持 Windows 的滞后时间模式的统计数字的音频延迟测试以下矩阵。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2264F1B3-27BC-4140-9A90-0532604298BC
ms.openlocfilehash: d76311bb2fa0873883764bb6e23e357709c14f9e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="exercise-1---assess-the-devices-audio-latency-performance-for-communications-scenarios"></a>练习 1-评估设备的音频延迟性能对于通信方案


在本练习中，我们将运行生成延迟方面的各种支持 Windows 的滞后时间模式的统计数字的音频延迟测试以下矩阵。 可以在运行测试的模式包括︰

-   默认模式 – 生成默认的瓜音频延迟。

-   Raw 模式 – 删除音频处理对象 （本地）。

-   低段 – 新的接近实时的情况下，如 Skype 的低滞后时间模式。

测试呈现被麦克风捕获的测试声音。

**请注意** 本分步指南也是可查看视频频道 9，功能的开发人员能够构建 Microsoft 产品和服务的人员从视频上的实验室为︰ <https://channel9.msdn.com/Events/WinHEC/2015/OWDHOL301>

 

## <a name="step-1-prepare-the-system-to-run-the-tests"></a>第 1 步︰ 准备系统来运行测试


1.  安装硬件实验室工具包 (HLK) 控制器。

2.  用鼠标右键单击**开始**菜单，然后单击**命令提示符 （管理员）**。

3.  定位到**\\ \\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\TE**文件夹。

4.  将下面的测试和诊断工具从硬件实验室工具包 (HLK) 控制器复制到测试计算机中︰ c:\\性能\\媒体
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\nttest\\multimediatest\\wmmftest\\glitchfreetaeftests.dll
    -   \\\\&lt;控制器名称&gt;\\TaefBinaries\\&lt;处理器体系结构&gt;\\\*
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\性能\\WindowsXRay\\工具\\EtwPattern.dll
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\测试\\MediaEngineTest.exe
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\音频测试\\bin\\audiospew.exe
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\音频测试\\bin\\audiostreaming.dll
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\nttest\\multimediatest\\wmmftest\\rws.exe
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\nttest\\multimediatest\\wmmftest\\stress.xml-音频-保真度
    -   \\\\&lt;控制器名称&gt;\\测试\\&lt;处理器体系结构&gt;\\音频测试\\bin\\LatencyTest.dll

5.  设置 100%到扬声器的音量。

## <a name="step-2-run-the-test-in-default-mode"></a>步骤 2︰ 在默认模式下运行测试


1.  运行以下命令︰

    ``` syntax
    te.exe latencytest.dll /name:LatencyTest::Vanilla
    ```

2.  查看**平均值**、**最大**和**最小**延迟值发送到命令提示符窗口。

## <a name="step-3-run-the-test-in-raw-mode"></a>步骤 3︰ 在原始模式中运行测试


1.  运行以下命令︰

    ``` syntax
    te.exe latencytest.dll /name:LatencyTest::Raw
    ```

2.  查看**平均值**、**最大**和**最小**延迟值发送到命令提示符窗口。

## <a name="step-4-run-the-test-in-low-latency-mode"></a>步骤 4︰ 在低滞后时间模式下运行测试


1.  运行以下命令︰

    ``` syntax
    te.exe latencytest.dll /name:LatencyTest::LowPeriod
    ```

2.  查看**平均值**、**最大**和**最小**延迟值发送到命令提示符窗口。

 

 






