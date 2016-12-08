---
author: Justinha
Description: "安全启动"
ms.assetid: 3917c13b-4a23-4d3b-b76a-f22b6f5e5fb1
MSHAttr: PreferredLib:/library/windows/hardware
title: "安全启动"
ms.openlocfilehash: 529e17c30e710062385acd5db161fcfd1388ee59
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="secure-boot"></a>安全启动


安全启动是由 PC 行业的成员，以帮助确保您的 PC 启动使用受信任的个人电脑制造商的软件开发的安全标准。 Windows 8 中引入了安全引导支持。

当计算机启动时，固件检查每个启动软件，包括固件驱动程序 (选项 Rom)、 EFI 应用程序和操作系统的签名。 如果签名是很好，PC 启动和固件将控制权交给操作系统。

 

## <a name="span-idfrequentlyaskedquestionsspanspan-idfrequentlyaskedquestionsspanspan-idfrequentlyaskedquestionsspanfrequently-asked-questions"></a><span id="Frequently_asked_questions_"></span><span id="frequently_asked_questions_"></span><span id="FREQUENTLY_ASKED_QUESTIONS_"></span>常见问题及的解答︰


-   **我要升级到最新版本的 Windows 需要安全启动？**

    No. 没有任何额外的硬件或固件要求从 Windows Vista 或 Windows 7 升级到最新版本的 Windows。


-   **如果新硬件不受信任的我的 PC 制造商，怎么样？**

    您的计算机可能无法启动。 有两种可能发生的问题︰

    -   固件可能不信任操作系统、 选项 ROM、 驱动程序或应用程序，因为它不受安全启动数据库。

    -   某些硬件所需的内核模式驱动程序必须签名。 注意︰ 许多较旧的 32 位 (x86) 驱动程序没有签名，因为内核模式驱动程序签名是安全引导的新要求。 有关更多信息，请参阅[安全引导功能签名对内核模式驱动程序的要求](http://msdn.microsoft.com/library/windows/desktop/hh848062.aspx)。

    有关更多信息，请参阅[与安全启动启用了 Windows 8 将不再启动安装新硬件后](http://support.microsoft.com/kb/2800988)。

-   **如何添加硬件或软件或运行的操作系统，没有已受信任的我的 PC 制造商？**

    -   大多数的软件和硬件应该无缝地在 Windows 由于工作了由 Microsoft 中的受信任证书签名以支持 UEFI 安全启动。

    -   您可以检查来自微软和/或 PC 制造商的软件更新。

    -   您可以联系您的制造商联系，以请求新的硬件或软件添加到安全启动数据库。

    -   对于大多数 Pc，您可以禁用安全通过 PC 的 BIOS 的启动。 有关详细信息，请参阅[禁用安全引导](disabling-secure-boot.md)。

    -   您可以自定义哪些证书信任的安全通过 PC 的 BIOS，在自定义安全启动菜单中的启动。

        
-   **如何编辑我的 PC 安全启动数据库？**

    这只可以通过个人电脑制造商。

## <a name="span-idmanufacturingrequirementsspanspan-idmanufacturingrequirementsspanspan-idmanufacturingrequirementsspanmanufacturing-requirements"></a><span id="Manufacturing_Requirements"></span><span id="manufacturing_requirements"></span><span id="MANUFACTURING_REQUIREMENTS"></span>制造要求


安全启动需要满足 UEFI 规范版本 2.3.1，堪误表 C 的 PC 或更高版本。

安全启动支持 UEFI 2 类和 3 类的 Pc。 UEFI 类 2 台 pc，启用安全启动时，兼容性支持模块 (CSM) 必须禁用，以使个人电脑只可以启动授权、 基于 UEFI 的操作系统。

安全启动不需要受信任的平台模块 (TPM)。

若要启用内核模式调试，请启用 TESTSIGNING，或禁用 NX，您必须禁用安全启动。 对于 oem 的详细信息，请参阅[Windows 8.1 安全启动密钥创建和管理指导](windows-secure-boot-key-creation-and-management-guidance.md)。

## <a name="span-idhowitworksspanspan-idhowitworksspanspan-idhowitworksspanhow-it-works"></a><span id="How_it_works"></span><span id="how_it_works"></span><span id="HOW_IT_WORKS"></span>它的工作原理


OEM 使用固件制造商提供的说明进行操作来创建安全启动键，并将它们存储在计算机固件中。 有关信息，请参阅[Windows 8.1 安全启动密钥创建和管理指导](windows-secure-boot-key-creation-and-management-guidance.md)，[安全启动密钥生成和签名使用 HSM （示例）](secure-boot-key-generation-and-signing-using-hsm--example.md)，或与硬件制造商联系。

添加 UEFI 驱动程序 (也称为选项 Rom) 时，您还需要确保这些签名并包含在安全启动数据库。 有关信息，请参阅[UEFI 验证选项 ROM 验证指南](uefi-validation-option-rom-validation-guidance.md)。

安全启动激活时在一台电脑上，电脑检查软件，包括选项 Rom 和操作系统、 数据库维护的固件中的已知良好签名的每个片段。 每款软件是有效的如果固件运行软件和操作系统。

### <a name="span-idsignaturedatabasesandkeysspanspan-idsignaturedatabasesandkeysspanspan-idsignaturedatabasesandkeysspansignature-databases-and-keys"></a><span id="Signature_Databases_and_Keys"></span><span id="signature_databases_and_keys"></span><span id="SIGNATURE_DATABASES_AND_KEYS"></span>数据库签名和密钥

PC 部署之前，OEM 将存储到计算机上的安全启动数据库。 这包括*签名数据库*(db)、*撤消签名数据库*(dbx) 和*密钥注册密钥数据库*(KEK) 到 PC 上。 这些数据库存储在生产的时候在固件非易失内存 (NV-RAM)。

*签名数据库*(db) 和*吊销签名数据库*(dbx) 列表签名或图像 （uefi） 应用程序，操作 （如 Microsoft 操作系统加载程序或启动管理器），系统加载程序的哈希值和 UEFI 驱动程序可以加载到单个 PC，并吊销的图像中的项的已不再可信，可能无法加载。

*键注册密钥数据库*(KEK) 是一个单独的数据库的签名可用于更新签名数据库和吊销的签名数据库的密钥。 Microsoft 要求使用指定的项包括在 KEK 数据库，以便将来 Microsoft 可以签名数据库中添加新的操作系统或吊销的签名数据库中添加已知错误的图像。

添加这些数据库之后，和最终的固件验证和测试后，OEM 锁定进行编辑，但用正确的密钥签名的更新固件，或正在使用固件菜单，然后生成的平台键 (PK) 的物理存在用户更新。 可以用于 PK，签名 KEK 的更新或关闭安全启动。

Oem 应该联系其固件制造商获得工具和帮助创建这些数据库。 有关更多信息，请参阅[Windows 8.1 安全启动密钥创建和管理指导](windows-secure-boot-key-creation-and-management-guidance.md)。

### <a name="span-idbootsequencespanspan-idbootsequencespanspan-idbootsequencespanboot-sequence"></a><span id="Boot_Sequence"></span><span id="boot_sequence"></span><span id="BOOT_SEQUENCE"></span>启动顺序

1.  打开电脑后，签名数据库每个对照检查的平台键。

2.  如果固件不是可信的 （uefi） 固件必须启动 OEM 特定的恢复来恢复信任的固件。

3.  如果问题与 Windows 启动管理器中，固件将尝试启动 Windows 启动管理器的一个备份副本。 如果这也失败了，固件必须启动 OEM 特定补救措施。

4.  Windows 启动管理器已开始运行，如果与 NTOS 内核的驱动程序有问题之后，将加载 Windows 恢复环境 (Windows RE)，以便可以恢复这些驱动程序或内核映像。

5.  Windows 加载恶意软件。

6.  Windows 加载其他驱动程序，内核和用户模式进程初始化。

有关详细信息，请参阅白皮书︰[安全引导和测量引导︰ 强化早期启动组件免受恶意软件](http://go.microsoft.com/fwlink/?LinkId=278911)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[未正确配置安全启动︰ 疑难解答](secure-boot-isnt-configured-correctly-troubleshooting.md)

[未正确配置安全启动︰ 确定计算机是否在制造模式下 （制造商的信息）](secure-boot-isnt-configured-correctly-determine-if-the-pc-is-in-a-manufacturing-mode--info-for-manufacturers.md)

[安全的引导和标准的引导︰ 强化防止恶意软件的早期启动组件](http://go.microsoft.com/fwlink/?LinkId=278911)

[UEFI 固件](uefi-firmware.md)

 

 






