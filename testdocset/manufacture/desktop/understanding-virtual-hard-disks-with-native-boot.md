---
author: Justinha
Description: "了解具有本机引导的虚拟硬盘"
ms.assetid: e063e475-6f39-4ed9-9473-ea7537adc30a
MSHAttr: PreferredLib:/library/windows/hardware
title: "了解具有本机引导的虚拟硬盘"
ms.openlocfilehash: bed073d5696d45f11a9dbf1cd60923501e06c5c3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="understanding-virtual-hard-disks-with-native-boot"></a>了解具有本机引导的虚拟硬盘


本机的引导，使虚拟硬盘 (Vhd) 在没有虚拟机或*虚拟机管理程序*的计算机上运行。 虚拟机监控程序是软件的在运行虚拟机的操作系统层。

## <a name="span-idbkmkwhatisvhdspanspan-idbkmkwhatisvhdspanspan-idbkmkwhatisvhdspanwhat-is-vhd-with-native-boot"></a><span id="BKMK_whatIsVHD"></span><span id="bkmk_whatisvhd"></span><span id="BKMK_WHATISVHD"></span>具有本机引导的 VHD 是什么？


虚拟硬盘可以用作指定硬件而无需任何其他父操作系统、 虚拟机或虚拟机监控程序上运行的操作系统。 可以使用 Windows 磁盘管理工具，DiskPart 工具和磁盘管理 Microsoft® 管理控制台 (Diskmgmt.msc) 创建一个 VHD 文件。 受支持的 Windows 映像 (.wim) 文件可以应用到 VHD，并且 VHD 可以复制到多个系统。 可以配置 Windows 启动管理器启动直接到 VHD。

VHD 还可以连接到虚拟机以用于 Windows 服务器中的 Hyper-V 角色。

本机引导 Vhd 不设计或来取代完整映像部署到所有客户端或服务器系统上。 已管理和使用的虚拟机部署.vhd 文件的企业环境将从本机引导 VHD 功能获得最大益处。 虚拟机和指定的硬件作为一种通用的图像容器格式使用.vhd 文件简化映像管理和企业环境中的部署。

在 Windows 中的虚拟化有关的详细信息，请参阅[此 Microsoft Web 站点](http://go.microsoft.com/fwlink/?LinkId=142055)。 有关如何使用具有本机引导的 Vhd 的详细信息，请参阅[此 Microsoft Web 站点](http://go.microsoft.com/fwlink/?LinkId=142054)。

## <a name="span-idbkmkcommonscenariosspanspan-idbkmkcommonscenariosspanspan-idbkmkcommonscenariosspancommon-scenarios"></a><span id="BKMK_commonScenarios"></span><span id="bkmk_commonscenarios"></span><span id="BKMK_COMMONSCENARIOS"></span>常见方案


具有本机引导的 Vhd 经常用于以下情况︰

-   使用磁盘管理工具来创建并*附加*VHD 脱机映像管理。 您可以通过使用**附加的虚拟磁盘**命令将激活 VHD，以使其显示为磁盘驱动器，而不是作为.vhd 文件的主机上附加 VHD。

-   在进行图像处理的远程共享文件夹上装载参考 VHD 映像。

-   维护和部署在虚拟或物理计算机中执行公共参考 VHD 映像。

-   而无需完整父安装配置本机引导的 VHD 文件。

-   计算机配置为启动多个本地 VHD 文件包含不同的应用程序工作负载，而不需要单独的磁盘分区。

-   网络部署到目标计算机的本机引导的 VHD 映像，使用 Windows 部署服务 (WDS)。

-   管理桌面映像部署。

## <a name="span-idbkmkrequirementsspanspan-idbkmkrequirementsspanspan-idbkmkrequirementsspanrequirements"></a><span id="BKMK_requirements"></span><span id="bkmk_requirements"></span><span id="BKMK_REQUIREMENTS"></span>要求


本机 VHD 引导具有以下依存关系︰

-   本地磁盘上必须至少两个分区︰ 包含 Windows 8 的引导环境文件和引导配置数据 (BCD) 存储系统分区和分区来存储 VHD 文件。 为与 Windows® 7 引导环境时，计算机上的本机引导支持.vhd 文件格式但必须更新到 Windows 8 环境中使用的.vhdx 文件格式的系统分区。 有关如何添加用于本机 VHD 引导 Windows 8 的引导环境的详细信息，请参阅[下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md)。

-   包含 VHD 文件的本地磁盘分区必须具有足够的磁盘空间用于将动态 VHD 扩展到其最大大小和创建引导 VHD 时的页面文件。 创建页面文件超出该 VHD 文件，与不同与页面文件位于 VHD 的虚拟机。

## <a name="span-idbkmkbenefitsspanspan-idbkmkbenefitsspanspan-idbkmkbenefitsspanbenefits"></a><span id="BKMK_benefits"></span><span id="bkmk_benefits"></span><span id="BKMK_BENEFITS"></span>优点


Vhd 的本机引导功能的好处包括︰

-   使用相同的映像管理工具创建、 部署和维护的系统映像以在指定硬件或虚拟机上安装。

-   部署的虚拟机或指定的计算机，具体取决于容量规划和可用性上的图像。

-   对于多个引导方案部署 Windows，而不需要单独的磁盘分区。

-   部署支持更快的可重用的开发和测试环境的部署 VHD 容器文件中的 Windows 映像。

-   替换为服务器重新部署或恢复 VHD 映像。

## <a name="span-idbkmklimitationsspanspan-idbkmklimitationsspanspan-idbkmklimitationsspanlimitations"></a><span id="BKMK_limitations"></span><span id="bkmk_limitations"></span><span id="BKMK_LIMITATIONS"></span>限制


本机 VHD 支持具有以下限制︰

-   本机 VHD 磁盘管理支持可以同时附加约 512 的 VHD 文件。

-   本机 VHD 引导不支持休眠状态的系统，虽然支持睡眠模式。

-   不能嵌套 VHD 文件。

-   通过服务器消息块 (SMB) 共享不支持本机 VHD 引导。

-   Windows BitLocker 驱动器加密，也不能用于加密主机卷包含 VHD 文件用于本机 VHD 引导，并且不能包含在 VHD 的卷上使用 BitLocker。

-   VHD 文件的父分区不能是卷快照的一部分。

-   附加的 VHD 不能配置为*动态磁盘*。 动态磁盘提供基本磁盘不能，例如创建卷跨越多个磁盘 （跨区卷和带区卷） 的能力以及创建容错卷 （镜像卷和 raid-5 卷） 的能力的功能。 在动态磁盘上的所有卷都称为动态卷。

-   VHD 的父卷不能配置为动态磁盘。

## <a name="span-idbkmkrecommendationsspanspan-idbkmkrecommendationsspanspan-idbkmkrecommendationsspanrecommended-precautions"></a><span id="BKMK_recommendations"></span><span id="bkmk_recommendations"></span><span id="BKMK_RECOMMENDATIONS"></span>推荐的预防措施


以下建议使用具有本机引导的 Vhd 的预防措施︰

-   使用固定 VHD 磁盘类型对于生产服务器，从而提高性能并有助于保护用户数据。 使用动态或差异 VHD 磁盘类型仅在非生产环境中，例如用于开发和测试。

-   当使用动态 Vhd，已超出了该 VHD 文件，如果可能的磁盘分区上存储关键的应用程序或用户数据。 这将减少 VHD 的大小要求。 它还使容易恢复 VHD 映像不再可用由于停电等灾难性系统关闭应用程序或用户数据。

## <a name="span-idbkmktypesofvhdsspanspan-idbkmktypesofvhdsspanspan-idbkmktypesofvhdsspantypes-of-virtual-hard-disks"></a><span id="BKMK_typesOfVHDs"></span><span id="bkmk_typesofvhds"></span><span id="BKMK_TYPESOFVHDS"></span>虚拟硬盘的类型


通过使用磁盘管理工具，可以创建三种类型的 VHD 文件︰

-   **固定的硬盘映像。** 固定的硬盘映像是一个分配给虚拟磁盘的大小的文件。 例如，如果您创建虚拟硬盘的 2 千兆字节 (GB) 的大小，系统将创建主机文件大约 2 GB 容量。 推荐固定的硬盘映像用于生产服务器和处理客户数据。

-   **动态硬盘映像。** 动态硬盘映像是一个文件，向其中写入在任意给定时间的实际数据一样大。 写入更多数据时的大小动态地增加该文件。 例如，支持 2 GB 虚拟硬盘文件的大小是最初约 2 兆字节 (MB) 在主机文件系统上。 随着数据写入此图像时，它可以随着最大为 2 GB。

    动态硬盘映像被建议用于开发和测试环境。 动态 VHD 文件较小、 易于复制和装载后将扩展。

-   **差异硬盘映像。** 差异硬盘映像描述父映像的修改。 这种类型的硬盘映像不是独立的;它取决于另一个硬盘映像才能完全正常工作。 父硬盘映像可以是任何提到的硬盘映像类型，包括另一差异硬盘映像。

## <a name="span-idbkmktechnologiesspanspan-idbkmktechnologiesspanspan-idbkmktechnologiesspantechnologies-related-to-vhds-with-native-boot"></a><span id="BKMK_technologies"></span><span id="bkmk_technologies"></span><span id="BKMK_TECHNOLOGIES"></span>具有本机引导的 Vhd 相关技术


具有本机引导的 Vhd 通常使用以下技术︰

### <a name="span-idbcdbootspanspan-idbcdbootspanspan-idbcdbootspanbcdboot"></a><span id="BCDboot"></span><span id="bcdboot"></span><span id="BCDBOOT"></span>BCDboot

BCDboot 工具用于初始化 BCD 存储并在映像部署期间将引导环境文件复制到系统分区。 BCD 文件描述引导应用程序和引导应用程序设置。 对象和存储区中的元素有效替代 Boot.ini 文件。 当指定硬件上安装本机引导 VHD，您可能需要更新到 Windows 8 BCD 存储。 BCDboot 工具有关的详细信息，请参阅[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)。

### <a name="span-idbcdeditspanspan-idbcdeditspanspan-idbcdeditspanbcdedit"></a><span id="BCDedit"></span><span id="bcdedit"></span><span id="BCDEDIT"></span>BCDedit

BCDedit 是用于管理 BCD 存储的命令行工具。 它可以用于各种目的，如创建新的存储、 修改现有的存储，以及添加引导菜单参数。 关于 BCDedit 工具的详细信息，请参阅[此 Microsoft Web 站点](http://go.microsoft.com/fwlink/?LinkId=128459)。

### <a name="span-iddiskpartspanspan-iddiskpartspanspan-iddiskpartspandiskpart"></a><span id="DiskPart"></span><span id="diskpart"></span><span id="DISKPART"></span>DiskPart

DiskPart 是在 Windows 中，您可以通过在命令提示符下使用脚本或直接输入管理磁盘、 分区或卷，如对象的命令行工具。 在 Windows 8 中可以使用 DiskPart 工具来创建分区和附加 Vhd。 DiskPart 工具有关的详细信息，请参阅[此 Microsoft Web 站点](http://go.microsoft.com/fwlink/?LinkId=128458)。

### <a name="span-idwindowsdeploymentservicesspanspan-idwindowsdeploymentservicesspanspan-idwindowsdeploymentservicesspanwindows-deployment-services"></a><span id="Windows_Deployment_Services_"></span><span id="windows_deployment_services_"></span><span id="WINDOWS_DEPLOYMENT_SERVICES_"></span>Windows 部署服务

Windows 部署服务是基于网络的安装服务器，使公司能够远程管理和部署新的操作系统，使用 Windows PE 和 Windows 部署服务服务器。 Windows 部署服务支持部署 VHD 映像.wim 文件的文件。 使用 Windows 部署服务时自动用于本机引导的 VHD 映像的网络部署。 Windows 部署服务处理将 VHD 映像复制到一个本地分区和配置本地 BCD 的本机引导的 VHD。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[部署 Windows 在 VHD （本机引导）](deploy-windows-on-a-vhd--native-boot.md)

[引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)

[下载并安装 Windows PE (WinPE)，以便您可以启动从 USB 闪存驱动器或外部 USB 硬盘驱动器](download-and-install-windows-pe--winpe--so-you-can-boot-from-a-usb-flash-drive-or-an-external-usb-hard-drive.md)

 

 






