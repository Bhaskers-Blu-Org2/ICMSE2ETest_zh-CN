---
author: Justinha
Description: "使用答案文件与 Sysprep 一起"
ms.assetid: baa66548-b1f8-42f4-8027-3d515441ac0c
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用答案文件与 Sysprep 一起"
ms.openlocfilehash: 90a374e51e6a8126ac71dcd75613398b6b25c868
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-answer-files-with-sysprep"></a>使用答案文件与 Sysprep 一起


(**Sysprep**) 的系统准备工具和应答文件可用于配置无人参与的 Windows® 安装设置。 本主题介绍一些注意事项和过程使用答案文件与**Sysprep**一起。 有关 Windows 组件和设置，您可以将它们添加到答案文件的详细信息，请参阅[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)。

本主题︰

-   [运行 Sysprep 无数次](#bkmk-skiprearm)

-   [通用化、 auditSystem 和 auditUser 配置阶段中应用设置](#bkmk-1)

-   [答案文件缓存到计算机](#bkmk-2)

-   [在通用化配置阶段期间保持插设备驱动程序](#bkmk-3)

-   [在答案文件中显示 RunSynchronous 操作](#bkmk-4)

## <a name="span-idbkmkskiprearmspanspan-idbkmkskiprearmspanspan-idbkmkskiprearmspanrunning-sysprep-an-unlimited-number-of-times"></a><span id="bkmk_skipRearm"></span><span id="bkmk_skiprearm"></span><span id="BKMK_SKIPREARM"></span>运行 Sysprep 无数次


如果指定产品密钥时，Windows 会自动激活，并无数次运行**Sysprep**命令。 要自动通过提供产品密钥来激活 Windows，请在 Microsoft Windows 的外壳程序-安装指定有效的产品密钥\\`ProductKey`无人参与的在[specialize](specialize.md)配置阶段的设置。 如果自动不通过提供产品密钥来激活 Windows，则 Windows 将提示最终用户提供产品密钥。 如果最终用户将在 OOBE 期间跳过此步骤，Windows 将提醒最终用户输入有效的产品密钥以后。

## <a name="span-idbkmk1spanspan-idbkmk1spanapplying-settings-in-the-generalize-auditsystem-and-audituser-configuration-passes"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>通用化、 auditSystem 和 auditUser 配置阶段中应用设置


在 Windows 安装过程中，并不是所有的配置阶段运行。 仅当运行**Sysprep**，[一般化](generalize.md)、 [auditSystem](auditsystem.md)和[auditUser](audituser.md)配置阶段不可用。

如果将设置添加到答案文件中这些配置阶段中，您必须运行**Sysprep**来应用这些设置如下︰

-   若要应用中的[auditSystem](auditsystem.md)和[auditUser](audituser.md)配置阶段的设置，必须使用**Sysprep/审核**命令引导在审核模式下。

-   若要应用中的[一般化](generalize.md)配置阶段的设置，必须使用**Sysprep**一般化/命令。 通用化的配置阶段中移除系统特定的设置，以便您可以部署在多台计算机上相同的图像。

有关详细信息，请参阅[如何配置阶段的工作](how-configuration-passes-work.md)。

## <a name="span-idbkmk2spanspan-idbkmk2spancaching-answer-files-to-the-computer"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>答案文件缓存到计算机


如果使用答案文件安装 Windows，该答案文件会缓存到系统中。 当后续配置阶段运行时，计算机将该答案文件中的设置应用到系统。 由于此答案文件会缓存，运行**Sysprep**命令时，系统会采用缓存的答案文件中的设置。 如果您使用不同的应答文件中的设置，您可以通过指定一个单独 Unattend.xml 文件**Sysprep /unattend:***&lt;文件\_名称&gt;*选项。 有关详细信息，请参阅[Sysprep 命令行选项](sysprep-command-line-options.md)。 有关如何使用隐式应答文件搜索的详细信息，请参阅[Windows 安装程序自动化概述](windows-setup-automation-overview.md)。

## <a name="span-idbkmk3spanspan-idbkmk3spanpersisting-plug-and-play-device-drivers-during-the-generalize-configuration-pass"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>在通用化配置阶段期间保持插设备驱动程序


当您运行**Sysprep**命令和**一般化 /**选项时，可以保持设备驱动程序。 若要执行此操作，请指定`PersistAllDeviceInstalls`PnPSysprep-Microsoft 的 Windows 组件中的设置。 在[specialize](specialize.md)配置阶段中，插扫描设备，计算机，然后再安装检测到的设备的设备驱动程序。 默认情况下，计算机这些设备驱动器从系统中删除时对系统进行一般化。 如果您设置 Microsoft Windows PnPSysprep\\ `PersistAllDeviceInstalls`在应答文件中设置为**true** ，Sysprep 不会删除检测到的设备驱动程序。

## <a name="span-idbkmk4spanspan-idbkmk4spandisplaying-runsynchronous-actions-in-an-answer-file"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>在答案文件中显示 RunSynchronous 操作


在审核模式下，可以查看 Microsoft Windows 部署的状态\\`RunSynchronous`在[auditUser](audituser.md)配置阶段运行的命令。 **AuditUI**窗口显示命令的状态，并提供这些服务︰

-   可视进度指示安装进行且未挂起。

-   何时何地出现故障的可视指示。 如果该命令不创建日志文件，这会提供快速的诊断。

如果答案文件中包含 Microsoft Windows 部署\\`RunSynchronous`在[auditUser](audituser.md)配置命令传递，在**AuditUI**窗口中显示的命令列表。 命令的顺序出现，Microsoft Windows 部署\\`RunSynchronous` \\ `RunSynchronousCommand` \\ `Order`设置指定。 每个列表项的用户界面是从下列任一字符串︰

-   Microsoft Windows 部署\\`RunSynchronous` \\ `RunSynchronousCommand` \\ `Description` （如果存在）

-   Microsoft Windows 部署\\`RunSynchronous`\\`RunSynchronousCommand`\\`Path`

**Sysprep**处理所有`RunSynchronous`命令顺序。 如果此命令成功执行，其相关的列表项将接收一个绿色的复选标记批注。 如果命令失败，其相关的列表项将接收一个红色的 X 批注。 如果该命令要求重新启动，在启动之后，将显示**AuditUI**窗口，但仅未处理的列表项显示。 以前已处理的项不再**AuditUI**窗口中显示。 如果**AuditUI**窗口中的项的列表超出的高度显示，列表将被截断到显示并不会滚动。 因此，您可能无法查看某些项目。

Windows 安装程序将返回代码解释为在**AuditUI**窗口中的状态值。 零值指示成功。 一个非零值指示故障。 该命令的返回值可能会影响 Windows 安装程序的行为取决于 Microsoft Windows 部署的值\\`RunSynchronous`\\`RunSynchronousCommand`\\**WillReboot**设置。

如果`WillReboot`命令设置为**始终**:

-   如果命令返回 0，其相关的列表项将接收一个绿色的复选标记批注。 将立即重新启动。

-   如果该命令返回非零值，其相关的列表项接收一个红色的 X 批注。 将立即重新启动。 一个非零的返回值不视为致命错误时`WillReboot`设置为**始终**或**从不**。

如果`WillReboot`命令设置为**从不**:

-   如果命令返回 0，其相关的列表项将接收一个绿色的复选标记批注。

-   如果该命令返回非零值，其相关的列表项接收一个红色的 X 批注。 一个非零的返回值不视为致命错误时`WillReboot`设置为**始终**或**从不**。

如果`WillReboot`命令设置为**OnRequest**:

-   如果命令返回 0，其相关的列表项将接收一个绿色的复选标记批注。

-   如果该命令返回 1，其相关的列表项将接收一个绿色的复选标记批注。 将立即重新启动。

-   如果该命令返回 2，则其相关的列表项暂时接收一个绿色的复选标记批注。 将立即重新启动。 在重新启动后相关的列表项会再次出现在**AuditUI**窗口中不带批注由于命令仍在进行。

-   如果该命令返回其他值，则会发生致命错误并阻止对话框出现。 如果 Errorhandler.cmd 文件，则不显示对话框。 有关 Errorhandler.cmd 文件的详细信息，请参阅[添加到 Windows 安装程序的自定义脚本](add-a-custom-script-to-windows-setup.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)

[Sysprep 命令行选项](sysprep-command-line-options.md)

[Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)

[Sysprep 过程概述](sysprep-process-overview.md)

[部署疑难解答和日志文件](deployment-troubleshooting-and-log-files.md)

 

 






