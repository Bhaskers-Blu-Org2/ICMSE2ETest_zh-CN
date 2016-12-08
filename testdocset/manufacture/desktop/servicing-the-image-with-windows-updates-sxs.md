---
author: KPacquer
Description: "添加更新，然后升级版。"
ms.assetid: 9a8f525c-bb8f-492c-a555-0b512e44bcd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 4︰ 添加更新和升级版"
ms.openlocfilehash: 05e2029fca31dfb47457f8b6d7c44758b84a753b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-4-add-updates-and-upgrade-the-edition"></a>实验室 4︰ 添加更新和升级版

对于很多自定义，添加驱动程序.inf 样式，如 Windows 更新或升级版本，您可以装载和编辑 Windows 映像。 装入映像将文件的内容映射到一个临时位置，您可以编辑这些文件或使用 DISM 可以执行常见的部署任务。

**备注** 

* 添加更新之前添加语言。 如果您的映像，然后添加更新后已添加的语言，请转回并[添加您的语言再次](add-drivers-langs-universal-apps-sxs.md)。

-  **对于重大的更新，更新恢复映像太**︰ 它们中可能包含的修补程序、 常规分发版本、 service pack 或其他预发布更新。 我们将向您展示如何更新这些随后在[实验室 10︰ 更新恢复映像](update-the-recovery-image.md)。

-  **服务堆栈更新 (SSU): 是必需的[KB3199209](http://www.catalog.update.microsoft.com/Search.aspx?q=KB3199209)**应用最新的常规分发版本 （GDR） 当前 KB3200970 或任何未来的 Gdr 之前。

![图像︰ 复制图像文件和部署脚本](images/dep-win8-sxs-createmodelspecificfiles.jpg)

注意︰ 若要添加包含安装程序包的驱动程序，请参阅[实验室 12︰ 添加桌面应用程序和设置变得分散化配置软件包 (Spp)](add-desktop-apps-wth-spps-sxs.md)

## <a name="span-idmounttheimagespanmount-the-image"></a><span id="Mount_the_image"></span>装入该映像

**步骤 1︰ 装载映像**

使用步骤，可从[实验室 3︰ 添加设备驱动程序 （.inf 样式）](add-device-drivers.md)装载映像。 短的版本︰

1.  打开命令行以管理员身份 (**开始**> 键入**部署**> 右键单击**部署和图像处理工具环境** > **以管理员身份运行**。)

2.  对该文件进行备份 (`copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim`)

3.  装入该映像 (`md C:\mount\windows`，然后`Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize`)

## <a name="span-idaddcustomizationstotheimagespanadd-customizations-to-the-image"></a><span id="Add_customizations_to_the_image"></span>将自定义项添加到映像
    
**步骤 2︰ 将在家版升级到专业**

使用此过程可以将版本升级。 不能设置为更低版本的 Windows 映像。 您不应该在图像已更改为较高版本上使用此过程。

1.  确定哪些图像可以升级到的图像︰ 注意版本 Id 可用。

    ``` syntax
    Dism /Get-TargetEditions /Image:C:\mount\windows
    ```

2.  升级版。

    ``` syntax
    Dism /Set-Edition:Professional /Image:C:\mount\windows
    ```
    
**步骤 3︰ 添加 Windows 更新软件包**

1.  获取 Windows 更新软件包。 例如，抓住[Microsoft 更新目录](http://www.catalog.update.microsoft.com)中的[Windows 10 更新历史记录](https://support.microsoft.com/en-us/help/12387/windows-10-update-history)中列出的最新的累积更新。 提取到一个文件夹，例如，c:.msu 文件更新\\WindowsUpdates\\windows10.0-kb3194798-x64_8bc6befc7b3c51f94ae70b8d1d9a249bb4b5e108.msu。

2.  将更新添加到图像中。 对于具有依赖关系的软件包，请确保按顺序安装软件包。 如果您不能确定的依赖项，则确定以将它们放在同一文件夹中，并将其所有通过添加多个 /PackagePath 项目使用相同的 DISM /Add-Package 命令。

    示例︰ 将添加一个累积更新︰

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\WindowsUpdates\windows10.0-kb3194798-x64_8bc6befc7b3c51f94ae70b8d1d9a249bb4b5e108.msu"  /LogPath=C:\mount\dism.log
    ```

    示例︰ 将添加多个更新程序︰

    ``` syntax
    Dism /Add-Package /Image:"C:\mount\windows" /PackagePath="C:\WindowsUpdates\windows10.0-kb00001-x64.msu" /PackagePath="C:\WindowsUpdates\windows10.0-kb00002-x64.msu" /PackagePath="C:\WindowsUpdates\windows10.0-kb00003-x64.msu" /LogPath=C:\mount\dism.log
    ```

3.  锁定在更新以便在恢复过程中还原它们。 

    ``` syntax
    DISM /Cleanup-Image /Image=C:\ /StartComponentCleanup /ResetBase /ScratchDir:C:\Temp
    ```

## <a name="span-idunmounttheimagespanunmount-the-image"></a><span id="Unmount_the_image"></span>卸载映像
    
**步骤 4︰ 卸载映像**

1.  关闭所有应用程序可能会访问从图像文件。

2.  提交更改并卸载 Windows 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

**步骤 5︰ 将映像应用到新计算机**

使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将该图像复制到 USB 驱动器的存储，应用该映像，并启动它。 短的版本︰

1.  将图像文件复制到的存储驱动器。
2.  [引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备](install-windows-pe-sxs.md)。
3.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。
4.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install.wim`。
5.  断开连接的驱动器，然后重新启动 (`exit`)。

**第 6 步︰ 检查更新**
1.  计算机启动后，或者创建新的用户帐户，否则按 Ctrl + Shift + F3 要重新启动到内置的管理员帐户 （也称为是审核模式）。

2.  用鼠标右键单击**开始**按钮，然后选择**命令提示符 （管理员）**。

3.  验证版本正确︰

    ``` syntax
    dism /online /get-currentedition
    ```

    请确保它是正确的版本。 例如︰

    ``` syntax
    Current edition is:

    Current Edition : Professional

    The operation completed successfully.
    ```

4.  验证程序包正确显示︰

    ``` syntax
    Dism /Get-Packages /Online
    ```

    检查生成的软件包列表并验证列表包含的软件包。 例如︰

    ``` syntax
    Package Identity : Package_for_RollupFix~31bf3856ad364e35~amd64~~14393.321.1.5
    State : Installed
    Release Type : Security Update
    Install Time : 10/13/2016 6:26 PM

    The operation completed successfully.
    ```

下一步︰[实验室 5︰ 添加语言](add-drivers-langs-universal-apps-sxs.md)