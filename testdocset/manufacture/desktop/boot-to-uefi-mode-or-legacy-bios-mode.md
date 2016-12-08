---
author: Justinha
Description: "引导至 UEFI 模式或传统 BIOS 模式"
ms.assetid: 04ad6b97-b41d-40fd-88a7-d63d4722c336
MSHAttr: PreferredLib:/library/windows/hardware
title: "引导至 UEFI 模式或传统 BIOS 模式"
ms.openlocfilehash: a574e00054ceb2017cc6af10d22c065ac858669b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-to-uefi-mode-or-legacy-bios-mode"></a>引导至 UEFI 模式或传统 BIOS 模式


从您的 USB、 DVD 或网络位置安装 Windows 时，到 UEFI 模式或旧的 BIOS 兼容性模式下引导。

如果安装 Windows 使用错误的模式时，将无法使用该固件模式下的功能，而无需重新格式化驱动器。

**在启动过程中选择固件模式**

1.  启动 PC。 在固件启动时运行，请按打开启动设备菜单键。 例如，按下 esc 键、 F2、 F9、 f12 键或其他键输入固件或引导菜单。

2.  在启动设备菜单中，选择标识固件模式和设备的命令。 例如，选择**UEFI USB 驱动器**或**网络上的 BIOS**。

    **请注意**  
    您可能会看到同一个设备的单独命令。 例如，您可能会看到**UEFI USB 驱动器**和**BIOS USB 驱动器**。 每个命令使用相同的设备和媒体，但在不同的固件模式下启动电脑。

     

    如果您的设备没有启动设备选项︰

    -   检查固件菜单，用于启用或禁用 BIOS 兼容性模式中的选项。

    -   要使用 BIOS 兼容模式，请检查固件菜单中的选项来禁用 UEFI SecureBoot 功能。

    -   对于较旧的 Pc (Windows® 7 时代或更早版本)，查找选项**从文件引导**，并浏览到\\EFI\\启动\\BOOTX64。EFI 在该设备上的文件。

**使用下列任一方法来帮助确保使用正确的固件模式安装 Windows**

1.  如果使用 Windows 安装程序或 Windows 安装 DVD 安装 Windows 时，请在目标电脑上使用预先设好格式的硬盘。 （uefi） 模式或 BIOS 模式的 MBR 文件格式使用 GPT 文件格式。 Windows 安装程序运行时，如果计算机引导到错误模式，Windows 将无法安装。 有关详细信息，请参阅[Windows 安装︰ 安装使用 MBR 或 GPT 分区样式](windows-setup-installing-using-the-mbr-or-gpt-partition-style.md)。

2.  您可以从 Windows PE 或 Windows 安装程序删除 （uefi） 或 BIOS 的启动文件。 例如，如果只包括在 Windows 安装 DVD UEFI 模式的启动文件，在制造过程中意外地尝试引导至 BIOS 模式 PC 电脑立即将无法启动，并可以立即诊断。

    -   **（uefi)**: 为防止 Windows 安装程序或 Windows PE 启动 BIOS 模式下，删除**bootmgr**文件介质的根上。

    -   **BIOS**︰ 要防止在 UEFI 模式下启动 Windows 安装程序或 Windows PE，删除介质的根上的**efi**文件夹。

3.  从 Windows PE 中，您可以检查[GetFirmwareEnvironmentVariable 函数](http://go.microsoft.com/fwlink/p/?LinkId=698644)。 有关详细信息，请参阅[WinPE: UEFI 或旧版 BIOS 模式中的启动](winpe-boot-in-uefi-or-legacy-bios-mode.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

 

 






