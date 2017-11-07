---
author: Justinha
Description: "配置 Windows 修复源"
ms.assetid: 00c879d8-5c56-4e96-9c44-df0c2fc4371d
MSHAttr: PreferredLib:/library/windows/hardware
title: "配置 Windows 修复源"
ms.openlocfilehash: 2a463563e4e38a03b3d34b86216846393422db19
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-a-windows-repair-source"></a>配置 Windows 修复源


您可以使用组策略指定要在您的网络内使用 Windows 映像修复源。 若要还原 Windows 功能或修复损坏的 Windows 映像，则可以使用修复源。

即需即装功能使您能够从 Windows® 图像中删除一项可选功能，然后在以后恢复。 您可以禁用可选功能并删除文件与 Windows 映像使用部署映像服务和管理 (DISM) 工具中的那些功能。 当您**使用/删除**参数使用 DISM **/Disable-Feature**选项、 清单文件服务器角色的功能保留在图像中。 但是，会删除所有其他文件的功能。 这使您可以存储、 下载和部署较小的图像，而不会丢失功能。 一旦部署了该图像，用户通过使用即需即装功能修复从源检索所需的文件可以在其计算机上的功能任何时候启用。 有关详细信息，请参阅[启用或禁用 Windows 功能使用 DISM](enable-or-disable-windows-features-using-dism.md)。

自动损坏修复提供修复 Windows 操作系统已损坏的文件。 用户还可以使用网络上的指定的修复源或使用 Windows Update 来检索所需，若要启用某项功能或修复 Windows 映像的源文件。 有关详细信息，请参阅[修复 Windows 映像](repair-a-windows-image.md)。

在此部分中︰

-   [选择修复源](#bkmk-specify)

-   [设置组策略](#bkmk-setgpo)

-   [维护维修源](#bkmk-maintain)

## <a name="span-idbkmkspecifyspanspan-idbkmkspecifyspanspan-idbkmkspecifyspanchoose-a-repair-source"></a><span id="BKMK_Specify"></span><span id="bkmk_specify"></span><span id="BKMK_SPECIFY"></span>选择修复源


可以使用 Windows Update 提供还原 Windows 功能或修复损坏的操作系统所需的文件。 您还可以配置组策略以收集所需的文件，从网络位置。 可以在组策略中指定多个源位置。

**若要使用 Windows 更新以恢复可选功能和修复 Windows 映像**

1.  如果允许在计算机上的策略设置，将默认使用 Windows 更新。

2.  如果您想要使用 Windows 更新作为主要或后备源用于恢复可选功能或修复 Windows 映像的文件，应确保您的防火墙配置为允许访问 Windows 更新。

**若要使用的网络位置还原可选功能并修复 Windows 映像**

1.  可用于安装的 Windows 映像的 WIM 文件中作为源恢复可选功能和修复已损坏的操作系统。 例如，c:\\测试\\装载\\窗口。 有关捕获 WIM 文件的 Windows 映像的详细信息，请参阅[捕获映像的硬盘分区使用 DISM](capture-images-of-hard-disk-partitions-using-dism.md)。

2.  可以使用运行 Windows 安装作为源来还原可选功能共享 c:\\网络上的 Windows 文件夹。

3.  Windows 通过并行文件夹从一个网络共享或可移动媒体，如 Windows DVD，可用作源的文件。 例如，z:\\源\\SxS。

4.  可以作为源使用网络共享上的 Windows 映像 (.wim) 文件还原的可选功能。 必须要使用，您必须使用.wim 文件中指定的 Windows 映像的索引`Wim:`前缀来标识此文件格式的路径中。 例如，在名为 contoso.wim 的文件中指定索引 3，请键入︰ Wim:\\\\网络\\图像\\contoso.wim:3。

## <a name="span-idbkmksetgpospanspan-idbkmksetgpospanspan-idbkmksetgpospanset-group-policy"></a><span id="BKMK_SetGPO"></span><span id="bkmk_setgpo"></span><span id="BKMK_SETGPO"></span>设置组策略


您可以使用组策略来指定何时使用 Windows Update 或网络位置作为修复源需求和损坏自动修复的功能。

**根据需要配置组策略的功能**

1.  打开组策略编辑器。 例如，在计算机上运行 Windows 10，从**开始**屏幕，键入**编辑组策略**，然后选择要打开组策略编辑器的**编辑组策略**。

2.  单击**计算机配置****管理模板**单击**系统**和，然后双击**指定设置为可选组件的安装和维修组件**设置。

3.  选择您想要使用的即需即装功能的设置。

## <a name="span-idbkmkmaintainspanspan-idbkmkmaintainspanspan-idbkmkmaintainspanmaintaining-a-repair-source"></a><span id="BKMK_Maintain"></span><span id="bkmk_maintain"></span><span id="BKMK_MAINTAIN"></span>维护维修源


如果您不使用 Windows 更新为功能要求和自动损坏的修复源修复，应考虑以下原则进行维护修复源。

### <a name="span-idservicingupdatesspanspan-idservicingupdatesspanspan-idservicingupdatesspanservicing-updates"></a><span id="Servicing_updates"></span><span id="servicing_updates"></span><span id="SERVICING_UPDATES"></span>服务更新

应保留当前的最新服务更新修复的任何源。 如果使用即需即装功能的 WIM 文件中的图像，则可以使用 DISM 工具映像提供服务。 有关详细信息，请参阅[安装和修改 Windows 映像使用 DISM](mount-and-modify-a-windows-image-using-dism.md)。 如果您使用的在线修复图像将本地网络上共享的 Windows 安装，应确保计算机有权访问 Windows 更新。

### <a name="span-idmultilingualimagesspanspan-idmultilingualimagesspanspan-idmultilingualimagesspanmultilingual-images"></a><span id="Multilingual_images"></span><span id="multilingual_images"></span><span id="MULTILINGUAL_IMAGES"></span>多语言映像

必须将所有相关的语言包包括修复源代码文件映像支持的区域设置。 如果您尝试恢复而不需要该功能的 Windows 安装的本地化组件的所有功能，则安装将失败。

还原功能后，您可以安装其他语言包。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[启用或禁用使用 DISM 的 Windows 功能](enable-or-disable-windows-features-using-dism.md)

[修复 Windows 映像](repair-a-windows-image.md)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

 

 






