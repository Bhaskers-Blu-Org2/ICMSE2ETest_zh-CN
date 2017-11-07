---
author: KPacquer
Description: "实验室 6︰ 添加通用的 Windows 应用程序，启动图块和任务栏的针脚"
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 6︰ 添加通用的 Windows 应用程序，启动图块和任务栏的针脚"
ms.openlocfilehash: 82258242c0a5083e95a5e8a193f28e56825eeb5c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-idaddappsspanlab-6-add-universal-windows-apps-start-tiles-and-taskbar-pins"></a><span id="Add_apps"></span>实验室 6︰ 添加通用的 Windows 应用程序，启动图块和任务栏的针脚

将应用程序添加到您的图像，以满足不同客户需求。 一些具有不同的安装过程︰

-  **Windows 通用平台的应用程序 （UWP 应用程序）**︰ 这些可以添加或重新安装使用本主题中描述的工具。    
-  **Windows 桌面应用程序**︰ 我们将向您展示如何添加在[实验室 12︰ 添加桌面应用程序和设置变得分散化配置软件包 (Spp)](add-desktop-apps-wth-spps-sxs.md)。

**备注** 

*    **添加更新语言之前。** 其中包括的修补程序、 常规分发版本或服务包。 如果您以后添加更新，您将需要重新添加该语言。

*    **在应用程序之前添加语言**。 这包括通用的 Windows 应用程序和桌面应用程序。 如果您以后添加一种语言，您将需要重新安装应用程序。

## <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>装入该映像

**步骤 1︰ 装载映像**

使用步骤，可从[实验室 3︰ 添加设备驱动程序 （.inf 样式）](add-device-drivers.md)装载映像。 短的版本︰

1.  打开命令行以管理员身份 (**开始**> 键入**部署**> 右键单击**部署和图像处理工具环境** > **以管理员身份运行**。)

2.  对该文件进行备份 (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  装入该映像 (`md C:\mount\windows`，然后`Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idaddorreinstallappsspanaddreinstall-apps"></a><span id="Add_or_reinstall_apps"></span>添加/重新安装应用程序
    
**步骤 2︰ 添加并重新安装 （需要时添加语言） 的收件箱应用程序**

注意，在以前的版本中，它都需要先删除收件箱的应用程序。 这不再是必需的并且如果那样的话，命令可能会失败。

注意︰ Windows 10 1607年版本，应用程序捆绑包现在只包含属于该应用程序的依赖项文件包。 您不再需要检查哪些依赖项安装的 prov.xml 文件。 安装所有的依赖包的文件夹中找到。

1.  转到<https://microsoftoem.com>并获得补充 OPK。 此软件包中包含 Windows 10 版本 1607年收件箱的应用程序。 不将这些应用程序的每月更新。 

2.  将程序包解压缩到一个文件夹，例如，E:\apps\amd64。

3.  添加并重新安装收件箱应用程序。 下面的示例演示如何开始收件箱应用程序重新安装。 用适当的包每个收件箱的应用程序 （除了 AppConnector) 重复上述步骤。

    ``` syntax
    Dism /Add-ProvisionedAppxPackage /Image:c:\mount\windows /PackagePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.appxbundle /LicensePath:e:\apps\amd64\Microsoft.3DBuilder_8wekyb3d8bbwe.xml /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x64.14.00.appx /DependencyPackagePath:e:\apps\amd64\Microsoft.VCLibs.x86.14.00.appx
    ```

    请参阅[示例脚本](windows-deployment-sample-scripts-sxs.md#Reinstall_Windows_inbox_apps)。

**步骤 3︰ 添加并重新安装 Windows 通用应用程序 （可选）**

在我们的示例中，我们尽管可以安装任何的 UWP 应用程序使用此过程安装 Office 移动。

**注意**︰ 安装任一 Office 单个图像 (或者用出永久或订购许可证) 或办公室移动 （不能同时）。 必须与屏幕大小的 10.1"和下面的设备上使用办公移动，必须上方 10.1" 屏幕大小的设备上使用 Office 单个图像。 对于有一个固定的存储驱动器具有小于 32 GB 的设备，Oem 可能预办公室移动安装与屏幕大小无关。 若要了解详细信息，请参阅[Office 移动通信](https://myoem.microsoft.com/oem/myoem/en/product/office/Pages/COMM-OfficeUnvrslAppsOPKRlsTmng.aspx)。

1.  转到<https://microsoftoem.com>并获得补充 OPK。 此软件包中包含 Windows 10 版本 1607年收件箱的应用程序。 不将这些应用程序的每月更新。 

2.  将程序包解压缩到一个文件夹，例如，e:\Universal_Office。

3.  添加并重新安装 Office 移动︰

    ``` syntax
    Dism /Add-ProvisionedAppxPackage /Image:"c:\mount\windows" /packagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\1b0569bd5fbd41d6bf0669beb013073c.appxbundle" /dependencypackagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Excelim.appxbundle_Windows10_PreinstallKit\1b0569bd5fbd41d6bf0669beb013073c_License1.xml"

    Dism /Add-ProvisionedAppxPackage /Image:"c:\mount\windows"  /packagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\7f255062294a415a974b4958961df056.appxbundle" /dependencypackagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Pptim.appxbundle_Windows10_PreinstallKit\7f255062294a415a974b4958961df056_License1.xml"

     Dism /Add-ProvisionedAppxPackage /Image:"c:\mount\windows" /packagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\532f710ca9d34f0aae6af4abe0af0592.appxbundle" /dependencypackagepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\Microsoft.VCLibs.140.00_14.0.22929.0_x86__8wekyb3d8bbwe.appx" /licensepath:"e:\Universal_Office\PC_TH1_store.16.0.6228.1011.Wordim.appxbundle_Windows10_PreinstallKit\532f710ca9d34f0aae6af4abe0af0592_License1.xml"
    ```

    其中 PackagePath 是指向应用程序捆绑包。


**步骤 4︰ 修改开始图标和任务栏针布局 （可选）**

您可以定义单独的默认开始平铺布局和任务栏区间不同地区或市场。

1.  创建一个 LayoutModification.xml 文件。 对于我们实验室中，您可以使用从 USB B 或[LayoutModification.xml 的示例](windows-deployment-sample-scripts-sxs.md)的示例。 本示例说明两组称为"Fabrikam 组 1"和"两个区域在基于 Fabrikam 组 2"，包含应用的图块。 

    当创建您自己的 LayoutModification 文件︰

    若要添加桌面应用程序或旧的 URL (.url) 快捷方式，使用开始︰ DesktopApplicationTile 标记。

     -  对于桌面应用程序，如果您知道应用程序用户模型 ID，使用的。

     -  否则，对于桌面应用程序或遗留.url 链接，创建链接文件 (.lnk) 传统的开始菜单文件夹之一︰

         -  %APPDATA%\Microsoft\Windows\Start Menu\Programs\

         -  %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\ 

     您将在后面的一节中添加对桌面应用程序︰[实验室 12︰ 添加桌面应用程序和设置变得分散化配置软件包 (Spp)](add-desktop-apps-wth-spps-sxs.md)。    

2.  将 LayoutModification.xml 文件添加到 Windows 映像。 您需要将文件放在第一次启动之前以下特定位置。 如果该文件存在，则应当替换图像中已包含 LayoutModification.XML。

    ``` syntax
    C:\Mount\Windows\Users\Default\AppData\Local\Microsoft\Windows\Shell\
    ```

3.  如果您锁定要求.url 或.lnk 文件的图块，请将文件添加到以下的传统开始菜单目录︰
    -   应用程序数据 %%\\Microsoft\\Windows\\「 开始 」 菜单\\程序\\
    -   %ALLUSERSPROFILE%\\Microsoft\\Windows\\「 开始 」 菜单\\程序\\

**请注意** 如果用户重置其 PC 使用内置的恢复工具，开始布局可能会丢失。 您将学习如何确保这些设置都保留在[示例脚本](windows-deployment-sample-scripts-sxs.md)中的设备上。

4.  将任务栏布局第 10 Windows 版本 1607，您可以添加一个类似[任务栏布局修改文件 （请参阅下面的附加步骤）](https://msdn.microsoft.com/library/windows/hardware/mt736838.aspx)，或使用[传统无人参与设置](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)。 

## <a name="span-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanspan-idaddorchangelanguagesandcortanafeaturesondemandoptionalspanadd-or-change-languages-and-cortana-features-on-demand-optional"></a><span id="Add_or_change_languages_and_Cortana_features_on_demand__Optional_"></span><span id="add_or_change_languages_and_cortana_features_on_demand__optional_"></span><span id="ADD_OR_CHANGE_LANGUAGES_AND_CORTANA_FEATURES_ON_DEMAND__OPTIONAL_"></span>添加或更改语言和 Cortana 功能按需 （可选）

## <a name="span-idunmounttheimagesspan-unmount-the-images"></a><span id="Unmount_the_images"></span>卸载映像

**步骤 5︰ 卸载映像**

1.  关闭所有应用程序可能会访问从图像文件。

2.  提交更改并卸载 Windows 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

    其中*C*是驱动器的包含图像的驱动器号。

    此过程可能需要几分钟。

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

**步骤 6︰ 将映像应用到新的 PC**使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将映像复制到 USB 驱动器的存储中，将 Windows 映像和恢复映像，应用和启动它。 短的版本︰

1.  将图像文件复制到的存储驱动器。
2.  [引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备](install-windows-pe-sxs.md)。
3.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。
4.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install.wim`。
5.  断开连接的驱动器，然后重新启动 (`exit`)。
    
**第 7 步︰ 验证应用程序**
1.  计算机启动后，或者创建新的用户帐户，否则按 Ctrl + Shift + F3 要重新启动到内置的管理员帐户 （也称为是审核模式）。

2.  请检查以确保应用程序可以使用开始菜单。

3.  检查 「 开始 」 菜单和任务栏，请确保您选择的应用程序都正确固定。
    
下一步: [实验室 7︰ 更改设置，输入产品密钥，并使用应答文件 (unattend.xml) 运行脚本]