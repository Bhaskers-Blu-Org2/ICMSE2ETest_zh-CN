---
author: Justinha
Description: "使用审核模式下添加 Windows 桌面应用程序和其他数据的方式。"
ms.assetid: 61e94d42-5d12-4c54-9efc-1e38ea94f750
MSHAttr: PreferredLib:/library/windows/hardware
title: "与 Windows 桌面应用程序中创建的资源调配包"
ms.openlocfilehash: 0ebbf9b83919bd4ce0a81f805f6dd1db8fae2acf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-provisioning-package-with-windows-desktop-applications"></a>与 Windows 桌面应用程序中创建的资源调配包


下面介绍了如何通过使用审核模式下添加 Windows 桌面应用程序和其他数据。 将使用扫描状态工具，再次这些 Windows 桌面应用程序和数据捕获到一个包中提供。 随着释放新的 Windows 版本，以及为不同的市场做准备，您可以混用和匹配的 Windows 映像和调配包，而不是重建和自定义图像每次。

一旦捕获设置包后，可以直接将其添加到您的映像，使用 Windows ICD。

恢复工具也使用此配置包。 当用户刷新设备 （通常使用设备出现故障时） 或者复位 （通常用来清洗的新用户设备） 的设备时，设备置备该包中保留其已安装的 Windows 更新，再加上更新。

## <a name="span-idstep1prepareacopyofscanstatespanspan-idstep1prepareacopyofscanstatespanspan-idstep1prepareacopyofscanstatespanstep-1-prepare-a-copy-of-scanstate"></a><span id="Step_1__Prepare_a_copy_of_ScanState"></span><span id="step_1__prepare_a_copy_of_scanstate"></span><span id="STEP_1__PREPARE_A_COPY_OF_SCANSTATE"></span>第 1 步︰ 准备一份扫描状态


1.  在技术人员计算机，插入另一个 usb 闪存盘或驱动器。
2.  文件资源管理器中创建新的文件夹上的 USB 密钥，例如︰ **d:\\扫描状态 x64**。
3.  将文件从复制**"c:\\程序文件 (x86)\\窗口工具包\\10\\评估和部署工具包\\用户状态迁移工具\\amd64"**到**d:\\扫描状态 x64**。 您不需要复制子文件夹。
4.  将文件从复制**"c:\\程序文件 (x86)\\窗口工具包\\10\\评估和部署工具包\\Windows 安装程序\\amd64\\源"**到**d:\\扫描状态 x64**。 将重复文件，而是确定以跳过复制这些文件。 您不需要复制子文件夹。

## <a name="span-idinstalldesktopappspanspan-idinstalldesktopappspanspan-idinstalldesktopappspanstep-2-install-a-windows-desktop-application-in-audit-mode"></a><span id="installDesktopApp"></span><span id="installdesktopapp"></span><span id="INSTALLDESKTOPAPP"></span>步骤 2︰ 在审核模式下安装 Windows 桌面应用程序


使用此方法来安装 Windows 桌面应用程序和任何驱动程序需要安装 （而不是样式.inf 驱动）。

1.  引用的设备，安装在实验室 1a 中创建的图像。 如果已经安装图像，开始参考设备。 **语言**或**那里的你好**屏幕显示。
2.  按**Ctrl + Shift + F3**进入审核模式。 该设备将重新启动到桌面，并系统准备工具 (Sysprep) 出现。 Sysprep，您可将其关闭。
3.  确保[实验室 1a](install-windows-automatically-from-a-usb-drive-sxs.md)从自定义项都可用。 为此，请在**设置**下**系统&gt;关于**，您应该会看到技术出现先前输入的支持信息 （公司名称、 客服电话号码和支持网站）。

4.  安装 Windows 桌面应用程序的应用程序。 例如，要安装 Office 2013，放在 USB 密钥与 Office 安装程序、 打开文件资源管理器，定位到`oemsetup.en-us.com`。 若要了解详细信息，请从 Office OPK 连接网站下载 Office OPK 更新映像。

## <a name="span-idsavewithusmtspanspan-idsavewithusmtspanspan-idsavewithusmtspanstep-3-save-your-updates-to-a-provisioning-package"></a><span id="saveWithUSMT"></span><span id="savewithusmt"></span><span id="SAVEWITHUSMT"></span>步骤 3︰ 保存到资源调配包更新


**捕获到一个包中提供的更新**

首先，参考设备插入 usb 闪存盘与扫描状态。

-   **如果您想保留此设置包的副本并将其部署到其他设备**，将文件保存到 USB 驱动器。

    捕获到资源调配的包中，所做的更改并将其保存在 usb 闪存盘上。

    ``` syntax
    D:\ScanState_x64\scanstate.exe /apps /ppkg D:\Provisioning\ClassicApps.ppkg /o /c /v:13 /l:D:\ScanState.log
    ```

    其中*D*是扫描状态与驱动器的盘符。

   
-   **照到生产设备**，可以总结这些更改，并准备立即交货的设备。 捕获到资源调配包中，更改并将其保存为 c:\\恢复\\的自定义\\usmt.ppkg:

    ``` syntax
    D:\ScanState_x64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\usmt.ppkg /o /c /v:13 /l:D:\ScanState.log
    ```

## <a name="span-idstep4preparethedeviceforanenduserspanspan-idstep4preparethedeviceforanenduserspanspan-idstep4preparethedeviceforanenduserspanstep-4-prepare-the-device-for-an-end-user"></a><span id="Step_4__Prepare_the_device_for_an_end_user"></span><span id="step_4__prepare_the_device_for_an_end_user"></span><span id="STEP_4__PREPARE_THE_DEVICE_FOR_AN_END_USER"></span>步骤 4︰ 为最终用户准备设备


-   **对于单生成设备**，为最终用户准备好设备︰ 右键单击**开始**，选择**命令提示符 （管理员）**，然后运行以下命令︰

    ``` syntax
     
    C:\Windows\System32\Sysprep\sysprep /oobe /shutdown
    ```

    Sysprep 工具重新封装设备。 此过程可能需要几分钟的时间。 在过程完成后，该设备自动关闭。 现在，您可以向客户发送设备。

 

 





