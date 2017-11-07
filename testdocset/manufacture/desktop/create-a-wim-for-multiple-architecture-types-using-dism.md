---
author: Justinha
Description: "使用 DISM 的多种体系结构类型创建 WIM"
ms.assetid: fcb1b461-72c1-40c5-8405-38a5db05dd34
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 DISM 的多种体系结构类型创建 WIM"
ms.openlocfilehash: 932c4d8e47e23bd7514c6fc1f7fdc64be571f46a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="create-a-wim-for-multiple-architecture-types-using-dism"></a>使用 DISM 的多种体系结构类型创建 WIM


在计划部署方案时，考虑如何将部署和维护不同体系结构类型的映像。 有几种方法，您可以管理多种体系结构类型的多个 Windows® 图像。 您可以部署从 32 位预安装环境的 32 位和 64 位 Windows 映像，因为可以保持在同一个 Windows 映像 (.wim) 文件或单独的.wim 文件的 32 位和 64 位 Windows 映像。

由于您可以在单个.wim 文件中存储多个 Windows 映像，您可以创建体系结构特定.wim 文件或单个.wim 文件包含多种体系结构类型的映像。

-   32 位的图像

    您可以创建包含单一体系结构类型的 Windows 映像的.wim 文件。 在这种情况下，您可以生成包含仅适用于 32 位系统的一个或多个 Windows 映像的.wim 文件。 创建单独的.wim 文件的不同体系结构类型。

-   64 位的图像

    您可以创建包含一个或多个部署 64 位 Windows 映像的.wim 文件。

-   32 位和 64 位的图像

    您可以创建包含多种体系结构类型的多个 Windows 版本的 a.wim 文件。 例如，可以创建包含两个版本的 Windows，32 位体系结构，64 位体系结构的 Windows 映像。

## <a name="span-idtocreateawindowsimageformultiplearchitecturetypesspanspan-idtocreateawindowsimageformultiplearchitecturetypesspanspan-idtocreateawindowsimageformultiplearchitecturetypesspanto-create-a-windows-image-for-multiple-architecture-types"></a><span id="To_Create_a_Windows_Image_for_Multiple_Architecture_Types"></span><span id="to_create_a_windows_image_for_multiple_architecture_types"></span><span id="TO_CREATE_A_WINDOWS_IMAGE_FOR_MULTIPLE_ARCHITECTURE_TYPES"></span>为多种体系结构类型创建 Windows 映像


您可以创建单个.wim 文件，其中包括 32 位和 64 位的 Windows 图像。 您必须具有 32 位 Windows 分发和 64 位 Install.wim 文件。 （Windows 分发是包括不仅 Install.wim 文件，但其他文件和目录所需的安装 Windows 安装介质上的文件的集合）。仅从 32 位 Windows 安装程序支持跨平台部署。

1.  将整个 32 位 Windows 分发复制到本地计算机上的临时目录。

2.  将 64 位 Install.wim 文件复制到本地计算机上的一个单独的临时目录。

3.  在命令提示符下，使用**Dism**命令导出到 Windows 通讯组中的 Install.wim 文件的 64 位的 Windows 图像。

4.  对于每个要添加到 Windows 分发的 64 位 Windows 映像中重复**Dism /Export-Image**命令。

例如，如果您将通讯组复制到 c:\\WindowsDistribution 和 64 位 Install.wim 文件到 c:\\Windows64 位，您将在命令提示符下使用以下。

``` syntax
Dism /Export-Image /SourceImageFile:c:\windows64-bit\install.wim /SourceIndex:1 /DestinationImageFile:c:\windowsdistribution\sources\install.wim /DestinationName:"Fabrikam 64-bit Image"
```

**请注意**  
务必要添加的 Windows 映像，以指示它是 64 位的计算机的名称。

 

64 位 Windows 映像和随附的所有元数据复制到 Install.wim 文件到一个新的索引，在导出过程。 所有 Windows 映像添加到 Install.wim 文件后，就可以在您的环境中使用 Windows 分发。

在有人参与的安装过程将提示用户选择要安装 （x86 或 x64 映像） 的特定于体系结构的 Windows 映像。

在无人参与安装中，如果将多种体系结构类型的多个 Windows 版本存储在单个.wim 文件中，则必须显式指定要 Windows 安装过程中安装的映像`MetaData`设置。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






