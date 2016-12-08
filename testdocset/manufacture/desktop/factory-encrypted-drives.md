---
author: Justinha
Description: "工厂加密的驱动器"
ms.assetid: 3469481b-f380-4585-87c8-ca8a267fe607
MSHAttr: PreferredLib:/library/windows/hardware
title: "工厂加密的驱动器"
ms.openlocfilehash: fcc0d7626018fcafe25af1e14b2f1fdd39cd1cf0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="factory-encrypted-drives"></a>工厂加密的驱动器


您可以将 Windows 安装在工厂加密的驱动器，也称为加密的硬盘驱动器 (eHDD) 上。 *工厂加密的驱动器*是能够完全磁盘加密的驱动器。

默认情况下，工厂加密的驱动器上安装 Windows 时 Windows 自动将驱动器使用受信任的计算组 (TCG) 和 IEEE 1667 传输加密标准。

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


要到工厂加密的驱动器上安装 Windows，请使用以下方法︰

1.  固件︰ UEFI 版本 2.3.1 已配置为使用 EFI 存储安全协议。

2.  硬件︰ 硬盘驱动器能够使用 TCG 和 IEEE 1667 传输加密标准。

## <a name="span-idusingotherencryptionstandardsspanspan-idusingotherencryptionstandardsspanspan-idusingotherencryptionstandardsspanusing-other-encryption-standards"></a><span id="Using_other_encryption_standards"></span><span id="using_other_encryption_standards"></span><span id="USING_OTHER_ENCRYPTION_STANDARDS"></span>使用其他加密标准，


若要使用其他加密标准上您的驱动器，则必须首先禁用自动资源调配 Windows 提供的驱动器。 为此在新的安装，设置无人参与的 Microsoft 的 Windows-EnhancedStorage-Adm/TCGSecurityActivationDisabled 为**true**。 有关详细信息，请参阅[无人参与的 Windows 安装程序参考](https://msdn.microsoft.com/library/windows/hardware/dn923277)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[硬盘驱动器和分区](hard-drives-and-partitions.md)

 

 






