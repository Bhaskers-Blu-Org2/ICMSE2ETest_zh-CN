---
author: Justinha
Description: "配置多个硬盘驱动器"
ms.assetid: 2cb7386a-b3f6-40dd-b084-fce52a7aed9b
MSHAttr: PreferredLib:/library/windows/hardware
title: "配置多个硬盘驱动器"
ms.openlocfilehash: f0ed2a7118ffa79b462524444cee74a0a79bcdbe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-multiple-hard-drives"></a>配置多个硬盘驱动器


如果要部署到的计算机中有多个硬驱 Windows，您可以验证图像通过使用特定于硬件的标识符，如位置路径或硬件中断值应用到特定硬盘。

位置路径是一个字符串，指定的物理位置的每个驱动器连接到计算机，例如︰ `PCIROOT(0)#PCI(0100)#ATA(C00T00L00)`。 当制造计算机，连接您的驱动器时使用一致的物理位置，然后使用位置路径字符串来标识每个硬驱。

为基于 BIOS 的计算机或计算机正在运行虚拟磁盘服务 (VDS)，您可以使用**选择磁盘 = 系统**和**选择磁盘 = 下一步**命令来选择适当的硬驱。

本主题︰

-   [确定驱动器的位置路径](#identifyingdisklocationpath)
-   [选择系统驱动器](#selectingsystemdisk)
-   [选择非系统驱动器](#selectingnonsystemdisks)
-   [在重新启动后识别系统驱动器](#exampleidentifyingsystemdiskafterreboot)
-   [非系统驱动器的格式](#exampleformattingnonsystemdisks)

## <span id="IdentifyingDiskLocationPath"></span><span id="identifyingdisklocationpath"></span><span id="IDENTIFYINGDISKLOCATIONPATH"></span>


 **确定磁盘位置路径**

-   使用 DiskPart 命令︰**磁盘列表**和**选择磁盘&lt;磁盘号&gt;**(示例︰**选择磁盘 1**) 您的计算机上的驱动器之间进行导航。

    若要显示所选驱动器的位置路径，请使用 DiskPart 命令`detail disk`。

    在以下示例中，所选驱动器的位置路径是 PCIROOT(0)\#PCI(0100)\#ATA(C00T00L00)。

    ``` syntax
    DISKPART> detail disk

    HITACHI HTS722016K9SA00
    Disk ID: 5E27161A
    Type   : ATA
    Bus    : 0
    Target : 0
    LUN ID : 0
    Location Path : PCIROOT(0)#PCI(0100)#ATA(C00T00L00)
    Read-only  : No
    Boot Disk  : Yes
    PagefileDisk  : Yes
    Hibernation File Disk  : No
    CrashdumpDisk  : Yes
    Clustered Disk  : No


      Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
      ----------  ---  -----------  -----  ----------  -------  ---------  --------
      Volume 1     C                NTFS   Partition    149 GB  Healthy    System

    DISKPART>
    ```

## <a name="span-idselectingdrivesspanspan-idselectingdrivesspanspan-idselectingdrivesspanselecting-drives"></a><span id="Selecting_Drives"></span><span id="selecting_drives"></span><span id="SELECTING_DRIVES"></span>选择驱动器


<span id="SelectingSystemDisk"></span><span id="selectingsystemdisk"></span><span id="SELECTINGSYSTEMDISK"></span>
 **选择系统驱动器**

1.  **基于 BIOS 的计算机**︰ 使用命令**选择磁盘 = 系统**中选择默认的系统驱动器。

    此命令选择的中断 13h 值为 80h 的驱动器。 如果 80 h 的值分配给一个 USB 闪存驱动器，则此命令将选择硬盘的值为 81 h。 有关详细信息，请访问下面的 Microsoft 开发人员网络 (MSDN) 网站︰

    [转换为 MS-DOS INT 13 H 磁盘驱动器号的驱动器号](http://go.microsoft.com/fwlink/?LinkId=164574)

2.  **基于 UEFI 的计算机**︰ 若要选择一个驱动器，请使用 DiskPart 命令**选择磁盘 =&lt;位置路径&gt;**。

    **请注意**  
    不要使用**选择磁盘 = 系统**命令或 GetSystemDiskNTPath API 基于统一可扩展固件接口 （uefi） 的计算机上选择的系统驱动器。 **选择磁盘 = 系统**命令和 GetSystemDiskNTPath API 确定从系统驱动器作为引导操作系统的驱动器。 如果您从 Windows® PE 启动，此命令将选择 Windows PE 驱动器与系统驱动器。 如果从具有多个驱动器包含一个 EFI 系统分区 (ESP) 的系统启动，此命令可能会选择错误的驱动器。

     

<span id="SelectingNonSystemDisks"></span><span id="selectingnonsystemdisks"></span><span id="SELECTINGNONSYSTEMDISKS"></span>
 **选择非系统驱动器**

1.  **选择的驱动器的位置路径。** 若要选择一个驱动器，请使用 DiskPart 命令**选择磁盘 =&lt;位置路径&gt;**，其中&lt;*位置路径*&gt;为您的驱动器的位置路径。 此命令有助于指定驱动器的位置。

    示例：

    ``` syntax
    SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C00T00L00)
    ```

2.  **通过使用"下一个"驱动器选择的驱动器。** 使用 DiskPart 命令**选择磁盘 = 下一步**。 此命令有助于指定任何剩余的硬盘驱动器，而不用考虑位置。 若要选择多个驱动器，重复**选择磁盘 = 下一步**命令按顺序选择每个驱动器。 如果没有选择多个驱动器，则 DiskPart 将返回一个错误。

    **请注意**  
    计算机维护的上下文**选择磁盘 = 下一步**命令，只要 DiskPart 继续运行。 如果 DISKPART 退出，计算机将失去此上下文。

     

    基于 UEFI 的示例︰

    ``` syntax
    SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C00T00L00)
    clean
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    rem    ** NOTE: For Advanced Format 4Kn drives,
    rem               change this value to size = 260 ** 
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=16
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
    assign letter="W"
    rem === 4. Recovery tools partition ================
    create partition primary
    format quick fs=ntfs label="Recovery tools"
    assign letter="R"
    set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
    gpt attributes=0x8000000000000001
    rem NON-SYSTEM DRIVE ===============================
    SELECT DISK=NEXT
    clean
    convert gpt
    rem == 1. Microsoft Reserved (MSR) partition =======
    create partition msr size=16
    rem == 2. Data partition ===========================
    create partition primary
    format quick fs=ntfs label="Data"
    assign letter=z
    ```

### <a name="span-idexampleidentifyingsystemdiskafterrebootspanspan-idexampleidentifyingsystemdiskafterrebootspanspan-idexampleidentifyingsystemdiskafterrebootspanidentifying-the-system-drive-after-a-reboot"></a><span id="ExampleIdentifyingSystemDiskAfterReboot"></span><span id="exampleidentifyingsystemdiskafterreboot"></span><span id="EXAMPLEIDENTIFYINGSYSTEMDISKAFTERREBOOT"></span>在重新启动后识别系统驱动器

重新引导之后，可以更改驱动器号。 可以使用以下示例脚本来选择系统驱动器，然后重新分配到 ESP、 恢复和 Windows 分区的字母。

``` syntax
SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C01T01L00)
select partition=1
assign letter=s
select partition=2
assign letter=t
select partition=3
assign letter=w
```

### <a name="span-idexampleformattingnonsystemdisksspanspan-idexampleformattingnonsystemdisksspanspan-idexampleformattingnonsystemdisksspanformatting-non-system-drives"></a><span id="ExampleFormattingNonSystemDisks"></span><span id="exampleformattingnonsystemdisks"></span><span id="EXAMPLEFORMATTINGNONSYSTEMDISKS"></span>非系统驱动器的格式

此示例脚本选择的系统驱动器，然后跳过驱动器而无需修改该驱动器的内容。 脚本然后选择两个非系统驱动器，并在每个驱动器上创建一个单独的、 已格式化的、 空的分区。 分区不接收图像，因此不需要进行专门标识。

基于 UEFI 的示例︰

``` syntax
SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C01T01L00)
SELECT DISK=NEXT
clean
convert gpt
create partition msr size=16
create partition primary
format quick fs=ntfs label="DataDrive1"
SELECT DISK=NEXT
clean
convert gpt
create partition primary
format quick fs=ntfs label="DataDrive2"
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[硬盘上的位置的路径格式](hard-disk-location-path-format.md)

[DiskPart 命令行语法](http://go.microsoft.com/fwlink/?LinkId=128458)

 

 






