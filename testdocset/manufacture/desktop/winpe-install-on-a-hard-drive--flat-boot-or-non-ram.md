---
author: Justinha
Description: "WinPE︰ 安装在硬盘上 （平面引导或非 RAM）"
ms.assetid: f4495adf-63db-4fdc-ae56-70166eed930c
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 安装在硬盘上 （平面引导或非 RAM）"
ms.openlocfilehash: 74fd03850a62fd1e9ab40f218f8e317bb017926d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-install-on-a-hard-drive-flat-boot-or-non-ram"></a>WinPE︰ 安装在硬盘上 （平面引导或非 RAM）


Windows 预安装环境 (Windows PE) 是最小操作系统，您可以安装、 部署和维护的 Windows 为准备一台电脑。 下面介绍了如何下载并安装到内部或外部硬盘。

这些过程说明如何设置从驱动器中运行的基本 Windows PE 安装。 这有时会显示比从内存，启动性能好，可以帮助您在 Pc 或低内存的虚拟环境中运行 Windows PE。 此过程也称为*非 RAMDISK 启动*或*简单的引导*。

**请注意**  
当从驱动器运行 Windows PE 时，您必须关闭 PC 断开连接的驱动器，以避免丢失所做的工作之前。

 
## <a name="span-idinstallthewindowsadkspan-install-the-windows-adk"></a><span id="Install_the_Windows_ADK"></span>安装 Windows ADK

-   获取[Windows 评估和部署工具包 (Windows ADK) 技术参考](http://go.microsoft.com/fwlink/p/?LinkId=526803)，包括 Windows PE 功能。

**创建一组的是 32 位还是 64 位 Windows PE 文件**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  在**部署和图像处理工具环境**，Windows PE 文件复制要用来启动的电脑。

    64 位版本的 Windows PE 可以引导 UEFI 64-位和 64 位 BIOS Pc:

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

    32 位版本的 Windows PE 可以引导 32 位 （uefi）、 32 位 BIOS 和 64 位 BIOS Pc:

    ``` syntax
    copype x86 C:\WinPE_x86
    ```

## <a name="span-idcreateaworkingdirectoryspan-create-a-working-directory-for-windows-pe-files"></a><span id="Create_a_Working_Directory"></span>创建一个有效的 Windows PE 文件的目录

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  从**部署和图像处理工具环境**，创建 Windows PE 文件的工作目录。

    ``` syntax
    copype amd64 C:\WinPE_amd64
    ```

## <a name="span-idinstallwindowspespan-install-windows-pe-to-the-media"></a><span id="Install_Windows_PE"></span>将 Windows PE 安装到媒体

1.  使用 DiskPart，可以准备分区。

    **请注意**  
    下面的命令准备的 USB 硬盘可以引导基于 BIOS 的或基于 UEFI 的计算机上。

    在基于 UEFI 的计算机，Windows PE 需要引导分区使用的唯一支持文件大小最大为 4 GB 的 FAT32 文件格式进行格式化。 我们建议，以便 Windows 映像和其他大型的文件可以存储使用 NTFS，在格式化的驱动器上创建一个单独的分区。 若要了解详细信息，请参阅[WinPE︰ 使用脚本确定驱动器号](winpe-identify-drive-letters.md)。 

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
    rem === Create a partition for images ===
    create partition primary
    format fs=ntfs quick label="Images"
    assign letter=I
    list vol
    exit
    ```

    其中*&lt;磁盘号&gt;*是外部 USB 硬盘驱动器的列的数。

2.  将 Windows PE 映像应用到硬盘驱动器。

    ``` syntax
    dism /Apply-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /Index:1 /ApplyDir:P:\
    ```

3.  设置启动文件。

    ``` syntax
    BCDboot P:\Windows /s P: /f ALL
    ```

    **请注意**  
    忽略所有警告消息，指出"警告︰ 继续应用程序找不到。"

     

## <a name="span-idboottowindowspespan-boot-to-windows-pe"></a><span id="Boot_to_Windows_PE"></span>引导至 Windows PE

1.  连接到您想要使用的 PC 的设备 （内部或外部 USB 硬盘驱动器）。

2.  打开计算机，并使用启动菜单选择 Windows PE 的驱动器。 通常这需要按硬件按钮或 Esc 键的键。

    **请注意**  
    基于 UEFI 的计算机，您可能需要查找选项来手动选择 UEFI 引导文件，例如，USBDrive01\\EFI\\启动\\BOOTX64。EFI。

    Windows PE 将自动启动。 命令窗口出现后，wpeinit 命令将自动运行。 这可能需要几分钟的时间。

    
## <a name="span-idtroubleshootingspano-troubleshooting"></a><span id="Troubleshooting"></span>o 疑难解答

1.  如果计算机无法启动，在序列中，尝试执行以下步骤，并尝试在每步操作之后启动 PC:

    1.  外部 USB 驱动器，请尝试将驱动器插入到另一个 USB 端口。 避免使用 USB 集线器或电缆，因为它们可能检测不到在启动过程中。 如果固件没有本机支持 USB 3.0，请避免 USB 3.0 端口。

    2.  如果您的电脑需要驱动程序才能启动，例如存储驱动程序或视频驱动程序，或者如果您的驱动程序需要对注册表的更改，将驱动程序添加到 Windows PE 映像中。 有关详细信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

    3.  计算机的固件更新为最新版本。

2.  在连接到网络上的提示，请参阅[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)。

**从 Windows PE 运行 Windows 安装程序**

-   有关 Windows 安装在 UEFI Pc 支持 UEFI 和传统 BIOS 固件模式，提示和使用 (x86) 的 32 位版本的 Windows PE 安装 64 位版本的 Windows，请参阅[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span>相关的主题

[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 使用脚本确定驱动器号](winpe-identify-drive-letters.md)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






