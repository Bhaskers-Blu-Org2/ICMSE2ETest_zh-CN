---
author: KPacquer
Description: "WinPE︰ 存储或拆分映像来部署 Windows 使用一个 USB 密钥"
ms.assetid: 66036c4e-f64c-4175-b4fe-15e4cc1fc600
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 存储或拆分映像来部署 Windows 使用一个 USB 密钥"
ms.openlocfilehash: a747d21c165e29690af81b500afc36848a282e0d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-store-or-split-images-to-deploy-windows-using-a-single-usb-key"></a>WinPE︰ 存储或拆分映像来部署 Windows 使用一个 USB 密钥

如何可以将部署 Windows 于个人电脑与只有一个 USB 端口？

使用默认 Windows 预安装环境 (WinPE) 驱动器格式，FAT32 引导基于 UEFI 的计算机，但这也太小，无法存储大多数 Windows 映像︰

-   FAT32 具有最大文件大小为 4 GB 的大小。 大多数自定义的 Windows 映像是超过 4 GB。
-   FAT32 有 32 GB 的最大分区大小。 某些 Windows 映像是大于 32 GB。

    (您仍可以使用 64 GB 或 128gb 的容量的 usb 闪存盘，但对它进行格式设置，您需要使用仅使用其空间的 32GB。)

这里有几种方式可以避免这些限制︰

## <a name="span-idoption1storetheimageonaseparateusbdrivespanspan-idoption1storetheimageonaseparateusbdrivespanspan-idoption1storetheimageonaseparateusbdrivespanoption-1-store-the-image-on-a-separate-usb-drive"></a><span id="Option_1__Store_the_image_on_a_separate_USB_drive"></span><span id="option_1__store_the_image_on_a_separate_usb_drive"></span><span id="OPTION_1__STORE_THE_IMAGE_ON_A_SEPARATE_USB_DRIVE"></span>选项 1︰ 将图像存储在单独的 USB 驱动器


即使您的计算机只有一个 USB 端口，您仍可以部署 Windows 使用两个单独的 USB 密钥。

1.  引导至 WinPE。
2.  删除 WinPE 驱动器。 （引导后, WinPE 运行在内存中。
3.  插入您的图像与一个单独的存储驱动器并将其应用到设备。

## <a name="span-idoption2storetheimageonanetworklocationspanspan-idoption2storetheimageonanetworklocationspanspan-idoption2storetheimageonanetworklocationspanoption-2-store-the-image-on-a-network-location"></a><span id="Option_2__Store_the_image_on_a_network_location"></span><span id="option_2__store_the_image_on_a_network_location"></span><span id="OPTION_2__STORE_THE_IMAGE_ON_A_NETWORK_LOCATION"></span>选项 2︰ 将映像存储到网络上


1.  例如，将图像复制到您的网络上的服务器\\\\服务器\\共享\\install.wim

2.  引导至 WinPE。

3.  连接网络驱动器的驱动器号，例如，n。

    ``` syntax
    net use N: \\server\share
    ```

4.  将映像从网络中应用。
    ```
    Dism /apply-image /imagefile:N:\install.wim /index:1 /applydir:D:\
    ```

## <a name="span-idoption3splittheimagespanspan-idoption3splittheimagespanspan-idoption3splittheimagespanoption-3-split-the-image"></a><span id="Option_3__Split_the_image"></span><span id="option_3__split_the_image"></span><span id="OPTION_3__SPLIT_THE_IMAGE"></span>选项 3︰ 拆分映像


**限制︰**

-   Windows 安装程序不支持从拆分.wim 文件安装为 Windows 10.您不能修改拆分.wim 文件。
-   您不能修改拆分.wim 文件。
-   若要使用密钥为 64 GB 或 128gb 的容量，将其格式化只用 32 GB 的空间。
-   对于图像大于 32 GB，则需要第二个 usb 闪存盘仍因为 FAT32 分区大小限制。

1.  从技术人员计算机，创建 WinPE 密钥。 请参阅[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)。

2.  以管理员身份打开**部署和图像处理工具环境**。

3.  拆分成文件的 Windows 映像小于 4 GB:

    ``` syntax
    Dism /Split-Image /ImageFile:C:\install.wim /SWMFile:C:\images\install.swm /FileSize:4000
    ```

    其中：

    -   `C:\images\install.wim`是的名称以及要分割的图像文件的位置。

    -   `D:\images\install.swm`是目标名称和拆分.wim 文件的位置。

    -   `4000`是以 mb 为单位为每个要创建拆分.wim 文件的最大大小。

    在此示例中，*拆分*选项创建 install.swm 文件、 install2.swm、 install3.swm 文件以及等等，d:，在\\的图像目录。

4.  将文件复制到 WinPE 键。

5.  在目标计算机上，启动 WinPE，，然后再使用 DISM /Apply-Image /SWMFile 命令的图像。
    ```
    Dism /apply-image /imagefile:install.swm /swmfile:install*.swm /index:1 /applydir:D:\
    ```

## <a name="span-idcreateamultiplepartitionusbdrivespanoption-4-create-a-multiple-partition-usb-drive-windows-to-go-or-other-storage-drive"></a><span id="Create_a_multiple_partition_USB_drive"></span>第 4 种选择︰ 创建多个分区 USB 驱动器 （转到 Windows 或其他存储驱动器）

最闪存驱动器报告本身作为可移动驱动器，但在 USB 驱动器是驱动器上创建多个分区必须将自身报告为固定 （不可移动） 驱动器。 如果您有权访问[Windows 转 (WTG) 认证的驱动器](http://technet.microsoft.com/library/hh831833.aspx)您可以使用它，因为 WTG 驱动器报告为固定。 某些 USB 外置硬盘还报告其自身为固定。

**请验证该驱动器报告本身作为固定或可移动**

1.  插入驱动器中。
2.  用鼠标右键单击开始，选择**磁盘管理**。
3.  在屏幕底部的左窗格中，将说**基本**而不是**可移动**的驱动器。

**创建带有多个分区的驱动器**

1.  以管理员身份启动**部署和图像处理工具环境**。

2.  键入**diskpart** ，然后按 enter 键。

3.  使用 Diskpart WinPE 和图像创建两个新的分区并重新格式化驱动器︰

    ``` syntax
    List disk
    select disk X    (where X is your USB drive)
    clean
    create partition primary size=2048
    active
    format fs=FAT32 quick label="WinPE"
    assign letter=P
    create partition primary
    format fs=NTFS quick label="Images"
    assign letter=I  
    Exit
    ```

4.  将包含 WinPE 文件复制到 WinPE 分区︰

    ``` syntax
    copype amd64 C:\WinPE_amd64
    xcopy C:\WinPE_amd64\media P:\ /s
    ```

5.  将 Windows 映像文件复制到映像分区︰

    ``` syntax
    xcopy C:\Images\install.wim I:\install.wim
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[WinPE︰ 使用脚本确定驱动器号](winpe-identify-drive-letters.md)

[将 Windows 映像文件 (.wim) 拆分为 FAT32 介质或跨越多个 Dvd](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)