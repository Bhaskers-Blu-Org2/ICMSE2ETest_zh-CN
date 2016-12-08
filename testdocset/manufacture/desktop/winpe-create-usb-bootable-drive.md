---
author: Justinha
Description: "WinPE︰ 创建可引导 USB 驱动器"
ms.assetid: 9e7216ed-5a12-4f26-a0cb-da303589c806
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 创建可引导 USB 驱动器"
ms.openlocfilehash: 261714b0add0b17dc7a6e4d46447bfae7821cc60
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-create-usb-bootable-drive"></a>WinPE︰ 创建可引导 USB 驱动器


创建 Windows PE (WinPE) 可引导 USB 闪存驱动器或外部 USB 硬盘驱动器。

默认安装运行从内存 （RAM 磁盘），以便运行 Windows PE 时，您可以删除该驱动器。

**安装 Windows ADK**

-   从[Windows 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/?LinkId=526803)安装以下功能︰

    -   **部署工具**︰ 包括**部署和图像处理工具环境**。

    -   **Windows 预安装环境**︰ 包括用于安装 Windows PE 文件。

**安装 Windows PE**

1.  作为**管理员**启动**部署和图像处理工具环境**。

2.  创建 Windows PE 文件的工作副本。 指定任一 x86，amd64 或配置︰

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

3.  将 Windows PE 安装到 USB 闪存驱动器，指定的驱动器号︰

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

    **警告**  
    此命令将重新格式化驱动器。

     

**引导至 Windows PE**

1.  将 USB 设备连接到您想要使用的电脑。

2.  打开电脑，并按键打开固件引导菜单。

3.  选择的 USB 驱动器。 Windows PE 将自动启动。

    命令窗口出现后，`wpeinit`命令运行时，该设置系统。 这可能需要几分钟的时间。

**故障排除**

1.  如果`copype`命令无法识别，请确保您正在运行该命令的部署和图像处理工具环境中，它是 Windows ADK 的一部分。

2.  如果 Windows PE 没有出现，请尝试以下的解决方法，每次都重新启动计算机︰

    -   要引导固件引导菜单中支持 （uefi） 模式下，PC，请尝试手动选择引导文件︰ \\EFI\\启动\\BOOTX64。EFI。

    -   请尝试另一个 USB 端口。 避免集线器或电缆。

    -   如果固件不包含本机支持 USB 3.0，请避免 USB 3.0 端口。

    -   清洁的 USB 闪存驱动器，并重新安装 Windows PE。 这可以帮助删除额外的启动分区或其他引导软件。

        ``` syntax
        diskpart
          list disk
          select disk <disk number>
          clean
          create partition primary
          format quick fs=fat32 label="Windows PE"
          assign letter="F"
          exit

        MakeWinPEMedia /UFD C:\winpe_amd64 F:
        ```

    -   尝试重新启动 dvd 的 Windows PE，而。 创建您可以将其刻录到 DVD 的 ISO 文件︰

        ``` syntax
        MakeWinPEMedia /ISO C:\winpe_amd64 c:\winpe_amd64\winpe.iso
        ```

        文件资源管理器中定位到 c:\\winpe\_amd64，右键单击**winpe.iso**，然后选择**刻录到光盘**。 按照提示创建 DVD。

    -   如果您的电脑需要存储或视频驱动程序启动，请尝试将这些相同的驱动程序添加到 Windows PE 映像。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

    -   计算机的固件更新为最新版本。

3.  如果计算机没有连接到网络位置，请参阅[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)。

**将 Windows 映像存储在 Windows PE 驱动器上**

1.  通常，您将无法存储或捕获 Windows 映像，使用 Windows PE USB 闪存驱动器上。

    大多数 USB 闪存驱动器支持单个驱动器分区。 `MakeWinPEMedia`命令格式化为 FAT32，支持引导同时基于 BIOS 以及基于 UEFI 的计算机的驱动器。 此文件格式只支持文件大小最大为 4 GB。

2.  对于外部 USB 硬盘，您可以创建一个单独的 NTFS 分区可以处理较大的文件大小︰

    ``` syntax
    diskpart
      list disk
      select <disk number>
      clean
      rem === Create the Windows PE partition. ===
      create partition primary size=2000
      format quick fs=fat32 label="Windows PE"
      assign letter=P
      active
      rem === Create a data partition. ===
      create partition primary
      format fs=ntfs quick label="Other files"
      assign letter=O
      list vol
      exit

    MakeWinPEMedia /UFD C:\WinPE_amd64 P:
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






