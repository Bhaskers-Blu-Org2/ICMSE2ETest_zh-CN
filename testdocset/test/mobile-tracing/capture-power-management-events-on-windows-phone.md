---
title: "捕获窗口 10 移动电源管理事件"
description: "捕获窗口 10 移动电源管理事件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 23f40b02-33ec-4a67-8a1c-f036e720c5bf
ms.openlocfilehash: c3e5a9682bd5ef13c4171e9fc16417ed44a8eb78
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="capture-power-management-events-on-windows-10-mobile"></a>捕获窗口 10 移动电源管理事件


Tracelog 和 Xperf 用于捕获 Windows 10 移动电源管理事件跟踪日志。

**重要**  
要捕获跟踪日志，必须使用适当类型和包生成电话图像。 这是通过修改 OEMInput 文件，将**ReleaseType**元素设置为**测试**，并将**TESTINFRASTRUCTURE**添加到**功能**元素。

 

## <a name="step-1-install-the-windows-performance-toolkit"></a>步骤 1︰ 将安装 Windows 性能 Toolkit


Windows 性能 Toolkit (WPT)，则需要使用 Xperf 处理事件跟踪日志。 WPT 是[Windows 评估和部署工具包 (Windows ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526803)的一部分。

## <a name="step-2-install-and-configure-tshell"></a>步骤 2︰ 安装和配置 TShell


TShell 需要运行 Tracelog。

## <a name="step-3-verify-device-is-connected"></a>第 3 步︰ 验证设备已连接


请验证该设备连接到 TShell 通过 TShell 命令窗口中运行命令 dird。 确保已显示目录列表通过电话。 如果出现一条错误消息，确保 TShell 的配置正确、 且设备命令提示上述类似于下面的 TShell 窗口中的常规命令提示符︰

``` syntax
DEVICE C:\
PS C:\>
```

## <a name="step-4-run-tracelog-to-start-power-management-event-trace-logging"></a>步骤 4︰ 运行 Tracelog 启动电源管理事件跟踪日志记录


使用 TShell 命令窗口，运行下面设置推荐的电源管理提供程序与 Tracelog。

**重要**  
在 Windows 10 手机，Tracelog 必须放置在 c︰ 驱动器中的其日志\\由于分区大小限制的数据目录。 请务必使用-f 标志，用于配置要使用 c: Tracelog\\数据。

 

有关详细的 Tracelog 命令行语法，请参阅[Tracelog 命令语法](http://msdn.microsoft.com/library/windows/hardware/ff553012.aspx)。 有关其他示例，请参阅[Tracelog 示例](https://msdn.microsoft.com/library/windows/hardware/ff553026)。

使用以下命令创建一个名为"MyPowerTrace"的会话并启用 Microsoft Windows 内核电源提供。

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

启用附加的电源与管理相关的提供程序，如果需要。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Provider</th>
<th>命令行</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft.Windows.Kernel.Processor.Power</p></td>
<td><p>cmdd ' tracelog-启用 MyPowerTrace-guid #0F67E49F-FE51-4E9F-B490-6F2948CC6027</p></td>
</tr>
<tr class="even">
<td><p>Microsoft.Windows.PDC</p></td>
<td><p>cmdd ' tracelog-启用 MyPowerTrace-guid #A6BF0DEB-3659-40AD-9F81-E25AF62CE3C7</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft.Windows.Kernel.ACPI</p></td>
<td><p>cmdd ' tracelog-启用 MyPowerTrace-guid #C514638F-7723-485B-BCFC-96565D735D4A</p></td>
</tr>
</tbody>
</table>

 

以下命令请求记录状态信息的提供程序。 在开头或结尾的跟踪启动捕获的状态信息。 这将确保确定跟踪在特定时刻的状态所需的信息将记录。

``` syntax
cmdd 'tracelog -capturestate MyPowerTrace -guid #331C3B3A-2005-44C2-AC5E-77220C37D6B4'
```

## <a name="step-5-run-scenarios-or-tests"></a>步骤 5︰ 运行方案或测试


事件跟踪日志记录现已启用。 方案或您要分析的测试运行。

## <a name="step-6-run-tracelog-to-flush-the-buffers-and-stop-event-trace-logging"></a>第 6 步︰ 运行 Tracelog 刷新缓冲区和停止事件跟踪日志记录


方案或测试完成后，使用 Tracelog 刷新缓冲区和停止事件跟踪日志记录。

``` syntax
cmdd 'tracelog -flush MyPowerTrace'
cmdd 'tracelog -stop MyPowerTrace'
```

## <a name="step-7-run-xperf-on-the-device"></a>第 7 步︰ 运行 Xperf 设备上


处理日志的设备上运行 Xperf。

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
PS C:\> getd C:\data\MyPowerLogOut.etl C:\Users\username\Documents\NewName.etl
C:\data\MyPowerLogOut.etl
1 file(s) copied from device.
DEVICE C:\
PS C:\>
```

## <a name="step-9-run-xperf-on-the-pc"></a>步骤 9︰ 在 PC 上运行 Xperf


在执行其他处理 PC 上运行 Xperf。 在 32 位操作系统，Xperf 安装在 c:\\程序文件\\窗口工具包\\10\\Windows 性能 Toolkit。 在 64 位操作系统，它将安装在 c:\\程序文件 (x86)\\窗口工具包\\10\\Windows 性能 Toolkit。

``` syntax
C:\>cd Users\username\Documents
C:\Users\username\Documents>xperf -i MyPowerLogOut.etl -o MyPowerLogCSV.csv -tle
[1/2]    100.0%
[2/2]    100.0%

C:\Users\username\Documents>
```

 

 






