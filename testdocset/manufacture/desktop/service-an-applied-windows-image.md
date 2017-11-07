---
author: Justinha
Description: "应用的 Windows 映像提供服务"
ms.assetid: cdf543f7-7810-4ec5-9992-af0f3b6a789f
MSHAttr: PreferredLib:/library/windows/hardware
title: "应用的 Windows 映像提供服务"
ms.openlocfilehash: 8138359ebba3872c401f045bd0ba3bde7cfbb4bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="service-an-applied-windows-image"></a>应用的 Windows 映像提供服务


Windows® 映像 (.wim) 文件包含一个或多个卷映像对于 Windows® 的操作系统。 卷映像表示捕获的卷或分区的 Windows 操作系统的系统。 如果您需要重新捕获 Windows 映像，或特定.wim 文件的副本导出到另一个.wim 文件中，或将卷映像附加到现有.wim 文件，可以使用部署映像服务和管理 (DISM) 工具来应用该映像，并再处理映像，应用时。 然后您可以启动到审核模式解决挂起的联机操作，并添加应用程序或进行其他自定义。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成本演练，您需要以下各项︰

-   有最新版本的 Windows 评估和部署工具包 (Windows ADK) 工具在其上安装一台计算机。

-   您可以将 Windows 映像应用到硬盘驱动器上的分区之前，必须在目标计算机上创建硬盘分区。 有关详细信息，请参阅[硬盘驱动器和分区](hard-drives-and-partitions.md)。

-   在可用的位置，将它们添加到 Windows 映像，必须具有主 Windows 映像 （.wim 文件） 和语言包、 驱动程序或其他程序包。

-   Windows PE 启动盘。 有关详细信息，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)还可以将图像应用从同一台计算机上，如 Windows 8 或 Windows 7 最新 ADK 工具安装的其他操作系统。

## <a name="span-idproceduresspanspan-idproceduresspanspan-idproceduresspanprocedures"></a><span id="Procedures"></span><span id="procedures"></span><span id="PROCEDURES"></span>过程


### <a name="span-idstep1boottowindowspeandapplythewindowsimagespanspan-idstep1boottowindowspeandapplythewindowsimagespanspan-idstep1boottowindowspeandapplythewindowsimagespanstep-1-boot-to-windows-pe-and-apply-the-windows-image"></a><span id="Step_1__Boot_to_Windows_PE_and_Apply_the_Windows_Image"></span><span id="step_1__boot_to_windows_pe_and_apply_the_windows_image"></span><span id="STEP_1__BOOT_TO_WINDOWS_PE_AND_APPLY_THE_WINDOWS_IMAGE"></span>步骤 1︰ 启动 Windows PE 并将 Windows 映像应用

在此步骤中，您将引导到 Windows PE 并将 Windows 映像应用，这样可以离线提供服务。

**应用映像**

1.  在目标计算机上，启动 Windows PE。 有关详细信息，请参阅[WinPE 的 Windows 10](winpe-intro.md)。

2.  在命令提示符下，将应用使用 DISM 的主 Windows 映像。 例如︰

    ``` syntax
    Dism /Apply-Image /ImageFile:C:\test\wim\install.wim /Index:1 /ApplyDir:C:\test\AppliedImages
    ```

    有关 DISM 命令的详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

### <a name="span-idstep2addpackagestothewindowsimagespanspan-idstep2addpackagestothewindowsimagespanspan-idstep2addpackagestothewindowsimagespanstep-2-add-packages-to-the-windows-image"></a><span id="Step_2__Add_Packages_to_the_Windows_Image"></span><span id="step_2__add_packages_to_the_windows_image"></span><span id="STEP_2__ADD_PACKAGES_TO_THE_WINDOWS_IMAGE"></span>步骤 2︰ 将包添加到 Windows 映像

使用 DISM 将程序包添加到您的主 Windows 映像。

**若要将程序包添加到映像**

1.  在命令提示符下，使用**/Add-Package**选项运行 DISM 和指向您想要添加到 Windows 映像的.cab 或.msu 包。 可以在一个命令行添加多个程序包。 例如，键入以下命令来添加多个程序包︰

    ``` syntax
    Dism /Image:C:\test\AppliedImages /Add-Package /PackagePath:C:\Test\Packages\package1.cab /PackagePath:C:\Test\Packages\package2.cab 
    ```

    有关 DISM 命令行选项的详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

    此外可以使用 DISM 命令行选项，在应用 Windows 映像中添加驱动程序、 添加语言包，更改为较高版本的 Windows，或将无人参与的答案文件应用。 有关详细信息，请参阅︰

    -   [DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)

    -   [DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

    -   [DISM Windows 版本服务命令行选项](dism-windows-edition-servicing-command-line-options.md)

    -   [DISM 无人参与服务命令行选项](dism-unattended-servicing-command-line-options.md)

2.  检查日志文件，以验证已成功添加程序包。

    某些软件包和驱动程序添加或移除了可能处于挂起状态。 这通常是因为需要重新启动才能完成操作。 将映像启动到审核模式将满足重新启动要求，并允许您添加应用程序和进行其他自定义。 有关详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

## <a name="span-idnextstepspanspan-idnextstepspanspan-idnextstepspannext-step"></a><span id="Next_Step"></span><span id="next_step"></span><span id="NEXT_STEP"></span>下一步


本演练演示在 Windows PE 应用 Windows 映像的基本脱机服务。 当您完成此过程时，包添加到 Windows 映像。 您现在可以运行`sysprep /generalize /oobe`删除特定于计算机的自定义设置并重新捕获映像用于以后的部署或执行`sysprep /oobe`保留专用的自定义项并运送这台计算机。 使用`/oobe`选项将确保计算机开始的全新安装体验 (OOBE) 模式引导下一次。 有关详细信息，请参阅[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[了解处理策略](understanding-servicing-strategies.md)

[使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[Windows ADK](http://go.microsoft.com/fwlink/p/?linkid=526803)

 

 






