---
author: Justinha
Description: "已安装的 Windows 映像提供服务"
ms.assetid: fbfd9166-f522-4c73-a866-7d97cab32ed8
MSHAttr: PreferredLib:/library/windows/hardware
title: "已安装的 Windows 映像提供服务"
ms.openlocfilehash: ae46fda9d6ecca2045f4811b42eba3d406a5ba73
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="service-a-mounted-windows-image"></a>已安装的 Windows 映像提供服务


可以使用部署映像服务和管理 (DISM) 工具将 Windows 映像装载 WIM 或 VHD 文件并对其进行修改。 在本演练的第一部分，您可以添加语言包，配置国际设置和启用 Windows 功能。 第二部分，删除包，然后再升级到更高版本的 Windows® 的 Windows 映像。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成本演练，您需要以下各项︰

-   具有在其上安装的 Windows ADK 工具的计算机。

-   若要更新一个.wim、.vhd 或.vhdx 文件。

-   语言包或其他程序包添加和从映像中删除。

## <a name="span-idproceduresspanspan-idproceduresspanspan-idproceduresspanprocedures"></a><span id="Procedures"></span><span id="procedures"></span><span id="PROCEDURES"></span>过程


### <a name="span-idstep1mountanimagewithreadwritepermissionsspanspan-idstep1mountanimagewithreadwritepermissionsspanspan-idstep1mountanimagewithreadwritepermissionsspanstep-1-mount-an-image-with-readwrite-permissions"></a><span id="Step_1__Mount_an_Image_with_Read_Write_Permissions"></span><span id="step_1__mount_an_image_with_read_write_permissions"></span><span id="STEP_1__MOUNT_AN_IMAGE_WITH_READ_WRITE_PERMISSIONS"></span>步骤 1︰ 装载具有读/写权限的映像

在此步骤中，您装载到指定的目录，Windows 映像，这样就为提供服务。

1.  将复制.vhd 或.vhdx，其中包含 Windows 映像，到本地驱动器.wim 文件。 例如，c:\\测试\\图像。

2.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

3.  创建已装载的映像的文件夹。 例如，c:\\测试\\脱机。

4.  运行**DISM /Get-ImageInfo**命令的名称或索引号，则需要更新的图像检索。 例如︰

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\MyImage.wim
    ```

5.  将 Windows 映像进行安装。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\MyImage.wim /Index:1 /MountDir:C:\test\offline
    ```

    由于 WIM 文件可以包含一个或多个图像，您必须指定索引或名称值。 装载从 VHD 映像，您必须指定`/Index:1`。

### <a name="span-idstep2addpackagestotheimagespanspan-idstep2addpackagestotheimagespanspan-idstep2addpackagestotheimagespanstep-2-add-packages-to-the-image"></a><span id="Step_2__Add_Packages_to_the_Image"></span><span id="step_2__add_packages_to_the_image"></span><span id="STEP_2__ADD_PACKAGES_TO_THE_IMAGE"></span>步骤 2︰ 将程序包添加到映像

在此步骤中，您可以将程序包添加到安装的 Windows 映像。

1.  在提升的命令提示符处，将程序包添加到安装的 Windows 映像。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Add-Package /PackagePath:C:\test\packages\package1.cab /PackagePath:C:\test\packages\package2.cab
    ```

2.  如果您添加语言包，可以通过键入以下命令来更改已装载的脱机映像中的所有国际语言设置︰

    ``` syntax
    Dism /Image:C:\test\offline /Set-SKUIntlDefaults:fr-FR
    ```

    或者，您可以配置不同的设置，包括用户界面语言、 系统的区域设置、 用户区域设置、 输入法区域设置，和其他人不同的值。 有关如何指定各个值的每个设置的详细信息，请参阅[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)。

3.  在命令提示符下，更改的提交。 使用**/Unmount-Image**选项时才装入图像。 例如︰

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

### <a name="span-idstep3removeapackagefromthemountedimagespanspan-idstep3removeapackagefromthemountedimagespanspan-idstep3removeapackagefromthemountedimagespanstep-3-remove-a-package-from-the-mounted-image"></a><span id="Step_3__Remove_a_Package_from_the_Mounted_Image"></span><span id="step_3__remove_a_package_from_the_mounted_image"></span><span id="STEP_3__REMOVE_A_PACKAGE_FROM_THE_MOUNTED_IMAGE"></span>步骤 3︰ 从已装载的映像中删除程序包

在此步骤中，您查看已安装在您的映像中的程序包，然后从映像中删除特定程序包。

1.  在提升的命令提示符下，查找您的映像中的程序包的名称。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Get-Packages
    ```

    如果大量的程序包列表，可以将输出到一个文本文件的信息。 例如，您可以添加`>C:\PackageList.txt`到命令行的末尾。

2.  查看可用在已装载的映像，并记下该程序包的程序包标识的程序包列表中。

3.  在命令提示符下，指定程序包的程序包标识和删除已装载的映像。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Remove-Package /PackageName:Microsoft.Windows.Calc.Demo~6595b6144ccf1df~x86~en~1.0.0.0
    ```

### <a name="span-idstep4upgradetoahighereditionofwindowsspanspan-idstep4upgradetoahighereditionofwindowsspanspan-idstep4upgradetoahighereditionofwindowsspanstep-4-upgrade-to-a-higher-edition-of-windows"></a><span id="Step_4__Upgrade_to_a_Higher_Edition_of_Windows"></span><span id="step_4__upgrade_to_a_higher_edition_of_windows"></span><span id="STEP_4__UPGRADE_TO_A_HIGHER_EDITION_OF_WINDOWS"></span>步骤 4︰ 升级到 Windows 的更高版本

所有您所做的更改也应用于每个潜在的目标版本的 Windows。 图像中，每个目标版本被转移。 当您升级到更高版本的 Windows 时，所做的更改不会丢失。 有关详细信息，请参阅[Windows 版 DISM 服务命令行选项](dism-windows-edition-servicing-command-line-options.md)。

1.  在提升的命令提示符下，列出了可用于升级的版本。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Get-TargetEditions
    ```

    注意目标版本 id。

2.  在命令提示符下，指定您想要升级到的版本。 例如︰

    ``` syntax
    Dism /Image:C:\test\offline /Set-Edition:Ultimate
    ```

最终用户可以使用 Windows 随时升级去与较低版本的 Windows 不使用相关的文件。

### <a name="span-idstep5reducethesizeoftheimagespanspan-idstep5reducethesizeoftheimagespanspan-idstep5reducethesizeoftheimagespanstep-5-reduce-the-size-of-the-image"></a><span id="Step_5__Reduce_the_Size_of_the_Image"></span><span id="step_5__reduce_the_size_of_the_image"></span><span id="STEP_5__REDUCE_THE_SIZE_OF_THE_IMAGE"></span>步骤 5︰ 减小图像的大小

在此步骤中，您可以通过清理被取代的组件来降低存储大小的组件，减少图像的足迹，还重置基取代的组件，它可进一步减少组件存储大小。

-   在提升的命令提示符处，运行以下命令来减小图像文件的大小︰

    ``` syntax
    Dism /cleanup-image /StartComponentCleanup /ResetBase 
    ```

### <a name="span-idstep6committhechangesandunmounttheimagespanspan-idstep6committhechangesandunmounttheimagespanspan-idstep6committhechangesandunmounttheimagespanstep-6-commit-the-changes-and-unmount-the-image"></a><span id="Step_6__Commit_the_Changes_and_Unmount_the_Image"></span><span id="step_6__commit_the_changes_and_unmount_the_image"></span><span id="STEP_6__COMMIT_THE_CHANGES_AND_UNMOUNT_THE_IMAGE"></span>第 6 步︰ 提交更改并卸载映像

在此步骤中，您可以卸载映像并保存所做的更改。

-   在提升的命令提示符下，卸载映像并提交到图像文件的更改。 例如︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idnextstepspanspan-idnextstepspanspan-idnextstepspannext-step"></a><span id="Next_Step"></span><span id="next_step"></span><span id="NEXT_STEP"></span>下一步


本演练阐释的基本脱机服务安装的 Windows 映像。 对一幅图像，并且升级映像时保留所做的所有更改。 更新的映像已准备就绪可以部署。 因为您复制到本地硬盘驱动器上的图像文件，您可以从服务器中删除原始图像文件。 可以将其替换为新的活动中，也可以保留一份供参考的较早版本。

有关其他详细信息的脱机处理操作，可以在脱机映像上执行[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)，请参阅。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[了解处理策略](understanding-servicing-strategies.md)

[使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

 

 






