---
author: Justinha
Description: "在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导"
ms.assetid: bc3c4d41-c4f7-4432-b11a-f409e171d60d
MSHAttr: PreferredLib:/library/windows/hardware
title: "在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导"
ms.openlocfilehash: bc26e1e6c128737bdff873fa13447e2a36bca079
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-boot-in-uefi-or-legacy-bios-mode"></a>在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导


当您启动 Windows PE UEFI PC 时，您可能需要检查是否在 UEFI 或旧版 BIOS 兼容性模式下启动电脑。

例如，Windows PE 通过运行 Windows 安装程序要求您正确的固件模式。

对于很多操作，如应用 Windows 映像使用 Diskpart，DISM，固件模式不可能产生效果。

**引导至 UEFI 模式**

-   当启动计算机时，您可能需要手动选择 UEFI 启动文件︰ \\EFI\\启动\\BOOTX64。EFI。

    1.  启动计算机，然后按键进入固件菜单 (示例︰ Esc，F2、 F9，f12 键)。

    2.  寻找一个固件选项可供选择的引导程序文件 (示例︰ 引导至文件，引导至 EFI 文件)。

    3.  从 USB 驱动器中选择文件︰ `\EFI\BOOT\BOOTX64.EFI`。

**检测是否在 BIOS 或 UEFI 模式下启动 Windows PE**

1.  检查**HKLM\\系统\\开目前控制设置\\控件\\PEFirmwareType**注册表值，以确定是否计算机引导到 （uefi） 或 BIOS 模式。 注意︰ 您可能需要运行`wpeutil UpdateBootInfo`，以确保此值是否存在。

    ``` syntax
    reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType
    ```

    如果 PC 启动 BIOS 模式或 0x2 如果 PC 启动 （uefi） 模式中，该命令将返回 0x1。

    示例脚本︰

    ``` syntax
    wpeutil UpdateBootInfo
    for /f "tokens=2* delims=    " %%A in ('reg query HKLM\System\CurrentControlSet\Control /v PEFirmwareType') DO SET Firmware=%%B
    :: Note: delims is a TAB followed by a space.
    if %Firmware%==0x1 echo The PC is booted in BIOS mode.
    if %Firmware%==0x2 echo The PC is booted in UEFI mode.
    ```

2.  如果这是一个常见的问题，您可以删除 UEFI 模式或 BIOS 模式，以防止在不正确的模式下启动电脑的启动文件。 如果 PC 固件设置了错误的方式启动，媒体将立即无法启动，使您可以立即重试到正确的模式下启动电脑。

    -   **在 UEFI 模式下引导**︰ 为防止在 BIOS 模式下启动 Windows PE，删除**bootmgr**文件介质的根上。

    -   **在 BIOS 模式下引导**︰ 为防止在 UEFI 模式下启动 Windows PE，删除介质的根上的**efi**文件夹。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[使用 MBR 或 GPT 分区形式安装 Windows 安装程序︰](windows-setup-installing-using-the-mbr-or-gpt-partition-style.md)

[Wpeutil 命令行选项](wpeutil-command-line-options.md)

[UEFI 固件](uefi-firmware.md)

 

 






