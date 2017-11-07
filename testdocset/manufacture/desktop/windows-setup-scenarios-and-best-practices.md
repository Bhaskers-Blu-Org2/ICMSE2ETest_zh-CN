---
author: Justinha
Description: "Windows 安装程序方案和最佳做法"
ms.assetid: 651cb9c3-121d-40d3-9e17-47f1a78a000f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序方案和最佳做法"
ms.openlocfilehash: 02d4264091ab6962556f9d0e0b370073aa052b88
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-scenarios-and-best-practices"></a>Windows 安装程序方案和最佳做法


Windows® 安装程序安装的 Windows 操作系统。 Windows 安装程序使用称为基于映像的安装程序 (IBS) 提供了单一、 统一的过程，与所有的客户可以将 Windows 安装程序的技术。 IBS 执行全新安装和升级的 Windows，并在客户端和服务器安装中使用。 Windows 安装程序还可以使用自定义 Windows 安装过程中的安装的答案文件设置。

本主题︰

-   [常见使用情形](#commoninstallationscenarios)

-   [Windows 安装程序最佳做法](#bestpractices)

-   [Windows 安装程序局限性](#limitations)

## <a name="span-idcommoninstallationscenariosspanspan-idcommoninstallationscenariosspanspan-idcommoninstallationscenariosspancommon-usage-scenarios"></a><span id="CommonInstallationScenarios"></span><span id="commoninstallationscenarios"></span><span id="COMMONINSTALLATIONSCENARIOS"></span>常见使用情形


常见安装方案包括执行干净安装、 升级和无人参与的安装。

### <a name="span-idcustominstallationsspanspan-idcustominstallationsspanspan-idcustominstallationsspancustom-installations"></a><span id="Custom_Installations"></span><span id="custom_installations"></span><span id="CUSTOM_INSTALLATIONS"></span>自定义安装

Windows 安装程序的最常见方案执行自定义安装。 在此方案中，您将 Windows 安装到没有一个操作系统，也有以前版本的 Windows 的计算机上。 该方案包括以下阶段︰

1.  从您的 Windows 产品 DVD 或网络共享中运行 Setup.exe。

2.  选择**自定义**安装类型。

3.  如果您从以前安装的 Windows 安装，Windows 安装程序会创建一个本地启动目录和将所有所需的 Windows 安装程序文件复制到此目录。

4.  Windows 安装程序重新启动、 安装和配置 Windows 组件，安装完成后，启动 Windows 欢迎。

自定义安装不从以前安装的 Windows 版本迁移的任何设置或首选项。 从以前的 Windows 版本的文件被复制到\\Windows.old 目录。 在 Windows 安装，包括用户、 程序文件和 Windows 目录中的所有数据将都保存到此目录。

### <a name="span-idupgradesspanspan-idupgradesspanspan-idupgradesspanupgrades"></a><span id="Upgrades"></span><span id="upgrades"></span><span id="UPGRADES"></span>升级

从受支持的操作系统，Windows 安装程序还可以执行升级。

此方案包括以下阶段︰

1.  在以前版本的 Windows 上运行 Setup.exe。

2.  选择**升级**安装类型。 Windows 安装程序将升级该系统，并在安装过程中保护您的文件、 设置和首选项。

3.  Windows 安装程序将重新启动并还原您的受保护的文件、 设置和首选项。 Windows 安装程序并启动 Windows 欢迎。

**请注意**  
升级被用来将一台计算机升级到 Windows 8。 升级还支持将用户数据迁移到新系统。

 

### <a name="span-idautomatedinstallationsspanspan-idautomatedinstallationsspanspan-idautomatedinstallationsspanautomated-installations"></a><span id="Automated_Installations"></span><span id="automated_installations"></span><span id="AUTOMATED_INSTALLATIONS"></span>自动的安装

自动的安装使您能够自定义 Windows 安装并删除用户与 Windows 安装程序进行交互的需求。 通过使用 Windows 系统映像管理器 (Windows SIM) 或组件平台接口 (CPI) Api，您可以创建一个或多个自定义的 Windows 安装，然后可通过部署跨许多不同的硬件配置。

自动的安装，也称为无人参与的安装方案包括以下阶段︰

1.  使用 Windows sim 卡或 CPI Api 来创建无人参与的安装应答文件，通常称为 Unattend.xml。 此答案文件包含所有您在 Windows 映像中配置的设置。 有关详细信息，请参阅[Windows 系统映像管理器帮助主题](https://msdn.microsoft.com/library/windows/hardware/dn915116)。

2.  从 Windows PE 中，早期版本的 Windows 或其他的预安装环境，运行 Setup.exe 的显式路径到答案文件。 如果不包括答案文件的路径，Setup.exe 会搜索几个特定位置中一个有效的应答文件。 有关详细信息，请参阅[Windows 安装程序命令行选项](windows-setup-command-line-options.md)。

3.  然后，Windows 安装程序安装操作系统，并配置答案文件中列出的所有设置。 其他应用程序、 设备驱动程序和更新也可以在 Windows 安装过程中安装。 在安装操作系统后，启动欢迎使用 Windows 安装程序。

## <a name="span-idbestpracticesspanspan-idbestpracticesspanspan-idbestpracticesspan-windows-setup-best-practices"></a><span id="BestPractices"></span><span id="bestpractices"></span><span id="BESTPRACTICES"></span>Windows 安装程序最佳做法


下一节介绍一些使用 Windows 安装程序的最佳做法。

-   **验证有足够的空间供 Windows 安装程序的临时文件。** 如果从早期版本的 Windows 中运行安装程序，确认临时的 Windows 安装程序文件的磁盘上没有足够的空间。 所需的空间可能会有所不同，但它可以达 500 兆字节 (MB)。

-   **以前的 Windows 安装移动到 Windows.old 文件夹中。** 作为一种最佳做法，您应该备份您的数据在升级之前。 如果将 Windows 安装在以前的 Windows 安装，所有以前的 Windows 文件和目录移动到 Windows.old 文件夹中，包括用户、 程序文件和 Windows 目录的内容。 在 Windows 安装完成后，可以访问 Windows.old 文件夹中的数据。 如果您不在的用户、 程序文件或 Windows 目录中的其他文件夹，这些文件夹不会移动。 例如，如果您有一个名为 c︰ 的文件夹\\驱动程序，该文件夹将不被移动到 Windows.old 文件夹。

-   **检查 Windows 安装程序日志文件。** 如果在 Windows 安装过程中遇到问题，请查看日志文件在 %WINDIR%\\黑豹。 您将能够识别并通过查看安装日志文件解决很多问题。 有关详细信息，请参阅[部署故障排除和日志文件](deployment-troubleshooting-and-log-files.md)， [Windows 安装程序日志文件和事件日志](windows-setup-log-files-and-event-logs.md)。

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspan-windows-setup-limitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>Windows 安装程序局限性


以下各节描述一些 Windows 安装程序的限制。 运行 Windows 安装程序之前，请阅读此部分。

-   **启用基于 UEFI 的计算机上安装的 （uefi） 兼容性模式**。 在某些 （uefi） 的计算机上不能将 Windows 安装在 BIOS 兼容模式下。 您可能需要切换到 UEFI 兼容性模式。

-   **应用程序可能需要一致的驱动器号。** 如果安装到 Windows 映像的自定义应用程序，我们建议，您将 Windows 安装到目标计算机上相同的驱动器号因为某些应用程序需要一致的驱动器号。 卸载方案、 提供服务方案和修复方案可能无法正常执行如果系统的驱动器号与应用程序中指定的驱动器号不匹配。 此限制适用于部署映像服务和管理 (DISM) 工具和 Windows 安装程序。

-   **将多个映像部署到多个分区。** 如果您捕获和部署多个分区上的多个图像，则必须满足以下要求︰

    -   分区结构、 总线位置和磁盘数必须相同，在参考计算机和目标计算机上。

    -   分区类型 （主要、 扩展，或逻辑） 必须匹配。 参考计算机上的活动分区必须与目标计算机相匹配。

-   **安装自定义.wim 文件需要一个.wim 文件中的描述值。** 创建自定义的.wim 文件时，Windows 安装程序要求您始终包含一个描述值。 如果.wim 文件不包含一个描述值，该图像可能无法正确安装。 在**dism**命令使用**/capture-image**选项时，您可以提供一个描述值。 如果您安装的.wim 文件没有描述值，重新捕获映像并提供有效的描述值。 有关详细信息，请参阅[DISM 的部署映像服务和管理技术参考的窗口](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)。

**请注意**  
对于 Windows® 预安装环境 (Windows PE)，引导文件的版本必须匹配的计算机体系结构。 X64 UEFI 的计算机只可以使用 x64 的 Windows PE 启动引导文件。 计算机只可以通过使用 Windows PE x86 引导 x86 引导文件。 这是不同于旧的 BIOS。 在旧的 BIOS，x64 计算机可以引导使用 x86 引导文件。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序安装过程](windows-setup-installation-process.md)

[Windows 安装程序自动化概述](windows-setup-automation-overview.md)

[审核模式概述](audit-mode-overview.md)

[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






