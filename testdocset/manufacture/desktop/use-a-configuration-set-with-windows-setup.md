---
author: Justinha
Description: "使用 Windows 安装程序配置集"
ms.assetid: 6dc2e7b3-f1fb-4d46-b248-1e96c912db38
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 Windows 安装程序配置集"
ms.openlocfilehash: 45398fde83bbe1d8e10f544f9e23cc35d1967aaf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-a-configuration-set-with-windows-setup"></a>使用 Windows 安装程序配置集


使用配置集向 Windows 安装过程中添加应用程序、 驱动程序、 程序包、 脚本、 文件和文件夹。 配置集是可移植可以放置在 USB 闪存驱动器 (UFD) 或网络共享上的文件和文件夹的集合。

若要使用配置集，您需要以下︰

-   配置集。 有关详细信息，请参阅[创建配置集](https://msdn.microsoft.com/library/windows/hardware/dn915081)。

-   Windows 产品 DVD。

-   如果想要不通过网络安装，可移动媒体，如 USB 闪存驱动器 (UFD)。

-   可引导的 Windows PE 媒体如果想要从网络安装。 有关详细信息，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。

**如何使用 Windows DVD 使用配置集**

1.  打开计算机。

2.  插入两个包含您的配置集和 Windows 产品 DVD 插入新计算机的可移动媒体。

    **请注意**  
    当使用 USB 闪存驱动器，插入驱动器直接插入计算机的 USB 端口中的主要组。 对于台式计算机，这是通常在计算机的背面。

     

3.  通过按下 CTRL + ALT + del 键重新启动计算机。

4.  当计算机重新启动时，您可能会提示您按任意键从光驱启动。 按任何键，Windows 安装程序 (**Setup.exe**) 将自动启动。

    默认情况下，Windows 安装程序搜索答案文件，名为**Autounattend.xml**的所有可移动介质。 Autounattend.xml 必须位于根目录下的可移动媒体。

    安装开始时，将应用答案文件中配置的设置。

**如何使用网络中的配置设置**

1.  在存储产品 DVD 源文件和配置集的网络共享上创建两个文件夹。 例如，

    ``` syntax
    net use N: \\server\share
    md N:\WindowsDVD
    md N:\ConfigurationSets
    ```

2.  复制内容的 DVD 产品为**\\WindowsDVD**文件夹。

3.  复制您的配置设置为**\\ConfigurationSets**文件夹。

4.  使用可引导的 Windows PE 介质引导目标计算机。

    有关创建可引导 Windows PE 介质的信息，请参阅[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。

5.  在 Windows PE 在命令提示符下，将网络驱动器映射到网络共享。 例如，

    ``` syntax
    net use N: \\server\share
    ```

6.  从网络上运行 Windows 安装程序和答案文件中配置集的引用。 例如，

    ``` syntax
    N:\WindowsDVD\setup /unattend:N:\ConfigurationSets\autounattend.xml
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[将自定义命令添加到答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915058)

[从 DVD 启动](boot-from-a-dvd.md)

[部署自定义映像](deploy-a-custom-image.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[向 Windows 安装程序中添加自定义脚本](add-a-custom-script-to-windows-setup.md)

 

 






