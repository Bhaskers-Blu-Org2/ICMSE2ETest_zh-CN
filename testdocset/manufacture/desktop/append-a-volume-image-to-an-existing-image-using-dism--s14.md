---
author: Justinha
Description: "将卷映像附加到现有图像使用 DISM"
ms.assetid: c537f8bb-05ed-48cd-b75a-a8c1ed3bc66f
MSHAttr: PreferredLib:/library/windows/hardware
title: "将卷映像附加到现有图像使用 DISM"
ms.openlocfilehash: ec7d721ff9a14d5a75c888ec60c5d53012fc6dbc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="append-a-volume-image-to-an-existing-image-using-dism"></a>将卷映像附加到现有图像使用 DISM


部署映像服务和管理 (DISM) 工具是一个命令行工具，它能够创建的 Windows® 在制造业或企业 IT 环境中部署的映像 (.wim) 文件。 **/Append-Image**选项将卷映像附加到现有.wim 文件使您可以将多个自定义的 Windows 映像存储在空间的一小部分。 当您在单个.wim 中组合两个或多个 Windows 图像文件时，复制图像之间的所有文件都仅都存储一次。

## <a name="span-idmultiplewindowsimagesinawimfilespanspan-idmultiplewindowsimagesinawimfilespanmultiple-windows-images-in-a-wim-file"></a><span id="multiple_windows_images_in_a_.wim_file"></span><span id="MULTIPLE_WINDOWS_IMAGES_IN_A_.WIM_FILE"></span>.Wim 文件中的多个 Windows 映像


可以将数据追加到图像之前，您必须具有以下︰

-   技术人员计算机使用 Windows 评估和部署工具包 (Windows ADK) 工具安装在其上运行 Windows 8 或技术人员计算机。

-   Windows 映像 (.wim) 文件。 有关如何捕获映像使用 DISM 的详细信息，请参阅[捕获映像的硬盘分区使用 DISM](capture-images-of-hard-disk-partitions-using-dism.md)。

**若要向现有映像附加卷映像**

1.  使用管理员权限打开命令提示符。 如果使用非 Windows 8 的 Windows 的版本，则导航到 DISM 目录。

2.  向现有映像附加卷映像。 例如，您可以附加现有图像称为我 windows partition.wim D 驱动器的映像。

    ``` syntax
    Dism /Append-Image /ImageFile:c:\my-windows-partition.wim /CaptureDir:D:\ /Name:Drive-D
    ```

**下一步行动**

1.  可以将映像应用由指称它的图像或图像名称，例如︰

    ``` syntax
    Dism /apply-image /imagefile:install.wim /name:Drive-D /ApplyDir:D:\
    ```

2.  可以使用**/Export-Image**选项到单独的文件中提取图像。 例如︰

    ``` syntax
    Dism /Export-Image /SourceImageFile:install.wim /SourceName:Drive-D /DestinationImageFile:DriveD.wim
    ```

有关详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[捕获硬盘分区使用 DISM 的图像](capture-images-of-hard-disk-partitions-using-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

 

 






