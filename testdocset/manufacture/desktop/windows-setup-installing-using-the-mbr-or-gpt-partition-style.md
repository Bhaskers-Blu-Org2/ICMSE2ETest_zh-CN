---
author: Justinha
Description: "使用 MBR 或 GPT 分区形式安装 Windows 安装程序︰"
ms.assetid: d8d8901f-9e0c-4f73-b331-8c0d36a1ba47
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 MBR 或 GPT 分区形式安装 Windows 安装程序︰"
ms.openlocfilehash: 318a0085ba860c588fbd48712f6d7e186ee51d3d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-installing-using-the-mbr-or-gpt-partition-style"></a>使用 MBR 或 GPT 分区形式安装 Windows 安装程序︰


当使用 Windows 安装程序的基于 UEFI 的计算机上安装 Windows，请必须设置硬盘分区样式，以支持 UEFI 模式或传统 BIOS 兼容性模式。

例如，如果您收到错误消息:"无法将 Windows 安装到该磁盘。 所选的磁盘不是 GPT 分区形式"，这是因为您的电脑启动在 UEFI 模式中，但您的硬盘未配置 UEFI 模式。 已经有几种选择︰

1.  重新启动电脑在旧的 BIOS 兼容性模式下。 此选项使您可以保持现有的分区形式。 更多的信息，请参阅[为 UEFI 模式或传统 BIOS 模式的引导](boot-to-uefi-mode-or-legacy-bios-mode.md)。

2.  通过使用 GPT 分区形式为 UEFI 重新格式化驱动器。 此选项允许您使用 PC UEFI 固件功能。

    可以通过重新格式化驱动器使用以下说明，不要自行，或如果您需要保留的数据，使用第三方实用程序将驱动器转换为 GPT 格式。

## <a name="span-idwhyshouldiconvertmydrivespanspan-idwhyshouldiconvertmydrivespanspan-idwhyshouldiconvertmydrivespanwhy-should-i-convert-my-drive"></a><span id="Why_should_I_convert_my_drive_"></span><span id="why_should_i_convert_my_drive_"></span><span id="WHY_SHOULD_I_CONVERT_MY_DRIVE_"></span>为什么应将转换我的驱动器？


在很多 Pc 现在包括︰ 能够使用 UEFI 版本的 BIOS，可以加快启动和关机时间，并可以提供额外的安全优势。 若要在 UEFI 模式下启动计算机，您需要使用使用 GPT 驱动器格式格式化的驱动器。

许多个人电脑就可以使用 （uefi），但包括设置为使用旧的 BIOS 版本的兼容性支持模块 (CSM)。 此版本的 BIOS 1970 年开发和提供各种旧设备和网络配置的兼容性，需要使用 MBR 驱动器格式的驱动器。

但是，基本的 MBR 驱动器格式不支持驱动器超过 4 tb 的容量。 也很难设置四个以上分区。 GPT 驱动器格式使您可以设置驱动器大于 4 千兆字节 (TB)，并使您可以轻松地设置所需的任意多个分区。

## <a name="span-idreformattingthedriveusingadifferentpartitionstylespanspan-idreformattingthedriveusingadifferentpartitionstylespanspan-idreformattingthedriveusingadifferentpartitionstylespanreformatting-the-drive-using-a-different-partition-style"></a><span id="Reformatting_the_drive_using_a_different_partition_style"></span><span id="reformatting_the_drive_using_a_different_partition_style"></span><span id="REFORMATTING_THE_DRIVE_USING_A_DIFFERENT_PARTITION_STYLE"></span>重新格式化的驱动器使用不同的分区样式


**若要擦除并使用 Windows 安装程序转换驱动器**

1.  关闭计算机，并放入 Windows 安装 DVD 或 USB 密钥。

2.  在 UEFI 模式下启动 PC 至 DVD 或 USB 密钥。 更多的信息，请参阅[为 UEFI 模式或传统 BIOS 模式的引导](boot-to-uefi-mode-or-legacy-bios-mode.md)。

3.  选择安装类型时，选择**自定义**。

4.  在**要在其中安装 Windows®**屏幕，选择每个驱动器上的分区，然后选择**删除**。 该驱动器将显示单个区域的未分配空间。

5.  选择未分配的空间，然后单击**下一步**。 Windows 检测到 PC 到 UEFI 模式，引导和重新格式化的驱动器使用 GPT 驱动器的格式，并将开始安装。

**若要手动擦除驱动器并将其转换为 GPT:**

1.  关闭计算机，并放入 Windows 安装 DVD 或 USB 密钥。

2.  在 UEFI 模式下启动 PC 至 DVD 或 USB 密钥。 更多的信息，请参阅[为 UEFI 模式或传统 BIOS 模式的引导](boot-to-uefi-mode-or-legacy-bios-mode.md)。

3.  从内部 Windows 安装程序，请按**Shift + F10**打开命令提示窗口。

4.  打开 diskpart 工具︰

    ``` syntax
    diskpart
    ```

5.  标识要重新格式化的驱动器︰

    ``` syntax
    list disk
    ```

6.  选择驱动器，然后将其重新格式化︰

    ``` syntax
    select disk <disk number>
    clean
    convert gpt
    exit
    ```

7.  关闭命令提示符窗口。

8.  继续安装 Windows 安装程序。

    选择安装类型时，选择**自定义**。 该驱动器将显示为单个区域的未分配空间。

    选择未分配的空间，然后单击**下一步**。 Windows 将开始安装。

## <a name="span-idmakesurewindowssetupbootstothecorrectfirmwaremodespanspan-idmakesurewindowssetupbootstothecorrectfirmwaremodespanspan-idmakesurewindowssetupbootstothecorrectfirmwaremodespanmake-sure-windows-setup-boots-to-the-correct-firmware-mode"></a><span id="Make_sure_Windows_Setup_boots_to_the_correct_firmware_mode"></span><span id="make_sure_windows_setup_boots_to_the_correct_firmware_mode"></span><span id="MAKE_SURE_WINDOWS_SETUP_BOOTS_TO_THE_CORRECT_FIRMWARE_MODE"></span>请确保 Windows 安装引导到正确的固件模式


要自动完成此过程，您需要运行 Windows 安装程序通过 Windows PE 中，并使用一个脚本来检测您安装 Windows 之前处于哪种模式。 有关详细信息，请参阅[WinPE: UEFI 或旧版 BIOS 模式中的启动](winpe-boot-in-uefi-or-legacy-bios-mode.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[引导至 UEFI 模式或传统 BIOS 模式](boot-to-uefi-mode-or-legacy-bios-mode.md)

 

 






