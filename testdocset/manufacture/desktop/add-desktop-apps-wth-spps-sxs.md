---
author: KPacquer
Description: "实验室 12︰ 添加桌面应用程序和设置与各自为政的供应包 (Spp)"
ms.assetid: 142bc507-64db-43dd-8432-4a19af3c568c
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 12︰ 添加桌面应用程序和设置与各自为政的供应包 (Spp)"
ms.openlocfilehash: fa139116e0771746dd8c22c2a627501951eced95
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-12-add-desktop-applications-and-settings-with-siloed-provisioning-packages-spps"></a>实验室 12︰ 添加桌面应用程序和设置与各自为政的供应包 (Spp)

通过捕获它们各自为政的供应包 (Spp) 到安装 Windows 桌面应用程序和系统设置。

Spp 是一种新型的供应包可用于 Windows 10，1607年版本。 在以前版本的 Windows 10，来捕获这些应用程序，则会捕获它们同时到一个单一的供应包。  

通过 Spp，您可以捕获单个 Windows 桌面应用程序、.exe 式驱动程序和 Windows 设置。 然后您可以应用到您的 Pc 在应用 Windows 映像后。 这为生产过程提供了更大的灵活性，有助于降低生成运行 Windows 的个人电脑所需的时间。    

Spp 还支持应用程序包含可选的组件，如应用程序语言包捕获的附件包。

应用 Spp 后，它们将自动包含在恢复工具。 

当您应用 Spp 到紧凑的 OS 系统，应用程序，SPP 都是单一实例自动以节省空间。

**备注**

*  若要将这些应用程序添加到任务栏和开始菜单中，您将需要更新 LayoutModification.xml 和 TaskbarLayoutModification.xml 的文件，则在前面添加[实验室 6︰ 添加通用的 Windows 应用程序，开始拼贴和任务栏针脚](add-universal-apps-sxs.md)。 这些文件的新版本可以简单地复制到图像或目标设备直接。 

## <a name="best-practices-while-capturing-applications-use-clean-installations"></a>捕获应用程序时的最佳做法︰ 使用干净安装

我们建议捕获新 Windows 桌面应用程序，每次您启动清洁、 新安装的 Windows 映像，在审核模式下使用。

要做到这一点︰
*  使用的技术在中学到实验室快速应用于设备的图像
*  使用虚拟机 (Vm)。 使用 Hyper-V，可以创建干净的刚刚安装的 Windows 映像，然后创建检查点。 您可以使用检查点迅速弹回的清洁、 刚刚重新安装状态。 

## <a name="span-idprepareacopyofthedeploymentandimagingtoolsspanspan-idprepareacopyofthedeploymentandimaging-toolsspanspan-idprepareacopyofthedeploymentandimagingtoolsspanstep-1-prepare-a-copy-of-the-deployment-and-imaging-tools"></a><span id="Prepare_a_copy_of_the_Deployment_and_Imaging_Tools"></span><span id="prepare_a_copy_of_the_deployment_and_imaging Tools"></span><span id="PREPARE_A_COPY_OF_THE_DEPLOYMENT_AND_IMAGING_TOOLS"></span>第 1 步︰ 准备一份部署和图像处理工具

您将需要 Windows 10，1607年版本的部署并从 ADK 的图像处理工具。 这包括扫描状态工具以及 DISM 的最新版本。

**重要**  不会覆盖现有 DISM 文件 WinPE 映像上。

1.  以管理员身份启动部署和图像处理工具环境。

2.  从技术人员计算机上，将从 Windows ADK 的部署和图像处理工具复制到存储 usb 闪存盘。

    ``` syntax
    CopyDandI.cmd amd64 E:\ADKTools\amd64
    ```

## <a name="span-idprepareadeviceforimagecapturespanspan-idprepareadeviceforimagecapturespanspan-idprepareadeviceforimagecapturespanstep-2-prepare-a-device-for-image-capture"></a><span id="Prepare_a_device_for_image_capture"></span><span id="prepare_a_device_for_image_capture"></span><span id="PREPARE_A_DEVICE_FOR_IMAGE_CAPTURE"></span>步骤 2︰ 准备用于图像捕获设备

**进入审核模式**

1.  如果尚未启动时，启动参考设备 （或虚拟机）。

2.  如果设备引导到**语言**或**获得持续快速**屏幕，请按**Ctrl + Shift + F3**进入审核模式。

3.  在审核模式下，设备将重新启动到桌面，并系统准备工具 (Sysprep) 出现。 暂时忽略 Sysprep。

4.  为虚拟机，创建此清洁、 新安装的 Windows 映像的检查点。

## <a name="span-idcaptureasettingspanspan-idcaptureasettingspanstep-3-capture-a-setting-windows-store-id"></a><span id="Capture_a_setting"></span><span id="capture_a_setting"></span>第 3 步︰ 捕获设置 (Windows 商店 ID)

通过 Windows 应用商店，有品牌和设备优势，收入创建和客户访问的巨大机会。 

Windows 应用商店应用程序是在 Windows 10 体验中心。 为 OEM，可以提供吸引人的用户体验，并通过提供软件和将值添加到您的 Pc，您构建的服务提高品牌忠诚度。

若要了解详细信息，请参阅[Windows 存储程序 2016年指南](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2016/Pages/DP-WindowsStoreOEMProgramGuide2016FinalCL.aspx)和[应用程序和存储 Windows 工程指南 (WEG)](https://myoem.microsoft.com/oem/myoem/en/topics/Licensing/roylicres/ost2016/Pages/DP-WinEngnrngGdAppsStore.aspx)。

1.  添加一个设置。 例如，将您的 Windows 存储程序 ID 添加到 Windows 注册表中︰

    一。  启动注册表编辑器。

    b。  导航到 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Store。

    c。  单击**编辑 > 新建 > 字符串值**。

    d。  根据协议的类型，键入`OEMID`或`StoreContentModifier`。

    电子。  双击 OEMID 或 StoreContentModifier，然后在**值**中键入您的 Windows 存储程序的 id。

2.  捕获到各自为政的供应包中，所做的更改并将其保存到硬盘上︰

    ``` syntax
    E:\ADKTools\amd64\ScanState.exe /config:E:\ADKTools\amd64\Config_SettingsOnly.xml /o /v:13 /ppkg e:\SPPs\store.spp
    ```

    其中*E*是扫描状态的 USB 驱动器的驱动器号。

    **可选**︰ 删除扫描状态日志文件︰ `del C:\Scanstate.log`。

## <a name="span-idinstallandcaptureawindowsdesktopapplicationspanspan-idinstallandcaptureawindowsdesktopapplicationspanspan-idinstallandcaptureawindowsdesktopapplicationspanstep-3-install-and-capture-a-windows-desktop-application-microsoft-office"></a><span id="Install_and_capture_a_Windows_desktop_application"></span><span id="install_and_capture_a_windows_desktop_application"></span><span id="INSTALL_AND_CAPTURE_A_WINDOWS_DESKTOP_APPLICATION"></span>步骤 3︰ 安装并捕获 Windows 桌面应用程序 (Microsoft Office)

1.  安装 Windows 桌面应用程序。 例如，要安装 Office 2016。

    一。  在技术人员计算机，装载 ISO 部署工具从"X21 05453 Office v16.2 OEM OPK\Software-DVD\X21 05495 软件 DVD5 办公室 2016 v16.2 部署工具 for OEM\X21 05495.img 的部署工具"

    b。  已装入的驱动器的文件复制到 USB-B （其中 E:\ 是 USB b 的字母） E:\OfficeV16.2
    
    c。  双击 e:\Officev16.2\officedeploymenttool.exe


2.  启动命令提示符。

3.  捕获到各自为政的供应包中，所做的更改并将其保存到硬盘上︰

    ``` syntax
    E:\ADKTools\amd64\ScanState.exe /apps:-sysdrive /o /v:13 /config:E:\ADKTools\amd64\Config_AppsOnly.xml /ppkg e:\SPPs\office16_base.spp
    ```

    其中*E*是扫描状态的 USB 驱动器的驱动器号。

    **可选**︰ 删除扫描状态日志文件︰ `del C:\Scanstate.log`。

4.  要捕获一个加载项包，请重复此过程。 
    示例︰ 添加 Office 2016 语言包。 从 Office OPK 连接网站获取这些从 Office OPK 更新映像。
    
    1.  安装 fr fr 语言包。
    
    2.  作为加载项包捕获了合并的文件。
        ``` syntax
        E:\ADKTools\amd64\ScanState.exe /apps:-sysdrive /o /v:13 /config:E:\ADKTools\amd64\Config_AppsOnly.xml /diff:e:\SPPs\office16_base.spp /ppkg E:\SPPs\office16_fr-fr.spp
        ```

        Sysprep 工具重新封装设备。 此过程可能需要几分钟的时间。 在过程完成后，该设备自动关闭。
    
    3. 捕获更多的加载项包︰
       -  重新安装 Windows 和 Office 基本应用程序中，并捕获下一个加载项包。
          或
       -  为虚拟机，恢复到检查点，应用基本产品包，然后捕获下一个加载项包。

5.  捕获更多应用程序︰
    -  重新安装 Windows，然后捕获下一个应用程序或
    -  为虚拟机，恢复为在检查点，然后捕获下一个应用程序。

## <a name="span-idtryitoutspanspan-idtryitoutspanspan-idtryitoutspanstep-4-try-it-out"></a><span id="Try_it_out"></span><span id="try_it_out"></span><span id="TRY_IT_OUT"></span>第 4 步︰ 尝试
    
**应用映像**

使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将该图像复制到 USB 驱动器的存储，应用该映像，并启动它。 

短的版本︰

1.  启动 Windows PE PC 参考。

2.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。

3.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install-updated.wim`。

**应用 Spp**

1.  复制到不可移动的文件的位置，如主硬盘，将其分配到 W ApplyImage 命令后 ADK 工具。 
    将文件复制到一个固定位置，避免了与安装 DISM 从可移动驱动器关联的错误。
    ``` syntax
    xcopy D:\ADKTools\ W:\ADKTools\ /s
    ```

2.  安装通过使用**/q WimMountAdkSetupAmd64.exe /Install**或**WimMountAdkSetupX86.exe /Install /q**ADK 工具。

    ``` syntax
    W:\ADKTools\amd64\WimMountAdkSetupAmd64.exe /Install /q
    ```

3.  应用 Spp。 本示例将 Office 基包，再加上两个语言包︰ fr fr 和消除重复。
    
    ```syntax
    W:\ADKTools\amd64\DISM.exe /Apply-SiloedPackage /ImagePath:W:\ /PackagePath:"e:\SPPs\store.spp" /PackagePath:"D:\SPPs\office16_base.spp" /PackagePath:"D:\SPPs\office16_fr-fr.spp" /PackagePath:"D:\SPPs\office16_de-de.spp"
    ```

    若要了解详细信息，请参阅[Siloed 调配包](siloed-provisioning-packages.md)。 有关语法，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。 

**应用恢复映像**
1.  应用应用 Spp 后恢复映像︰`D:\ApplyRecovery.bat`

2.  断开连接的驱动器，然后重新启动 (`exit`)。
    
**验证应用程序**

1.  计算机启动后，或者创建新的用户帐户，否则按 Ctrl + Shift + F3 要重新启动到内置的管理员帐户 （也称为是审核模式）。

2.  如果安装 Windows 桌面应用程序和加载项，请参阅。

