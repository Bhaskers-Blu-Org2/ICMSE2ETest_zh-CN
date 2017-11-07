---
author: Justinha
Description: "Sysprep （系统准备） 概述"
ms.assetid: f16f9f4e-c897-4a08-8c0f-e9d64043738c
MSHAttr: PreferredLib:/library/windows/hardware
title: "Sysprep （系统准备） 概述"
ms.openlocfilehash: 661dd1af3778f98c7348c37707223e32e8bff5f5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-system-preparation-overview"></a>Sysprep （系统准备） 概述

**Sysprep**（系统准备） 准备 Windows 安装 （Windows 客户端和 Windows 服务器） 进行图像处理，使您能够捕获自定义的安装。 **Sysprep**删除特定于计算机的信息从 Windows 安装，"通用化"安装以便它可以安装在不同的 Pc 上。 通过**Sysprep** ，您可以配置计算机启动到审核模式下，可以对图像进行其他更改或更新。 或者，您可以将 Windows 配置为启动到外的全新体验 (OOBE)。

Sysprep 属于 Windows 映像，并在审核模式期间使用。

## <a name="span-idbkmkoverspanspan-idbkmkoverspanfeature-description"></a><span id="BKMK_OVER"></span><span id="bkmk_over"></span>功能说明


Sysprep 提供以下功能︰

-   Windows 映像，包括 PC 的安全标识符 (SID) 中删除特定于计算机的信息。 这允许您捕获映像并将其应用到其他计算机。 这被称为泛化电脑。

-   卸载 Windows 映像中特定于计算机的驱动程序。

-   通过将计算机启动到 OOBE 设置电脑准备交付给客户。

-   允许您添加应答文件 （无人参与） 设置应用于现有安装。

## <a name="span-idbkmkappspanspan-idbkmkappspanpractical-applications"></a><span id="BKMK_APP"></span><span id="bkmk_app"></span>实际应用


Sysprep 可以帮助您解决业务目标，如︰

-   可帮助您创建可用于跨多个硬件设计的通用图像来管理多台 Pc。

-   通过捕获和部署映像的唯一的安全标识符中部署的 Pc。

-   在审核模式下添加应用程序、 语言、 或驱动程序调整单个 Pc 的设置。 有关详细信息，请参阅[审核模式概述](audit-mode-overview.md)。

-   通过它们交付给客户之前在审核模式下测试提供更可靠的电脑。

## <a name="span-idbkmknewspanspan-idbkmknewspannew-and-changed-functionality"></a><span id="BKMK_NEW"></span><span id="bkmk_new"></span>新建和更改的功能

Sysprep 开头第 10 Windows 版本 1607，用于准备已升级的映像。 例如︰

- 您可以从运行 Windows 10、 版本 1511年或 Windows 10 版本 1507年的计算机开始。
- 升级计算机运行 Windows 10，1607年版本。
- 运行的 Sysprep 归纳在升级后的映像、 重新捕获更新后的映像，并将映像部署到新的设备。

此过程允许企业高效、 持续推出最新的 Windows 10 部署映像。 

从开始 Windows 8.1，Sysprep 用户界面已被否决。 Sysprep UI 将继续支持在本版本中，但可能在将来的版本中删除。 我们建议您更新您的部署工作流，以便从命令行使用 Sysprep。 有关详细信息，请参阅[Sysprep 命令行选项](sysprep-command-line-options.md)。

## <a name="span-iddependenciesspanspan-iddependenciesspanspan-iddependenciesspandependencies"></a><span id="Dependencies"></span><span id="dependencies"></span><span id="DEPENDENCIES"></span>依赖项


-   使用 Sysprep 之前，您必须运行 Windows 安装程序。

-   您需要一种工具来捕获映像的安装，如[DISM 的部署映像服务和管理技术参考 Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)或其他磁盘映像软件。

**请注意**  
复制 Pc 之间的 Windows 映像时，引用和目标 Pc 可能不需要具有兼容的硬件抽象层 (Hal)。 引导配置数据 (BCD) 中的 /detecthal 选项，使系统已运行 Sysprep 来安装正确的 HAL。

 

## <a name="span-idbkmk4spanspan-idbkmk4spanlimitations"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>限制


Sysprep 具有以下限制︰

-   当您执行 Sysprep 操作系统的系统卷上的安全标识符 (SID) 只替换。 如果一台计算机有多个操作系统，则必须分别在每个图像上运行 Sysprep。

-   在某些情况下，自定义应用程序安装之前重新捕获 Windows 映像可能需要一致的驱动器号。 某些应用程序中存储包含系统的驱动器号的路径。 卸载方案、 提供服务方案和修复方案可能无法正确运行如果系统的驱动器号与应用程序将指定的驱动器号不匹配。

-   引用和目标上的插设备 Pc 未安装来自同一制造商。 这些设备包括调制解调器、 声卡、 网络适配器和视频卡。 但是，安装必须包含这些设备的驱动程序。

-   不是所有的服务器角色支持 Sysprep。 一般化有特定的服务器角色配置的 Windows 服务器安装时，如果这些服务器角色不可能会继续工作后的映像和部署过程。 有关详细信息，请参阅[Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)。

-   如果在包含加密的文件或文件夹的 NTFS 文件系统分区上运行 Sysprep，这些文件夹中的数据变得完全不能读取且不可恢复。

-   仅当计算机是工作组，而不是域的成员运行 Sysprep 工具。 如果计算机已加入域，Sysprep 会从域中删除计算机。

-   如果计算机加入到域，并且该域的组策略为计算机分配强帐户密码策略，所有用户帐户都需要强密码。 运行 Sysprep 或 OOBE 不会删除强密码策略。

    **警告**  
    如果运行 Sysprep 或 OOBE 之前不到一个用户帐户分配一个强密码，您可能无法登录到计算机上。 我们建议您始终为您的用户帐户使用强密码。

     

## <a name="span-idbkmk3spanspan-idbkmk3spanunsupported-scenarios"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>不受支持的方案


不支持以下方案︰

-   移动或复制到不同的计算机的 Windows 映像，而无需使通用 PC 不受支持。

-   不支持使用 Sysprep 工具的不同版本配置的映像。 您必须使用 Sysprep 工具与想要配置的 Windows 映像安装的版本。 Sysprep 与每个版本的 Windows 安装。 必须始终从 %WINDIR%运行 Sysprep\\system32\\sysprep 目录。

-   如果使用的 Windows 10 版本 1607年以前版本的 Windows 不支持使用 Sysprep 工具升级安装类型，或要重新配置现有的已部署的 Windows 安装。 在这种情况下，必须使用 Sysprep 只能用于配置新安装的 Windows。 您可以运行 Sysprep 无数次生成和配置的 Windows 安装。

-   通过使用 Microsoft Windows 部署自动化 Sysprep\\[RunSynchronous](http://go.microsoft.com/fwlink/?LinkId=286336)命令不受支持。 但是，您可以使用 Microsoft Windows 部署\\[通用化](http://go.microsoft.com/fwlink/?LinkId=286337)设置电脑准备安装后的成像。

-   虚拟机 (VM) 的外部运行虚拟机模式不受支持。 不能使用虚拟机模式 VHD 准备部署到任何 PC。

-   不能在系统帐户的上下文中运行 Sysprep。 在系统帐户的上下文中运行 Sysprep 使用任务计划程序或 PSExec，例如，不支持。

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>请参见


下表包含与此方案相关的资源的链接。

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
<td align="left"><p><strong>产品评估</strong></p></td>
<td align="left"><p>[Sysprep 过程概述](sysprep-process-overview.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>操作</strong></p></td>
<td align="left"><p>[Sysprep （通用化） Windows 安装](sysprep--generalize--a-windows-installation.md) | [自定义默认用户配置文件通过使用 CopyProfile](customize-the-default-user-profile-by-using-copyprofile.md) | [使用答案文件与 Sysprep 一起](use-answer-files-with-sysprep.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>工具和设置</strong></p></td>
<td align="left"><p>[Sysprep 命令行选项](sysprep-command-line-options.md) | [Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>相关的技术</strong></p></td>
<td align="left"><p>[Windows 安装程序](http://microsoft.com) | [审核模式概述](audit-mode-overview.md) | [启动 Windows 审核模式还是 OOBE](boot-windows-to-audit-mode-or-oobe.md)</p></td>
</tr>
</tbody>
</table>

 

 

 






