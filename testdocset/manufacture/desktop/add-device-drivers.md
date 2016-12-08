---
author: KPacquer
Description: "添加设备驱动程序"
ms.assetid: 9a8f525c-bb8f-492c-a555-0b512e44bcd1
MSHAttr: PreferredLib:/library/windows/hardware
title: "实验室 3︰ 添加设备驱动程序"
ms.openlocfilehash: a93bcfce576f633c174905777869d8cfc716b7fc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lab-3-add-device-drivers"></a>实验室 3︰ 添加设备驱动程序 

添加到您的图像，以支持您的硬件设备驱动程序。 一些具有不同的安装过程︰

-  **驱动程序.inf 样式**︰ 许多驱动程序包括信息 （.inf 扩展名文件） 来安装驱动程序。 这些都可以使用本主题中描述的工具安装。    
-  **驱动程序.exe 样式**︰ 不经常使用.inf 文件的驱动程序必须安装类似于典型 Windows 桌面应用程序。 我们将向您展示如何添加在[实验室 12︰ 添加桌面应用程序和设置变得分散化配置软件包 (Spp)](add-desktop-apps-wth-spps-sxs.md)。
-  **引导关键驱动程序**︰ 图形和存储驱动程序有时可能需要添加到 Windows 映像 （如本主题中所示），以及 Windows PE 映像 (如上文所示的[实验室 1︰ 安装 Windows PE](install-windows-pe-sxs.md))，并在 Windows 恢复映像。 我们将向您展示如何更新恢复映像以后在[实验室 10︰ 更新恢复映像](update-the-recovery-image.md)。

## <a name="span-idprepareandmounttheimagespanprepare-and-mount-the-image"></a><span id="Prepare_and_mount_the_image"></span>准备并装入该映像
若要对 Windows 映像进行更改，将装载到一个临时文件夹中，将图像内容和使用 DISM 之类的工具来进行更改。 卸载映像保存更改，然后使用部署脚本测试图像。 

![图像︰ 装入图像，进行更改，并卸载映像](images/dep-win8-sxs-createmodelspecificfiles.jpg)

**步骤 1︰ 备份 Windows 映像文件 （推荐测试新设计时）**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  制作的图像文件的一个备份︰
``` syntax
copy "C:\Images\Win10_x64\sources\install.wim" C:\Images\install-backup.wim
```

**第 2 步︰ 将 Windows 映像文件装载**创建一个临时文件夹，若要装载的文件，并将映像装载到它︰ 
``` syntax
md C:\mount\windows
Dism /Mount-Image /ImageFile:"C:\Images\install.wim" /Index:1 /MountDir:"C:\mount\windows" /Optimize
```
其中 /Index:1 是指图像要装入。 对于 Windows 10 家/Pro 版中，使用 /Index:2 来选择的家庭版。

此步骤可能需要几分钟。

**故障排除︰**

-   不装入图像到受保护的文件夹，例如，您的用户\\文档文件夹。

-   如果 DISM 进程被打断，可以考虑暂时断开与公用网络的连接和禁用病毒防护。
    
-   如果已装入图像的文件夹之前，请尝试清理与安装映像相关联的资源︰

    ``` syntax
    Dism /Cleanup-Mountpoints
    ```

-   对于某些 DISM 命令，您需要确保您的**部署和图像处理工具环境**而不是标准的命令提示符下使用。

## <a name="span-idaddcustomizationstotheimagespanadd-customizations-to-the-image"></a><span id="Add_customizations_to_the_image"></span>将自定义项添加到映像
这是只是示例-无需添加所有这些。

**步骤 3︰ 添加驱动程序**

1.  添加单个驱动程序的.inf 文件包含︰

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf"
    ```

    其中"c:\\驱动程序\\PnP.Media.V1\\media1.inf"是驱动程序软件包中的基.inf 文件。

    **疑难解答**︰ 可以为许多 DISM 命令，通过添加 /LogPath 选项有关错误的详细的信息。 例如︰

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:"C:\Drivers\PnP.Media.V1\media1.inf" /LogPath=C:\mount\dism.log
    ```

2.  通过使用 /Recurse 选项来安装驱动程序的一组。 这将具有该文件夹及其所有子文件夹中的.inf 文件添加的所有驱动程序。

    **警告**︰ 尽管 /Recurse 可能很方便，很容易膨胀与图像。 某些驱动程序包包括多个.inf 驱动程序包，通常有效负载从共享文件所在的文件夹。 安装过程中，每个.inf 驱动程序包扩展到一个单独的文件夹，每个都有有效载荷文件的副本。 我们看到其中有 900 MB 文件夹中的常见驱动程序将添加到图像时使用 /Recurse 选项添加 10 GB 的情况。

    ``` syntax
    Dism /Add-Driver /Image:"C:\mount\windows" /Driver:c:\drivers /Recurse 
    ```
    
3.  验证驱动程序是图像的一部分︰

    ``` syntax
    Dism /Get-Drivers /Image:"C:\mount\windows"
    ```

    检查生成的软件包列表并验证列表包含的驱动程序。


## <a name="span-idunmounttheimagespanunmount-the-image"></a><span id="Unmount_the_image"></span>卸载映像
    
**步骤 4︰ 卸载映像**

1.  关闭所有应用程序可能会访问从图像文件。

2.  提交更改并卸载 Windows 映像︰
    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\mount\windows" /Commit
    ```

## <a name="span-idtryitoutspantry-it-out"></a><span id="Try_it_out"></span>试一下

**第 5 步︰ 将映像应用到新的 PC**使用步骤，可从[实验室 2︰ 使用脚本的部署 Windows](deploy-windows-with-a-script-sxs.md)将该图像复制到 USB 驱动器的存储，应用该映像，并启动它。 短的版本︰

1.  将图像文件复制到的存储驱动器。
2.  [引导到 Windows PE 中使用 Windows PE usb 闪存盘的参考设备](install-windows-pe-sxs.md)。
3.  查找存储驱动器的驱动器号 (`diskpart, list volume, exit`)。
4.  将映像应用︰ `D:\ApplyImage.bat D:\Images\install.wim`。
5.  断开连接的驱动器，然后重新启动 (`exit`)。

**第 6 步︰ 验证驱动程序**
1.  计算机启动后，或者创建新的用户帐户，否则按 Ctrl + Shift + F3 要重新启动到内置的管理员帐户 （也称为是审核模式）。

2.  用鼠标右键单击**开始**按钮，然后选择**命令提示符 （管理员）**。

3.  验证的驱动程序正确显示︰

    ``` syntax
    Dism /Get-Drivers /Online
    ```

    查看生成的驱动程序列表。 例如︰

    ``` syntax
    Deployment Image Servicing and Management tool
    Version: 10.0.14393.0

    Image Version: 10.0.14393.0

    Obtaining list of 3rd party drivers from the driver store...

    Driver packages listing:

    Published Name : oem0.inf
    Original File Name : contoso.graphicsdriver.inf
    Inbox : No
    Class Name : Graphics
    Provider Name : Contoso
    Date : 10/19/2016
    Version : 10.0.0.1

    The operation completed successfully.
    ```

## <a name="span-idlearnmorespanlearn-more"></a><span id="Learn_more"></span>了解更多信息

* 当创建多个设备具有相同的硬件配置，可以加快安装时间和启动的第一次由[维护时捕获 Windows 映像的驱动程序配置](maintain-driver-configurations-when-capturing-a-windows-image.md)。 


下一步︰[实验室 4︰ 添加更新和升级版本](servicing-the-image-with-windows-updates-sxs.md)