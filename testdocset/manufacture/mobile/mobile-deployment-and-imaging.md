---
Description: "10 Windows Mobile 将移动设备与 Windows 10 中可用的功能。"
ms.assetid: 8ee995d9-420d-4bba-9ab0-decf4b3dc39b
MSHAttr: PreferredLib:/library
title: "移动部署和图像处理"
author: CelesteDG
ms.openlocfilehash: 59eab072c3b7fc19a5a6434f23b3d09d658a9e86
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-deployment-and-imaging"></a>移动部署和图像处理


10 Windows Mobile 将移动设备与 Windows 10 中可用的功能。 此外，在满足所需的硬件组件的设备，Windows 10 移动还增加统一体; 电话，从而允许用户将其 Windows phone 连接到监视器，并且即使与鼠标和键盘，使像一个桌面电话等功能。

## <a name="span-idintendedaudiencespanspan-idintendedaudiencespanspan-idintendedaudiencespanintended-audience"></a><span id="Intended_audience"></span><span id="intended_audience"></span><span id="INTENDED_AUDIENCE"></span>目标的读者


完整的或部分，本演练旨在以供使用︰

-   新的或有经验 Windows Oem 和 Odm，那些想要构建和部署自定义的 Windows 10 移动图像。

-   想要了解流程的构建和部署自定义移动图像的移动操作员。

## <a name="span-idoverviewspanspan-idoverviewspanspan-idoverviewspanoverview"></a><span id="Overview"></span><span id="overview"></span><span id="OVERVIEW"></span>概述


此移动部署和成像指南的结构基础上的两种方式，您可以自定义、 生成和闪烁到移动设备的 Windows 映像︰

**第 1 步︰**[准备用于 Windows 移动开发](preparing-for-windows-mobile-development.md)提供 preprequisites，有关的信息工具，以及如何设置您的开发环境。

**第 2 步︰**[创建移动包](creating-mobile-packages.md)提供了有关如何使用创建一个移动包示例驱动程序的分步信息以及何时使用 MCSF 设置架构中的声明的 MCSF 设置。 pkg.xml。

**第 3 步︰**[配置开始布局](configure-the-start-layout.md)显示如何自定义包括 Web 链接、 辅助磁贴、 文件夹等移动设备上的开始布局。 开始布局在胜利中使用新的统一的架构\_阈值，因此，如果正在使用启动 MCSF 设置或启动 Windows 配置设置添加到图像的布局并不重要。 此外请注意在移动设备上的默认布局只能作为成像过程的一部分进行自定义。

**步骤 4:**完成所有的准备步骤后，您就可以开始自定义和构建映像。 我们建议首先学习经典移动部署过程，因为 MCSF 仍然提供了一套更为可靠的 Oem 和 Odm 可以为其映像配置的自定义设置。 但是，Windows 资源调配提供了很多企业策略、 注册和企业设置不能通过 MCSF 提供因此建议成为太熟悉 Windows 资源调配部署过程。

-   [第 1 部分︰ 经典移动部署](lab-1--classic-mobile-deployment.md)

    配置自定义项只能通过管理集中设置框架 (MCSF)，使用传统的 Windows 移动命令行工具生成软件包和一个自定义的图像，然后闪存设备的图像。

-   [第 2 部分︰ 使用 Windows 资源调配的移动部署](lab-2--mobile-deployment-using-windows-provisioning.md)

    使用 Windows 资源调配应答文件 (WPAF) 来配置仅有通过 Windows 提供的框架的自定义设置。 使用 WPAF MCSF 咖啡馆作为 Windows 图像处理和配置设计器 (ICD) 的命令行界面的输入来生成自定义移动图像。

 

 



