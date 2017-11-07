---
author: Justinha
Description: "WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD"
ms.assetid: d60de9b6-6775-41e7-bc52-dfafede554df
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD"
ms.openlocfilehash: ab7d15abe370e5960efbb7a698dec547bc070205
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-create-a-boot-cd-dvd-iso-or-vhd"></a>WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD


创建可引导 Windows PE (WinPE) 的 DVD，CD ISO 文件，或者虚拟硬盘驱动器 (VHD)。

从内存 （即 RAM 磁盘），您可以删除 USB 驱动器运行 Windows PE 时，默认安装运行。

**安装 Windows ADK**

-   从[Windows 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/p/?LinkID=526803)安装以下功能︰

    -   **部署工具**︰ 包括**部署和图像处理工具环境**。

    -   **Windows 预安装环境**︰ 包括用于安装 Windows PE 文件。

**将 Windows PE 安装到 DVD、 CD 或 ISO 文件**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  创建 Windows PE 文件的工作副本。 X86 或 amd64 指定︰

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

3.  创建一个包含 Windows PE 文件的 ISO 文件︰

    ``` syntax
    MakeWinPEMedia /ISO C:\WinPE_amd64 C:\WinPE_amd64\WinPE_amd64.iso
    ```

4.  刻录 DVD 或 CD︰ 在 Windows 资源管理器中，右击该 ISO 文件，并选择**刻录光盘映像** &gt; **刻录**，按照提示进行操作。

## <a name="span-idusinghyper-vspanspan-idusinghyper-vspanspan-idusinghyper-vspanusing-hyper-v"></a><span id="Using_Hyper-V"></span><span id="using_hyper-v"></span><span id="USING_HYPER-V"></span>使用 Hyper-V


当运行 Windows PE 在 Hyper-V 中，请考虑使用 ISO 文件格式而不一个 VHD，若要启用的虚拟 PC 的快速安装程序。 有关详细信息，请参阅上一节。

**若要将 Windows PE 安装到 VHD**

1.  创建虚拟硬盘 （.vhd 或.vhdx）︰

    ``` syntax
    diskpart
    create vdisk file="C:\WinPE.vhdx" maximum=1000
    attach vdisk
    create partition primary
    assign letter=V
    format fs=ntfs quick
    exit
    ```

2.  通过使用 MakeWinPEMedia 准备驱动器︰

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 V:
    ```

3.  断开驱动器︰

    ``` syntax
    diskpart
    select vdisk file="C:\WinPE.vhdx"
    detach vdisk
    exit
    ```

**故障排除**

1.  如果 Windows PE 没有出现，请尝试以下的解决方法，每次都重新启动计算机︰

    -   要启动 PC 支持 UEFI 模式︰ 在固件引导菜单中，请尝试手动选择引导文件︰ \\EFI\\启动\\BOOTX64。EFI。

    -   如果您的电脑需要存储或视频驱动程序启动，请尝试将这些相同的驱动程序添加到 Windows PE 映像。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

2.  如果计算机没有连接到网络位置，请参阅[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






