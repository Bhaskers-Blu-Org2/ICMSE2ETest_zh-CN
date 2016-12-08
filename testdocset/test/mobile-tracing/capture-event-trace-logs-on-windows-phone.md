---
title: "捕获窗口 10 移动上的事件跟踪日志"
description: "捕获窗口 10 移动上的事件跟踪日志"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5a4a7408-3dd8-4322-91ce-73ab75135470
ms.openlocfilehash: 5d91f2a45bb48a4c7eb0cdff71ea5bff15edb39e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-event-trace-logs-on-windows-10-mobile"></a>捕获窗口 10 移动上的事件跟踪日志


Tracelog 和 Xperf 用于捕获 Windows 10 移动上的事件跟踪日志。

**重要**  
要捕获跟踪日志，必须使用适当类型和包生成设备图像。 这是通过修改 OEMInput 文件，将**ReleaseType**元素设置为**测试**，并将**TESTINFRASTRUCTURE**添加到**功能**元素。

 

## <a name="step-1-install-the-windows-performance-toolkit"></a>步骤 1︰ 将安装 Windows 性能 Toolkit


Windows 性能 Toolkit (WPT)，则需要使用 Xperf 处理事件跟踪日志。 WPT 是[Windows 评估和部署工具包 (Windows ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526803)的一部分。

## <a name="step-2-install-and-configure-tshell"></a>步骤 2︰ 安装和配置 TShell


TShell 需要运行 Tracelog。

## <a name="step-3-verify-device-is-connected"></a>第 3 步︰ 验证设备已连接


请验证该设备连接到 TShell 通过 TShell 命令窗口中运行命令 dird。 确保目录从设备列表已显示。 如果出现一条错误消息，确保 TShell 配置正确，并且设备命令提示上述类似于下面的 TShell 窗口中的常规命令提示符︰

``` syntax
DEVICE C:\
PS C:\>
```

## <a name="step-4-run-tracelog-to-start-event-trace-logging"></a>步骤 4︰ 运行 Tracelog 来启动事件跟踪日志记录


使用 TShell 命令窗口，运行所需的参数来启动事件跟踪日志记录 Tracelog。 两个基本示例如下。

**重要**  
在 Windows 10 手机，Tracelog 必须放置在 c︰ 驱动器中的其日志\\由于分区大小限制的数据目录。 请务必使用-f 标志，用于配置要使用 c: Tracelog\\数据。

 

有关详细的 Tracelog 命令行语法，请参阅[Tracelog 命令语法](http://msdn.microsoft.com/library/windows/hardware/ff553012.aspx)。 有关其他示例，请参阅[Tracelog 示例](http://msdn.microsoft.com/library/windows/hardware/ff553026.aspx)。

### <a name="example-1"></a>示例 1

下面的命令启动的会话，则启用跟踪的进程和线程创建/删除操作、 内核和用户模式下图像加载/卸载事件、 DPC 事件、 上下文切换和 CPU 的示例配置文件。

``` syntax
DEVICE C:\
PS C:\> cdd data
DEVICE C:\data
PS C:\> cmdd 'tracelog -start MyTrace -f c:\data\MyLog.etl -eflag PROC_THREAD+LOADER+DPC+CSWITCH+PROFILE'

Turning On group: PROC_THREAD
Turning On group: LOADER
Turning On group: DPC
Turning On group: CSWITCH
Turning On group: PROFILE
Adding GroupMask ExtItem
Logger Started...
Operation Status:       0L      The operation completed successfully.

Logger Name:            MyTrace
Logger Id:              0x14
Logger Thread Id:       0000054C
Guid:                   77eaa944-426b-11e1-86a3-fb317490c92a
Session Security:       D:(A;;0x800;;;WD)
Buffer Size:            8 Kb
Maximum Buffers:        26
Minimum Buffers:        4
Number of Buffers:      26
Free Buffers:           0
Buffers Written:        28
Events Lost:            177
Log Buffers Lost:       0
Real Time Buffers Lost: 0
AgeLimit:               0
Real Time Consumers:    0
ClockType:              PerfCounter
Log Mode:               Sequential
Hybrid Shutdown:        Persist
Maximum File Size:      not set
Buffer Flush Timer:     not set
Enabled tracing:        Process Thread ImageLoad CxtSwap Dpc Profile
Log Filename:           c:\data\MyLog.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

### <a name="example-2"></a>示例 2

下面的命令启动一个名为"MyPowerTrace"的新会话并启用 Microsoft Windows 内核电源提供程序。

``` syntax
DEVICE C:\
PS C:\> cdd data
DEVICE C:\data
PS C:\> cmdd 'tracelog -start MyPowerTrace -b 1024 -f C:\data\MyPowerLog.etl -eflags Process'
Turning On group: PROCESS
Adding GroupMask ExtItem
Logger Started...
Operation Status:       0L      The operation completed successfully.

Logger Name:            MyPowerTrace
Logger Id:              0x1d
Logger Thread Id:       00000C38
Guid:                   52dd9cee-926c-11e1-bc7e-0011beb0dbf4
Session Security:       D:(A;;0x800;;;WD)
Buffer Size:            1024 Kb
Maximum Buffers:        26
Minimum Buffers:        4
Number of Buffers:      4
Free Buffers:           3
Buffers Written:        1
Events Lost:            0
Log Buffers Lost:       0
Real Time Buffers Lost: 0
AgeLimit:               0
Real Time Consumers:    0
ClockType:              PerfCounter
Log Mode:               Sequential
Hybrid Shutdown:        Persist
Maximum File Size:      not set
Buffer Flush Timer:     not set
Enabled tracing:        Process
Log Filename:           C:\data\MyPowerLog.etl

Exit Code : 0

DEVICE C:\data
PS C:\> cmdd 'tracelog -enable MyPowerTrace -guid #331C3B3A-2005-44C2-AC5E-77220C37D6B4'
Enabling 331c3b3a-2005-44c2-ac5e-77220c37d6b4 (Flags = 0x00000000 Level = 0  ) to logger 29
Operation Status:       0L      The operation completed successfully.

Logger Name:            MyPowerTrace
Logger Id:              0x1d
Logger Thread Id:       00000C38
Guid:                   52dd9cee-926c-11e1-bc7e-0011beb0dbf4
Session Security:       D:(A;;0x800;;;WD)
Buffer Size:            1024 Kb
Maximum Buffers:        26
Minimum Buffers:        4
Number of Buffers:      4
Free Buffers:           2
Buffers Written:        1
Events Lost:            0
Log Buffers Lost:       0
Real Time Buffers Lost: 0
AgeLimit:               0
Real Time Consumers:    0
ClockType:              PerfCounter
Log Mode:               Sequential
Hybrid Shutdown:        Persist
Maximum File Size:      not set
Buffer Flush Timer:     not set
Enabled tracing:        Process
Log Filename:           C:\data\MyPowerLog.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

## <a name="step-5-run-scenarios-or-tests"></a>步骤 5︰ 运行方案或测试


事件跟踪日志记录现已启用。 方案或您要分析的测试运行。

## <a name="step-6-run-tracelog-to-flush-the-buffers-and-stop-event-trace-logging"></a>第 6 步︰ 运行 Tracelog 刷新缓冲区和停止事件跟踪日志记录


方案或测试完成后，使用 Tracelog 刷新缓冲区和停止事件跟踪日志记录。

### <a name="example-1"></a>示例 1

下面的命令将刷新并停止"MyTrace"会话。

``` syntax
cmdd 'tracelog -flush MyTrace'
cmdd 'tracelog -stop MyTrace'
```

### <a name="example-2"></a>示例 2

下面的命令将刷新并停止"MyPowerTrace"会话。

``` syntax
cmdd 'tracelog -flush MyPowerTrace'
cmdd 'tracelog -stop MyPowerTrace'
```

## <a name="step-7-run-xperf-on-the-device"></a>第 7 步︰ 运行 Xperf 设备上


处理日志的设备上运行 Xperf。

### <a name="example-1"></a>示例 1

``` syntax
DEVICE C:\data
PS C:\> cmdd 'xperf -merge MyLog.etl c:\data\MyLogOut.etl'
Merged Etl: c:\data\MyLogOut.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

### <a name="example-2"></a>示例 2

``` syntax
DEVICE C:\data
PS C:\> cmdd 'xperf -merge MyPowerLog.etl c:\data\MyPowerLogOut.etl'
Merged Etl: c:\data\MyPowerLogOut.etl

Exit Code : 0

DEVICE C:\data
PS C:\>
```

## <a name="step-8-copy-trace-log-from-device"></a>步骤 8︰ 将跟踪日志从设备复制


通过 TShell 命令窗口中使用**getd**命令通过电话来复制合并的跟踪日志。

### <a name="example-1"></a>示例 1

``` syntax
DEVICE C:\data
PS C:\> getd MyLogOut.etl C:\Users\username\Documents
C:\data\MyLogOut.etl
1 file(s) copied from device.
DEVICE C:\data
PS C:\>
```

### <a name="example-2"></a>示例 2

``` syntax
DEVICE C:\data
PS C:\> getd MyPowerLogOut.etl C:\Users\username\Documents
C:\data\MyPowerLogOut.etl
1 file(s) copied from device.
DEVICE C:\data
PS C:\>
```

您还可以在复制时重命名文件。

``` syntax
DEVICE C:\
PS C:\> cdd data
DEVICE C:\
PS C:\> getd C:\data\MyPowerLogOut.etl C:\Users\username\Documents\NewName.etl
C:\data\MyPowerLogOut.etl
1 file(s) copied from device.
DEVICE C:\
PS C:\>
```

## <a name="step-9-run-xperf-on-the-desktop-pc"></a>步骤 9︰ 运行 Xperf 在桌面 PC 上


运行在桌面 PC 上执行其他处理 Xperf。 在 32 位操作系统，Xperf 安装在 c:\\程序文件\\窗口工具包\\10\\Windows 性能 Toolkit。 在 64 位操作系统，它将安装在 c:\\程序文件 (x86)\\窗口工具包\\10\\Windows 性能 Toolkit。

### <a name="example-1"></a>示例 1

``` syntax
C:\>cd Users\username\Documents
C:\Users\username\Documents>xperf -i d:\MyLogOut.etl -o MyLogCSV.csv -tle
[1/2]    100.0%
[2/2]    100.0%

C:\Users\username\Documents>
```

### <a name="example-2"></a>示例 2

``` syntax
C:\>cd Users\username\Documents
C:\Users\username\Documents>xperf -i MyPowerLogOut.etl -o MyPowerLogCSV.csv -tle 
[1/2]    100.0%
[2/2]    100.0%

C:\Users\username\Documents>
```

 

 






