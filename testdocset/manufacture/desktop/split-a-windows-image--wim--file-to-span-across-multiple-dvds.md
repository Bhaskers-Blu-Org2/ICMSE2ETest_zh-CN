---
author: Justinha
Description: "将 Windows 映像文件 (.wim) 若要跨越多个 Dvd 拆分"
ms.assetid: 3861fd65-4c2b-4955-a0af-233e0bbce454
MSHAttr: PreferredLib:/library/windows/hardware
title: "将 Windows 映像文件 (.wim) 若要跨越多个 Dvd 拆分"
ms.openlocfilehash: 1c9f206fdcf6e8e7928da9c79b4c4795aaa50403
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="split-a-windows-image-file-wim-to-span-across-multiple-dvds"></a>将 Windows 映像文件 (.wim) 若要跨越多个 Dvd 拆分


拆分的.wim 文件的.swm 文件到 Dvd 或 FAT32 文件系统。 当拆分.swm 文件不适合单个的媒体，如这种情况下，请使用此步骤︰

-   部署 Windows 使用 Dvd。 （标准的单面 DVD 存储 4.7 GB）。
-   部署 Windows 映像的 Windows PE usb 闪存盘。 （标准的 Windows PE 安装使用 FAT32 文件系统的最大文件大小为 4 GB）。有关详细信息，请参阅[WinPE︰ 存储或拆分映像来部署 Windows 使用一个 USB 密钥](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim.md)。

注︰ 拆分 Wim DISM /Apply-Image 支持，但不是支持 Windows 安装程序的 Windows 10 版本中。

文件被拆分后，您可以将它们复制到单独的 Dvd 或 USB 密钥。

请注意，您可以应用映像之前，必须首先放置时拆分文件的所有同一文件夹中，例如，通过将它们复制到目标计算机上的临时文件夹。 然后使用 DISM 应用该映像，而指定拆分.swm 文件的位置和文件名模式。 DISM 不支持应用单独的文件夹或 Dvd 的文件。

默认情况下，此选项创建新的拆分.wim 文件具有.swm 扩展名。 第一个文件的名称基于指定的文件名，以下每个文件后收到很多。 例如，当拆分"Install.wim"，默认文件名是"Install.swm"、"Install2.swm"、"Install3.swm"等。

**重要**  
-   Windows 安装程序不支持从拆分.swm 文件安装为 Windows 10。
-   您不能修改拆分的.swm 文件。

 

## <a name="span-idscenariodeploywindowsusingdvdsspanspan-idscenariodeploywindowsusingdvdsspanspan-idscenariodeploywindowsusingdvdsspanscenario-deploy-windows-using-dvds"></a><span id="Scenario__Deploy_Windows_using_DVDs"></span><span id="scenario__deploy_windows_using_dvds"></span><span id="SCENARIO__DEPLOY_WINDOWS_USING_DVDS"></span>方案︰ 部署 Windows 使用 Dvd


1.  在技术人员计算机，打开**部署和图像处理工具环境**作为管理员。
2.  拆分窗口的图像︰

    ``` syntax
    Dism /Split-Image /ImageFile:C:\images\install.wim /SWMFile:C:\images\install.swm /FileSize:4700
    ```

    其中：

    -   `C:\images\install.wim`是的名称以及要分割的图像文件的位置。

    -   `C:\images\install.swm`是目标名称和拆分.swm 文件的位置。

    -   `4700`为每个要创建拆分.swm 文件以 mb 为单位的最大大小。

    在此示例中，*拆分*选项创建 install.swm 文件、 install2.swm、 install3.swm 文件以及等等，在 c:\\图像目录。

3.  将文件复制到单独的 Dvd。 例如，插入第一张 DVD 和类型︰
    ```
    copy C:\images\install.swm D:\*
    ```

    然后插入第二个 DVD 和类型︰
    ```
    copy C:\images\install2.swm D:\*
    ```

    依次类推，直到.swm 的所有文件都复制到 Dvd。
4.  启动 Windows 预安装环境 (WinPE) 到目标计算机。 有关详细信息，请参阅[WinPE︰ 创建启动 CD、 DVD、 ISO 或 VHD](winpe-create-a-boot-cd-dvd-iso-or-vhd.md)。
5.  配置和设置格式的硬盘分区，[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)中所示。
6.  将文件复制到一个临时文件夹中。 例如，插入第一张 DVD 和类型︰
    ```
    md C:\temp
    copy d:\install.swm c:\TempDVDFolder\*
    ```

    然后插入第二个 DVD 和类型︰
    ```
    copy d:\install2.swm c:\TempDVDFolder\*
    ```

    等等，直到所有的.swm 文件被复制。
7.  应用图像使用 DISM /Apply-image /swmfile 选项︰
    ```
    Dism /apply-image /imagefile:c:\temp\install.swm /swmfile:c:\temp\install*.swm /index:1 /applydir:D:\
    ```

8.  删除临时文件夹︰
    ```
    rd c:\TempDVDFolder /s /q
    ```

9.  设置系统和恢复分区[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)中所示。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)

[WinPE: WinPE 和 WIM 文件 (.wim) 使用一个 USB 密钥](winpe--use-a-single-usb-key-for-winpe-and-a-wim-file---wim.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

 

 






