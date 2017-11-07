---
author: Justinha
Description: "Windows 安装程序日志文件和事件日志"
ms.assetid: f3f32c6c-c1f9-4b85-ba0f-1e2a0b07c50f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序日志文件和事件日志"
ms.openlocfilehash: e0c24f990683c7a85412759b959ff3e48cba2e69
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-log-files-and-event-logs"></a>Windows 安装程序日志文件和事件日志


Windows® 安装程序会创建在安装过程中发生的所有操作的日志文件。 如果遇到安装 Windows 时出现问题，请查阅日志文件来解决安装问题。

Windows 安装程序日志文件位于以下目录︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">日志文件的位置</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>$windows.~bt\Sources\Panther</p></td>
<td align="left"><p>安装程序可以访问驱动器之前，日志位置。</p></td>
</tr>
<tr class="even">
<td align="left"><p>$windows.~bt\Sources\Rollback</p></td>
<td align="left"><p>日志位置时出现致命错误时回滚安装。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>%WINDIR%\Panther</p></td>
<td align="left"><p>磁盘配置完成之后安装操作的日志位置。</p></td>
</tr>
<tr class="even">
<td align="left"><p>%WINDIR%\Inf\Setupapi*.log</p></td>
<td align="left"><p>用于记录插设备安装。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>%WINDIR%\Memory.dmp</p></td>
<td align="left"><p>来自错误检查的内存转储的位置。</p></td>
</tr>
<tr class="even">
<td align="left"><p>%WINDIR%\Minidump\*.dmp</p></td>
<td align="left"><p>检查来自错误日志小型转储的位置。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>%WINDIR%\System32\Sysprep\Panther</p></td>
<td align="left"><p>Sysprep 日志的位置。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idwindowssetupeventlogsspanspan-idwindowssetupeventlogsspanspan-idwindowssetupeventlogsspanwindows-setup-event-logs"></a><span id="Windows_Setup_Event_Logs"></span><span id="windows_setup_event_logs"></span><span id="WINDOWS_SETUP_EVENT_LOGS"></span>Windows 安装程序的事件日志


Windows 安装程序包括查阅 Windows 事件日志查看器中的 Windows 安装程序性能事件的能力。 这使您可以更轻松地查看 Windows 安装过程中发生的操作，并查看性能统计信息的 Windows 安装程序的不同部分。 您可以筛选日志，以便只查看相关项目感兴趣。 Windows 安装程序性能事件保存到名为 Setup.etl，可在 %WINDIR%日志文件\\黑豹的所有安装的目录。 若要查看的日志，必须使用事件查看器包含在正在生成的自定义图像的版本对应的 Windows 媒体。

不包括相应的包的计算机上查看的日志，您必须从媒体安装 Windows 事件跟踪 (ETW) 提供程序的根中运行脚本。 从命令行，请键入︰

``` syntax
Cscript D:\sources\etwproviders\etwproviderinstall.vbs install D:\sources\etwproviders
```

其中*D*是 Windows DVD 介质的驱动器号。

### <a name="span-idtoviewthewindowssetupeventlogsspanspan-idtoviewthewindowssetupeventlogsspanspan-idtoviewthewindowssetupeventlogsspanto-view-the-windows-setup-event-logs"></a><span id="To_view_the_Windows_Setup_event_logs"></span><span id="to_view_the_windows_setup_event_logs"></span><span id="TO_VIEW_THE_WINDOWS_SETUP_EVENT_LOGS"></span>若要查看 Windows 安装程序的事件日志

1.  启动事件查看器，展开 Windows 日志节点，然后单击**系统**。

2.  在**操作**窗格中单击**打开保存的日志**，然后找到 Setup.etl 文件。 默认情况下，此文件是在 %WINDIR%\\黑豹目录。

3.  日志文件内容将显示在事件查看器。

### <a name="span-idtoexportthelogtoafilespanspan-idtoexportthelogtoafilespanspan-idtoexportthelogtoafilespanto-export-the-log-to-a-file"></a><span id="To_Export_the_log_to_a_file"></span><span id="to_export_the_log_to_a_file"></span><span id="TO_EXPORT_THE_LOG_TO_A_FILE"></span>若要将日志导出到文件

从命令行使用**Wevtutil**或**Tracerpt**命令将日志保存到一个.xml 或文本的文件。 有关如何使用这些工具的信息，请参阅命令行帮助。 以下命令显示如何使用工具的示例︰

``` syntax
Wevtutil qe /lf C:\windows\panther\setup.etl 
```

-或者-

``` syntax
Tracerpt /l C:\windows\panther\setup.etl
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序命令行选项](windows-setup-command-line-options.md)

[Windows 安装程序状态](windows-setup-states.md)

[Windows 安装程序版本配置和产品 ID 文件 （EI.cfg 和 PID.txt）](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md)

 

 






