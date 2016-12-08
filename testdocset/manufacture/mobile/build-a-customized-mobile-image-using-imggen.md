---
Description: "可以使用两种不同的工具来构建在 Windows 10 中的自定义移动图像 （FFU 图像）︰"
ms.assetid: c29e417c-90a5-4928-b416-aa940efe68ab
MSHAttr: PreferredLib:/library
title: "生成使用 ImgGen 的移动图像"
author: CelesteDG
ms.openlocfilehash: f16f5946e392fa4074396ce46603a2b74c1a7046
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="build-a-mobile-image-using-imggen"></a>生成使用 ImgGen 的移动图像


可以使用两种不同的工具来构建在 Windows 10 中的自定义移动图像 （FFU 图像）︰

-   使用 ImgGen.cmd，即运行传统的图像处理工具 ImageApp.exe 的命令文件。 此工具也是用早期版本的 Windows 10 移动包括 Windows Phone 8.1 和各种 Gdr。

-   使用 Windows 图像处理和配置设计器 (ICD) 的命令行界面，即新的 Windows 10。

在本演练中，我们将介绍如何使用 ImgGen.cmd 来生成自定义移动图像。 在另一个演练中，我们将讨论如何创建另一个包含自定义设置，我们做为止只能通过 Windows 资源调配通过使用其他自定义设置以及使用 Windows ICD CLI 的移动图像。

**若要生成使用 ImgGen 的自定义的映像**

1.  以管理员身份打开**开发人员为 VS2015 的命令提示符**窗口。

2.  如果您运行的 Windows 8.1，完成以下步骤，将注册表 USN 日志的大小为 1 Mb 您的开发计算机上。 否则，请跳到下一步。

    1.  通过运行以下命令来更改 USN 的最小大小注册表项︰

        **reg 添加 HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\文件系统 /v NtfsAllowUsnMinSize1Mb /t REG\_DWORD /d 1**

    2.  重新启动然后再继续下一步的 PC。

3.  通过使用下面的命令运行 ImgGen.cmd。

    **ImgGen***TestFlash.ffuContosoTestOEMInput.xml* **"%WPDKCONTENTROOT%\\MSPackages"** *MobileCustomizations.xml 地址为 10.0.0.1*

    此命令将生成图像，将调用 TestFlash.ffu。

    **请注意** 此命令假定您已经经历了本节中的演练的其余部分。 对于 ImgGen.cmd 的命令行语法的详细信息，请参阅使用*ImgGen.cmd 生成图像*中[生成使用 ImgGen.cmd 的移动图像](https://msdn.microsoft.com/library/windows/hardware/dn756630)。

     

一旦生成图像，您将需要对其进行签名，以便它可以刷新到移动设备。

 

 



