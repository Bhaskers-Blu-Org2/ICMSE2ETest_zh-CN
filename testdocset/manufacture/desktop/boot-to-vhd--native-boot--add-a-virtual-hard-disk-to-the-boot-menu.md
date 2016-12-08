---
author: Justinha
Description: "引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单"
ms.assetid: e00d7f8f-502c-40e5-904c-8cc653c1899e
MSHAttr: PreferredLib:/library/windows/hardware
title: "引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单"
ms.openlocfilehash: 1a111e2ad8a07244fa198ffa552bd16a6d1d7eff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-to-vhd-native-boot-add-a-virtual-hard-disk-to-the-boot-menu"></a>引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单


本机引导允许您创建虚拟硬盘 (VHD)、 安装 Windows，然后再启动它，在您的 PC-并行与您现有的安装，或在新设备上。

本机引导 VHD 可以用作指定硬件而无需任何其他父操作系统上运行的操作系统。 这不同于其中一个 VHD 连接至具有父操作系统的计算机上的虚拟机的方案。

Vhd 可以应用到个人电脑或有没有安装的其他 Windows，不用虚拟机和虚拟机管理程序的设备。 （虚拟机监控程序是在运行虚拟机的操作系统软件层）。这使得工作负载分布在更大的灵活性，因为可以用于管理映像的虚拟机和指定硬件工具一套。

此外可以将 VHD 部署到已安装，Windows PC，并使用启动菜单选择的现有版本的 Windows 或将 VHD 上的版本之间。

在企业环境中使用 Vhd 的详细信息，请参阅[了解具有本机引导的虚拟硬盘](understanding-virtual-hard-disks-with-native-boot.md)。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


-   技术人员计算机与 Windows 评估和安装在其上部署工具包 (Windows ADK) 工具。

-   一个一般化 Windows 映像 (。WIM 文件）。 若要了解详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

-   可引导 Windows PE 驱动器。 若要了解详细信息，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。

-   目标 PC 或设备在其上安装 VHD。 此设备需要 30 千兆字节 (GB) 或多个可用磁盘空间。 您可以将 VHD 安装到设备已运行其他操作系统安装，或作为唯一的操作系统的设备上。

## <a name="span-idstep1createavhdfromdiskpartspanspan-idstep1createavhdfromdiskpartspanspan-idstep1createavhdfromdiskpartspanstep-1-create-a-vhd-from-diskpart"></a><span id="Step_1__Create_a_VHD_from_diskpart"></span><span id="step_1__create_a_vhd_from_diskpart"></span><span id="STEP_1__CREATE_A_VHD_FROM_DISKPART"></span>步骤 1︰ 创建从 diskpart VHD


1.  在技术人员计算机上，打开 Diskpart。

    ``` syntax
    diskpart
    ```

2.  创建并准备好新的 VHD。 在此示例中，我们创建一个 25 GB 固定类型 VHD。

    ``` syntax
    create vdisk file=C:\windows.vhd maximum=25600 type=fixed
    ```

3.  附加 VHD。 这将 VHD 磁盘作为添加到主机上的存储控制器。

    ``` syntax
    attach vdisk
    ```

4.  为 Windows 文件创建分区、 格式化，并为其分配一个驱动器号。 文件资源管理器中将显示该驱动器号。

    ``` syntax
    create partition primary
    format quick label=vhd
    assign letter=v
    ```

5.  Diskpart 退出

    ``` syntax
    exit
    ```

## <a name="span-idstep2applyawindowsimagetothevhdspanspan-idstep2applyawindowsimagetothevhdspanspan-idstep2applyawindowsimagetothevhdspanstep-2-apply-a-windows-image-to-the-vhd"></a><span id="Step_2__Apply_a_Windows_image_to_the_VHD"></span><span id="step_2__apply_a_windows_image_to_the_vhd"></span><span id="STEP_2__APPLY_A_WINDOWS_IMAGE_TO_THE_VHD"></span>步骤 2︰ 将 Windows 映像应用到 VHD


-   通用将 Windows 映像应用到 VHD 的主分区。

    ``` syntax
    Dism /Apply-Image /ImageFile:install.wim /index:1 /ApplyDir:V:\
    ```

## <a name="span-idstep3detachthevhdcopyittoanewdeviceandattachitoptionalspanspan-idstep3detachthevhdcopyittoanewdeviceandattachitoptionalspanspan-idstep3detachthevhdcopyittoanewdeviceandattachitoptionalspanstep-3-detach-the-vhd-copy-it-to-a-new-device-and-attach-it-optional"></a><span id="Step_3__Detach_the_VHD__copy_it_to_a_new_device__and_attach_it__optional_"></span><span id="step_3__detach_the_vhd__copy_it_to_a_new_device__and_attach_it__optional_"></span><span id="STEP_3__DETACH_THE_VHD__COPY_IT_TO_A_NEW_DEVICE__AND_ATTACH_IT__OPTIONAL_"></span>第 3 步︰ 分离 VHD、 将其复制到新设备，以及如何将它 （可选）


您可以将 VHD 部署到已有一份上，安装了 Windows 的设备或可以清洗和准备直接使用 VHD 的驱动器。

**分离 VHD 并将其保存到网络共享或存储驱动器**

1.  分离的虚拟磁盘。

    ``` syntax
    diskpart
    select vdisk file=C:\windows.vhd
    detach vdisk
    exit
    ```

2.  复制到网络共享或可移动存储驱动器 VHD。

    ``` syntax
    net use n: \\server\share\
    md N:\VHDs
    copy C:\windows.vhd n:\VHDs\
    ```

**清洁和准备新的本机引导设备**

1.  启动目标设备连接到 Windows 预安装环境 (WinPE)。
2.  清洁并准备驱动器。 创建一个系统分区 (S) 和存储 VHD 的主分区 (M)。

    BIOS:

    ``` syntax
    diskpart
    select disk 0
    clean
    rem == 1. System partition ======================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    rem == 2. Main partition ========================
    create partition primary
    format quick fs=ntfs label="Main"
    assign letter="M"
    exit
    ```

    （UEFI):

    ``` syntax
    diskpart
    select disk 0
    clean
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=128
    rem == 3. Main partition ===========================
    create partition primary 
    format quick fs=ntfs label="Main"
    assign letter="M"
    exit
    ```

3.  连接到网络驱动器或存储位置，并记下驱动器号。

    ``` syntax
    net use N: \\server\share
    ```

4.  将 VHD 复制到主分区。

    ``` syntax
    copy N:\VHDs\Windows.vhd M:
    ```

**附加 VHD**

1.  附加 VHD。

    ``` syntax
    diskpart
    select vdisk file=M:\windows.vhd
    attach vdisk
    ```

2.  标识的卷号。 (可选︰ 将其更改为另一个字母，更有意义，例如 V，并保留 diskpart 命令行打开下一步)。

    ``` syntax
    list volume
    select volume 3
    assign letter=v
    ```

## <a name="span-idstep4addabootentryspanspan-idstep4addabootentryspanspan-idstep4addabootentryspanstep-4-add-a-boot-entry"></a><span id="Step_4__Add_a_boot_entry"></span><span id="step_4__add_a_boot_entry"></span><span id="STEP_4__ADD_A_BOOT_ENTRY"></span>步骤 4︰ 添加启动项


1.  打开 Diskpart （如果需要），并确定驱动器号的 VHD 和系统分区，例如，V 和 s。

    ``` syntax
    diskpart
    list volume
    exit
    ```

2.  向设备中添加启动项。 您可以添加多个 VHD 文件使用此方法。

    BIOS:

    ``` syntax
    V:
    cd v:\windows\system32
    bcdboot v:\windows /s S: /f BIOS
    ```

    （UEFI):

    ``` syntax
    V:\
    cd v:\windows\system32
    bcdboot v:\windows /s S: /f UEFI
    ```

3.  删除 Windows PE usb 闪存盘。

4.  重新启动设备。

    如果只有一个启动项目，该设备将立即引导到 Windows。 如果存在多个启动项目，您将看到一个启动菜单，您可以选择 Windows 在该设备上的可用版本之间。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[了解具有本机引导的虚拟硬盘](understanding-virtual-hard-disks-with-native-boot.md)

[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

 

 






