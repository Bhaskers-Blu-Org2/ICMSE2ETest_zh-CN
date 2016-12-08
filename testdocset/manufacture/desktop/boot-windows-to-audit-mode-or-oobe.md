---
author: Justinha
Description: "引导到审核模式或 OOBE 的窗口"
ms.assetid: a928dea9-52b1-42b9-bee1-cbe9c8c0b07b
MSHAttr: PreferredLib:/library/windows/hardware
title: "引导到审核模式或 OOBE 的窗口"
ms.openlocfilehash: 16b0a5a0064abdbbd608892f1b1d257fc04fa1f8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-windows-to-audit-mode-or-oobe"></a>引导到审核模式或 OOBE 的窗口


可以使用审核模式下自定义您的计算机、 添加应用程序和设备驱动程序和在 Windows 环境中测试您的计算机。 启动到审核模式下启动计算机中内置的管理员帐户。 Windows® 在[一般化](generalize.md)配置阶段自动删除此帐户。 配置计算机启动到审核模式后，计算机将继续启动到审核模式，默认情况下，直到您在配置计算机时计算机附带的用户引导到外的全新体验 (OOBE)。

如果受密码保护的屏幕保护程序启动时在审核模式下，您无法重新登录到系统。 登录后立即禁用内置管理员帐户，用于登录到审核模式。 若要禁用屏幕保护程序，或者更改电源计划通过在 Windows 控制面板或配置和部署一个自定义计划。 有关详细信息，请参阅[创建自定义电源计划](create-a-custom-power-plan-technicalreference.md)。


## <a name="span-idbkmk1spanspan-idbkmk1spanboot-to-audit-mode-automatically-on-a-new-installation"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>启动到审核模式自动上全新安装


-   若要将 Windows 配置为启动到审核模式下，添加**Microsoft Windows 部署 |重新封装 |模式 = 审核**答案文件设置。

    Windows 完成安装过程中，计算机时自动启动到审核模式下，系统准备 (**Sysprep**) 工具出现。 有关在审核模式下使用 Sysprep 工具的详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

    **请注意**  
    在审核模式下不出现**oobeSystem**配置阶段从答案文件中的设置。 关于哪个答案时引导到审核模式或 OOBE 处理文件设置的详细信息，请参阅[如何配置阶段的工作](how-configuration-passes-work.md)。

     

## <a name="span-idbkmk2spanspan-idbkmk2spanboot-to-audit-mode-manually-on-a-new-or-existing-installation"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>启动到审核模式下手动 （在新的或现有安装）


-   在 OOBE 屏幕上，按下**ctrl 键**+**班次**+**F3**。

    Windows 将计算机重新启动到审核模式，并系统准备 (**Sysprep**) 工具出现。

    **请注意**  
    **Ctrl 键**+**班次**+**f3 键**键盘快捷方式不会忽略 OOBE 过程的所有部分，如运行脚本及应用答案文件设置在**oobeSystem**配置传递。

     

## <a name="span-idbkmk3spanspan-idbkmk3spanboot-to-oobe-automatically-on-a-new-installation"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>引导至 OOBE 自动上全新安装


-   若要将 Windows 配置为启动到 OOBE，添加**Microsoft Windows 部署 |重新封装 |****模式****= oobe**答案文件设置。

    如果您已配置 Windows 映像启动到 OOBE，但则需要在审核模式下进行进一步配置到您的图像，请参阅[的修改一个现有的图像，它是配置为启动到 OOBE](#bkmk-4)。

## <a name="span-idbkmk4spanspan-idbkmk4spanmodify-an-existing-image-that-is-configured-to-boot-to-oobe"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>修改现有的映像配置为 OOBE 启动


-   如果您已配置 Windows 映像引导至 OOBE，但需要在审核模式下进行进一步配置到您的映像，可以执行以下任一操作︰

    1.  使用**ctrl 键**+**班次**+**f3 键**键盘快捷方式。 计算机将重新启动到审核模式。

        此选项可能会触发已配置为在 OOBE 中启动的任何脚本。

        -或者-

    2.  装入该映像，使用**审核**设置，添加应答文件另存为**c:\\测试\\脱机\\Windows\\黑豹\\人参与\\Unattend.xml**。 这可能需要重写现有的应答文件在此位置。

        在下次启动时，Windows 将启动直接进入审核模式。

## <a name="span-idbkmk5spanspan-idbkmk5spanboot-to-audit-mode-automatically-from-an-existing-image"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>启动到审核模式自动从现有的映像


1.  创建新的应答文件，然后再添加**Microsoft Windows 部署 |重新封装 |模式 = 审核**设置。 将答案文件另存为**Unattend.xml**。

2.  在提升的命令提示符下，将 Windows 映像的安装。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\MyImage.wim /index:<image_index> /MountDir:C:\test\offline
    ```

    其中*&lt;图像\_索引&gt;*上的.wim 文件的所选图像的数字。

3.  复制到新的应答文件**c:\\测试\\脱机\\Windows\\黑豹\\人参与文件夹**。

4.  提交所做的更改，然后卸载映像。 例如︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /commit
    ```

    当图像应用于目标计算机和 Windows 启动时，计算机启动到审核模式，自动和**Sysprep**工具出现。 有关示例的过程，请参阅步骤 1︰ 将图像传输到不同的计算机和第 2 步︰ 准备[部署示例](#bkmk-6)中的客户计算机。

应用映像的选项还包括使用答案文件设置，例如指定要安装的映像和要在目标计算机上的磁盘配置。 有关详细信息，请参阅[无人参与的 Windows 安装程序参考指南](http://go.microsoft.com/fwlink/?linkid=206281)。

## <a name="span-idbkmk6spanspan-idbkmk6spandeployment-examples"></a><span id="bkmk_6"></span><span id="BKMK_6"></span>部署示例


要将图像传输到另一台计算机，您必须首先删除特定于计算机的信息从已配置的计算机通过泛化图像与**Sysprep**工具。 要为客户准备一台计算机，必须对计算机进行一般化，并将其引导到 OOBE 客户第一次启动计算机时。 在下面的示例中，我们将创建和将参考图像传输到另一台计算机，然后创建运送给客户一个特定模型的图像。

**步骤 1︰ 将图像传输到另一台计算机**

1.  在参考计算机上安装 Windows。

2.  完成安装后，启动计算机并安装任何其它设备驱动程序或应用程序。

3.  更新 Windows 安装后，运行**Sysprep**:

    -   在命令行运行**Sysprep / 一般化 /shutdown**命令。

        -或者-

    -   在系统准备工具窗口中，选择**关机选项**上的**系统清理操作**框下的**通用化**复选框，选择**关闭**，然后单击**确定**。

    **Sysprep**删除从 Windows 安装的系统特定的数据。 系统特定的信息包括事件日志、 唯一的安全 Id (Sid) 和其他独特的信息。 **Sysprep**会将唯一性系统信息删除后，关闭计算机。

4.  计算机关机后，插入 Windows PE USB 闪存驱动器或其它可引导介质并重新启动到 Windows PE。

5.  在 Windows PE 会话中，通过使用**Dism /capture-image**命令来捕获参考映像。

6.  继续执行下一步以创建特定模型参考映像。

**第 2 步︰ 为客户准备计算机**

1.  安装在您的客户发送到步骤 1 中创建参考映像。

2.  更新 Windows 安装中的，在命令行运行后**Sysprep/审核 / 一般化 /shutdown**命令，可以将 Windows 配置为启动到审核模式的计算机。 然后可以通过引导至另一个分区或使用 Windows PE 捕获 Windows 映像。

3.  使用新的特定模型参考映像的新计算机上安装 Windows。 将 Windows 映像应用于计算机，并且 Windows 启动到审核模式。

4.  （可选）您可以安装其他应用程序和其他更新基于客户的订单。 您还可以测试计算机以验证所有组件正常都工作。

5.  更新 Windows 安装后，运行**Sysprep /oobe /shutdown 命令**。

    **请注意**  
    如果使用安装的 Windows 映像**Sysprep 一般化 /oobe /**命令，用户体验不会理想。 在下次重新启动后运行**Sysprep 一般化 /oobe /**命令，Windows 运行在**specialize**配置阶段、 插和其他设置任务之前 Windows 启动 OOBE。 此过程可能要花费更多时间，可以延迟客户的第一次登录。

     

6.  打包并将计算机交付给客户。

    当客户启动计算机时，将运行 OOBE。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[审核模式概述](audit-mode-overview.md)

[在审核模式下添加驱动程序](add-a-driver-online-in-audit-mode.md)

[启用和禁用内置管理员帐户](enable-and-disable-the-built-in-administrator-account.md)

[从 DVD 启动](boot-from-a-dvd.md)

[使用 Windows 安装程序配置集](use-a-configuration-set-with-windows-setup.md)

[部署自定义映像](deploy-a-custom-image.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[向 Windows 安装程序中添加自定义脚本](add-a-custom-script-to-windows-setup.md)

 

 






