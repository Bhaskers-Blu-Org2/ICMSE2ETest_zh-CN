---
author: Justinha
Description: "下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器"
ms.assetid: 1799a91f-493a-4509-9937-ad6901358240
MSHAttr: PreferredLib:/library/windows/hardware
title: "下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器"
ms.openlocfilehash: 11ebcb0129e47f1f81e92eda49bb5b8119783c0e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="download-and-install-windows-pe-winpe-so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive"></a>下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器


通过使用 BCDEdit 工具到 VHD 文件 （"本机引导"） 启动您的 PC。 如果 VHD 添加到已有的 Windows 10 或 Windows 8 的安装的计算机，您将必须向菜单中添加启动项。 如果 VHD 添加到计算机正在运行旧版本的 Windows 中，例如 Windows Server 2008 中，您将需要更新使用 BCDboot 工具的系统分区，然后修改使用 BCDedit 工具启动菜单。

本机引导的 Windows 10 要求**.vhdx**格式，不到.vhd 格式。

## <a name="span-idupdatethebootmenutoaddavhdspanspan-idupdatethebootmenutoaddavhdspanspan-idupdatethebootmenutoaddavhdspanupdate-the-boot-menu-to-add-a-vhd"></a><span id="Update_the_Boot_Menu_to_Add_a_VHD"></span><span id="update_the_boot_menu_to_add_a_vhd"></span><span id="UPDATE_THE_BOOT_MENU_TO_ADD_A_VHD"></span>更新启动菜单添加一个 VHD


**若要更新基于 BIOS 的计算机，以包括 Windows 8 引导菜单**

1.  将.vhdx 文件复制到目标计算机。 例如，在命令提示符处，键入︰

    ``` syntax
    copy N:\VHDs\windows.vhdx C:
    ```

2.  在 Windows PE 中使用 DiskPart 工具附加 VHD 在目标计算机上。 您可以通过使用**附加的虚拟磁盘**命令附加 VHD。 这使 VHD，以使其显示为磁盘驱动器，而不是作为一个.vhdx 文件的主机上。 在命令提示符处，键入︰

    ``` syntax
    diskpart
    select vdisk file=c:\windows.vhdx
    attach vdisk
    list volume
    select volume <volume_number_of_attached_VHD>
    assign letter=v
    exit
    ```

3.  使用 BCDboot 工具，位于**\\System32**的 VHD 映像或在 Windows PE 的引导环境文件和引导配置数据 (BCD) 配置复制目录**\\Windows**目录在 VHD 到系统分区。 在计算机的 BIOS 固件上，系统分区是活动分区的第一个硬盘。 例如，要使用 BCDboot 从 VHD 映像，在命令提示符处，键入︰

    ``` syntax
    cd v:\windows\system32
    bcdboot v:\windows
    ```

BCDboot 工具将自动导入信息从现有安装更新 BCD 时。 计算机现在将更新以包括 Windows 8 的引导环境。 您现在可以在本主题后面，按照"可将本机引导 VHD 添加到现有的 Windows 8 的引导菜单"一节中的步骤。

**若要更新基于 UEFI 的计算机，以包括 Windows 8 引导菜单**

1.  将.vhdx 文件复制到目标计算机。 例如，在命令提示符处，键入︰

    ``` syntax
    copy N:\VHDs\windows.vhdx C:
    ```

2.  在 Windows PE 中使用 DiskPart 工具附加 VHD 在目标计算机上。 您可以通过使用**附加的虚拟磁盘**命令附加 VHD。 这使 VHD，以使其显示为磁盘驱动器，而不是作为一个.vhdx 文件的主机上。 在命令提示符处，键入︰

    ``` syntax
    diskpart
    select vdisk file=C:\windows.vhdx
    attach vdisk
    list volume
    select volume <volume_number_of_attached_VHD>
    assign letter=v
    exit
    ```

3.  在基于 UEFI 的计算机上，系统分区默认情况下隐藏，必须分配一个驱动器号之前运行 BCDboot 工具。 使用 DiskPart 工具找到 EFI 系统分区，然后给它指派一个驱动器号。 在命令提示符处，键入︰

    ``` syntax
    diskpart
    select disk 0
    list partition
    select partition <x>
    assign letter=s
    exit
    ```

    其中*&lt;x&gt;*是用 FAT 格式化的 100 兆字节 (MB) EFI 系统分区。

4.  使用 BCDboot 工具，位于\\VHD 映像或在 Windows PE 的引导环境文件和 BCD 配置复制 System32 目录\\中的系统分区 VHD Windows 目录。 例如，要使用 BCDboot 从 VHD 映像，在命令提示符处，键入︰

    ``` syntax
    cd v:\windows\system32
    bcdboot v:\windows
    ```

BCDboot 工具将自动导入信息从现有安装更新 BCD 时。 计算机现在将更新 Windows 10 的引导环境。 现在，您可以按照将本机引导 VHD 添加到一个现有的启动菜单的步骤。

**将本机引导 VHD 添加到现有的 Windows 8 引导菜单**

1.  BCD 存储备份使用 BCDedit**工具/导出**选项。 例如，在命令提示符处，键入︰`bcdedit /export c:\bcdbackup`

2.  复制一个现有的启动项目的 Windows 安装。 然后，您将修改用作 VHD 启动项目的副本。 在命令提示符处，键入︰

    ``` syntax
    bcdedit /copy {default} /d "vhd boot (locate)"
    ```

    BCDedit 命令成功完成，会在**命令提示**窗口中返回作为输出的 {GUID}。

3.  在前一个命令的命令提示符输出找到 {GUID}。 将复制的 GUID，包括大括号，在下面的步骤中使用。

4.  将 VHD 引导项目的**设备**和**osdevice**选项的设置。 在命令提示符处，键入︰

    ``` syntax
    bcdedit /set {guid} device vhd=[locate]\windows.vhdx
    bcdedit /set {guid} osdevice vhd=[locate]\windows.vhdx
    ```

5.  设置为默认启动项目 VHD 引导项。 计算机重新启动时，启动菜单将显示安装 Windows 的所有在计算机并引导至 VHD 操作系统选择倒计时完成后。 在命令提示符处，键入︰

    ``` syntax
    bcdedit /default {guid}
    ```

6.  某些基于 x86 的系统需要才能检测到某些硬件信息并成功本机引导 VHD 从内核的引导配置选项。 在命令提示符处，键入︰

    ``` syntax
    bcdedit /set {guid} detecthal on
    ```

有关如何使用 BCDedit 工具的详细信息，请参阅[此 Microsoft Web 站点](http://go.microsoft.com/fwlink/?LinkId=128459)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

[引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

[了解具有本机引导的虚拟硬盘](understanding-virtual-hard-disks-with-native-boot.md)

 

 






