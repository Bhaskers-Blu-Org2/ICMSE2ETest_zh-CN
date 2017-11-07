---
author: Justinha
Description: "部署 Windows 在 VHD （本机引导）"
ms.assetid: 0802bca0-646e-4453-b78c-6257f1ed7e80
MSHAttr: PreferredLib:/library/windows/hardware
title: "部署 Windows 在 VHD （本机引导）"
ms.openlocfilehash: 0d2913622d1f0d44709de456710b370c58a1e27c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-on-a-vhd-native-boot"></a>部署 Windows 在 VHD （本机引导）


创建和部署与测试设备或管理而无需重新分区驱动器在设备上的多个操作系统的本机引导功能的虚拟硬盘 (Vhd)。

## <a name="span-idcreatingvhdsspanspan-idcreatingvhdsspanspan-idcreatingvhdsspancreating-vhds"></a><span id="Creating_VHDs"></span><span id="creating_vhds"></span><span id="CREATING_VHDS"></span>创建 Vhd

您可以创建虚拟硬盘 （.vhd 或.vhdx 文件） 使用 DiskPart 工具或磁盘管理 Microsoft 管理控制台 (MMC)。 您可以从 PowerShell 创建.vhdx 文件时安装 Hyper-V 管理器角色。

您可以附加 VHD，以使其显示为系统驱动器，您可以进行分区、 格式化和应用到您的操作系统。

## <a name="span-iddeployingvhdsspanspan-iddeployingvhdsspanspan-iddeployingvhdsspandeploying-vhds"></a><span id="Deploying_VHDs"></span><span id="deploying_vhds"></span><span id="DEPLOYING_VHDS"></span>部署 Vhd

可支持的 Windows 映像部署到使用部署映像服务和管理 (DISM) 工具如磁盘映像软件附加 VHD。 VHD 可以再复制到一个或多个系统可以运行在虚拟机中或用于本机引导。

有关详细信息，请参阅[下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md)。

第一个本机引导，在*specialize*配置阶段运行和特定于计算机的信息应用到 VHD 上 Windows 操作系统。 无法复制到另一个系统或专业化配置阶段完成之后，在虚拟机中运行的 VHD 的实例。 原始的 Windows 映像的 VHD 可以继续复制并部署到多台计算机，如果图像已经已经准备**/ 专用**选项与使用 Sysprep 工具进行安装。 也可以使用答案文件若要通过使用 Microsoft Windows 部署准备安装图像 |对设置进行一般化。 有关**专用化**和**通用化**配置阶段的详细信息，请参阅[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)。 有关如何使用答案文件中的通用化设置的详细信息，请参阅 Windows® 无人参与安装参考。

Windows 部署服务器角色支持部署 VHD 映像.wim 文件的文件。 Windows 部署服务器自动使用本机引导的 VHD 映像的网络部署。 可以使用 Windows 部署服务器，可以将 VHD 映像复制到本地分区，并配置本地引导配置数据 (BCD) 对本机引导的 VHD。

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[了解具有本机引导的虚拟硬盘](understanding-virtual-hard-disks-with-native-boot.md)</p></td>
<td align="left"><p>包括常见方案、 要求和建议向具有本机引导的 VHD 安装 Windows。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)</p></td>
<td align="left"><p>创建和部署 VHD 的目标计算机上。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md)</p></td>
<td align="left"><p>更新计算机的 Windows 7 或 Windows 8 的引导环境并将 VHD 添加到 BCD 的配置。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

 

 






