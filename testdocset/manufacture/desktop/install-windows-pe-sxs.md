---
author: KPacquer
Description: "安装 Windows PE"
ms.assetid: e6e571df-8b4f-43f8-9a8c-cb5f25969a5d
MSHAttr: PreferredLib:/library/windows/hardware
title: "安装 Windows PE"
ms.openlocfilehash: ebe012dfb0c9389ff71930e377edeba6c3c22654
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-1-install-windows-pe"></a>实验室 1︰ 安装 Windows PE


Windows 预安装环境 (WinPE) 是一个小型的命令行根据的操作系统。 可以使用它来捕获、 更新和优化 Windows 映像，您将在后面的部分中进行。 在此部分中，您将准备基本的 WinPE 映像可引导的 USB 闪存驱动器上并试一下。

Windows PE USB 必须至少 512 MB 和最大 32GB。 它不应为 Windows 到转键或键标记为非可移动驱动器。

## <a name="span-idpreparethewinpefilesspanprepare-the-winpe-files"></a><span id="Prepare_the_WinPE_files"></span>准备包含 WinPE 文件

1.  在技术人员计算机，以管理员身份启动**部署和图像处理工具环境**︰
    -  单击**开始**，键入**部署和图像处理工具环境**。 右键单击**部署和图像处理工具环境**，选择**以管理员身份运行**。

2.  将基 WinPE 文件复制到新文件夹中︰

    ``` syntax
    copype amd64 C:\winpe_amd64
    ```

    如果您正在部署 x86 重复设备︰

    ``` syntax
    copype x86 C:\winpe_x86
    ```

   **疑难解答**︰ 如果这不起作用，请确保您在部署和图像处理工具环境中，并不是标准的命令提示符。 
    
## <a name="span-idaddtowinpespanadd-to-winpe-usually-not-needed"></a><span id="Add_to_WinPE"></span>将添加到 WinPE （通常不需要）

常见的情况︰

* **添加视频或网络驱动程序**。 （WinPE 包括通用视频和网络驱动程序，但在某些情况下，需要附加的驱动程序以显示屏幕或连接到网络）。

* **添加 PowerShell 的脚本支持**。 若要了解详细信息，请参阅[WinPE︰ 添加 Windows PowerShell 支持添加到 Windows PE](winpe-adding-powershell-support-to-windows-pe.md)。 在此实验室中不包括 PowerShell 脚本。

请注意，当 WinPE 中添加多个程序包，它降低了 WinPE 性能和启动时间。 只能添加其他文件包，在必要时。  

与有限的 RAM 和存储 （例如，1 GB RAM/16GB 存储） 设备︰ 添加到 Windows PE 的驱动程序或其他自定义项之后，请参阅[WinPE︰ 优化并缩小图像](winpe-optimize.md)有助于缩短启动时间。

1.  WinPE 映像装载。 装入映像将文件的内容映射到在其中您可以查看和修改它们的位置。

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

2.  添加驱动程序。

    ``` syntax
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

3.  卸载的 WinPE 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

## <a name="span-idcreateabootabledrivespancreate-a-bootable-drive"></a><span id="Create_a_bootable_drive"></span>创建可启动驱动器

1.  插入您不介意格式化 usb 闪存盘。 请注意驱动器号使用，例如，d。

2.  安装 WinPE 到空的 USB 驱动器︰

    ``` syntax
    MakeWinPEMedia /UFD C:\winpe_amd64 D:
    ```

    出现提示时，按**Y**将驱动器格式化和安装 WinPE。

    如果有必要，请在部署 x86 时单独使用 usb 闪存盘插入重复的设备︰

    ``` syntax
    MakeWinPEMedia /UFD C:\winpe_x86 E:
    ```

    出现提示时，按**Y**将驱动器格式化和安装 WinPE。

3.  在文件资源管理器中，用鼠标右键单击该驱动器，然后选择**弹出**。

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

1.  WinPE USB 驱动器连接到参考设备。

2.  关闭设备，然后启动到 USB 驱动器。 您通常通过实现打开设备电源并迅速按下一个键 （例如， **Esc**键或**调高音量**键）。

    **请注意**  在某些设备中，您可能需要进入引导菜单，用于选择 USB 驱动器。 如果您提供了引导 UEFI 模式或 BIOS 模式之间进行选择，选择 UEFI 模式。 若要了解详细信息，请参阅[为 UEFI 模式或传统 BIOS 模式的引导](http://go.microsoft.com/fwlink/?LinkId=526943)。
    如果该设备不能从 USB 驱动器启动，请参阅中的故障排除提示[WinPE︰ 创建 USB 可启动驱动器](http://go.microsoft.com/fwlink/?LinkId=526944)。

    WinPE 在命令行中，将启动并运行**wpeinit**来设置系统。 这可能需要几分钟的时间。

将引导至 Windows PE 中，现在这台电脑。 

下一步︰[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)
 