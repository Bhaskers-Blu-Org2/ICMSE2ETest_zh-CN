---
author: Justinha
Description: "部署 Windows RE"
ms.assetid: 93c71c50-b3f9-49f7-bf3a-32a412b048ed
MSHAttr: PreferredLib:/library/windows/hardware
title: "部署 Windows RE"
ms.openlocfilehash: 4bb8621b39ce915f6e75841f0ae74ad5f168ae00
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-re"></a>部署 Windows RE


使用下列步骤来部署 Windows® 恢复环境 (Windows RE) 到新计算机，以帮助最终用户修复一台电脑，在系统出现故障时。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成本演练，您需要以下各项︰

-   目标计算机已配置恢复图像分区与 Windows RE 工具分区，并 （可选）。 有关详细信息，请参阅[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)。
-   可选︰ 自定义恢复媒体。 有关详细信息，请参阅[自定义 Windows RE](customize-windows-re.md)。
-   可选︰ 自定义恢复媒体以包括自定义工具。 有关详细信息，请参阅[添加到 Windows 重新启动选项菜单的自定义工具](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)。

## <a name="span-iddeploywindowsrespanspan-iddeploywindowsrespanspan-iddeploywindowsrespanstep-1-deploy-windows-re"></a><span id="DeployWindowsRE"></span><span id="deploywindowsre"></span><span id="DEPLOYWINDOWSRE"></span>步骤 1︰ 将部署 Windows RE


1.  在 Windows RE 工具分区中，创建一个新目录，然后将您自定义的 Windows RE 工具图像 (Winre.wim) 复制到此目录。 以下是基于固件类型的示例︰

    **（UEFI):**

    ``` syntax
    mkdir T:\Recovery\WindowsRE

    xcopy /h W:\Windows\System32\Recovery\Winre.wim T:\Recovery\WindowsRE
    ```

    其中*t︰*是 Windows RE 工具分区的驱动器号。 例如︰

    **BIOS:**

    ``` syntax
    mkdir S:\Recovery\WindowsRE

    xcopy /h W:\Windows\System32\Recovery\Winre.wim S:\Recovery\WindowsRE
    ```

    *s︰*所在的系统分区。

2.  注册自定义 Windows RE 工具映像︰

    **（UEFI):**

    ``` syntax
    C:\Windows\System32\Reagentc /setreimage /path T:\Recovery\WindowsRE /target W:\Windows
    ```

    其中*t︰*是 Windows RE 工具分区。

    **BIOS**

    ``` syntax
    C:\Windows\System32\Reagentc /setreimage /path S:\Recovery\WindowsRE /target W:\Windows
    ```

    *s︰*所在的系统分区。

3.  可选︰ 如果您到 Windows RE 启动映像添加了自定义工具，注册它，以便它将出现在**启动选项**菜单︰

    ``` syntax
    Reagentc /setbootshelllink /configfile E:\Recovery\BootMenu\AddDiagnosticsToolToBootMenu.xml
    ```

    有关添加自定义工具的详细信息，请参阅[添加到 Windows 重新启动选项菜单自定义工具](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)。

4.  可选︰ 配置硬件恢复按钮 （或按钮组合） 来运行包含 Windows RE 的辅助引导路径。 有关详细信息，请参阅[添加到启动 Windows RE 硬件恢复按钮](add-a-hardware-recovery-button-to-start-windows-re.md)。

## <a name="span-idpreparescriptsspanspan-idpreparescriptsspanspan-idpreparescriptsspanstep-2-identify-the-recovery-partitions-and-hide-the-drive-letters"></a><span id="PrepareScripts"></span><span id="preparescripts"></span><span id="PREPARESCRIPTS"></span>步骤 2︰ 标识恢复分区和隐藏驱动器号


**请注意**  如果您想要配置按钮重置 Windows 8 版的功能，请跳过此部分，并进入主题︰[部署 Push-Button 重置功能](deploy-push-button-reset-features.md)。

 

将分区配置为恢复分区，并使分区不出现在常见 Windows 菜单，如文件资源管理器然后隐藏的驱动器号。

**准备 DiskPart 脚本以确定恢复分区并隐藏驱动器号**

1.  在记事本中，创建一个文本文件，包含用于标识和隐藏恢复分区的命令。 下面的示例基于固件类型︰

    **（UEFI):**

    使用 ID︰ 分区\_MSFT\_恢复\_GUID (de94bba4-06d1-4d40-a16a-bfd50179d6ac) 可以定义为恢复分区的分区。

    使用 GPT 属性︰ 0x8000000000000001 要隐藏驱动器号，并将它们标记为必需的通过使用两个属性的组合︰ GPT\_基本\_数据\_特性\_NO\_驱动器\_号和 GPT\_特性\_平台\_必需的。

    关于 UEFI 硬盘分区属性的详细信息，请参阅[分区\_信息\_GPT 结构](http://go.microsoft.com/fwlink/?LinkId=240300)。

    ``` syntax
    rem == HideRecoveryPartitions-UEFI.txt
    select disk 0
    select partition 1
    remove
    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    gpt attributes=0x8000000000000001
    rem == If Push-button reset features are included, add the following commands:
    rem    select partition 5
    rem    remove
    rem    set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
    rem    gpt attributes=0x8000000000000001
    list volume
    ```

    **BIOS:**

    使用该特性︰`id=27`定义系统分区中，并使用`remove`命令以删除驱动器号。

    ``` syntax
    rem == HideRecoveryPartitions-BIOS.txt
    select disk 0
    select partition 3
    set id=27
    remove
    list volume
    exit
    ```

2.  保存您已完成的文件为 e:\\恢复\\HideRecoveryPartitions UEFI.txt 或 e:\\恢复\\HideRecoveryPartitions BIOS.txt，基于固件类型。

**识别并隐藏驱动器号**

-   运行 diskpart 脚本，以确定并隐藏恢复分区︰

    ``` syntax
    Diskpart /s E:\Recovery\HideRecoveryPartitions-<firmware>.txt
    ```

    其中*&lt;固件&gt;*（uefi） 或 BIOS。

**验证已正确设置了 Windows RE 配置**

-   打开管理员命令提示符。

    验证 Windows RE 信息︰

    ``` syntax
    reagentc /info
    ```

    验证以下各项︰

    -   Windows RE 状态为已启用。
    -   Windows RE 的位置是正确的分区上。
    -   WinRE BCD GUID 项是 WinRE GUID 文件中的项相同︰ reagent.xml。 在基于 BIOS 的电脑，此文件是系统分区上，在\\恢复\\(GUID)\\。 于基于 UEFI 的 Pc 上，此文件是 Windows RE 工具分区上，在\\恢复\\WindowsRE\\。
    -   WinRE 位于\\恢复\\WindowsRE 目录

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 恢复环境 (Windows RE) 技术参考](windows-recovery-environment--windows-re--technical-reference.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[自定义 Windows RE](customize-windows-re.md)

[向 Windows 重新启动选项菜单中添加自定义工具](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)

 

 






