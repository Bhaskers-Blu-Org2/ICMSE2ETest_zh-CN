---
author: Justinha
Description: "WinPE︰ 安装和自定义"
ms.assetid: 5d5c13e8-8754-4fff-afd1-dcc3fb757bb9
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 安装和自定义"
ms.openlocfilehash: 5283cbb0c827a3909a98203f232d270cd5ba70f1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-mount-and-customize"></a>WinPE︰ 安装和自定义


如图形驱动程序或网络驱动程序对 Windows 预安装环境 (WinPE) 添加驱动程序。

常见的自定义︰

-   [添加设备驱动程序 （.inf 文件）](winpe-add-drivers.md)。 您可以自定义设备驱动程序，例如支持的网卡或存储设备的驱动程序。
-   [添加软件包 （.cab 文件，也称为 WinPE 可选组件）](winpe-add-packages--optional-components-reference.md)添加语言、 修补程序或对 PowerShell 和 HTML 应用程序语言 (HTA) 等功能的支持。
-   [添加一种语言](winpe-add-packages--optional-components-reference.md)。 若要在多种语言下运行 WinPE，添加用于这些语言的软件包 （可选组件）。
-   添加文件和文件夹。 这些可以直接添加到 WinPE 映像。
-   [添加 DISM 的较新版本](copy-dism-to-another-computer.md)。 当新版本的 Windows 要求 DISM 的最新版本中的功能时，您可以添加 DISM 直接到 WinPE。
-   [添加启动脚本](#addstartupscript)。 例如，设置网络连接，或添加一个自定义的应用程序，如诊断软件。
-   [添加应用程序](#addapp)。 请注意，WinPE 仅支持旧式应用程序。
-   [添加临时存储 （暂存空间）](#scratchspace)。 如果您的应用程序要求临时文件存储，您可以保留在 RAM 中的额外的内存空间。
-   [替换的背景图像](#addwallpaper)
-   [添加的答案文件设置](#addanswerfilesettings)

**使用 Windows PE 工具获取 Windows 评估和部署工具包**

-   安装[Windows 评估和部署工具包 (Windows ADK) 技术参考](http://go.microsoft.com/fwlink/p/?LinkId=526803)，其中包括**Windows PE**功能。

**创建一套 32 位或 64 位的 Windows PE 文件**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  中的**部署工具和图像管理环境**，WinPE 文件复制要用来启动的电脑。

    -   64 位版本可以引导 UEFI 64-位和 64 位 BIOS 电脑。

        ``` syntax
        copype amd64 C:\WinPE_amd64
        ```

    -   32 位 （uefi）、 32 位 BIOS 和 64 位 BIOS Pc，可以引导 32 位版本的 WinPE。

        ``` syntax
        copype x86 C:\WinPE_x86
        ```

**装载 Windows PE 启动映像**

-   WinPE 映像装载。

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

## <a name="span-idaddcustomizationsspanspan-idaddcustomizationsspanspan-idaddcustomizationsspanadd-customizations"></a><span id="Add_customizations"></span><span id="add_customizations"></span><span id="ADD_CUSTOMIZATIONS"></span>添加自定义项


**添加设备驱动程序 （.inf 文件）**

-   将设备驱动程序添加到 WinPE 映像中。

    ``` syntax
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

    虽然使用一条命令，可以将多个驱动程序添加到映像中，但是很容易通过单独添加每个驱动程序软件包，解决问题。

    若要了解有关驱动程序的详细信息，请参阅[添加设备驱动程序 （.inf 文件）](winpe-add-drivers.md)。

**添加每个.cab 文件包/语言/可选组件文件**

-   到 WinPE 添加的可选组件。 若要添加可选组件，您需要添加的可选组件和其相关的语言包。

    ``` syntax
    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-HTA.cab"  

    Dism /Add-Package /Image:"C:\WinPE_amd64\mount" /PackagePath:"C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-HTA_en-us.cab"
    ```

    若要了解有关添加程序包的详细信息，请参阅[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)。

**添加文件和文件夹**

-   将文件和文件夹复制到 c:\\WinPE\_amd64\\安装文件夹。 这些文件会显示在 x:\\文件夹中 WinPE。

    不要添加的文件太多，因为这些将减慢 WinPE，可以填满默认 RAMDisk 环境中的可用内存。

<span id="AddStartupScript"></span><span id="addstartupscript"></span><span id="ADDSTARTUPSCRIPT"></span>
**添加一个启动脚本**

-   修改 Startnet.cmd 脚本以包括您的自定义的命令。 此文件位于`C:\WinPE_amd64\mount\Windows\System32\Startnet.cmd`。

    此外可以从该文件中调用其他批处理文件或命令行脚本。

    对于插或网络支持，请确保您在您的自定义 Startnet.cmd 脚本中包含对**wpeinit**的调用。 有关详细信息，请参阅[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)。

<span id="AddApp"></span><span id="addapp"></span><span id="ADDAPP"></span>
**添加应用程序**

1.  创建应用程序目录内装载的 WinPE 映像。

    ``` syntax
    md "C:\WinPE_amd64\mount\windows\<MyApp>"
    ```

2.  将所需的应用程序文件复制到本地的 WinPE 目录。

    ``` syntax
    Xcopy C:\<MyApp> "C:\WinPE_amd64\mount\windows\<MyApp>"
    ```

3.  稍后启动 WinPE，从 x︰ 目录中运行应用程序测试应用程序。

    ``` syntax
    X:\Windows\System32> X:\Windows\<MyApp>
    ```

    如果您的应用程序要求临时存储，或者 WinPE 变得没有反应在运行应用程序时，您可能需要增加临时存储 （暂存空间） 分配到 WinPE 的量。

4.  若要自动启动一个外壳程序或启动 WinPE 时运行的应用程序，添加到 Winpeshl.ini 文件的路径位置。 有关详细信息，请参阅[Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序](winpeshlini-reference-launching-an-app-when-winpe-starts.md)。

<span id="ScratchSpace"></span><span id="scratchspace"></span><span id="SCRATCHSPACE"></span>
**添加临时存储 （暂存空间）**

-   WinPE 保留在 x︰ 驱动器解压缩 WinPE 文件，再加上额外的临时文件存储，称为暂存空间，可以使用您的应用程序的内存。 默认情况下，这是 512 MB Pc 具有 1 GB 以上的 RAM，否则默认值是 32 MB。 有效值为 32、 64、 128、 256 或 512 个。

    ``` syntax
    Dism /Set-ScratchSpace:256 /Image:"C:\WinPE_amd64\mount"
    ```

<span id="AddWallpaper"></span><span id="addwallpaper"></span><span id="ADDWALLPAPER"></span>
**替换的背景图像**

1.  如果您有多个版本的 WinPE，您可以设置背景图像，以便您可以立即了解正在运行哪个版本的 WinPE。

    更改安全权限的 WinPE 背景图像文件 (`\windows\system32\winpe.jpg`)。 这允许您修改或删除该文件。

    1.  在 Windows 资源管理器中，导航到`C:\WinPE_amd64\mount\windows\system32`。

    2.  用鼠标右键单击`C:\WinPE_amd64\mount\windows\system32\winpe.jpg`文件中，并选择**属性** &gt; **安全**选项卡&gt;**高级**。

    3.  旁边的所有者，选择**更改**。 将所有者更改为**管理员**。

    4.  应用这些更改，然后退出属性窗口，以保存更改。

    5.  用鼠标右键单击`C:\WinPE_amd64\mount\windows\system32\winpe.jpg`文件中，并选择**属性** &gt; **安全**选项卡&gt;**高级**。

    6.  修改以允许完全访问权限的**管理员**的权限。

    7.  应用这些更改，然后退出属性窗口，以保存更改。

2.  更换`winpe.jpg`文件与您自己的图像文件。

<span id="AddAnswerFileSettings"></span><span id="addanswerfilesettings"></span><span id="ADDANSWERFILESETTINGS"></span>
**添加的答案文件设置**

-   可以通过使用应答文件，如防火墙、 网络和显示设置管理某些 WinPE 设置。 创建应答文件、 将它命名为 unattend.xml，并将其添加到根的 WinPE 媒体处理这些设置。 有关详细信息，请参阅[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)。

**卸载 Windows PE 映像并创建媒体**

1.  卸载 WinPE 映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  创建可引导介质，如 USB 闪存驱动器。

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  引导介质。 自动启动 WinPE。 WinPE 窗口出现后，wpeinit 命令将自动运行。 这可能需要几分钟的时间。 请验证您的自定义。

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


-   无法启动 WinPE 吗？ 请参见本主题结尾处的故障排除提示︰ [WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)
-   在连接到网络上的提示，请参阅[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)。
-   如果 WinPE 映像变为 unserviceable 时，您可能需要清理图像，您可以再次装入该映像之前。 有关信息，请参阅[修复 Windows 映像](repair-a-windows-image.md)。

### <a name="span-idtodeleteaworkingdirectoryspanspan-idtodeleteaworkingdirectoryspanspan-idtodeleteaworkingdirectoryspanto-delete-a-working-directory"></a><span id="To_delete_a_working_directory_"></span><span id="to_delete_a_working_directory_"></span><span id="TO_DELETE_A_WORKING_DIRECTORY_"></span>若要删除一个工作目录︰

在某些情况下，您可能不能恢复已装载的映像。 DISM 将防止您意外地删除工作目录中，因此您可能需要尝试以下步骤删除已装载的目录的访问。 请尝试以下步骤︰

1.  请尝试重新装载映像︰

    ``` syntax
    dism /Remount-Image /MountDir:C:\mount
    ```

2.  尝试卸载映像、 放弃更改︰

    ``` syntax
    dism /Unmount-Image /MountDir:C:\mount /discard
    ```

3.  请尝试清理与安装映像相关联的资源︰

    ``` syntax
    dism /Cleanup-Mountpoints
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[WinPE︰ 优化并缩小图像](winpe-optimize.md)

[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)

 

 






