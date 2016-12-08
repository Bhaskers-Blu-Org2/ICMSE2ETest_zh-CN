---
author: Justinha
Description: "装载和修改 Windows 映像使用 DISM"
ms.assetid: f48b4681-bc59-4eb1-89c9-0163594467f7
MSHAttr: PreferredLib:/library/windows/hardware
title: "装载和修改 Windows 映像使用 DISM"
ms.openlocfilehash: 82d127bdda4e6f7eef73a53f27b0784a04f1559e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mount-and-modify-a-windows-image-using-dism"></a>装载和修改 Windows 映像使用 DISM


可以使用部署映像服务和管理 (DISM) 工具从 WIM 或 VHD 文件安装的 Windows 映像。 装载一个图像图像的内容映射到一个目录，以便您可以为服务使用 DISM 未引导到该图像的图像。 您还可以执行常见的文件操作，如复制、 粘贴和编辑上已装载的映像。

**请注意**  
DISM 无法在 Windows Vista with Service Pack 1 (SP1) 或 Windows Server 2008 上装载了从 VHD 的 Windows 映像。 您必须将附加 VHD 使用 DiskPart 工具之前，您可以使用 DISM 映像提供服务。 当服务使用 DiskPart 工具已附加 VHD 映像时，所做的更改与每个操作自动提交，不能放弃。

 

您可以装载和修改单个计算机上的多个图像。 有关详细信息，请参阅[部署映像服务和管理 (DISM) 最佳做法](deployment-image-servicing-and-management--dism--best-practices.md)。

## <a name="span-idmountinganimagespanspan-idmountinganimagespanspan-idmountinganimagespanmounting-an-image"></a><span id="Mounting_an_Image"></span><span id="mounting_an_image"></span><span id="MOUNTING_AN_IMAGE"></span>装载一个图像


可以装载映像使用**/ 优化**选项来减少初始装载时间。 但是，使用**/ 优化**选项时，通常在安装期间执行的进程将改为完成第一次访问一个目录。 因此，可能会在装载映像使用**/optimize**选项后第一次访问目录所需的时间增加。

**若要装载映像**

1.  使用管理员权限打开命令提示符。 如果使用非 Windows 8 的 Windows 或 Windows 10 的版本时，使用部署工具命令提示安装 ADK 或导航到您的本地计算机上的 DISM 目录。

2.  将映像装载。

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline
    ```

    **请注意**  
    从 VHD 文件安装的 Windows 映像，则必须指定`/index:1`。

     

    您还可以添加选项具有只读权限的映像安装或减少**/Optimize**选项的初始装载时间。 例如，

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\myimage.wim /index:1 /MountDir:C:\test\offline /ReadOnly /Optimize
    ```

    有关 DISM 中的**/Mount-Image**选项可用选项的详细信息，请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

## <a name="span-idmodifyinganimagespanspan-idmodifyinganimagespanspan-idmodifyinganimagespanmodifying-an-image"></a><span id="Modifying_an_Image"></span><span id="modifying_an_image"></span><span id="MODIFYING_AN_IMAGE"></span>修改图像


装入映像后，您可以浏览图像的目录。 可以查看文件和文件夹结构，并添加、 编辑或删除文件和文件夹。

此外可以使用 DISM 工具来添加和删除驱动程序和程序包，包括语言包、 枚举驱动程序和程序包、 修改配置设置等。 有关详细信息，请参阅[Windows 映像使用 DISM 服务](service-a-windows-image-using-dism.md)。

**若要查看和修改映像**

1.  在技术人员计算机上打开装入的目录。 例如，

    ``` syntax
    cd C:\mounted_images
    ```

2.  删除、 编辑或添加其他文件和文件夹必须显示后应用到目标计算机的位置。 例如，c:\\程序\_文件\\应用程序\_名。

    **重要**  
    如果必须添加应用程序或设备，请验证包含了所有所需的文件。 尽管您可以添加应用程序文件和文件夹，您不能安装应用程序。

     

## <a name="span-idcommittingchangestoanimagespanspan-idcommittingchangestoanimagespanspan-idcommittingchangestoanimagespancommitting-changes-to-an-image"></a><span id="Committing_Changes_to_an_Image"></span><span id="committing_changes_to_an_image"></span><span id="COMMITTING_CHANGES_TO_AN_IMAGE"></span>将更改提交到图像


可以为图像提交更改，而无需卸载映像。

**若要提交对映像的更改**

-   在命令提示符下，键入︰

    ``` syntax
    Dism /Commit-Image /MountDir:C:\test\offline
    ```

    使用**/CheckIntegrity**来检测和跟踪.wim 文件损坏时您提交对映像的更改。 在应用或装入该映像时，使用**/CheckIntegrity**再次检测到文件损坏时停止该操作。 **/CheckIntegrity**不能使用虚拟硬盘 (VHD) 文件。

## <a name="span-idunmountinganimagespanspan-idunmountinganimagespanspan-idunmountinganimagespanunmounting-an-image"></a><span id="Unmounting_an_Image"></span><span id="unmounting_an_image"></span><span id="UNMOUNTING_AN_IMAGE"></span>卸载映像


修改映像后，必须将其卸载。 如果装入您的图像与默认读取/写入权限时，您可以提交更改。 这使得您的修改图像的永久组成部分。

**卸载映像**

1.  使用管理员权限打开命令提示符。 如果使用非 Windows 8 的 Windows 或 Windows 10 的版本时，使用部署工具命令提示安装 ADK 或导航到您的本地计算机上的 DISM 目录。


2.  卸载该映像。

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /commit
    ```

    其中`C:\test\offline`已装载目录的位置。 如果不指定卸载参数，此选项将列出所有装入的映像，但不执行卸载操作。

    **重要**  
    当您使用**/ 卸载**选项，则必须使用**/commit**或****放弃/参数。

     

修改后的图像，您可以应用映像从网络共享或本地媒体，如 CD/DVD 或 USB 闪存驱动器 (UFD)。

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


**如果在本主题中的 DISM 命令失败，请尝试以下方法︰**

1.  请确保您正在使用 DISM 安装与 Windows ADK 的 Windows 10 版本。

2.  如果您使用的 Windows 8.1、 Windows 8 或 Windows 7 电脑，使用**部署和图像处理工具环境**来访问 Windows ADK 的 Windows 10 版本一起安装的工具。

3.  不装入图像到受保护的文件夹，例如，您的用户\\文档文件夹。

4.  如果 DISM 进程被打断，可以考虑暂时断开与网络的连接和禁用病毒防护。

5.  如果 DISM 进程被打断，可以考虑改为从 Windows 预安装环境 (WinPE) 运行的命令。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

 

 






