---
author: Justinha
Description: "BitLocker 驱动器加密"
ms.assetid: 47d6aadf-0496-4a8a-b0a5-dfb6fa9f5748
MSHAttr: PreferredLib:/library/windows/hardware
title: "BitLocker 驱动器加密"
ms.openlocfilehash: 25fed58132322a1c114e031978dd7a4d2579b831
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bitlocker-drive-encryption"></a>BitLocker 驱动器加密


本主题重点介绍部署 Windows BitLocker 驱动器加密解决方案的要求。 BitLocker 有关的详细信息，请参阅 TechNet 网站上的[BitLocker 驱动器加密](http://go.microsoft.com/fwlink/?LinkId=116601)。

## <a name="span-idwhatisbitlockerdriveencryptionspanspan-idwhatisbitlockerdriveencryptionspanspan-idwhatisbitlockerdriveencryptionspanwhat-is-bitlocker-drive-encryption"></a><span id="What_Is_BitLocker_Drive_Encryption_"></span><span id="what_is_bitlocker_drive_encryption_"></span><span id="WHAT_IS_BITLOCKER_DRIVE_ENCRYPTION_"></span>BitLocker 驱动器加密是什么？


BitLocker 提供保护计算机的脱机数据和操作系统。 BitLocker 可确保如果已的安装的操作系统处于脱机状态时，计算机被篡改，运行 Windows® 的计算机存储的数据不会显示。 BitLocker 将使用被称为受信任的平台模块 (TPM) 以提供增强的数据保护并保留早期引导组件的完整性的微芯片。 TPM 可帮助保护您的数据被盗或未经授权的查看加密整个 Windows 卷。

BitLocker 旨在提供最无缝与具有兼容 TPM 微芯片和 BIOS 的计算机的最终用户体验。 兼容的 TPM 指 1.2 版 TPM 具有支持所需度量静态根的信任，由受信任计算组定义的 BIOS 修改。 TPM 使用 BitLocker 可帮助提供无缝的保护，当计算机重新启动时进行交互。

TPM 驱动程序文件的路径是 %WINDIR%\\Inf\\Tpm.inf。 有关如何将 TPM 驱动程序添加到 Windows 预安装环境 (Windows PE) 的信息，请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

## <a name="span-idbitlockerdriveencryptionpartitioningrequirementsspanspan-idbitlockerdriveencryptionpartitioningrequirementsspanspan-idbitlockerdriveencryptionpartitioningrequirementsspanbitlocker-drive-encryption-partitioning-requirements"></a><span id="BitLocker_Drive_Encryption_Partitioning_Requirements"></span><span id="bitlocker_drive_encryption_partitioning_requirements"></span><span id="BITLOCKER_DRIVE_ENCRYPTION_PARTITIONING_REQUIREMENTS"></span>BitLocker 驱动器加密分区要求


BitLocker 必须使用不同于 Windows 分区的系统分区。 系统分区︰

-   必须配置为活动分区。

-   不能加密或用于存储用户文件。

-   必须有至少 100 兆字节 (MB) 的空间。

-   必须有至少 50 MB 的可用空间。

-   可能与恢复分区共享。

BitLocker 分区要求有关的详细信息，请参阅[硬盘驱动器和分区概述](hard-drives-and-partitions.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[硬驱动器和分区概述](hard-drives-and-partitions.md)

 

 






