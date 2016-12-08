---
author: Justinha
Description: "WinPE︰ 添加驱动程序"
ms.assetid: 9eecfba3-2a0d-4c38-8cec-6d5e839ae8d4
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 添加驱动程序"
ms.openlocfilehash: 9c6385c5fefa35af6e8fd444e78732da07a0c31c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-add-drivers"></a>WinPE︰ 添加驱动程序


如图形驱动程序或网络驱动程序添加到 Windows PE 的驱动程序。

设备驱动程序通常包括一个包含多个文件的文件夹。 这些文件夹包含的文件`.inf`文件的扩展名。 此文件管理设备驱动程序软件包中的其他文件。 Windows 映像中和在 Windows PE 中，可以使用多个启动关键驱动程序。

当您运行的 Windows PE 时，还可以更新设备驱动程序。 有关详细信息，请参阅[Drvload 命令行选项](drvload-command-line-options.md)。

**使用 Windows PE 工具获取 Windows 评估和部署工具包**

-   安装[Windows 评估和部署工具包 (Windows ADK) 技术参考](http://go.microsoft.com/fwlink/p/?LinkId=526803)，其中包括 Windows PE 功能。

**创建一套 32 位或 64 位的 Windows PE 文件**

1.  单击**开始**，然后键入**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

2.  中的**部署工具和图像管理环境**，Windows PE 文件复制要用来启动的电脑。

    -   64 位版本可以引导 UEFI 64-位和 64 位 BIOS 电脑。

        ``` syntax
        copype amd64 C:\WinPE_amd64
        ```

    -   32 位 （uefi）、 32 位 BIOS 和 64 位 BIOS Pc，可以引导 32 位版本。

        ``` syntax
        copype x86 C:\WinPE_x86
        ```

**装载 Windows PE 启动映像**

-   Windows PE 映像装载。

    ``` syntax
    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

## <a name="span-idaddcustomizationsspanspan-idaddcustomizationsspanspan-idaddcustomizationsspanadd-customizations"></a><span id="Add_customizations"></span><span id="add_customizations"></span><span id="ADD_CUSTOMIZATIONS"></span>添加自定义项


**添加设备驱动程序 （.inf 文件）**

1.  将设备驱动程序添加到 Windows PE 映像。

    ``` syntax
    Dism /Add-Driver /Image:"C:\WinPE_amd64\mount" /Driver:"C:\SampleDriver\driver.inf"
    ```

    **请注意**  
    虽然使用一条命令，可以将多个驱动程序添加到映像中，但是很容易通过单独添加每个驱动程序软件包，解决问题。

     

2.  验证驱动程序软件包是图像的一部分︰

    ``` syntax
    Dism /Get-Drivers /Image:"C:\WinPE_amd64\mount"
    ```

    检查生成的驱动程序列表并验证，该列表包含您添加驱动程序包。

**视频驱动程序︰ 更改显示分辨率**

-   对于大多数的图形驱动程序，WinPE 自动挑选出的最大的原始分辨率。

    若要手动调整大小，请使用答案文件和包含 Microsoft Windows 安装程序的设置 /[显示](https://msdn.microsoft.com/library/windows/hardware/dn915285)。 若要了解详细信息，请参阅[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)。

**卸载 Windows PE 映像并创建媒体**

1.  卸载 Windows PE 映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

2.  创建可引导介质，如 USB 闪存驱动器。

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

3.  引导介质。 Windows PE 将自动启动。 Windows PE 窗口出现后，wpeinit 命令将自动运行。 这可能需要几分钟的时间。 请验证您的自定义。

**故障排除**

1.  无法启动 Windows PE 吗？ 请参见本主题结尾处的故障排除提示︰[安装 Windows PE](http://go.microsoft.com/fwlink/?LinkId=526830)。

2.  在连接到网络上的提示，请参阅[WinPE 网络驱动程序︰ 初始化和添加驱动程序](winpe-network-drivers-initializing-and-adding-drivers.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[WinPE︰ 优化并缩小图像](winpe-optimize.md)

[对于 Windows 10 WinPE](winpe-intro.md)

[安装 Windows PE](http://go.microsoft.com/fwlink/?LinkId=526830)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md)

[在 UEFI 或旧版 BIOS 模式下的 WinPE︰ 引导](winpe-boot-in-uefi-or-legacy-bios-mode.md)

[WinPE︰ 添加软件包 （可选的组件参考）](winpe-add-packages--optional-components-reference.md)

 

 






