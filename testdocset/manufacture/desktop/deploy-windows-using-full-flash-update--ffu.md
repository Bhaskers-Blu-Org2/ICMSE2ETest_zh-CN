---
author: Justinha
Description: "部署 Windows 更快地在工厂车间使用全闪存更新 (FFU) 图像格式。"
ms.assetid: af2b402f-9a5c-4c6a-8852-61039e5bec2a
MSHAttr: PreferredLib:/library/windows/hardware
title: "部署 Windows 使用全闪存更新 (FFU)"
ms.openlocfilehash: db7953b314c6da60b14fbb3cf28d6ebee47a05b5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-using-full-flash-update-ffu"></a>部署 Windows 使用全闪存更新 (FFU)


部署 Windows 更快地在工厂车间使用全闪存更新 (FFU) 图像格式。

FFU 的图像，您可以将 Windows 映像应用直接到驱动器或 SD 卡，走势整个驱动器，包括分区信息。

若要创建并应用映像，您可以使用[Windows 图像处理和配置设计器 (ICD)](https://msdn.microsoft.com/library/windows/hardware/dn916112.aspx)。 也可以使用 DISM 的 Windows 10 版本应用 FFU 图像，Windows 预安装环境 (WinPE) 的 Windows 10 版本中包括的

一旦您已经创建了 FFU 图像，它无法修改或脱机编辑。

若要使用 FFU 图像压缩的操作系统，必须作为压缩图像准备 FFU 原始图像。

FFU 图像通常都太大，无法适应标准的 WinPE FAT32 格式化 USB 闪存驱动器上。 为避免这一问题，您可以使用一个单独的存储驱动器或网络位置，或您可以拆分图像分解成较小。SFU 的文件。

## <a name="span-idusingffusspanspan-idusingffusspanspan-idusingffusspanusing-ffus"></a><span id="Using___FFUs"></span><span id="using___ffus"></span><span id="USING___FFUS"></span>使用 FFUs


**若要创建 FFU 图像**

1.  在技术人员计算机，打开 Windows ICD，并创建您的项目。
2.  插入 USB 闪存驱动器，请注意驱动器盘符 (示例︰ d:)。
3.  单击**创建** &gt; **生产介质** &gt; **FFU** &gt; **启用操作系统文件压缩︰** （**是**或**否**）&gt;来命名该文件，例如 d:\\install.ffu &gt; **生成**。

**若要将 Windows 部署直接到 SD 卡或可移动驱动器**

1.  单击**部署**从 Windows ICD &gt; （**到 USB 连接设备**或**可移动驱动器**） &gt; **浏览** &gt; FFU 图像浏览&gt;**下一步**&gt;选择了 SD 卡或设备&gt;**下一步** &gt; **闪存**。
2.  如果您正在部署到 SD 卡，然后闪烁过程完成后，将 SD 卡插入目标设备。

**若要部署来自 WinPE 的窗口**

1.  启动 WinPE 到目标设备。
2.  连接存储驱动器或网络位置，并注意到驱动器号，例如，n。

    ``` syntax
    net use N: \\server\share
    ```

3.  确定您将映像应用到该驱动器。 您可以使用 diskpart，或[添加到 WinPE Windows PowerShell 支持](winpe-adding-powershell-support-to-windows-pe.md)并[获取磁盘](https://technet.microsoft.com/library/hh848657.aspx)用于 scriptability 和如服务器有多个磁盘的复杂设置。 

    ``` syntax
    diskpart 
    list disk
    exit
    ```

4.  将映像应用到某个驱动器。 物理驱动器*x:*，该字符串应该是以下形式:"\\\\。\\PhysicalDrive*X*"，其中*X*是磁盘的磁盘编号的 diskpart 提供，如\\ \\。\\PhysicalDrive0。 硬磁盘编号从 0 开始的。 PhysicalDrive*X*有关的详细信息，请参阅[CreateFile 函数](https://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)。
    
    有关 /SkipPlatformCheck 的详细信息，请参阅[/Apply-Image 在 DISM 图像管理命令行选项](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/dism-image-management-command-line-options-s14#apply-image) 

    ``` syntax
    DISM /Apply-Image /ImageFile:N:\flash.ffu /ApplyDrive:\\.\PhysicalDrive0 /SkipPlatformCheck
    ```

**用于单个驱动器 WinPE 和 FFU 图像**

1.  将 FFU 图像拆分为更小的文件︰

    ``` syntax
    DISM.exe /Split-Image /ImageFile:flash.ffu /SFUFile:flash.sfu /FileSize:3500
    ```

2.  将文件复制到 WinPE usb 闪存盘。
3.  启动 WinPE 到目标设备。
4.  标识 Windows PE 驱动器号，例如，e。

    ``` syntax
    diskpart
    list volume
    ```

5.  在 diskpart 菜单中，确定到您将在应用该图像，例如，驱动器\\ \\。\\PhysicalDrive0。

    ``` syntax 
    list disk
    exit
    ```

6.  将映像应用到某个驱动器。

    ``` syntax
    DISM.exe /Apply-Image /ImageFile:E:\flash.sfu /SFUFile:flash*.sfu /ApplyDrive:\\.\PhysicalDrive0 /SkipPlatformCheck
    ```

**若要使用以前版本的 WinPE**

1.  插入 WinPE usb 闪存盘，请注意驱动器字母，例如，e。
2.  添加到 WinPE 驱动器使用 DISM Windows 10 版本。 若要了解详细信息，请参阅[将 DISM 复制到另一台计算机](copy-dism-to-another-computer.md)。

    ``` syntax
    copy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\amd64\DISM" E:\DISM_Win10 /s
    ```

3.  启动目标设备使用 Windows PE usb 闪存盘。
4.  识别的驱动器 FFU 的存储位置，例如，E.号

    ``` syntax
    diskpart
    list volume
    ```

5.  在 diskpart 菜单中，确定到您将在应用该图像，例如，驱动器\\ \\。\\PhysicalDrive0。

    ``` syntax
    list disk
    exit
    ```

6.  安装 Windows 10 的 DISM 版本。

    ``` syntax
    E:\DISM_Win10\WimMountAdkSetupAmd64.exe /Install /q
    ```

7.  将映像应用到某个驱动器。

    ``` syntax
    E:\DISM_Win10\DISM.exe /Apply-Image /ImageFile:E:\flash.sfu /SFUFile:E:\flash*.sfu /ApplyDrive:\\.\PhysicalDrive0 /SkipPlatformCheck
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[Windows 图像处理和配置设计器](https://msdn.microsoft.com/library/windows/hardware/dn916113)

[FFU 图像格式](../mobile/ffu-image-format.md)

[WIM 与 VHD 与 FFU︰ 比较图像文件格式](wim-vs-ffu-image-file-formats.md)

[配置管理器中的多址广播的战略规划](http://go.microsoft.com/fwlink/?LinkId=286313)

[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[CreateFile 函数](https://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)

 




