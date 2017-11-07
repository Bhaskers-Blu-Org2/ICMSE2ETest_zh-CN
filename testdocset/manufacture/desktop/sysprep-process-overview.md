---
author: Justinha
Description: "Sysprep 过程概述"
ms.assetid: e764e19f-8a8a-4fae-aa1f-22e70caf1599
MSHAttr: PreferredLib:/library/windows/hardware
title: "Sysprep 过程概述"
ms.openlocfilehash: d25dee3b0e055479d5d91687eb7ed0a9e4bcf045
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-process-overview"></a>Sysprep 过程概述


系统准备 (**Sysprep**) 工具用于 Windows® 图像从通用的状态更改为专用的状态，然后再返回到一个通用的状态。 通用的映像可以在任何计算机上进行部署。 特殊的图像对准特定的计算机。 您必须重新封装，或者对进行一般化 Windows 映像之前捕获和部署映像。 例如，当您使用**Sysprep**工具对图像进行一般化， **Sysprep**删除所有系统特定的信息，并重置计算机。 在下次计算机重新启动时，您的客户可以添加特定于用户的信息的全新体验 (OOBE) 通过并接受 Microsoft 软件许可条款。

**Sysprep.exe**位于**%WINDIR%\\system32\\sysprep**在所有 Windows 安装目录。

如果将 Windows 映像传送到另一台计算机中，则必须运行**Sysprep**命令和**一般化**选项，即使另一台计算机具有相同的硬件配置。 **Sysprep 一般化 /**命令将唯一信息删除从您的 Windows 安装，这样您可以重用该映像在另一台计算机上的。 有关详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

本主题︰

-   [Sysprep 的可执行文件](#sysprepexecutable)

-   [Sysprep 过程概述](#sysprepprocess)

-   [持续的硬件配置](#bkmk-new)

-   [添加设备驱动程序](#device)

-   [启动到审核模式或 OOBE](#bootingtoauditmodeorwindowswelcome)

-   [检测的 Windows 映像的状态](#detectingthestateofawindowsimage)

-   [Sysprep 日志文件](#syspreplogfiles)

-   [创建和使用 Sysprep 提供程序](#creatingandusingsysprepproviders)

## <a name="span-idsysprepexecutablespanspan-idsysprepexecutablespanspan-idsysprepexecutablespansysprep-executable"></a><span id="SysprepExecutable"></span><span id="sysprepexecutable"></span><span id="SYSPREPEXECUTABLE"></span>Sysprep 的可执行文件


**Sysprep.exe**是主程序调用准备 Windows 安装其他可执行文件。 **Sysprep.exe**位于**%WINDIR%\\system32\\sysprep**在所有 Windows 安装目录。 如果您使用命令行而不是**系统准备工具**GUI，您必须首先关闭 GUI，然后运行**Sysprep**从**%WINDIR%\\system32\\sysprep**目录。 您还必须在相同版本的 Windows，您用来安装**Sysprep**运行**Sysprep** 。

**重要**  
从开始 Windows 8.1，Sysprep 用户界面已被否决。 Sysprep UI 将继续支持在本版本中，但可能在将来的版本中删除。 我们建议您更新您的 Windows 部署工作流要使用 Sysprep 命令行。 Sysprep 命令行工具的详细信息，请参阅[Sysprep 命令行选项](sysprep-command-line-options.md)。

 

## <a name="span-idsysprepprocessspanspan-idsysprepprocessspanspan-idsysprepprocessspansysprep-process-overview"></a><span id="SysprepProcess"></span><span id="sysprepprocess"></span><span id="SYSPREPPROCESS"></span>Sysprep 过程概述


Sysprep 运行时，它会经历以下过程︰

1.  **Sysprep 验证**。 验证可以运行 Sysprep。 只有管理员可以运行 Sysprep。 一次可以运行 Sysprep 的一个实例。 此外，Sysprep 必须使用 Sysprep 安装的 Windows 版本上运行。

2.  **初始化日志记录**。 初始化日志记录。 有关详细信息，请参阅[Sysprep 的日志文件](#syspreplogfiles)。

3.  **分析命令行参数**。 分析命令行参数。 如果用户不提供命令行参数，系统准备工具窗口将出现，并使用户能够指定 Sysprep 操作。

4.  **处理 Sysprep 操作**。 处理 Sysprep 操作，调用相应的.dll 文件和可执行文件，并将操作添加到日志文件。

5.  **验证 Sysprep 处理操作**。 验证所有.dll 文件都处理他们的所有任务，然后关闭或重新启动系统。

## <a name="span-idbkmknewspanspan-idbkmknewspanpersisting-the-hardware-configuration"></a><span id="bkmk_new"></span><span id="BKMK_NEW"></span>持续的硬件配置


如果您创建到另一台计算机部署此安装映像，则必须运行**Sysprep**命令和**一般化**选项，即使另一台计算机具有相同的硬件配置。 **Sysprep 一般化 /**命令从 Windows 安装移除唯一的信息，以便您可以重用该图像在不同的计算机上。 下次您启动 Windows 映像，在[specialize](specialize.md)配置阶段运行。

如果您要将 Windows 映像安装到具有相同硬件配置的计算机，您可以保留设备驱动程序安装在 Windows 映像中。 为此，请在应答文件中指定**Microsoft 的 Windows PnPSysprep**组件中的**PersistAllDeviceInstalls**设置。 默认值为**false**。 如果您将设置为**true**，插设备保留在计算机上在[一般化](generalize.md)配置阶段。 不需要重新安装这些设备，在[specialize](specialize.md)配置阶段。 有关详细信息，请参阅[使用答案文件与 Sysprep 一起](use-answer-files-with-sysprep.md)和无人参与的 Windows 安装程序参考指南 》。

## <a name="span-iddevicespanspan-iddevicespanadding-device-drivers"></a><span id="device"></span><span id="DEVICE"></span>添加设备驱动程序


插拔设备包括调制解调器、 声卡、 网络适配器和视频卡。 参考计算机和目标计算机上的即插设备不需要来自同一制造商。 但是，必须在安装中包括这些设备的驱动程序。 有关详细信息，请参见[添加和移除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)和[Windows 安装过程中 Windows 到添加设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)。

## <a name="span-idbootingtoauditmodeorwindowswelcomespanspan-idbootingtoauditmodeorwindowswelcomespanspan-idbootingtoauditmodeorwindowswelcomespanbooting-to-audit-mode-or-oobe"></a><span id="BootingToAuditModeOrWindowsWelcome"></span><span id="bootingtoauditmodeorwindowswelcome"></span><span id="BOOTINGTOAUDITMODEORWINDOWSWELCOME"></span>启动到审核模式或 OOBE


当 Windows 启动时，可以在两种模式之一启动计算机︰

-   OOBE

    OOBE，也称为的全新安装体验 (OOBE)，是首次用户体验。 OOBE 使最终用户能够自定义 Windows 安装。 最终用户可以创建用户帐户、 阅读并接受 Microsoft （） 软件许可条款，然后选择其语言和时区。 默认情况下，所有 Windows 安装都引导至 OOBE 第一次。 在[oobeSystem](oobesystem.md)配置阶段运行 OOBE 开始之前。

    如果您没有通过使用产品密钥自动激活 Windows，OOBE 会提示用户输入产品密钥。 如果用户将在 OOBE 期间跳过此步骤，Windows 将提醒用户以后输入有效的产品密钥。 若要自动通过使用产品密钥激活 Windows，请指定有效的产品密钥在**Microsoft Windows 外壳程序安装\\的产品密钥**无人参与的在[specialize](specialize.md)配置阶段的设置。 有关详细信息，请参阅[使用产品密钥和激活](work-with-product-keys-and-activation-auth-phases.md)。

-   审核模式

    如果在审核模式下，配置为启动到 OOBE 安装，正在运行的计算机，请使用**Sysprep** GUI 或者运行**Sysprep /oobe**命令。 为最终用户准备计算机，您必须将计算机配置为最终用户首次启动计算机时启动 OOBE。 在默认的 Windows 安装，OOBE 启动后安装完成，但您可以跳过 OOBE 和引导直接到审核模式下自定义图像。

    您可以将 Windows 配置为直接启动到审核模式，通过使用 Microsoft Windows 部署**|重新封装 |模式**在应答文件中设置。 在审核模式下，计算机处理无人参与的答案文件中的[auditSystem](auditsystem.md)和[auditUser](audituser.md)配置阶段的设置。

    审核模式使您可以将自定义项添加到 Windows 映像。 审核模式不需要应用中 OOBE 设置。 通过跳过 OOBE，可以更快地访问桌面并执行自定义。 可以添加多个设备驱动程序，安装应用程序，以及测试安装的有效性。

有关详细信息，请参阅︰

-   [审核模式概述](audit-mode-overview.md)

-   [引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

-   [配置阶段的工作](how-configuration-passes-work.md)

-   [启用和禁用内置管理员帐户](enable-and-disable-the-built-in-administrator-account.md)

-   [在审核模式下添加驱动程序](add-a-driver-online-in-audit-mode.md)

## <a name="span-iddetectingthestateofawindowsimagespanspan-iddetectingthestateofawindowsimagespanspan-iddetectingthestateofawindowsimagespandetecting-the-state-of-a-windows-image"></a><span id="DetectingTheStateOfAWindowsImage"></span><span id="detectingthestateofawindowsimage"></span><span id="DETECTINGTHESTATEOFAWINDOWSIMAGE"></span>检测的 Windows 映像的状态


可以使用 Sysprep 来标识 Windows 映像的状态。 即，可以确定映像将启动到审核模式或 OOBE，还是图像仍然正在安装。 有关详细信息，请参阅[Windows 安装程序安装过程](windows-setup-installation-process.md)。

## <a name="span-idsyspreplogfilesspanspan-idsyspreplogfilesspanspan-idsyspreplogfilesspansysprep-log-files"></a><span id="SysprepLogFiles"></span><span id="syspreplogfiles"></span><span id="SYSPREPLOGFILES"></span>Sysprep 日志文件


**Sysprep**工具将 Windows 安装程序的操作记录在不同目录中，具体取决于配置阶段。 在[一般化](generalize.md)配置阶段中删除某些 Windows 安装程序日志文件，因为**Sysprep**工具日志一般化超出标准的 Windows 安装程序日志文件的操作。 下表显示了不同的日志文件使用**Sysprep**的位置。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">项目</th>
<th align="left">日志路径</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>一般化</strong></p></td>
<td align="left"><p><strong>%WINDIR%\System32\Sysprep\Panther</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>专门负责</strong></p></td>
<td align="left"><p><strong>%WINDIR%\Panther\</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p>无人参与的 Windows 安装程序操作</p></td>
<td align="left"><p><strong>%WINDIR%\Panther\Unattendgc</strong></p></td>
</tr>
</tbody>
</table>

 

有关详细信息，请参阅[部署故障排除和日志文件](deployment-troubleshooting-and-log-files.md)。

## <a name="span-idcreatingandusingsysprepprovidersspanspan-idcreatingandusingsysprepprovidersspanspan-idcreatingandusingsysprepprovidersspancreating-and-using-sysprep-providers"></a><span id="CreatingAndUsingSysprepProviders"></span><span id="creatingandusingsysprepproviders"></span><span id="CREATINGANDUSINGSYSPREPPROVIDERS"></span>创建和使用 Sysprep 提供程序


独立软件供应商 (Isv) 和独立硬件供应商 (Ihv) 可以创建**Sysprep**的提供程序使其应用程序以支持映像和部署方案。 如果应用程序当前不支持使用**Sysprep**工具一般化的操作，您可以创建一个提供程序，从应用程序移除所有的软件和硬件的特定信息。

创建**Sysprep**提供程序，必须执行以下操作︰

1.  确定哪些配置通过**清理**、**归纳**，（**专门**） 您 Sysprep 提供程序的地址。

2.  **Sysprep**提供程序，根据您选择的配置阶段创建适当的入口点。

3.  注册的**Sysprep**提供程序使用**Sysprep**工具。

4.  测试**Sysprep**提供程序来验证提供程序工作正常。 请确保您查看警告和错误的日志文件。

**Sysprep**提供程序的详细信息，请参阅[系统准备 (Sysprep) 提供程序开发人员工具指南](http://go.microsoft.com/fwlink/?LinkId=205568)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)

[Sysprep 命令行选项](sysprep-command-line-options.md)

[Sysprep （通用化） Windows 安装](sysprep--generalize--a-windows-installation.md)

[Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)

[使用答案文件与 Sysprep 一起](use-answer-files-with-sysprep.md)

 

 






