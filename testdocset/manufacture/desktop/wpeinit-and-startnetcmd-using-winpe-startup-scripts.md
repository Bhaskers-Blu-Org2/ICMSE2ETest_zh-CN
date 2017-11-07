---
author: Justinha
Description: "Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本"
ms.assetid: d43621bb-b9ab-4e19-8fb4-8d05d5ee3d07
MSHAttr: PreferredLib:/library/windows/hardware
title: "Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本"
ms.openlocfilehash: c1071e6ddcdb51f1506bda8f4927eb0e78cd9f1b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpeinit-and-startnetcmd-using-winpe-startup-scripts"></a>Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本


使用 Wpeinit 和 Startnet.cmd 在 Windows PE (WinPE) 第一次运行时运行启动脚本。

Wpeinit 输出记录到消息**c:\\Windows\\system32\\wpeinit.log**。

## <a name="span-idstartnetcmdspanspan-idstartnetcmdspanstartnetcmd"></a><span id="startnet.cmd"></span><span id="STARTNET.CMD"></span>Startnet.cmd


通过使用 Startnet.cmd，可以在 Windows PE 添加自定义命令行脚本。 默认情况下，Windows PE 包括 Startnet.cmd 脚本在 %SYSTEMROOT%位于\\的自定义 Windows PE 映像 System32。

Startnet.cmd 将启动 Wpeinit.exe。 Wpeinit.exe 安装插设备、 处理 Unattend.xml 设置并加载网络资源。

有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

## <a name="span-idwpeinitcommand-lineoptionsspanspan-idwpeinitcommand-lineoptionsspanspan-idwpeinitcommand-lineoptionsspanwpeinit-command-line-options"></a><span id="Wpeinit_Command-Line_Options"></span><span id="wpeinit_command-line_options"></span><span id="WPEINIT_COMMAND-LINE_OPTIONS"></span>Wpeinit 命令行选项


下面的命令行选项是可用的 Wpeinit:

**Wpeinit**\[-无人参与的︰*&lt;路径\_到\_答案\_文件&gt;*\]

示例：

``` syntax
Wpeinit -unattend:"C:\Unattend-PE.xml"
```

## <a name="span-idsupportedunattendsettingsspanspan-idsupportedunattendsettingsspanspan-idsupportedunattendsettingsspansupported-unattend-settings"></a><span id="Supported_Unattend_settings"></span><span id="supported_unattend_settings"></span><span id="SUPPORTED_UNATTEND_SETTINGS"></span>支持无人参与设置


可以创建一个应答文件和包含所有使用 Windows PE 的以下设置︰

-   Microsoft Windows 安装程序 /[显示](https://msdn.microsoft.com/library/windows/hardware/dn915285)

-   Microsoft Windows 安装程序 /[EnableFirewall](https://msdn.microsoft.com/library/windows/hardware/dn915375)

-   Microsoft Windows 安装程序 /[EnableNetwork](https://msdn.microsoft.com/library/windows/hardware/dn915383)

-   Microsoft Windows 安装程序 /[LogPath](https://msdn.microsoft.com/library/windows/hardware/dn915490)

-   Microsoft Windows 安装程序 /[页面文件](https://msdn.microsoft.com/library/windows/hardware/dn915671)

-   Microsoft Windows 安装 /[重新启动](https://msdn.microsoft.com/library/windows/hardware/dn915783)

-   Microsoft Windows 安装程序 /[RunAsynchronous](https://msdn.microsoft.com/library/windows/hardware/dn915800)

-   Microsoft Windows 安装程序 /[RunSynchronous](https://msdn.microsoft.com/library/windows/hardware/dn915804)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[WinPE︰ 使用脚本确定驱动器号](winpe-identify-drive-letters.md)

[对于 Windows 10 WinPE](winpe-intro.md)

[Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序](winpeshlini-reference-launching-an-app-when-winpe-starts.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)

 

 






