---
author: Justinha
Description: "UEFI 固件"
ms.assetid: 63cab521-9f35-4428-85b6-5561889243fd
MSHAttr: PreferredLib:/library/windows/hardware
title: "UEFI 固件"
ms.openlocfilehash: 73560ed69bb28b1297ab8b4fca7ce6a3e13a708f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="uefi-firmware"></a>UEFI 固件


基于统一可扩展固件接口 （uefi） 的设备上部署 Windows 时，下面是一些注意事项。

## <a name="span-idwhatisuefispanspan-idwhatisuefispanspan-idwhatisuefispanwhat-is-uefi"></a><span id="What_is_UEFI_"></span><span id="what_is_uefi_"></span><span id="WHAT_IS_UEFI_"></span>（uefi） 是什么？


设备启动时，固件接口控制 PC，执行引导过程，然后将控制权传递给 Windows 或者其他操作系统。

（uefi） 是取代旧的 BIOS 固件接口和可扩展固件接口 (EFI) 1.10 规范。

140 多家领先的技术公司参与统一 EFI 论坛，包括 AMD、 AMI、 苹果、 戴尔、 HP、 IBM、 Insyde、 英特尔、 联想、 微软和菲尼克斯技术。

## <a name="span-idbenefitsspanspan-idbenefitsspanspan-idbenefitsspanbenefits-of-uefi"></a><span id="Benefits"></span><span id="benefits"></span><span id="BENEFITS"></span>（uefi） 的好处


固件，以满足 UEFI 2.3.1 规格提供了以下好处︰

-   更快的启动和恢复时间。

-   能够使用安全功能，如安全启动和工厂加密的驱动器，以防止不受信任的代码运行在操作系统加载之前。 有关详细信息，请参阅[安全引导概述](secure-boot-overview.md)和[工厂加密的驱动器](factory-encrypted-drives.md)。

-   能够更轻松地支持大容量硬盘 （超过 2 万亿字节） 和四个以上分区的驱动器。

-   与旧版 BIOS 兼容性。 某些基于 UEFI 的计算机包含模拟较早的 BIOS，为最终用户提供更多的灵活性和兼容性兼容性支持模块 (CSM)。 若要使用网吧点点通，必须禁用安全启动。

-   对于多播部署，允许个人电脑制造商广播可以由多台 Pc 而急剧的网络或映像服务器接收 PC 图像的支持。

-   支持 UEFI 固件驱动程序、 应用程序和选项 Rom。

具有其他的优点是[英特尔 EFI 和 UEFI 概述和规范](http://www.intel.com/technology/efi/)中所述。

## <a name="span-idwindowssupportofuefispanspan-idwindowssupportofuefispanspan-idwindowssupportofuefispanwindows-support-of-uefi"></a><span id="Windows_support_of_UEFI"></span><span id="windows_support_of_uefi"></span><span id="WINDOWS_SUPPORT_OF_UEFI"></span>Windows 支持的 （uefi）


以下的 Windows 版本包括 UEFI 的支持︰

-   Windows 10 对于桌面版本 （家庭、 Pro、 企业和教育），Windows 服务器 2016年技术预览、 Windows 8.1 和 Windows 8 支持本机 UEFI 2.0 或在以后使用 32 位 (x86)、 64 位 (x64) 和基于 ARM 的 Pc。 它们还支持基于 BIOS 的电脑，并基于 UEFI 的计算机在传统 BIOS 兼容性模式下运行。

    一些功能，如安全启动需要 UEFI 2.3.1 堪误表 C 或更高版本。

-   Windows Server 2012 R2 和 Windows Server® 2012年支持本机 UEFI 2.0 或在以后使用 64 位系统。 一些功能，如安全启动需要 UEFI 2.3.1。

-   Windows 7 和 Windows Server 2008 R2:

    -   支持 UEFI 2.0 或在以后使用 64 位系统。 它们还支持基于 BIOS 的电脑，并基于 UEFI 的计算机在传统 BIOS 兼容性模式下运行。

    -   在使用网吧点点通中，以便他们可以使用旧的 BIOS INT10 功能运行在旧的 BIOS 兼容性模式下的 2 类系统上支持。

    -   不支持在第 3 类系统中，因为这些操作系统的系统取得传统 BIOS INT10 支持的固件中存在该功能不可用 3 类 （uefi） 实现。

    -   在基于 Itanium 的系统上，Windows Server 2008 R2 还支持 EFI 1.10。

**请注意**  
-   在 UEFI 模式下，Windows 版本必须匹配的 PC 体系结构。 64 位 UEFI 电脑只可以启动 64 位版本的 Windows。 32 位 PC 仅可以引导 32 位版本的 Windows。 在某些情况下，在旧的 BIOS 模式下，您可能无法在 64 位 PC 上，假定制造商支持 32-位传统 BIOS 模式在 PC 上运行 32 位 Windows。

-   Windows 支持 （uefi） 规范中定义的功能的一个子集。 对更高版本的固件不显式检查 Windows 实现

-   其他 （uefi） 要求，请参阅[UEFI 安装媒体格式和默认引导行为](uefi-installation-media-format-and-default-boot-behavior.md)和[（uefi） 要求︰ 启动时，运行时，休眠状态 (S4)](uefi-requirements-boot-time-runtime-hibernation-state--s4.md)。

 

## <a name="span-idconsiderationsspanspan-idconsiderationsspanspan-idconsiderationsspanbefore-you-begin"></a><span id="Considerations"></span><span id="considerations"></span><span id="CONSIDERATIONS"></span>开始之前


基于 UEFI 的计算机上安装 Windows 之前，请注意以下事项︰

-   对于某些平台或硬件配置，您可能需要执行额外的步骤，以确保在 UEFI 模式或传统 BIOS 兼容性模式安装 Windows。 有关详细信息，请参阅[为 UEFI 模式或传统 BIOS 模式的引导](boot-to-uefi-mode-or-legacy-bios-mode.md)。

-   UEFI 硬盘要求的 GUID 分区表 (GPT) 分区结构，而不是主启动记录 (MBR) 分区结构在 BIOS 中使用。

    通过使用 Windows 产品 DVD 安装 Windows 时，Windows 安装程序将检测是否在 UEFI 或 BIOS 兼容性模式下，启动电脑并且可以配置基于此选择窗口。

-   可以配置 Windows 预安装环境 (Windows PE) 来支持 UEFI 模式和 BIOS 兼容性模式。

     **请注意**  
    在 UEFI 模式 PC 时，Windows PE 版本必须与 PC 体系结构相匹配。 在 64 位 UEFI 固件模式下 PC 仅可以启动 64 位版本的 Windows PE。 在 32 位 UEFI 固件模式下电脑只可以引导 32 位版本的 Windows PE。 在支持 UEFI 模式和旧的 BIOS 模式下的个人电脑，可能能够通过从"UEFI 模式"的 BIOS 菜单设置更改为"BIOS 模式"，在 64 位计算机上运行 32 位 Windows PE 假设制造商支持旧版 BIOS 模式。

    有关说明，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)或[WinPE︰ 硬驱动器 （平面引导或非 RAM） 上安装](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)。
    
-   与固件制造商的注意︰ 不要使用工具或应用程序来改变特定 Windows 的启动文件，包括在 c︰ 驱动器中的文件\\引导和 c:\\EFI 文件夹。 更改这些文件可能会干扰电脑的能力来启动、 从休眠中恢复，或者运行系统恢复工具。 相反，使用 BCDboot 工具设置引导顺序。 有关详细信息，请参阅[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)。

## <a name="span-idresourcesspanspan-idresourcesspanspan-idresourcesspansee-also"></a><span id="Resources"></span><span id="resources"></span><span id="RESOURCES"></span>请参见


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>（uefi） 要求</p></td>
<td align="left"><p>[（uefi） 安装媒体格式和默认引导行为](uefi-installation-media-format-and-default-boot-behavior.md) | [（uefi） 要求︰ 启动时，运行时，休眠状态 (S4)](uefi-requirements-boot-time-runtime-hibernation-state--s4.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p>（uefi） 的功能</p></td>
<td align="left"><p>[Microsoft 硬件开发人员中心︰ 固件和引导环境](http://go.microsoft.com/fwlink/?LinkId=244007) | [安全引导概述](secure-boot-overview.md) | [工厂加密的驱动器](factory-encrypted-drives.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>到 UEFI 或旧版 BIOS 模式引导一台电脑</p></td>
<td align="left"><p>[引导至 UEFI 模式或传统 BIOS 模式](boot-to-uefi-mode-or-legacy-bios-mode.md) | [WinPE: UEFI 或旧版 BIOS 模式中的启动](winpe-boot-in-uefi-or-legacy-bios-mode.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p>管理 （uefi） 硬盘和启动配置数据</p></td>
<td align="left"><p>[硬驱动器和分区](hard-drives-and-partitions.md) | [配置基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md) | [UEFI 的 BCD 系统存储设置](bcd-system-store-settings-for-uefi.md) | [（uefi） 验证选项 ROM 指导](uefi-validation-option-rom-validation-guidance.md) | [Windows UEFI 固件更新平台](http://go.microsoft.com/fwlink/p/?linkid=523808) | [验证 Windows UEFI 固件更新平台功能](validating-windows-uefi-firmware-update-platform-functionality.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>论坛</p></td>
<td align="left"><p>[统一可扩展固件接口论坛 （UEFI 论坛）](http://go.microsoft.com/fwlink/?LinkId=244009)</p></td>
</tr>
</tbody>
</table>

 

 

 






