---
author: KPacquer
Description: "自定义 Windows RE"
ms.assetid: ce94e3c4-03f6-46d1-b2a8-cc5d75c7a66d
MSHAttr: PreferredLib:/library/windows/hardware
title: "自定义 Windows RE"
ms.openlocfilehash: 160345af0b5ddbdf05ea5c39615ef997d05cce48
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="customize-windows-re"></a>自定义 Windows RE


通过添加语言、 包驱动程序和自定义诊断或诊断工具，可以自定义 Windows 恢复环境 (Windows RE)。

WinRE 图像包含在 Windows 10 和 Windows 服务器 2016年的图像，并最终将被复制到目标计算机或设备上的 Windows RE 工具分区。 要对其进行修改，将装载 Windows 映像，然后装载 WinRE 映像内。 进行更改，卸载 WinRE 映像，然后卸载 Windows 映像。 

   ![图像︰ 安装的 Windows 映像，然后装载恢复映像内的。 进行更改，然后卸载恢复映像，并最后将 Windows 映像](images/customize-recovery-image.jpg)

我们建议，当您使用语言，并启动关键驱动程序更新更新 Windows 映像时 Windows RE 映像在同一时间。

本主题还提供了它更新后优化 Windows RE 映像的可选步骤。

   
## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成本演练，您需要以下各项︰

-   使用 Windows 评估和部署工具包 (ADK) 安装技术人员计算机。
-   Windows 映像 (install.wim)。 这可以从 Windows 安装媒体或参考映像。

## <a name="span-idbkmkextractimagespanspan-idbkmkextractimagespanspan-idbkmkextractimagespanstep-1-mount-the-windows-and-windows-re-image"></a><span id="BKMK_ExtractImage"></span><span id="bkmk_extractimage"></span><span id="BKMK_EXTRACTIMAGE"></span>步骤 1︰ 装载 Windows 和 Windows RE 映像

**将这些映像装载**

1.  以管理员身份打开**部署和图像处理工具环境**的命令提示符︰

    单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行** &gt; **是**。

2.  用于编辑 Windows 基本映像装载。

    ``` syntax
    md C:\mount\windows

    Dism /Mount-Image /ImageFile:C:\mount\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

3.  装载 Windows RE 图像进行编辑。

    ``` syntax
    md C:\mount\winre 

    Dism /Mount-Image /ImageFile:c:\mount\windows\windows\system32\recovery\winre.wim /Index:1 /MountDir:C:\mount\winre
    ```

    **请注意**  Windows RE 映像应始终是索引号为 1。

     

## <a name="span-idbkmkaddlanguagepacksspanspan-idbkmkaddlanguagepacksspanspan-idbkmkaddlanguagepacksspanstep-2-adding-languages"></a><span id="BKMK_AddLanguagePacks"></span><span id="bkmk_addlanguagepacks"></span><span id="BKMK_ADDLANGUAGEPACKS"></span>步骤 2︰ 添加语言


当您将语言添加到 Windows RE 时，您需要添加基本语言包和相应的语言包的 Windows PE 可选组件，Windows RE 工具图像中每个。

从 Windows 10、 版本 1607年和 Windows 服务器 2016年，基本的语言包和可选组件自定义 Windows RE 所需的语言包包含在语言包 Windows 10 个 Dvd 和 Windows 服务器 2016年。 Windows PE 语言包的 Windows 10 ADK 不应该用于自定义 Windows RE。

**请注意**  
以确保一致的语言体验在恢复方案中，对 Windows RE 映像添加到 Windows 映像中添加一组相同的语言。

我们建议将不超过十个语言包添加到 Windows 或 Windows RE 映像。 多个语言包增加 Windows 映像的大小，也会影响系统的部署和维护过程的整体性能。

 

**若要添加语言包**

1.  列出 Windows RE 工具图像中的 Windows PE 可选组件︰

    ``` syntax
    Dism /Get-Packages /Image:C:\mount\winre
    ```

2.  查看生成的包列表，然后在图像中，包括了基本的 Windows PE 的语言包，但不是包括**WinPE WiFi 包**中添加相应的语言包，每包。

    下面的代码演示如何将法语 (fr fr) 语言包添加到基本的 Windows PE 映像，然后给每个存在于默认 Windows RE 映像的可选组件︰

    ``` syntax
    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Rejuv_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-EnhancedStorage_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Scripting_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SecureStartup_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-SRT_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WDS-Tools_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WMI_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-StorageWMI_fr-fr.cab"

    Dism /Add-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-HTA_fr-fr.cab"
    ```

    **WinPE WiFi 程序包**不是特定于语言的并且不需要添加其他语言时要添加。

3.  如果您要添加的日本、 韩国或中国的语言包，添加这些语言的字体软件包。 这里是日本的一个示例︰

    ``` syntax
    Dism /image:C:\mount\winre /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Font Support-JA-JP.cab"
    ```

    若要了解详细信息，请参阅[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)。

4.  若要节省空间并加速恢复过程，删除不需要的语言。 反转顺序以避免具有相关性的问题。

    注意， **WinPE WiFi 程序包**不是特定于语言和不应删除。

    ``` syntax
    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-StorageWMI_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WDS-Tools_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SRT_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-EnhancedStorage_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Rejuv_en-us.cab"

    Dism /Remove-Package /Image:C:\mount\winre /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\lp.cab"
    ```

## <a name="span-idbkmkadddriversspanspan-idbkmkadddriversspanspan-idbkmkadddriversspanstep-3-adding-boot-critical-drivers"></a><span id="BKMK_AddDrivers"></span><span id="bkmk_adddrivers"></span><span id="BKMK_ADDDRIVERS"></span>步骤 3︰ 添加启动关键驱动程序


请确保您引用的设备需要任何第三方驱动程序添加到启动，存储或视频驱动程序等。 如果启动关键驱动程序添加到 Windows 映像，使用 Windows 图像处理和配置设计器 (ICD)，它们将被添加到 Windows RE 图像在此 Windows 映像。

**添加启动关键驱动程序**

1.  如有必要，解压缩或解包设备制造商提供的驱动程序文件。
2.  确定驱动程序的安装 (.inf) 文件，并将其添加。

    ``` syntax
    Dism /Image:C:\mount\winre /Add-Driver /Driver:"C:\SampleDriver\driver.inf" 
    ```

    其中*c:\\SampleDriver\\driver.inf*是该.inf 文件的位置。

## <a name="span-idbkmkaddcustomtoolsspanspan-idbkmkaddcustomtoolsspanspan-idbkmkaddcustomtoolsspanstep-4-adding-a-custom-tool"></a><span id="BKMK_AddCustomTools"></span><span id="bkmk_addcustomtools"></span><span id="BKMK_ADDCUSTOMTOOLS"></span>步骤 4︰ 添加一个自定义工具


可以向 Windows RE 映像中添加的自定义诊断或诊断工具。 若要了解详细信息，请参阅[添加到 Windows 重新启动选项菜单自定义工具](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)。

## <a name="span-idbkmkaddupdatesspanspan-idbkmkaddupdatesspanspan-idbkmkaddupdatesspanstep-5-adding-windows-updates"></a><span id="BKMK_AddUpdates"></span><span id="bkmk_addupdates"></span><span id="BKMK_ADDUPDATES"></span>步骤 5︰ 添加 Windows 更新


有时，Windows 更新可能要求您更新 Windows RE 映像。

-   添加 Windows 更新包，例如，c:\\MSU\\Windows8.1-KB123456-x64.msu。

    ``` syntax
    Dism /Add-Package /PackagePath:C:\MSU\Windows8.1-KB123456-x64.msu /Image:C:\mount\winre /LogPath:AddPackage.log
    ```

## <a name="span-idstep6optimizingtheimagepart1optionalspanspan-idstep6optimizingtheimagepart1optionalspanspan-idstep6optimizingtheimagepart1optionalspanstep-6-optimizing-the-image-part-1-optional"></a><span id="Step_6__Optimizing_the_image__part_1__optional_"></span><span id="step_6__optimizing_the_image__part_1__optional_"></span><span id="STEP_6__OPTIMIZING_THE_IMAGE__PART_1__OPTIONAL_"></span>第 6 步︰ 优化图像，第 1 （可选） 部分

添加语言或 Windows 更新包后, 可以通过检查重复的文件，并将标记为取代旧的版本来减少最终 Windows RE 包的大小。

1.  优化图像︰

    ``` syntax
    Dism /Image:c:\mount\winre /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

2.  以后，将导出的图像中删除旧的文件。

## <a name="span-idbkmksaveimagespanspan-idbkmksaveimagespanspan-idbkmksaveimagespanstep-7-unmount-the-winre-image"></a><span id="BKMK_SaveImage"></span><span id="bkmk_saveimage"></span><span id="BKMK_SAVEIMAGE"></span>第 7 步︰ 卸载 WinRE 映像


-   卸载，然后将图像保存为︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\winre /Commit
    ```

## <a name="span-idstep8optimizingtheimagepart2optionalspanspan-idstep8optimizingtheimagepart2optionalspanspan-idstep8optimizingtheimagepart2optionalspanstep-8-optimizing-the-image-part-2-optional"></a><span id="Step_8__Optimizing_the_image__part_2__optional_"></span><span id="step_8__optimizing_the_image__part_2__optional_"></span><span id="STEP_8__OPTIMIZING_THE_IMAGE__PART_2__OPTIONAL_"></span>步骤 8︰ 优化图像，部分 2 （可选）


如果已经优化图像，您将需要将映像导出以便查看文件大小的更改。 在导出过程中，DISM 删除文件所取代。

1.  将 Windows RE 映像导出到新的 Windows 位图文件。

    ``` syntax
    Dism /Export-Image /SourceImageFile:c:\mount\windows\windows\system32\recovery\winre.wim /SourceIndex:1 /DestinationImageFile:c:\mount\winre-optimized.wim
    ```

2.  旧的 Windows RE 映像替换新优化的图像。

    ``` syntax
    del c:\mount\windows\windows\system32\recovery\winre.wim

    copy c:\mount\winre-optimized.wim c:\mount\windows\windows\system32\recovery\winre.wim
    ```

## <a name="span-idbkmkunmountwindowsspanspan-idbkmkunmountwindowsspanspan-idbkmkunmountwindowsspanstep-9-unmount-the-windows-image"></a><span id="BKMK_UnmountWindows"></span><span id="bkmk_unmountwindows"></span><span id="BKMK_UNMOUNTWINDOWS"></span>步骤 9︰ 卸载 Windows 映像


保存您的更改回基本 Windows 映像。

-   卸载基本的 Windows 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\windows /Commit
    ```

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动


如果部署使用**Windows 安装程序**窗口，更新基本 Windows 文件 (Install.wim) 内的其他 Windows 映像。

如果使用**Windows PE**， **Diskpart**， **DISM**来部署您的参考映像，然后转到[部署 Windows RE](deploy-windows-re.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[向 Windows 重新启动选项菜单中添加自定义工具](add-a-custom-tool-to-the-windows-re-boot-options-menu.md)

[部署 Windows RE](deploy-windows-re.md)

[将按钮重置功能的部署](deploy-push-button-reset-features.md)

[REAgentC 命令行选项](reagentc-command-line-options.md)
