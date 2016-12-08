---
title: "录制的堆分析"
description: "录制的堆分析"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9acc8558-67ef-471a-af69-1173cb49bdb4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 7d25f9dc4f7a467558aac20da83f5aeb7a5662d1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="recording-for-heap-analysis"></a>录制的堆分析


Windows 性能记录器 (WPR) 使堆分析系统上的所有进程。

**若要启用桌面应用程序的堆跟踪**

1.  从**更多选项**下拉菜单中，选择**堆使用率**配置文件。

2.  通过从提升的命令提示符窗口中，运行以下命令添加注册表项的进程替换*&lt;进程\_名称&gt;*要跟踪的过程的名称︰

    **reg 添加"HKLM\\软件\\Microsoft\\Windows NT\\CurrentVersion\\图像文件执行选项\\&lt;进程\_名称&gt;"/v TracingFlags /t REG\_dword 值 /d 1 /f**

**若要启用 Windows 应用商店应用程序的堆跟踪**

1.  从**更多选项**下拉菜单中，选择**堆使用率**配置文件。

2.  如果您想要跟踪的打包的应用程序承载于进程 （如 WWAHost.exe)，通过从提升的命令提示符窗口中，运行以下命令添加注册表项的进程替换*&lt;进程\_名称&gt;*，*&lt;软件包全名&gt;*，和*&lt;包相关的应用程序 ID&gt;*与您的应用程序信息︰

    **reg 添加"HKLM\\软件\\Microsoft\\Windows NT\\CurrentVersion\\图像文件执行选项\\&lt;进程\_名称&gt;\\&lt;软件包全名&gt;！&lt;包相关的应用程序 ID&gt;"/v TracingFlags /t REG\_dword 值 /d 1 /f**

    **请注意**  
    这种组合 （全名包 + 应用程序 ID） 不是应用程序用户模型 ID （包系列名称 + 应用程序 ID）。 IFEO 处理例程使用完整的名称，以便它们可以将不同的行为应用于单个的包/应用程序的不同版本。

     

## <a name="related-topics"></a>相关的主题


[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

[图像文件的执行选项](http://go.microsoft.com/fwlink/p/?LinkId=268419)

 

 







