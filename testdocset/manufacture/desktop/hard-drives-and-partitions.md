---
author: Justinha
Description: "硬盘驱动器和分区"
ms.assetid: bb453d9d-e819-4301-834d-09486d3e64e9
MSHAttr: PreferredLib:/library/windows/hardware
title: "硬盘驱动器和分区"
ms.openlocfilehash: 08575f3be7ef4edc973a368e7b7e64ea315fbbfc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="hard-drives-and-partitions"></a>硬盘驱动器和分区


在本节中，您将学习方法可以将 Windows 部署到不同的驱动器，包括硬盘驱动器、 固态驱动器 (SSDs) 或虚拟硬盘 (Vhd)。 您还将了解有关 Windows 部署时必须考虑的因素。

## <a name="span-idwhatsnewinwindows10spanspan-idwhatsnewinwindows10spanspan-idwhatsnewinwindows10spanwhats-new-in-windows-10"></a><span id="What_s_new_in_Windows_10"></span><span id="what_s_new_in_windows_10"></span><span id="WHAT_S_NEW_IN_WINDOWS_10"></span>Windows 10 中的新增功能


-   使用精简的操作系统和单采购在硬盘上保存更多的空间︰[袖珍 OS，单采购，和图像优化](compact-os.md)。
-   使用 FFU 图像格式应用到您的设备图像更快︰[部署 Windows 使用全闪存更新 (FFU)](deploy-windows-using-full-flash-update--ffu.md)
-   在 （家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10，我们已经更改的分区布局。 虽然我们仍然使用单独的恢复工具图像，Windows 将不再需要一个单独的完整系统恢复的图像使用点击式重置功能。 这样可以节省几 GB 的驱动器空间。

    现在，我们建议您将 Windows 恢复工具分区放在 Windows 分区后立即。 这允许 Windows 修改，如果将来的更新需要更大的恢复映像稍后重新创建该分区。

    如果您使用脚本来部署 Windows，签出我们对于不同设备固件类型 （更新的基于 UEFI 的 BIOS 或旧的 BIOS） 创建了新的示例脚本。 若要了解详细信息，请参阅[基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md)和[基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md)。

-   不再需要在 SSD 驱动器上运行 Windows 系统评估测试 (WinSAT)。 Windows 检测到 SSD 驱动器和相应地调整自身。
-   [基于 UEFI/GPT 的驱动器](configure-uefigpt-based-hard-drive-partitions.md)，我们已减少了推荐的 MSR 分区大小从 128 MB 到 16 MB。

## <a name="span-idharddisksspanspan-idharddisksspanspan-idharddisksspandrive-types"></a><span id="HardDisks"></span><span id="harddisks"></span><span id="HARDDISKS"></span>驱动器类型


您可以将 Windows 安装到硬盘，硬盘和固态驱动器。 为了提高安全性，可以使用工厂预先已加密的硬盘驱动器。 一台计算机可能包含多个驱动器。

### <a name="span-idssdsspanspan-idssdsspanspan-idssdsspansolid-state-drives"></a><span id="SSDs"></span><span id="ssds"></span><span id="SSDS"></span>固态驱动器

固态驱动器 (SSD) 是使用固态内存来存储持久数据的硬盘。 SSD 必须具有至少 16 千兆字节 (GB) 的空间来安装 Windows。 有关磁盘空间和 RAM 注意事项的详细信息，请参阅[袖珍 OS，单采购，和图像优化](compact-os.md)。

**请注意**  不再需要在 SSD 驱动器上运行 Windows 系统评估测试 (WinSAT)。 现在，Windows 检测到 SSD 驱动器，并将相应地调整自身。

 

### <a name="span-idadvancedformatspanspan-idadvancedformatspanspan-idadvancedformatspanadvanced-format-drives"></a><span id="AdvancedFormat"></span><span id="advancedformat"></span><span id="ADVANCEDFORMAT"></span>高级的格式的驱动器

可以使用一些高级格式化驱动器，以提供额外的驱动器空间。

在基于 BIOS 的或者基于 UEFI 的计算机支持高级的格式 512 模拟 (512e) 驱动器。

在基于 UEFI 的计算机支持高级的格式 4k 本机 (4Kn) 驱动器。

**警告**  
对于高级的格式 4k 本机驱动器 （4 KB 的每个的扇区） 驱动器，请最小分区大小是 260 MB，由于 FAT32 文件格式的限制。 FAT32 驱动器的最小分区大小将计算为 x 65527 = 256 MB 的扇区大小 (4 KB)。 有关详细信息，请参阅[Configure UEFI/GPT-Based 硬驱动器分区](configure-uefigpt-based-hard-drive-partitions.md)。

 

### <a name="span-idencrypteddisksandpartitionsspanspan-idencrypteddisksandpartitionsspanspan-idencrypteddisksandpartitionsspanfactory-encrypted-hard-drives"></a><span id="EncryptedDisksAndPartitions"></span><span id="encrypteddisksandpartitions"></span><span id="ENCRYPTEDDISKSANDPARTITIONS"></span>工厂加密硬盘

为了帮助保护您的部署环境，可以使用工厂的预加密的硬盘之前安装 Windows 或任何其他的软件，防止未授权的访问。 有关详细信息，请参阅[工厂加密的驱动器](factory-encrypted-drives.md)。

### <a name="span-idmultipleharddisksspanspan-idmultipleharddisksspanspan-idmultipleharddisksspanmultiple-hard-drives"></a><span id="MultipleHardDisks"></span><span id="multipleharddisks"></span><span id="MULTIPLEHARDDISKS"></span>多个硬盘

如果您有多个硬驱的设备上安装 Windows，您可以使用磁盘位置路径以确保您的图像应用到目标驱动器。

若要执行此操作，请使用`diskpart SELECT DISK=<disk location path>`命令以选择每个驱动器。 例如︰

`SELECT DISK=PCIROOT(0)#PCI(0100)#ATA(C00T00L00)`

**请注意**  
系统驱动器可能不显示为磁盘 0 的 DiskPart 工具。 重新启动时，系统可能到驱动器分配不同的数字。 不同的计算机具有相同的驱动器配置可以有不同的磁盘号。

若要了解详细信息，请参阅[配置多个硬盘驱动器](configure-multiple-hard-drives.md)和[硬盘位置路径格式](hard-disk-location-path-format.md)。

 

## <a name="span-idpartitionsspanspan-idpartitionsspanspan-idpartitionsspanpartitions"></a><span id="Partitions"></span><span id="partitions"></span><span id="PARTITIONS"></span>分区


可以将硬盘空间划分成多个分区。 您可以创建单独的系统，恢复、 Windows 或数据分区。

为提高 Windows 分区或数据分区的安全性，可以使用 BitLocker 加密分区。 有关详细信息，请参阅[BitLocker 驱动器加密](bitlocker-drive-encryption.md)。

分区类型必须匹配的计算机的固件。 您可以将 Windows 安装硬盘上的基于任何以下类型的固件︰

-   **基本输入/输出系统 (BIOS)**。 使用主启动记录 (MBR) 分区结构。

-   **可扩展固件接口 (EFI) (1 类)**: 使用 GUID 分区表 (GPT) 分区结构。

-   **统一可扩展固件接口 (UEFI) 类 2**︰ 使用 GPT 分区结构。 此外包括可以使用 BIOS 函数，其中包括 MBR 分区结构兼容性支持模块 (CSM)。 本模块可以启用或禁用在固件中。

-   **统一可扩展固件接口 (UEFI) 3 类**︰ 使用 GPT 分区结构。

若要确定您的系统类型，请咨询您的硬件制造商联系。

### <a name="span-idsystempartitionspanspan-idsystempartitionspanspan-idsystempartitionspansystem-and-utility-partitions"></a><span id="SystemPartition"></span><span id="systempartition"></span><span id="SYSTEMPARTITION"></span>系统和实用程序分区

*系统分区*是包含将加载 Windows 所必需的特定于硬件的文件的分区。

默认情况下，在 Windows 安装过程中 Windows 存储这些特定于硬件的文件在一个单独的分区中。 这使计算机能够使用下面的语句︰

-   **安全工具**。 某些安全工具，例如 BitLocker，都需要一个单独的系统分区。

-   **恢复工具**。 一些恢复工具，如 Windows 恢复环境 (Windows RE)，都需要一个单独的系统分区。

-   **多个操作系统**。 如果计算机有多个操作系统，如 Windows 桌面版本 10 和 Windows 7 计算机显示操作系统的列表。 然后，用户可以选择要启动的操作系统。 当系统启动文件在一个单独的分区上，可以很方便地删除 Windows 分区或 Windows 的新副本替换该分区。

我们建议添加系统实用程序分区之前 Windows 分区，因为该分区的顺序，需要全面系统恢复时，有助于防止恢复工具覆盖的系统和实用程序分区。

有关如何配置系统分区时应用映像的信息，请参阅[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)。

### <a name="span-idmicrosoftrecoverypartitionsspanspan-idmicrosoftrecoverypartitionsspanspan-idmicrosoftrecoverypartitionsspanmicrosoft-reserved-partition-msr"></a><span id="MicrosoftRecoveryPartitions"></span><span id="microsoftrecoverypartitions"></span><span id="MICROSOFTRECOVERYPARTITIONS"></span>Microsoft 保留分区 (MSR)

MSR UEFI/GPT 的系统上，用于支持软件组件的以前使用隐藏扇区。

有关配置 MSR 分区的详细信息，请参阅[Configure UEFI/GPT-Based 硬驱动器分区](configure-uefigpt-based-hard-drive-partitions.md)。

有关 MSR 分区的详细信息，请参阅[Windows 和 GPT 常见问题解答](http://go.microsoft.com/fwlink/?LinkId=267523)

### <a name="span-idrecoverypartitionspanspan-idrecoverypartitionspanspan-idrecoverypartitionspanrecovery-partitions"></a><span id="RecoveryPartition"></span><span id="recoverypartition"></span><span id="RECOVERYPARTITION"></span>恢复分区

建议针对 Windows 恢复环境 (Windows RE) 添加一个单独的分区末尾的硬驱。 使用此分区顺序，如果将来更新需要添加到或替换 Windows RE 工具分区，Windows 能够自动管理的分区大小。

对于基于 BIOS/MBR 系统，则仍然可以合并 Windows RE 工具分区与系统分区。 若要节省磁盘空间，请考虑创建逻辑分区可以避免四分区限制。 有关更多信息，请参阅[配置四个以上分区基于 BIOS/MBR 硬盘上](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md)。

桌面版本的 Windows 10，已不再有必要，可以创建和维护一个单独的完整系统恢复映像。 Windows 可执行刷新或重置使用内置的工具。

### <a name="span-iddatapartitionspanspan-iddatapartitionspanspan-iddatapartitionspandata-partitions"></a><span id="DataPartition"></span><span id="datapartition"></span><span id="DATAPARTITION"></span>数据分区

数据分区是一个分区用于存储用户数据。 主操作系统系统有可能被替换，或者在多个操作系统在同一设备上，如 Windows 10 和 Windows 7 存在时，不同的数据分区可以启用更容易维护的情况。 当设备有多个硬驱时，一个数据分区可能存储在另一个驱动器。

**警告**  
对于典型的单驱动器配置，不建议使用不同的数据分区。 有两个主要原因︰

-   分区不会自动保护存储在用户配置文件文件夹之外的数据。 例如，来宾用户可能可以访问到未受保护的数据分区中的文件。
-   如果将用户配置文件文件夹的默认位置更改为任何非系统卷的卷中时，不能服务您的图像。 计算机可能不适用于更新、 修补程序或服务包安装。 更改默认文件夹位置相关的已知问题列表，请参阅[的已知问题的 FolderLocation 设置的说明](http://go.microsoft.com/fwlink/?LinkId=142275)。

 

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>请参见


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">内容类型</th>
<th align="left">参考</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>部署</strong></p></td>
<td align="left"><p>[配置基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md) | [配置基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md) | [配置基于 BIOS/MBR 硬盘上的四个以上分区](configure-more-than-four-partitions-on-a-biosmbr-based-hard-disk.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>多个驱动器</strong></p></td>
<td align="left"><p>[配置多个硬盘驱动器](configure-multiple-hard-drives.md) | [硬盘位置路径格式](hard-disk-location-path-format.md) | [内部和外部的 SATA 端口配置](http://go.microsoft.com/fwlink/p/?LinkId=321830) | [配置磁盘镜像](http://go.microsoft.com/fwlink/?LinkId=733824)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>使用较小的驱动器</strong></p></td>
<td align="left"><p>[压缩的操作系统，单采购，和图像优化](compact-os.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>操作</strong></p></td>
<td align="left"><p>[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md) | [部署 Windows 使用全闪存更新 (FFU)](deploy-windows-using-full-flash-update--ffu.md) | [部署 VHD （本机引导） 上的 Windows](deploy-windows-on-a-vhd--native-boot.md) | [工厂加密的驱动器](factory-encrypted-drives.md) | [BitLocker 驱动器加密](bitlocker-drive-encryption.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>疑难解答</strong></p></td>
<td align="left"><p>[修复上双重引导计算机的启动菜单](repair-the-boot-menu-on-a-dual-boot-pc.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>工具和设置</strong></p></td>
<td align="left"><p>[UEFI 固件](uefi-firmware.md) | [Windows 和 GPT 常见问题](http://go.microsoft.com/fwlink/?LinkId=88211) | [BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md) | [DiskPart 命令行语法](http://go.microsoft.com/fwlink/?LinkId=128458) | [WIM 与 VHD 与 FFU︰ 比较图像文件格式](wim-vs-ffu-image-file-formats.md)</p></td>
</tr>
</tbody>
</table>

 

 

 






