---
author: kpacquer
Description: "实验室 9︰ 从 Windows （审核模式） 进行的更改"
ms.assetid: 142bc507-64db-43dd-8432-4a19af3c568c
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 9︰ 从 Windows （审核模式） 进行的更改"
ms.openlocfilehash: bb505db23d2c3eaaaa2b22d0437f86f63bebf7c2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-9-make-changes-from-windows-audit-mode"></a>实验室 9︰ 从 Windows （审核模式） 进行的更改

可以使用审核模式下自定义 Windows 使用熟悉的 Windows 环境。 在审核模式下，可以添加 Windows 桌面应用程序、 更改系统设置，添加数据，并运行脚本。  

为了确保审核模式更改包括恢复图像中，您需要捕获到一个包中使用扫描状态自动配置这些更改。 此图像获取系统恢复工具用于还原所做的更改，如果出了问题。 您可以选择保存压缩的恢复文件; 从直接运行应用程序的驱动器空间这被称为单实例存储。

如果您想要捕获图像中所做的更改并将其应用到其他设备，您需要使用 Sysprep 工具一般化映像。


## <a name="span-idprepareacopyofthedeploymentandimagingtoolsspanspan-idprepareacopyofthedeploymentandimaging-toolsspanspan-idprepareacopyofthedeploymentandimagingtoolsspanstep-1-prepare-a-copy-of-the-deployment-and-imaging-tools"></a><span id="Prepare_a_copy_of_the_Deployment_and_Imaging_Tools"></span><span id="prepare_a_copy_of_the_deployment_and_imaging Tools"></span><span id="PREPARE_A_COPY_OF_THE_DEPLOYMENT_AND_IMAGING_TOOLS"></span>第 1 步︰ 准备一份部署和图像处理工具

您将需要 Windows 10，1607年版本的部署并从 ADK 的图像处理工具。 这包括扫描状态工具以及 DISM 的最新版本。

**重要**  不会覆盖现有 DISM 文件 WinPE 映像上。

1.  从技术人员计算机上，将从 Windows ADK 的部署和图像处理工具复制到外部存储 (例如，存储 usb 闪存盘驱动器号 d:）。

    ``` syntax
    CopyDandI.cmd amd64 D:\ADKTools\amd64
    ```
    
## <a name="span-idgetintoauditmodespanstep-2-get-into-audit-mode"></a><span id="Get_into_audit_mode"></span>第 2 步︰ 进入审核模式

1.  如果尚未启动时，启动参考设备。

2.  如果设备引导到**语言**或**获得持续快速**屏幕，请按**Ctrl + Shift + F3**进入审核模式。

3.  在审核模式下，设备将重新启动到桌面，并系统准备工具 (Sysprep) 出现。 暂时忽略 Sysprep。

## <a name="span-idcustomizethepcspanstep-3-customize-the-pc-in-audit-mode"></a><span id="Customize_the_PC"></span>第 3 步︰ 自定义 PC 在审核模式下。

-   安装 Windows 桌面应用程序。 更改系统设置。 添加数据。 运行脚本。

## <a name="span-idcaptureyourchangesspanstep-4-capture-your-changes-for-the-recovery-tools"></a><span id="Capture_your_changes"></span>步骤 4︰ 捕获恢复工具所做的更改

1.  连接到外部存储 (例如，存储 usb 闪存盘驱动器号 d:）

2.  捕获到一个包中设置的更改。 这将创建桌面应用程序和驱动程序在审核模式下，可以使用恢复工具中添加压缩的副本。

    ``` syntax
    D:\ADKTools\amd64\scanstate.exe /apps /ppkg C:\Recovery\Customizations\usmt.ppkg /o /c /v:13 /l:C:\Recovery\ScanState.log
    ```

    **请注意** 可选︰ 删除扫描状态日志文件︰ `del C:\Recovery\Scanstate.log`。

## <a name="span-idprepareforimagecapturespanstep-5-prepare-for-image-capture"></a><span id="Prepare_for_image_capture"></span>第 5 步︰ 准备图像捕获

正在捕获映像应用到其他计算机时，此步骤是必需的。
    
1.  为最终用户准备好设备︰ 右键单击**开始**、 选择**命令提示符 （管理员）**，并从命令提示符下运行以下命令︰

    ``` syntax
    C:\Windows\System32\Sysprep\sysprep /oobe /generalize /shutdown
    ```

    Sysprep 工具重新封装设备。 此过程可能需要几分钟的时间。 在过程完成后，该设备自动关闭。

    **警告**︰ 如果您正在使用[各自为政调配包 (Spp)](add-desktop-apps-wth-spps-sxs.md)，未设置该图像以启动到审核模式再次 （sysprep 模式）。 没有一个已知的错误，使图像无法启动，如果您执行此操作的版本 1607 Windows 10 中。 相反，将其设置为启动到 OOBE，且需要启动到审核[模式︰ 审核设置的答案文件添加](update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)再次。 这将在以后解决版本。

2.  引导至 Windows PE 的设备。 若要执行此操作，可能需要按下键打开引导设备选择菜单中的设备 （例如， **Esc**键或**调高音量**键）。

    要引导到 USB 闪存驱动器的固件菜单中选择选项。

    **警告**  如果 Windows 开始而不 Windows PE 启动，您必须捕获映像之前一般化设备︰ 在 Windows 启动时，请按**Ctrl + Shift + F3**键进入审核模式。 该设备将重新启动。 再次归纳设备︰ `C:\Windows\System32\Sysprep\sysprep /oobe /generalize /shutdown`。

3.  可选︰ 加快优化和映像捕获过程的性能将电源方案设置为高︰

    ``` syntax
    powercfg /s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

4.  通过使用 DiskPart 中查找驱动器号︰

    ``` syntax
    diskpart
    DISKPART> list volume
    DISKPART> exit
    ```

    例如，驱动器可以用字母标明如下︰ *C* = 窗口;*D*是实验室 usb 闪存盘，和*E*是外部硬盘驱动器。

    请注意，某些分区可能不会收到一个驱动器号。

## <a name="span-idoptimizetheimagespanstep-6-optimize-the-image-to-take-up-less-drive-space-optional"></a><span id="Optimize_the_image"></span>第 6 步︰ 优化图像占用更少的驱动器空间 （可选）

1.  通过单实例存储图像来节省空间。 这将删除桌面应用程序的原始副本，以便从资源调配您在前面创建的软件包恢复运行这些应用程序中添加指针文件。

    ``` syntax
    DISM /Apply-CustomDataImage /CustomDataImage:C:\Recovery\Customizations\USMT.ppkg /ImagePath:C:\ /SingleInstance
    ```

    其中*C*是 Windows 分区的驱动器号。

    **警告** 不要将报价单与 /ImagePath:C:\\选项。

2.  清除窗口的文件︰

    ``` syntax
    md temp

    DISM /Cleanup-Image /Image=C:\ /StartComponentCleanup /ResetBase /ScratchDir:C:\Temp
    ```

    其中*C*是 Windows 分区的驱动器号。 开头第 10 Windows 版本 1607，可以在 /Resetbase 将推迟到下一步的自动维护任何长时间运行清理操作中指定 /Defer 参数。 但我们极力建议您**只**将 /Defer 用作其中 DISM /Resetbase 需要 30 分钟以上才能完成的工厂中的一个选项。

### <a name="span-idcapturetheimagespanspan-idcapturetheimagespanspan-idcapturetheimagespanstep-7-capture-the-image"></a><span id="Capture_the_image"></span><span id="capture_the_image"></span><span id="CAPTURE_THE_IMAGE"></span>第 7 步︰ 捕获映像

-   捕获的映像的 Windows 分区。

    ``` syntax
    dism /Capture-Image /CaptureDir:C:\ /ImageFile:"C:\WindowsWithFinalChanges.wim" /Name:"Final changes"
    ```

    其中*C*是 Windows 分区的驱动器号，*法语和桌面应用程序*的映像名称。

    DISM 工具捕获到一个新的图像文件的 Windows 分区。 此过程可能需要几分钟的时间。

    **故障排除**︰ 如果您收到:"参数是不正确的"错误消息当试图捕获或将文件复制到 usb 闪存盘时，该文件可能太大的目标文件系统。 将该文件复制到另一个驱动器格式化为 NTFS。

    2.  将图像复制到网络共享。 示例： 
    ```syntax
    net use N: \\server\share
    copy C:\WindowsWithFinalChanges.wim N:\Images\WindowsWithFinalChanges.wim
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

**步骤 6︰ 将映像应用到新的 PC**使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将映像复制到 USB 驱动器的存储中，将 Windows 映像和恢复映像，应用和启动它。 短的版本︰

1.  将图像文件复制到的存储驱动器。
2.  [引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备](install-windows-pe-sxs.md)。
3.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。
4.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install.wim`。
5.  断开连接的驱动器，然后重新启动 (`exit`)。
    
**第 7 步︰ 验证的自定义项**

1.  计算机启动后，或者创建新的用户帐户，否则按 Ctrl + Shift + F3 要重新启动到内置的管理员帐户 （也称为是审核模式）。

2.  在审核模式下所做的更改存在，请参阅。

下一步行动︰[实验室 10︰ 更新恢复映像](update-the-recovery-image.md)