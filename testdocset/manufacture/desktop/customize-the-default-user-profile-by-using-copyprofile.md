---
author: Justinha
Description: "通过使用 CopyProfile 自定义默认用户配置文件"
ms.assetid: 4aa887d1-1ecb-4fad-9119-ac851c273ab3
MSHAttr: PreferredLib:/library/windows/hardware
title: "通过使用 CopyProfile 自定义默认用户配置文件"
ms.openlocfilehash: 204212a2c11d16ffd18099f8a7df594a22fe7567
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customize-the-default-user-profile-by-using-copyprofile"></a>通过使用 CopyProfile 自定义默认用户配置文件


您可以使用`CopyProfile`若要自定义的用户配置文件，然后将该配置文件复制到默认用户配置文件的设置。 Windows® 使用的默认用户配置文件作为模板来为每个新用户指派配置文件。 通过自定义的默认用户配置文件，您可以配置为在计算机创建的所有用户帐户设置。 通过使用`CopyProfile`，您可以自定义安装的应用程序、 驱动程序、 桌面背景、 internet 浏览器设置，以及其他配置。 请注意，某些设置不保留使用`CopyProfile`。

企业和 IT 专业人员可以使用`CopyProfile`若要保留自定义平铺**开始**在屏幕上组的布局。

本主题︰

-   [保留用户配置文件设置](#bkmk-preserve)

-   [配置默认用户配置文件设置](#bkmk-configure)

-   [故障排除 CopyProfile](#bkmk-troubleshoot)

## <a name="span-idbkmkpreservespanspan-idbkmkpreservespancreating-an-answer-file-with-the-copyprofile-setting"></a><span id="bkmk_preserve"></span><span id="BKMK_PRESERVE"></span>CopyProfile 设置与创建答案文件


使用以下过程来创建应答文件来指导**Sysprep**来复制用户配置文件设置，当您一般化 Windows 映像。

**若要创建一个单独的应答文件复制用户配置文件设置**

1.  技术人员计算机上打开 Windows 系统映像管理器 （Windows sim 卡）。 单击**开始**，键入**Windows 系统映像管理器**，然后选择**Windows 系统映像管理器**。 有关 Windows sim 卡的详细信息，请参阅[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445)。

2.  创建新的答案文件与**sysprep 配合**使用︰

    1.  单击**文件**，然后单击**新的应答文件**。 在**应答文件**窗格中显示空白答案文件。

        **请注意**  
        如果**Windows 映像**窗格中没有该编录文件，请按照[打开 Windows 映像或编录文件](https://msdn.microsoft.com/library/windows/hardware/dn915104)中的说明进行操作。

         

    2.  在**Windows 映像**窗格中，展开**组件**中，右键单击**amd64\_Microsoft Windows 外壳程序安装**，然后单击**将设置添加到传递 4 专用化**。

    3.  在**应答文件**窗格中，选择**组件\\4\_专用\\amd64-Microsoft 的 Windows 的外壳程序-安装\_中性**文件夹。

    4.  在**Microsoft Windows 外壳程序安装属性**窗格中的**设置**部分中，键入的值`CopyProfile = true`。

    5.  将此新的应答文件保存到根目录下的可移动媒体或网络位置，并将其命名为**CopyProfile**。

有关详细信息，请参阅[创作答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)和[无人参与的 Windows 安装程序参考指南 》](http://go.microsoft.com/fwlink/?LinkId=206281)。

## <a name="span-idbkmkconfigurespanspan-idbkmkconfigurespanconfiguring-default-user-profile-settings"></a><span id="bkmk_configure"></span><span id="BKMK_CONFIGURE"></span>配置默认用户配置文件设置


使用以下过程可以在审核模式下配置用户设置，然后使用应答文件中包含的一般化 Windows 安装`CopyProfile`设置。 另一个答案文件安装 Windows 时，如果该答案文件不应包含`CopyProfile`设置或创建其他用户帐户的任何设置。

**若要配置默认用户配置文件设置和一般化映像**

1.  将 Windows 安装在参考计算机，在审核模式下启动。 有关详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

    **重要**  
    不要使用域帐户，因为`CopyProfile`设置运行后运行**Sysprep**时，计算机已从域中删除。 因此，您将丢失在域中配置的任何设置。 如果您更改默认用户配置文件，然后将计算机加入到域，默认用户配置文件所做的自定义将出现在新的域帐户。

     

2.  通过内置的管理员帐户安装的应用程序、 桌面快捷方式，以及其他设置。

    **重要**  
    没有提供基于 Windows 运行时的应用程序可以安装的数量限制。 但是，您可以创建脚本来安装其他非配置应用程序。 有关详细信息，请参阅[使用 DISM 的 Sideload 应用程序](sideload-apps-with-dism-s14.md)。

     

3.  完成自定义后，插入包含 CopyProfile 答案文件中的引用计算机中的媒体。 例如，您可以将答案文件复制到 USB 驱动器。

4.  在参考计算机上，打开提升的命令提示符下，然后键入以下命令︰

    ``` syntax
    C:\Windows\System32\Sysprep\Sysprep /generalize /oobe /shutdown /unattend: F:\CopyProfile.xml
    ```

    其中*F*是 USB 闪存驱动器或其他可移动媒体的字母。 **Sysprep**工具删除特定于计算机的信息从图像，同时保留您配置的用户配置文件设置。 有关详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

通用图像后，计算机将关闭捕获通过引导至 Windows PE 映像，然后通过使用 DISM 中捕获的 Windows 安装。 有关详细信息，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)和[捕获映像的硬盘分区使用 DISM](capture-images-of-hard-disk-partitions-using-dism.md)。 捕获映像后，您可以通过使用 DISM 将其部署到目标计算机中。 有关详细信息，请参阅[使用 DISM 应用图像](apply-images-using-dism.md)。

## <a name="span-idtesttheuserprofilecustomizationsspanspan-idtesttheuserprofilecustomizationsspanspan-idtesttheuserprofilecustomizationsspantest-the-user-profile-customizations"></a><span id="Test_the_User_Profile_Customizations"></span><span id="test_the_user_profile_customizations"></span><span id="TEST_THE_USER_PROFILE_CUSTOMIZATIONS"></span>测试用户配置文件自定义设置


自定义的映像部署到目标计算机后，您可以测试用户配置文件自定义设置。 您可以通过的全新体验 (OOBE) 来测试的最终用户体验，也可以在审核模式下测试用户自定义设置。

**重要**  
原因审核模式下使用内置的管理员帐户，将不会在审核模式下启动基于 Windows 运行时的应用程序。 运行基于 Windows 运行时的应用程序必须修改注册表项之前，您可以验证您的 Windows 安装在审核模式下。

 

**在 OOBE 后测试用户配置文件自定义设置**

1.  将 Windows 安装到一台测试计算机。

2.  在安装 Windows 之后，经过 OOBE 并指定计算机名、 用户帐户名称，以及其他项目。 OOBE 完毕后，将显示 Windows 启动屏幕。

3.  在 OOBE 期间指定的用户帐户具有登录到计算机并验证您的应用程序和自定义设置显示。

**在审核模式下测试用户配置文件自定义设置**

1.  启动到审核模式下，通过使用应答文件或 OOBE 启动时按 Ctrl + Shift + F3。 有关详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

2.  请验证您的自定义如预期那样工作。 若要测试基于 Windows 运行时的应用程序，请修改以下注册表项︰

    1.  从提升的命令提示符下，运行 Regedit.exe。

    2.  浏览到**HKEY\_本地\_机\\软件\\Microsoft\\Windows\\CurrentVersion\\策略\\系统\\FilterAdministratorToken**注册表项。

    3.  单击**FilterAdministrationToken**，然后键入**1**作为值数据。

    4.  从计算机注销。

    5.  重新登录到计算机，然后启动基于 Windows 运行时的应用程序以验证您的自定义如预期那样工作。

    6.  完成 Windows 运行时基于应用程序的验证后，请将**FilterAdministrationToken**注册表项重置为**0**。

## <a name="span-idbkmktroubleshootspanspan-idbkmktroubleshootspantroubleshooting-copyprofile"></a><span id="bkmk_troubleshoot"></span><span id="BKMK_TROUBLESHOOT"></span>故障排除 CopyProfile


如果没有成功复制用户配置文件设置︰

1.  请确保您设置`CopyProfile`在部署过程中一次只能设置。

2.  自定义用户设置时，只能使用只有内置的管理员帐户在计算机上以避免意外错误的配置文件中复制设置。

3.  确认您没有使用的域帐户。

4.  验证不是内置的管理员帐户配置任何其他用户帐户︰

    1.  单击**开始**，然后键入**控制面板**。

    2.  单击**控制面板**，然后单击**添加或删除用户帐户**。

    3.  选择非内置的管理员帐户配置，任何其他用户帐户，然后将其删除。

    **请注意**  
    删除计算机上的所有其他用户帐户，然后您自定义了内置管理员帐户。

     

5.  请确保在用户登录时应用程序注册新用户首次登录后保留在**启动**屏幕上，麻将牌布局的两个小时内已安装了非配置 Windows 运行时基于应用程序存储在麻将牌布局。

6.  有些设置可以配置只能通过使用`CopyProfile`无人参与的设置，并且可以通过使用组策略配置其他设置。

    -   使用组策略来配置新的用户登录过程由被重置的。 您也可以创建脚本以定义这些用户设置。

        -或者-

    -   使用`CopyProfile`无人参与的设置。 有关详细信息，请参阅[无人参与的 Windows 安装程序参考](http://go.microsoft.com/fwlink/?LinkId=206281)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)

[Sysprep 过程概述](sysprep-process-overview.md)

[Sysprep 命令行选项](sysprep-command-line-options.md)

 

 






