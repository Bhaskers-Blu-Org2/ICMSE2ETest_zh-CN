---
author: Justinha
Description: "多语言 Windows 映像创建"
ms.assetid: 5bec65d1-44b0-484c-a5b6-959f221a4290
MSHAttr: PreferredLib:/library/windows/hardware
title: "多语言 Windows 映像创建"
ms.openlocfilehash: 9b9b0f3370717a878cda272d9a94c5b18fe72ee0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="multilingual-windows-image-creation"></a>多语言 Windows 映像创建


本演练介绍如何使用 Windows 评估和部署工具包 (Windows ADK) 来创建和部署多语言版本的 Windows 10。 它描述了如何创建多语言 Windows 映像，以帮助减少需要维护针对不同地区的 Windows 映像的数目。 您可以部署使用此过程从网络共享、 服务器，或从媒体创建的图像。

本演练介绍如何将语言包和其他更新程序包添加到脱机 Windows 映像和恢复的 Windows 映像。 然后启动到审核模式并添加应用程序和驱动程序的 Windows。 然后，捕获安装映像并捕获新的主映像将用于测试目的。 测试图像后，使用它来创建区域图像，通过删除不需要的语言资源。 然后，您可以部署这些区域的图像。

在本演练中描述的过程主要是适用于想要减少它们维护的 Windows 映像的数目的 Oem。 将语言包添加到脱机映像，可以减小 Windows 安装时间并减少了维护的映像的数目。 但是，由于多个语言包添加到单个图像，Windows 映像的大小增长。

IT 专业人士想要减少其整体的图像的大小应该改用[添加多语言支持添加到 Windows 分发](add-multilingual-support-to-a-windows-distribution.md)中所描述的过程。 此过程描述如何将 lp.cab 文件复制到 Windows 分发，从而减少整体的图像大小。

在本指南︰

-   [步骤 1︰ 将语言包添加到 Windows 映像](#addlang)

-   [步骤 2 （可选）︰ 添加语言包的 Windows 安装程序](#optlang)

-   [步骤 3︰ 测试 Windows 安装](#test)

-   [步骤 4︰ 启动到审核模式，添加的应用程序并运行 sysprep](#bootaudit)

-   [步骤 5︰ 捕获映像](#imagex)

-   [第 6 步︰ 创建区域图像，通过删除语言包](#removepacks)

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


若要完成本演练，您应有熟知常用的桌面部署技术和过程。 此外应具有 Windows 映像 (.wim) 文件格式的一个基本的了解。 本指南中的步骤假定您在.wim 文件中使用的单一 Windows 映像。 如果您想要减少需要维护的映像数量，可以在.wim 文件中，使用 Windows 提供的最低版本，然后使用 DISM 将升级到更高版本的 Windows。 如果想要维护多个映像，您可以为要创建多个版本的区域的 Windows 映像的.wim 文件中的每个 Windows 图像重复本指南中的步骤操作。

在开始之前，请确保您有下列各项︰

-   Windows 安装媒体 （DVD 或 Windows 安装文件） 的多个语言。 本指南使用 EN-US，DE-DE 和 FR-FR 媒体。

-   一个或多个语言包。

-   具有 Windows 评估和部署工具包 (Windows ADK) 安装的技术人员计算机。

-   一台测试计算机，可以使用安装和测试 Windows。

## <a name="span-idaddlangspanspan-idaddlangspanstep-1-add-language-packs-to-a-windows-image"></a><span id="addlang"></span><span id="ADDLANG"></span>步骤 1︰ 将语言包添加到 Windows 映像


在此步骤中，您将使用部署映像服务和管理 (DISM) 将语言包添加到 Windows 映像。 添加语言包后，您可以添加更新程序包。 在任何语言中可以使用启动的 Windows 映像。 例如，可以开始用英语 (EN-US) 图像，并添加对法语 (FR-FR) 和德语 (de DE) 的支持。

将语言包添加到 Windows 映像时，显示一个对话框以选择其首选的语言过程中的全新体验 (OOBE) 给用户。

通过使用此方法，Windows 映像的大小会较大;但是，安装时速度更快，并且可以确保任何更新程序添加到 Windows 映像，应用于对该映像中安装的语言。 如果您想要尽可能快地安装 Windows，请使用此方法。

**重要**  
Windows 映像必须是最近已安装和已捕获的图像。 这样可确保，Windows 映像不包括任何挂起的联机操作。

一定要安装该更新之前安装语言包。 如果您安装的更新 (修补程序后，常规分发版本\[GDR\]，有限分发版本\[LDR\]，或服务包\[SP\]) 包含依赖于语言的资源在安装语言包之前，不会应用更新中包含的特定于语言的更改。 可以通过使用标识具有语言包的依赖关系的软件包`Dism /Get-PackageInfo`命令。 在报表的"自定义属性"部分，查找依赖项 ="语言包"键/值对。 如果具有此属性 LDR 或 GDR 程序包之后安装了语言包，则必须重新安装此更新。

 

**将语言包添加到 Windows 映像**

1.  打开提升的部署和图像处理工具环境的命令提示符。

2.  键入以下命令以创建以下文件夹︰

    ``` syntax
    Mkdir C:\mount\windows
    Mkdir C:\mount\winre 
    Mkdir C:\mount\boot
    Mkdir C:\LanguagePack
    Mkdir C:\my_Distribution 
    ```

3.  EN-US Windows DVD 的全部内容复制到 c:\\我\_分发。 例如︰

    ``` syntax
    xcopy e:\windows C:\my_distribution /s /e
    ```

4.  将每个语言包复制到技术人员计算机。 例如︰

    ``` syntax
    xcopy H:\LPs\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab C:\LanguagePack
    xcopy H:\LPs\Microsoft-Windows-Client-Language-Pack_x64_de-de.cab C:\LanguagePack
    ```

5.  键入下列命令以检索名称或要修改的映像的索引号︰

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\my_distribution\sources\install.wim
    ```

    请注意您要修改的图像的索引或名称值。

6.  使用 DISM 将 Windows 映像安装。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

7.  使用 DISM 装载 Windows 恢复环境图像存在于 Windows 映像。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\recovery\winre.wim /Index:1 /MountDir:C:\mount\winre
    ```

8.  将语言包添加到已装载的脱机 Windows 映像中。 您可以在一个命令行添加多个程序包。

    ``` syntax
    Dism /Add-Package /image:C:/mount/windows /PackagePath:C:\LanguagePack\Microsoft-Windows-Client-Language-Pack_x64_de-de.cab /PackagePath:C:\LanguagePack\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab 
    ```

9.  将语言包添加到已装载的脱机 Windows 恢复映像。 用于 Windows 恢复映像语言包是使用 Windows PE 相同的 lp.cab 文件。 使用 Windows PE 随 Windows ADK 安装语言包。 例如︰

    ``` syntax
    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\lp.cab"

    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"
    ```

    此过程可能需要几分钟的时间。

10. （可选）将附加的可选组件和语言包添加到 Windows 恢复映像。 如果您想要恢复映像上安装附加的可选组件，您必须安装非特定语言的 cab 文件，，然后添加语言特定的 cab 文件。 例如，运行以下命令以添加 WinPE WinReCfg.cab 可选组件︰

    ``` syntax
    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-WinReCfg.cab"

    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-WinReCfg_de-de.cab" 

    Dism /image:C:/mount/winre /Add-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WinReCfg_fr-fr.cab"
    ```

    我们建议您添加语言包，用于恢复的 Windows 映像中包含下列可选组件︰

    -   WinPE-WinReCfg

    -   WinPE-Rejuv

    -   WinPE-EnhancedStorage

    -   WinPE 脚本

    -   WinPE-SecureStartup

    -   WinPE SRT

    -   WinPE WDS 工具

    -   WinPE WMI

    -   WinPE HTA

11. 配置 Windows 映像中使用的默认语言设置。

    ``` syntax
    Dism /image:C:\mount\windows /set-allIntl:fr-fr
    ```

12. 配置 Windows 恢复映像中使用的默认语言设置。

    ``` syntax
    Dism /image:C:\mount\winre /set-allIntl:fr-fr
    ```

13. 重新创建 lang.ini 文件。

    ``` syntax
    Dism /image:C:\mount\windows /gen-langini /distribution:C:\my_distribution
    ```

14. 验证正确的语言配置为默认设置和安装这些语言。

    ``` syntax
    Dism /image:C:\mount\windows /get-intl /distribution:C:\my_distribution 
    Dism /image:C:\mount\winre /get-intl
    ```

    Windows 映像的输出应类似如下︰

    ``` syntax
    Reporting offline international settings.

    Default system UI language : fr-FR
    System locale : fr-FR
    Default time zone : Pacific Standard Time
    User locale for default user : fr-FR
    Location : France (GEOID = 84)
    Active keyboard(s) : 040c:0000040c
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)

    Installed language(s): de-DE
      Type : Fully localized language.
    Installed language(s): en-US
      Type : Fully localized language.
    Installed language(s): fr-FR
      Type : Fully localized language.

    Reporting distribution languages.

    The default language in the distribution is:
    en-US

    The other available languages in the distribution are:
    No languages found

    The operation completed successfully.
    ```

    Windows 恢复图像的输出应类似如下︰

    ``` syntax
    Reporting offline international settings.

    Default system UI language : fr-FR
    System locale : fr-FR
    Default time zone : Pacific Standard Time
    User locale for default user : fr-FR
    Location : France (GEOID = 84)
    Active keyboard(s) : 040c:0000040c
    Keyboard layered driver : PC/AT Enhanced Keyboard (101/102-Key)

    Installed language(s): de-DE
      Type : Fully localized language.
    Installed language(s): en-US
      Type : Fully localized language.
    Installed language(s): fr-FR
      Type : Fully localized language.

    The operation completed successfully.
    ```

15. 卸载映像，提交更改。 请注意，卸载并提交 Windows 映像之前，必须卸载 Windows 恢复映像。

    ``` syntax
    DISM /unmount-image /mountdir:C:\mount\winre /commit
    DISM /unmount-image /mountdir:C:\mount\windows /commit
    ```

## <a name="span-idoptlangspanspan-idoptlangspanstep-2-optional-add-language-packs-to-windows-setup"></a><span id="optlang"></span><span id="OPTLANG"></span>步骤 2 （可选）︰ 添加语言包的 Windows 安装程序


在此步骤中，您将添加多语言支持 Windows 安装程序。 这使最终用户能够运行 Windows 安装程序并选择安装特定的语言。 将语言包添加到默认 boot.wim 文件，然后将语言资源复制到 Windows 分发。

**请注意**  
此步骤是可选的。 如果您完成此步骤，您可以在您选择的操作系统的语言之外的语言运行 Windows 安装程序。 但是，这不包括添加字体支持的所有语言。

 

**将语言包添加到默认启动映像**

1.  使用提升的权限打开部署工具命令提示符。

2.  使用 DISM 装载索引为 2 的 Boot.wim 文件。 例如，

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\boot.wim /Index:2 /MountDir:C:\mount\boot
    ```

3.  将 Windows PE 的语言包和 Windows 安装可选组件添加到您想要支持的每种语言安装的映像。 例如︰

    ``` syntax
    DISM /add-package /image:C:\mount\boot /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab" 

    DISM /add-package /image:C:\mount\boot /packagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\lp.cab"
    ```

4.  添加 Windows PE 安装可选组件。 例如︰

    ``` syntax
    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Setup.cab" 

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-Setup-client.cab"
    ```

    **请注意**  
    对于 Windows 客户端版本只是这些 Windows 安装语言包。 对于 Windows 服务器，您必须使用 winpe 安装服务器.cab 文件。

     

5.  添加 Windows PE 语言特定的可选组件。 例如︰

    ``` syntax
    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-client_fr-fr.cab"

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-Setup_de-de.cab"

    DISM /add-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\de-de\WinPE-Setup-client_de-de.cab"
    ```

6.  在 Windows 分发，将从每个语言特定 Windows 分发特定语言设置资源复制到分布共享中的源文件夹。 例如，为 FR-FR 插入 Windows DVD，DVD 驱动器 （e:） 中，将 FR-FR 源文件夹复制到 Windows 分发。

    ``` syntax
    Mkdir C:\my_distribution\sources\fr-fr 
    Mkdir C:\my_distribution\sources\de-de

    xcopy E:\sources\fr-fr C:\my_distribution\sources\fr-fr /cherkyi 
    xcopy E:\sources\de-de C:\my_distribution\sources\de-de /cherkyi
    ```

7.  使用 DISM 将 Windows 映像安装。 例如︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\my_distribution\sources\install.wim /Index:1 /MountDir:C:\mount\windows
    ```

8.  获取使用 /Get-Intl 参数配置 Windows 映像中的语言设置。 例如

    ``` syntax
    Dism /image:C:\mount\windows /Get-Intl
    Dism /image:C:\mount\winre /Get-Intl
    ```

9.  通过使用 /set-allInlt 参数来更改默认语言、 区域设置，以及其他国际设置。

    ``` syntax
    Dism /image:C:\mount\boot /set-allIntl:fr-fr
    ```

10. 重新创建 lang.ini 文件。 Lang.ini 文件必须重新创建每次添加或删除语言资源从您的发行版，并且当您添加或从 Windows 映像中删除语言包。

    ``` syntax
    Dism /image:C:\mount\windows /Gen-Langini /distribution:C:\my_distribution
    ```

11. Windows 分发的 lang.ini 文件复制到 boot.wim 文件中。 使用的 Boot.wim 中的 Lang.ini 文件必须匹配操作系统映像的 Lang.ini 文件。

    ``` syntax
    Xcopy C:\my_distribution\sources\lang.ini C:\mount\winre\sources\lang.ini
    ```

12. 使用 DISM 卸载 Windows 启动映像并提交所做的更改。 您还必须卸载 Windows 映像。 因为 Windows 映像中更改了任何文件，您可以放弃所做的更改。 例如，

    ``` syntax
    Dism /Unmount-image /MountDir:C:\mount\boot /Commit 
    Dism /Unmount-image /MountDir:C:\mount\Windows /Discard
    ```

## <a name="span-idtestspanspan-idtestspanstep-3-test-the-windows-installation"></a><span id="test"></span><span id="TEST"></span>步骤 3︰ 测试 Windows 安装


在此步骤中，您将 Windows 安装，在 Windows 安装过程中选择一种语言，并验证已安装多种语言。

启动无操作系统的计算机，您必须创建可引导 Windows PE 介质。 本演练创建可引导的 USB 驱动器上的 Windows PE 提供指导。 有关其他选项，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。

**若要将 Windows 安装**

1.  在技术人员计算机上创建的 Windows PE 映像。 例如︰

    ``` syntax
    Copype amd64 C:\winpe_amd64
    ```

    将创建以下目录︰

    -   C:\\winpe\_amd64\\媒体

    -   C:\\winpe\_amd64\\装载

    如果您需要添加到 Windows PE 的启动关键驱动程序或其他可选组件，请参阅[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)。

2.  技术人员计算机中插入 USB 驱动器并运行下面的命令︰

    ``` syntax
    Makewinpemedia /ufd C:\winpe_amd64 F:
    ```

    其中*F*是 USB 驱动器的驱动器号。

    Windows PE 被复制到 usb 闪存盘。

3.  Windows 分发的内容复制到另一个 USB 驱动器具有足够的可用空间。 根据您的 install.wim 文件的大小，可能需要此 USB 驱动器格式化为 NTFS，才能支持大于 4 GB 的文件。

    例如，

    ``` syntax
    Xcopy C:\my_distribution G:\my_distribution /cherkyi
    ```

    其中*G*是第二个 USB 驱动器的盘符。

4.  Windows PE usb 闪存盘插入您的测试计算机。 启动测试计算机，确保 Windows PE USB 驱动器被配置为首先启动。 您可能需要更改计算机的固件中的启动选项。

5.  Windows PE 命令行提示符出现之后，插入 USB 驱动器，其中包含您在测试计算机上的 Windows 分发方案。

6.  确定驱动器、 卷和测试计算机上的驱动器号。 从 Windows PE 命令提示符下，键入︰

    ``` syntax
    Diskpart 
    List volume 
    ```

    标识包含 Windows 分发的 USB 驱动器的驱动器号。 此示例使用"f:\\"。 退出 diskpart。

    ``` syntax
    exit
    ```

7.  通过运行 Windows 安装程序来安装 Windows。

    ``` syntax
    F:\my_distribution\setup.exe
    ```

    Windows 安装程序启动并提示您选择您的语言 （法语、 德语或英语）。 选择一种语言并继续安装。 验证在安装过程中显示正确的语言。

## <a name="span-idbootauditspanspan-idbootauditspan-step-4-boot-to-audit-mode-add-applications-and-run-sysprep"></a><span id="bootaudit"></span><span id="BOOTAUDIT"></span>步骤 4︰ 启动到审核模式，添加的应用程序并运行 sysprep


在此步骤中，您可以在一台测试计算机上安装 Windows 映像并引导到审核模式。 在审核模式下运行计算机时，您将添加应用程序必须在线，安装和测试系统。 添加应用程序并测试计算机后，您可以运行 sysprep 工具来准备映像部署到计算机时，将交付给最终用户。

**启动到审核模式**

1.  请执行下列操作以将测试计算机启动到审核模式之一︰

    -   有关无人参与安装在 OOBE 屏幕上，按**Ctrl + Shift + F3**。

    -   在无人参与安装中，请使用 Microsoft Windows 部署使用答案文件\\重新封装\\配置为**审核**模式。 此设置会出现在**oobeSystem**配置阶段。

    -   在命令提示符窗口中运行**sysprep 模式**的命令。

    有关详细信息，请参阅[了解审核模式](http://go.microsoft.com/fwlink/?LinkId=148031)。

2.  安装 Microsoft Office 或其他应用程序，并测试计算机。 有关详细信息，请参阅[在审核模式下自定义 Windows](http://go.microsoft.com/fwlink/?LinkId=148032)。

3.  通过执行以下任一项准备部署计算机︰

    -   在审核模式下运行**Sysprep**命令与**/oobe /shutdown 一般化 /**选项。

    -   在无人参与安装中，配置 Microsoft Windows 部署\\重新封装\\模式设置为**oobe**。 有关此设置的详细信息，请参阅 Windows 无人参与安装参考 (Unattend.chm)。

    有关详细信息，请参阅[Sysprep 技术参考](http://go.microsoft.com/fwlink/?LinkId=148028)。

    Sysprep 完成后，关闭测试计算机。

## <a name="span-idimagexspanspan-idimagexspanstep-5-capture-the-windows-installation"></a><span id="imagex"></span><span id="IMAGEX"></span>步骤 5︰ 捕获 Windows 安装


在此步骤中，您可以捕获 Windows 映像从测试计算机并将其用作您的主映像存储。

**捕获映像**

1.  通过引导至 Windows PE 启动测试计算机。

2.  确定驱动器、 卷和测试计算机上的驱动器号。 从 Windows PE 命令提示符下，键入︰

    ``` syntax
    Diskpart 
    List volume 
    ```

    标识包含 Windows 分发的 USB 驱动器的驱动器号。 退出 diskpart。

    ``` syntax
    exit
    ```

3.  在 Windows PE 命令提示符下，捕获 Windows 映像。 此示例使用 e:\\作为 Windows 安装的位置。 例如︰

    ``` syntax
    dism /Capture-Image /CaptureDir:E:\ /ImageFile:E:\MyInstall.wim /Name:"Fabrikam"
    ```

4.  将图像复制到 USB 驱动器或网络共享。 例如︰

    ``` syntax
    xcopy E:\MyInstall.wim G:\MyInstall.wim
    ```

    其中*G*是 USB 驱动器的盘符。

## <a name="span-idremovepacksspanspan-idremovepacksspanstep-6-create-regional-images-by-removing-language-packs"></a><span id="removepacks"></span><span id="REMOVEPACKS"></span>第 6 步︰ 创建区域图像，通过删除语言包


在此步骤中，您通过从映像中删除语言包，它处于脱机状态时创建区域的 Windows 映像。 此映像包含只是在某些地区部署所需的语言。

**重要**  
如果有挂起的联机操作，不应该脱机 Windows 映像中删除语言包。 Windows 映像应最近已安装和已捕获的图像。 这将确保，Windows 映像不包括任何挂起的联机操作需要重新启动。

 

**若要删除语言包**

1.  找到您想要删除，从语言的 Windows 映像并将其复制到技术人员计算机。 例如︰

    ``` syntax
    xcopy F:\sources\MyInstall.wim C:\my_images\MyInstall.wim
    ```

2.  使用提升的权限打开部署工具命令提示符。

3.  键入以下命令以装载 Windows 映像。

    ``` syntax
    Dism /mount-image /ImageFile:C:\my_images\MyInstall.wim /Name:"Fabrikam" /MountDir:C:\mount\windows 
    Dism /Mount-Image /ImageFile:C:\mount\windows\Windows\System32\recovery\winre.wim /Index:1 /MountDir:C:\mount\winre
    ```

4.  可选︰ 键入以下命令以列出脱机映像中安装的程序包。

    ``` syntax
    Dism /Image:C:\mount\windows /Get-Packages 
    Dism /Image:C:\mount\winre /Get-Packages
    ```

    您可以使用`> packagelist.txt`输出到一个文本文件列表命名为 PackageList。 注意您想要删除语言包程序包的程序包标识。

5.  从映像中删除语言包。 您可以删除多个.cab 文件，使用一个命令行语句。

    **请注意**  
    您可以指定程序包标识使用**/PackageName**选项，也可以指向使用**/PackagePath**选项的程序包的原始源。 例如︰

    ``` syntax
    Dism /Image:C:\mount\windows /Remove-Package /PackagePath:C:\LanguagePack\Microsoft-Windows-Client-Language-Pack_x64_fr-fr.cab 
    Dism /Image:C:\mount\winre /Remove-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab"
    ```

    有关详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

6.  如果恢复映像中添加其他可选组件，删除特定于语言的可选组件，更改默认语言设置。 例如︰

    ``` syntax
    Dism /image:C:/mount/winre /Remove-Package /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-WinReCfg_fr-fr.cab"
    ```

7.  可选项。 如果到 boot.wim 文件添加其他语言支持，特定的语言资源和可选组件从文件中删除 boot.wim。 例如︰

    ``` syntax
    Dism /mount-image /ImageFile:C:\my_distribution\boot.wim /index:2 /MountDir:C:\mount\boot  

    Dism /remove-package /image:C:\mount\boot /packagepath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\lp.cab" 

    Dism /remove-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup_fr-fr.cab"

    Dism /remove-package /image:C:\mount\boot /PackagePath:"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\fr-fr\WinPE-Setup-client_fr-fr.cab" 

    Dism /image:C:\mount\boot /set-allIntl:de-de

    rmdir C:\my_distribution\sources\fr-fr /s

    ```

8.  重新创建 lang.ini 文件，并通过运行以下命令来更改默认语言设置︰

    ``` syntax
    Dism /image:C:\mount\winre /Set-AllIntl:de-de
    Dism /image:C:\mount/windows /Gen-LangINI /distribution:C:\my_distribution /Set-AllIntl:de-DE
    ```

9.  可选项。 如果从 boot.wim 文件中删除的语言，向启动映像复制更新的 lang.ini 文件。 在更新 lang.ini 文件 boot.wim 中的后，卸载 boot.wim 文件。

    ``` syntax
    Dism /unmount-image /MountDir:C:\mount\boot /Commit
    ```

10. 键入下列命令以提交更改并卸载映像。

    ``` syntax
    Dism /unmount-image /MountDir:C:\mount\winre /Commit 
    Dism /unmount-image /MountDir:C:\mount\windows /Commit
    ```

 

 





