---
author: Justinha
Description: "Sysprep （通用化） Windows 安装"
ms.assetid: 455fa70e-6c13-45ae-ad4f-5d12e3b844e5
MSHAttr: PreferredLib:/library/windows/hardware
title: "Sysprep （通用化） Windows 安装"
ms.openlocfilehash: ee0e7a959ce04b56aedb3fdc8a2141acb71f71e9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-generalize-a-windows-installation"></a>Sysprep （通用化） Windows 安装


使用**Sysprep**一般化 Windows 安装。 若要将 Windows 映像部署到不同的 Pc，您必须先准备映像。 您可以使用系统准备 (Sysprep) 工具也可以准备映像无人参与安装的一部分答案文件中指定的设置。 准备映像，您必须从映像中删除特定于计算机的信息。 此过程称为*泛化*图像。

在大多数部署方案中，您不再需要使用`SkipRearm`回答时多次在计算机上运行**Sysprep**命令重置 Windows 产品激活时钟的设置文件。 `SkipRearm`设置用于指定授权状态的窗口。 如果您指定的零售产品密钥或批量许可证产品密钥，将自动激活 Windows。 您可以运行**Sysprep**命令到 8 次的单一 Windows 映像上。 在运行 Sysprep 8 倍之后, 您必须重新创建 Windows 映像。 有关 Windows 组件和设置，您可以将它们添加到答案文件的详细信息，请参阅[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)。

**警告︰**  
不要使用 Windows 应用商店来更新您的 Windows 应用商店应用程序之前运行**sysprep 一般化 /**。 **Sysprep**不能归纳中这种情况下的图像。 此问题也适用于 Windows 应用商店应用程序 （例如，邮件、 地图、 Bing 财务、 Bing 新闻，和其他人）。 要自定义作为内置的管理员，在审核模式下安装或使用特定用户帐户时，可以发生这种情况。 Sysprep 日志文件中显示以下错误 (%WINDIR%\\System32\\Sysprep\\黑豹):

`<package name> was installed for a user, but not provisioned for all users. This package will not function properly in the sysprep image.`

**Sysprep 一般化 /**要求所有用户都提供了所有应用程序。 但是，从 Windows 应用商店应用程序更新时，该应用程序变为不可提供且与该用户帐户相关联。

而不是使用 Windows 应用商店要更新您的应用程序，您应 sideload 更新为您的业务线应用程序，或在目标电脑上使用 Windows 应用商店更新其应用程序的最终用户。 在托管环境中，如果 Windows 应用商店访问禁用由 IT 管理员，您将不能更新的 Windows 应用商店应用程序。

Sideloading 业务线的 Windows 应用商店应用程序有关的详细信息，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)和[自定义开始屏幕](customize-the-start-screen.md)。

 

如果您的服务器有远程身份验证拨入用户服务 (RADIUS) 客户端或网络策略服务器 (NPS) 配置中定义的远程 RADIUS 服务器组，应将其部署到另一台计算机之前删除这些信息。 有关详细信息，请参阅[准备图像处理网络策略服务器 (NPS)](prepare-a-network-policy-server--nps--for-imaging.md)。

本主题︰

-   [泛化图像](#bkmk-1)

-   [泛化虚拟硬盘](#bkmk-2)

## <a name="span-idbkmk1spanspan-idbkmk1spangeneralizing-an-image"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>泛化图像


当您一般化 Windows 映像时，Windows 安装程序处理中的[一般化](generalize.md)配置阶段的设置。 即使在技术人员计算机和参考计算机具有相同的硬件配置，您必须运行**Sysprep**命令和**一般化 /**选项。 **Sysprep 一般化 /**命令从 Windows 安装移除唯一的信息，以便可以安全地重复使用另一台计算机上的图像。 但是，可以将驱动程序保持通用化配置阶段。

**重要**  
当您设置参考计算机时，Windows 安装程序将安装任何检测到的设备的驱动程序。 默认情况下，Windows 安装程序将删除这些驱动程序时对系统进行一般化。 如果您正在向计算机具有相同的硬件和设备部署映像，您需要 Windows 安装程序以重新安装这些相同的驱动程序。 若要在系统归纳过程中在计算机上保留这些驱动程序，设置 Microsoft Windows PnPSysprep |`PersistAllDeviceInstalls`将设置为**true**。 **Sysprep**有关更多信息-相关的 Windows 组件添加到答案文件，请参阅[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)。

 

在运行**Sysprep**时，Windows 操作系统卷上替换仅计算机安全标识符 (SID)。 当**Sysprep**泛化图像时，其泛化只是常规的分区。 所以如果一台计算机有多个操作系统，则必须运行**Sysprep**上每个图像分别。

**要对图像进行一般化**

1.  向答案文件添加以下设置之一︰

    -   使用 Microsoft Windows 部署 |`Generalize`设置。 设置`Mode` **OOBE**或**审核**时，和一组`ForceShutdownNow`为**true**。 计算机自动泛化图像，并将关闭。

        -或者-

    -   添加 Microsoft Windows 部署 |`Reseal`设置到[oobeSystem](oobesystem.md)配置阶段。 设置`Mode`**审核**。 计算机在审核模式下启动，并显示**系统准备工具**窗口后，请使用以下方法之一︰

        -   在**系统准备工具**窗口中，单击**通用化**，单击**关机**，然后单击**确定**。 计算机图像泛化和关闭。

            -或者-

        -   关闭**系统准备工具**窗口，打开命令提示符窗口以管理员的身份，然后将移至**%WINDIR%\\system32\\sysprep**目录。 使用**Sysprep**命令和**/ 一般化**、 **/shutdown**和**/oobe**选项。 例如︰

            ``` syntax
            Sysprep /generalize /shutdown /oobe
            ```

            计算机图像泛化和关闭。

2.  关闭计算机后，使用映像捕获工具捕获图像。 为此目的，可以使用部署映像服务和管理 (**DISM**) 工具中的**Dism /capture-image**命令。

3.  将此映像部署到参考计算机。 参考计算机引导时，它显示出的全新体验 (OOBE) 屏幕。

有关详细信息，请参阅[自动执行 OOBE 设置](settings-for-automating-oobe.md)和[配置 Oobe.xml](configure-oobexml.md)。

如果您有其他自定义设置，可以手动输入审核模式和一般化和部署映像之前使这些自定义设置。

**可选︰ 输入审核模式前手动您一般化映像**

1.  在 OOBE 屏幕上，按 Ctrl + Shift + F3。 Windows 将在审核模式下，计算机重新启动，**系统准备工具**窗口将出现。

    **警告︰**  
    Ctrl + Shift + F3 键盘快捷方式不会绕过 OOBE 进程，如运行脚本及应用[oobeSystem](oobesystem.md)配置阶段中的答案文件设置的所有部分。

     

2.  添加您要包括的自定义项。

3.  在**系统准备工具**窗口中，单击**通用化**，单击**关机**，然后单击**确定**。 计算机图像泛化和关闭。

     -或者-

    关闭**系统准备工具**窗口，打开命令提示符窗口以管理员的身份，然后将移至**%WINDIR%\\system32\\sysprep**目录。 使用**Sysprep**命令和**/ 一般化**、 **/shutdown**和**/oobe**选项。 例如︰

    ``` syntax
    Sysprep /generalize /shutdown /oobe
    ```

    计算机图像泛化和关闭。

4.  关闭计算机后，使用映像捕获工具捕获图像。 为此目的，可以在**DISM**工具使用**Dism /capture-image**命令。

5.  将此映像部署到参考计算机。 参考计算机引导时，它会显示 OOBE 屏幕。

有关审核模式的详细信息，请参阅︰

-   [审核模式概述](audit-mode-overview.md)

-   [引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

-   [在审核模式下添加驱动程序](add-a-driver-online-in-audit-mode.md)

-   [启用和禁用内置管理员帐户](enable-and-disable-the-built-in-administrator-account.md)

## <a name="span-idbkmk2spanspan-idbkmk2spangeneralizing-a-virtual-hard-disk"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>泛化虚拟硬盘


您可以使用**Sysprep** VM 模式归纳要作为同一虚拟机或虚拟机监控程序 VHD 部署 VHD。 虚拟机模式支持快速部署的虚拟机。 仅在运行时从虚拟机中支持虚拟机模式。 另外，就只能通过命令行可以虚拟机模式。 不能使用虚拟机模式 VHD 准备部署到所有计算机。

**通用化 VHD**

1.  在审核模式下，打开一个命令提示符窗口以管理员的身份，然后再到**%WINDIR%\\system32\\sysprep**目录。

2.  使用**Sysprep**命令和**/ 一般化**、 **/oobe**和**/mode:vm**选项。 例如︰

    ``` syntax
    Sysprep /generalize /oobe /mode:vm
    ```

    计算机使一般化 VHD 映像。

3.  部署在同一个虚拟机上通用的 VHD 映像。 当虚拟机重新启动时，它会显示 OOBE 屏幕。

应用于虚拟机模式下的唯一额外选项**是/重引导**、 **/shutdown**，和**/ 退出**。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep 过程概述](sysprep-process-overview.md)

[Sysprep 命令行选项](sysprep-command-line-options.md)

[Sysprep 支持的服务器角色](sysprep-support-for-server-roles.md)

[使用产品密钥和激活](work-with-product-keys-and-activation-auth-phases.md)

 

 






