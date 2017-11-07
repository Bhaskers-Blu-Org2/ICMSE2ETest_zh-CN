---
author: Justinha
Description: "安装 Windows 10 使用早期版本的 Windows PE"
ms.assetid: 8abda3c5-0689-4a61-ae3e-7fa51c7e2028
MSHAttr: PreferredLib:/library/windows/hardware
title: "安装 Windows 10 使用早期版本的 Windows PE"
ms.openlocfilehash: 8c8eaea4a71a1979259c25b926f292f7a189a232
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="install-windows-10-using-a-previous-version-of-windows-pe"></a>安装 Windows 10 使用早期版本的 Windows PE


要安装的 Windows 10，精简的操作系统，例如某些功能需要 DISM 的版本 Windows 10。

可以在 Windows 预安装环境 (WinPE) 图像中，包括最新版本 DISM 或从运行一个单独的位置，如在可移动驱动器。 如果您把它包含 WinPE，它将大约 4 MB DISM 图像的大小。

您需要安装和配置了驱动程序所需的 DISM，包括 wimmount.sys 和 wofadk.sys 的驱动程序，每次您启动 WinPE。

**若要将 DISM 添加到 Windows PE 映像**

1.  在技术人员计算机，安装 Windows ADK 的 Windows 10。
2.  装载 WinPE。 对于 WinPE 3.x，装入文件︰\\源\\winpe.wim。 对于 WinPE 4.x 和 5.x 中，装入文件︰\\源\\boot.wim。

    ``` syntax
    md "C:\WinPE_amd64\mount"

    Dism /Mount-Image /ImageFile:"C:\WinPE_amd64\media\sources\boot.wim" /index:1 /MountDir:"C:\WinPE_amd64\mount"
    ```

3.  Windows ADK 的 DISM 文件夹复制到的新文件夹中安装的 WinPE 映像中。

    ``` syntax
    md C:\WinPE_amd64\mount\DISM

    robocopy "C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\amd64\DISM" C:\WinPE_amd64\mount\DISM
    ```

    **重要**  不会覆盖现有 DISM 郎**system32**文件夹 WinPE 映像中。 相反，在要复制到 Windows ADK 文件的主机上创建一个新文件夹。

     

4.  卸载 WinPE。

    ``` syntax
    Dism /Unmount-Image /MountDir:"C:\WinPE_amd64\mount" /commit
    ```

5.  创建 WinPE 可引导介质，或替换现有可移动媒体上的 WinPE 图像文件。

    ``` syntax
    MakeWinPEMedia /UFD C:\WinPE_amd64 F:
    ```

**安装和使用 DISM 从 WinPE**

1.  启动 WinPE 到目标设备。
2.  安装和配置使用**WimMountAdkSetupAmd64.exe /Install**或**WimMountAdkSetupX86.exe /Install**DISM 的必需的驱动程序。

    ``` syntax
    X:\DISM\WimMountAdkSetupAmd64.exe /Install /q
    ```

    默认 (RAMDisk) 版本的 WinPE，您将需要运行以下命令，每次您启动 WinPE。 若要了解如何启动 WinPE 时自动运行此命令，请参阅[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)。

3.  验证安装了 Windows 10 的 DISM 版本。

    ``` syntax
    X:\DISM\Dism.exe /?
    ```

    输出显示版本号，例如︰

    ``` syntax
    Deployment Image Servicing and Management tool
    Version: 10.0.10122.0
    ```

4.  新的文件夹中运行 DISM 命令。

    ``` syntax
    X:\DISM\Dism.exe /Apply-Image /ImageFile:install.wim /Index:1 /ApplyDir:W: /Compact
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 支持的平台](dism-supported-platforms.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

 

 






