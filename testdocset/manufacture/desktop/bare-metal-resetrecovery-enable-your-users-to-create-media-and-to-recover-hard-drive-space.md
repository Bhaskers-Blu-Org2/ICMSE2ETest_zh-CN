---
author: Justinha
Description: "裸露金属的重置恢复︰ 使用户可以创建恢复媒体"
ms.assetid: 2f12f7aa-2259-453a-a433-4fa56b03b375
MSHAttr: PreferredLib:/library/windows/hardware
title: "裸露金属的重置恢复︰ 使用户可以创建恢复媒体"
ms.openlocfilehash: 399a175b1309786856dbd58c25c26e7e3e28a064
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bare-metal-resetrecovery-enable-your-users-to-create-recovery-media"></a>裸露金属的重置恢复︰ 使用户可以创建恢复媒体


恢复介质 （裸机恢复） 帮助将 Windows 设备恢复到出厂状态时，即使用户需要替换硬驱或完全擦除驱动器清洗。

Windows 使用内置的 Windows 文件，其中包括最新的 Windows 和驱动程序的更新，以及 OEM 供应包中包含的所有自定义设置创建恢复媒体。

如果部署时使用的默认分区布局窗口，您的用户将能够创建默认的裸机恢复媒体。

如果使用自定义的分区布局来部署 Windows，您需要添加几个配置文件，使用户创建裸机恢复介质︰

-   **分区重新设置脚本**，这是修改后的 DiskPart 脚本，重置自定义的分区布局。
-   **依靠以点击方式重置配置文件**([ResetConfig XML](resetconfig-xml-reference-s14.md)) 标识的 Windows 和 Windows RE 分区。

**注意︰**在第 10 Windows 版本 1607，桌面应用程序和设置中[各自为政，资源调配的包](siloed-provisioning-packages.md)捕获不会还原使用此介质。 常规的自定义软件包 (.ppkg) 捕获使用扫描状态工具不受此问题。 

## <a name="span-idcreateconfigfilesspanspan-idcreateconfigfilesspanspan-idcreateconfigfilesspancreating-configuration-files"></a><span id="CreateConfigFiles"></span><span id="createconfigfiles"></span><span id="CREATECONFIGFILES"></span>创建配置文件


**分区重新设置脚本**

1.  在记事本创建分区的硬盘的硬驱已被重置后的配置文件。 此脚本应该是相同的脚本用于创建分区的硬驱，以下情况除外︰

    -   该脚本不应包含命令以选择或清除该驱动器。 Windows 会自动识别的系统驱动器。 若要了解详细信息，请参阅本主题中后面的[识别系统驱动器](#identifyingthesystemdrive)。

    -   该脚本应分配给系统分区，Windows 分区，Windows RE 工具分区号。

    示例︰

    （uefi) （根据[基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md)）︰

    ``` syntax
    rem == ResetPartitions-UEFI.txt ==
    rem == These commands are used with DiskPart to
    rem    reset the drive and recreate five partitions
    rem    for a UEFI/GPT-based computer.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    rem == The differences between this file and
    rem    CreatePartitions-UEFI.txt
    rem    are noted in parenthesis.
    rem       (NOT USED: select disk 0)
    rem       (NOT USED: clean)
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    rem    ** NOTE: For Advanced Format 4Kn drives,
    rem               change this value to size = 260 ** 
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=128
    rem == 3. Windows partition ========================
    rem ==    a. Create the Windows partition ==========
    create partition primary 
    rem ==    b. Create space for the recovery tools ===
    shrink minimum=500
    rem       ** NOTE: Update this size to match the
    rem                size of the recovery tools 
    rem                (winre.wim)                    **
    rem ==    c. Prepare the Windows partition ========= 
    format quick fs=ntfs label="Windows"
    assign letter="C"
    rem === 4. Recovery tools partition ================
    create partition primary
    format quick fs=ntfs label="Recovery tools"
    assign letter="R"
    set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
    gpt attributes=0x8000000000000001
    list volume
    ```

    BIOS （基于[基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md)）︰

    ``` syntax
    rem == ResetPartitions-BIOS.txt ==
    rem == These commands are used with DiskPart to
    rem    reset the drive and create three partitions
    rem    for a BIOS/MBR-based computer.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    rem == The differences between this file and
    rem    CreatePartitions-BIOS.txt
    rem    are noted in parenthesis.
    rem       (NOT USED: select disk 0 )
    rem       (NOT USED: clean )
    rem == 1. System partition ======================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    rem == 2. Windows partition =====================
    rem ==    a. Create the Windows partition =======
    create partition primary
    rem ==    b. Create space for the recovery tools  
    shrink minimum=500
    rem       ** NOTE: Update this size to match the
    rem                size of the recovery tools 
    rem                (winre.wim)                 **
    rem ==    c. Prepare the Windows partition ====== 
    format quick fs=ntfs label="Windows"
    assign letter="C"
    rem == 3. Recovery tools partition ==============
    create partition primary
    format quick fs=ntfs label="Recovery"
    assign letter="R"
    set id=27
    list volume
    ```

2.  保存您的文件，例如 e:\\恢复\\RecoveryImage\\ResetPartitions UEFI.txt。

**依靠以点击方式重置配置文件 (ResetConfig.xml)**

1.  在记事本创建指向您的点击式重新设置分区脚本的配置文件。

    有关配置此文件的信息，请参阅[ResetConfig XML 参考](resetconfig-xml-reference-s14.md)。

    （UEFI):

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- ResetConfig.xml for UEFI -->
    <Reset>
        <!-- May be combined with custom scripts – insert Run Phase elements here -->
        <SystemDisk>
            <DiskpartScriptPath>ResetPartitions-UEFI.txt</DiskpartScriptPath>
            <MinSize>75000</MinSize>
            <WindowsREPartition>4</WindowsREPartition>
            <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
            <OSPartition>3</OSPartition>
        </SystemDisk>
    </Reset>
    ```

    BIOS:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <!-- ResetConfig.xml for BIOS -->
    <Reset>
        <!-- May be combined with custom scripts – insert Run Phase elements here -->
        <SystemDisk>
            <DiskpartScriptPath>ResetPartitions-BIOS.txt</DiskpartScriptPath>
            <MinSize>75000</MinSize>
            <WindowsREPartition>3</WindowsREPartition>
            <WindowsREPath>Recovery\WindowsRE</WindowsREPath>
            <OSPartition>2</OSPartition>
        </SystemDisk>
    </Reset>
    ```

2.  将使用 utf-8 文件格式的文件︰

    单击**文件**，然后单击**另存为**。 在**编码**框中，选择**utf-8**，，然后将此文件另存为 e:\\恢复\\RecoveryImage\\ResetConfig.xml。

## <a name="span-idenableendusersspanspan-idenableendusersspanspan-idenableendusersspanenable-users-to-create-media"></a><span id="EnableEndUsers"></span><span id="enableendusers"></span><span id="ENABLEENDUSERS"></span>使用户可以创建媒体


用户可以使用此选项来创建恢复媒体，并回收从在需要时恢复图像分区的硬盘空间。

**步骤 1︰ 添加到目标计算机的配置文件**

1.  在目标计算机上，使用配置文件中插入 USB 闪存驱动器。

2.  将配置文件复制到目标计算机︰

    ``` syntax
    Copy E:\Recovery\RecoveryImage\* R:\RecoveryImage\*
    ```

    其中*E*是 USB 闪存驱动器和*R*的驱动器号是恢复图像分区的驱动器号。

**步骤 2︰ 测试 Windows 可以创建恢复媒体**

1.  重新启动目标计算机，然后完成的全新体验 (OOBE)。

2.  单击**开始**，键入**创建恢复驱动器**，并选择**创建恢复驱动器**，UAC 提示时单击**是**。

3.  插入 USB 闪存驱动器。

4.  选择**将复制到恢复驱动器的 PC 从恢复分区** &gt; **下** &gt; **下** &gt; **创建**。

**步骤 3︰ 测试恢复媒体**

1.  在没有操作系统的计算机，将恢复媒体。
2.  启动计算机，按下某个键打开固件引导菜单，然后选择相应的启动设备。
3.  在**Windows RE 工具**菜单中，选择一种键盘布局，例如，**我们**。
4.  单击**疑难解答** &gt; **重置您的 PC** &gt; **下一步**。 如果系统提示您清洁驱动器时，请选择**是**。
5.  选择**是，对驱动器重新分区** &gt; **只是删除我的文件** &gt; **重置**。

**故障排除︰**

-   请确保 ResetConfig.xml 保存为 utf-8 文件。
-   请确保文件名中列出&lt;DiskpartScriptPath&gt; ResetConfig.xml 文件中的元素与在 Diskpart 脚本文件名相匹配。
-   请确保 Diskpart 脚本不包含用于选择驱动器或清洁驱动器的命令 (`select disk 0`， `clean`)。

## <a name="span-ididentifyingthesystemdrivespanspan-ididentifyingthesystemdrivespanspan-ididentifyingthesystemdrivespanidentifying-the-system-drive"></a><span id="IdentifyingTheSystemDrive"></span><span id="identifyingthesystemdrive"></span><span id="IDENTIFYINGTHESYSTEMDRIVE"></span>标识系统驱动器


Windows 标识系统驱动器使用以下方法︰

**基于 BIOS 的计算机**︰ 用 BIOS 报告系统驱动器。

**基于 UEFI 的计算机**︰ 使用启用时 Windows RE`reagentc /setreimage`命令时，Windows 将适配器位置路径和系统磁盘的 GUID 写入 （uefi） 变量。 当系统和操作系统分区系统驱动器上时，才执行此步骤。 该变量时，更新如有必要禁用并重新启用 Windows RE 获取。

**如果检测到多个本地驱动器，则 Windows 标识系统驱动器通过按以下顺序搜索︰**

1.  Windows 搜索的驱动器固件中存储的值匹配的 GUID。

2.  Windows 搜索匹配的固件中存储的值的位置路径使用的驱动器。

3.  Windows 搜索现有的 ESP 使用的驱动器。

    如果找到多个驱动器的 ESP，恢复过程不会继续。

4.  Windows 搜索未初始化 （裸容量） 的磁盘。

    如果找到多个未初始化的磁盘，则不会继续恢复过程。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[点击式重新设置概述](push-button-reset-overview.md)

[ResetConfig XML 参考](resetconfig-xml-reference-s14.md)

[裸露金属的重置恢复︰ 在部署新设备的过程创建恢复媒体](create-media-to-run-push-button-reset-features-s14.md)

[基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md)

[基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md)

 

 






