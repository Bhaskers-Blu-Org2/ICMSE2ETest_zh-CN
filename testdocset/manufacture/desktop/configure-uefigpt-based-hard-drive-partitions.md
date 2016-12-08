---
author: Justinha
Description: "基于 UEFI/GPT 的硬盘分区"
ms.assetid: a6c97be2-1d1f-4639-9771-3b17234370e6
MSHAttr: PreferredLib:/library/windows/hardware
title: "基于 UEFI/GPT 的硬盘分区"
ms.openlocfilehash: 5e95875f7bc2c5219f79a082325d518e087760a0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefigpt-based-hard-drive-partitions"></a>基于 UEFI/GPT 的硬盘分区


为基于统一可扩展固件接口 （uefi） – 设备部署 Windows 时创建自定义的分区布局的硬盘驱动器 (Hdd)、 固态驱动器 (SSDs) 和其它驱动器。

**请注意** 如果您使用 Windows 10 上桌面版本 （家庭、 Pro、 企业和教育），更新按钮恢复脚本自定义的分区布局因此恢复工具可以重建时所需的自定义的分区布局。

 

本主题︰

-   [驱动器分区规则](#diskpartitionrules)
-   [默认的布局](#recommendedpartitionconfigurations)
-   [Diskpart 脚本示例](#relatedsamplefiles)

## <a name="span-iddiskpartitionrulesspanspan-iddiskpartitionrulesspanspan-iddiskpartitionrulesspandrive-partition-rules"></a><span id="DiskPartitionRules"></span><span id="diskpartitionrules"></span><span id="DISKPARTITIONRULES"></span>驱动器分区规则


在 Windows 部署到基于 UEFI 的设备时，必须使用 GUID 分区表 (GPT) 文件系统包含 Windows 的分区的硬盘进行格式化。 GPT 或主引导记录 (MBR) 文件格式，可以使用其他驱动器。

GPT 驱动器可能有多达 128 个分区。

每个分区可以有最多 18 千兆兆字节 （~18.8 百万兆兆字节） 的空间。

**Windows 分区要求︰**

-   **系统分区**

    该设备必须包含一个系统分区。 GPT 在驱动器上，这被称为 EFI 系统分区或 ESP。 此分区通常存储在主硬盘上。 该设备引导到此分区。

    此分区的最小大小是 100 MB，并且必须使用 FAT32 文件格式进行格式化。

    此分区管理的操作系统，并且不应包含任何其他文件，包括 Windows RE 工具。

    **请注意**  
    对于高级的格式 4k 本机驱动器 （4 KB 的每个的扇区） 驱动器，最小是 260 MB，由于 FAT32 文件格式的限制。 FAT32 驱动器的最小分区大小将计算为 x 65527 = 256 MB 的扇区大小 (4 KB)。

    高级的格式的 512e 驱动器不受此限制，因为它们仿真的扇区大小为 512 字节。 512 字节 x 65527 = 32 MB，这小于 100 MB 此分区的最小大小。

     

-   **Microsoft® 保留分区 (MSR)**

    从 Windows 10 开始，MSR 的大小为 16 MB。

    将 MSR 添加到每个 GPT 驱动器用于进行分区管理。 MSR 是保留的分区不接收分区 id。 它不能存储用户数据。

-   **其他实用程序分区**

    在 Windows、 数据和图像恢复分区之前必须位于不受 Windows 的其他实用程序分区。 这样，最终用户可以执行操作，如调整 Windows 分区大小而不影响系统实用程序。

    防止最终用户意外修改实用程序分区，通过识别其使用 GPT 属性。 这可防止这些分区文件资源管理器中显示。

    **若要将分区设置为实用程序分区**

    -   当要通过使用**DiskPart**工具来部署 Windows 时，使用**属性卷采用 GPT\_特性\_平台\_必需的**命令后创建分区标识为实用工具分区的分区。 有关详细信息，请参阅 MSDN 主题︰[分区\_信息\_GPT 结构](http://go.microsoft.com/fwlink/p/?linkid=240300)。

    **若要验证有系统和实用程序分区**

    1.  单击**开始**，右键单击**该计算机**，然后单击**管理**。 打开**计算机管理**窗口。
    2.  单击**磁盘管理**。 将显示可用的驱动器和分区的列表。
    3.  在驱动器和分区的列表中，请确认的系统和实用程序分区存在，并且未分配驱动器号。
-   **Windows 分区**
    -   分区必须有至少 20 千兆字节 (GB) 的 64 位版本的驱动器空间或 16 GB 的 32 位版本。
    -   Windows 分区必须使用 NTFS 文件格式进行格式化。
    -   用户已完成全新体验 (OOBE) 之后，Windows 分区必须有足够 10 GB 的可用空间。
-   **恢复工具分区**

    此分区必须至少 300 MB。

    此分区必须有足够的空间用于 Windows 恢复环境工具图像 (winre.wim，通常之间 250-300 MB，这取决于基本语言和自定义项添加)，再加上足够的可用空间，以便由备份实用程序可以捕获该分区︰

    -   如果小于 500 MB 的分区，必须至少 50 MB 的可用空间。
    -   如果分区是 500 MB 或更大，它必须具有至少 320 MB 的可用空间。
    -   如果分区大于 1 GB，我们建议，它应该有至少 1 GB 的空闲空间。
    -   此分区必须使用类型 ID: DE94BBA4-06 D D 1-4 40-A16A-BFD50179D6AC。
    -   恢复工具应该会比 Windows 分区支持自动故障切换，从而支持一个单独的分区中启动 Windows BitLocker 驱动器加密通过加密分区。

    我们建议您在 Windows 分区后立即放置此分区。 这允许 Windows 修改，如果将来的更新需要更大的恢复映像稍后重新创建该分区。

-   **数据分区**

    Windows 10 的建议的分区布局不包括数据分区。 但是，如果需要的数据分区，应将它们放在 Windows RE 分区后。 这样，以后对 Windows RE 通过收缩 Windows 分区发展 Windows RE 分区更新。

    此布局，使最终用户能够删除数据分区和合并与 Windows 分区的空间更难。 为此，Windows RE 分区必须移至末尾的数据分区，从回收未使用的空间，以便 Windows 分区可以扩展。

    Windows 10 不包括功能或实用程序，以促进这一过程。 但是，制造商可以开发和提供这类实用工具，如果电脑附带的数据分区。

## <a name="span-idrecommendedpartitionconfigurationsspanspan-idrecommendedpartitionconfigurationsspanspan-idrecommendedpartitionconfigurationsspanpartition-layout"></a><span id="RecommendedPartitionConfigurations"></span><span id="recommendedpartitionconfigurations"></span><span id="RECOMMENDEDPARTITIONCONFIGURATIONS"></span>分区布局


基于 UEFI 的计算机的默认分区布局︰ 一个系统分区、 MSR、 Windows 分区和恢复工具分区。 如果安装 Windows 使用由 Windows 图像处理和配置设计器 (ICD) 创建可引导 usb 闪存盘时，默认情况下创建以下布局。

![缺省分区布局示意图︰ 系统、 msr、 窗口和恢复](images/dep-win10-partitions-uefi.png)

此布局允许您使用 Windows BitLocker 驱动器加密通过这两个窗口和 Windows 恢复环境。

## <a name="span-idrelatedsamplefilesspanspan-idrelatedsamplefilesspanspan-idrelatedsamplefilesspansample-files-configure-drive-partitions-by-using-windows-pe-and-diskpart-scripts"></a><span id="RelatedSampleFiles"></span><span id="relatedsamplefiles"></span><span id="RELATEDSAMPLEFILES"></span>示例文件︰ 使用 Windows PE 和 DiskPart 脚本配置的驱动器分区


对于基于映像的部署，引导到[Windows PE](winpe-intro.md)，PC，然后使用**DiskPart**工具在目标计算机上创建的分区结构。

**请注意**  
在**DiskPart**这些示例中，分区指派的盘符︰ 系统 = S，Windows = W 和恢复 = R。 MSR 分区不接收驱动器号。

我们建议将 Windows 的驱动器号更改为末尾的字母，例如 W，以避免驱动器号冲突的信件。 不要使用 X，因为 Windows PE 为保留该驱动器号。 重新启动设备后，Windows 分区分配的字母 C，和其他分区不接收驱动器号。

如果在重新启动时，Windows PE 重新分配磁盘字母按字母顺序，开头字母 C，而不考虑 Windows 安装程序中的配置。 这种配置可以更改根据存在的不同的驱动器，如 USB 闪存驱动器。

 

以下步骤描述如何在您的硬盘进行分区，并准备好应用映像。 在以下各节来完成这些步骤中，您可以使用代码。

**以硬盘进行分区，并准备好应用映像**

1.  将以下代码保存在 USB 闪存驱动器上的文本文件 (CreatePartitions UEFI.txt)。

    ``` syntax
    rem == CreatePartitions-UEFI.txt ==
    rem == These commands are used with DiskPart to
    rem    create four partitions
    rem    for a UEFI/GPT-based PC.
    rem    Adjust the partition sizes to fill the drive
    rem    as necessary. ==
    select disk 0
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
    rem                (winre.wim) plus free space                   **
    rem ==    c. Prepare the Windows partition ========= 
    format quick fs=ntfs label="Windows"
    assign letter="W"
    rem === 4. Recovery tools partition ================
    create partition primary
    format quick fs=ntfs label="Recovery tools"
    assign letter="R"
    set id="de94bba4-06d1-4d40-a16a-bfd50179d6ac"
    gpt attributes=0x8000000000000001
    list volume
    exit
    ```

2.  使用 Windows PE 启动目标计算机。

3.  清理和分区的驱动器。 在此示例中， *F*是 USB 闪存驱动器的盘符。

    ``` syntax
    DiskPart /s F:\CreatePartitions-UEFI.txt
    ```

4.  如果您使用自定义的分区布局上 Windows 10 对于桌面版本，更新按钮恢复脚本，以便恢复工具可以重新创建自定义的分区布局时需要。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="NextSteps"></span><span id="nextsteps"></span><span id="NEXTSTEPS"></span>下一步行动


使用部署脚本将 Windows 映像应用于新创建的分区。 有关详细信息，请参阅[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[配置基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md)

[BitLocker 驱动器加密](bitlocker-drive-encryption.md)

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[配置磁盘镜像](http://go.microsoft.com/fwlink/?LinkId=733824)

[窗口和 GPT 常见问题解答](http://go.microsoft.com/fwlink/?LinkId=88211)

 

 






