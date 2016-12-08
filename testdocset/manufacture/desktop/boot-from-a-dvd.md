---
author: Justinha
Description: "从 DVD 启动"
ms.assetid: f64eb16b-15b3-4a6d-af68-526a8097edb7
MSHAttr: PreferredLib:/library/windows/hardware
title: "从 DVD 启动"
ms.openlocfilehash: 56d22fdebefede6547e5b01aac605bea9ba9c765
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="boot-from-a-dvd"></a>从 DVD 启动


在新硬件上安装 Windows 的最简单方法是直接从 Windows 产品 DVD 启动使用名为 Autounattend.xml 的答案文件。 当网络访问不可用或生成只有几台计算机时，此方法提供了灵活性。 可以使用相同的方法来构建初始在基于映像的部署方案中，通常称为*主安装*映像。

通过使用应答文件，您可以自动化的全部或部分的 Windows 安装程序。 您可以使用 Windows 系统映像管理器 (Windows SIM) 创建答案文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)。

## <a name="span-idprerequisitesspanspan-idprerequisitesspanspan-idprerequisitesspanprerequisites"></a><span id="Prerequisites"></span><span id="prerequisites"></span><span id="PREREQUISITES"></span>系统必备组件


若要完成本演练，您需要以下各项︰

-   应答文件在可移动媒体 （CD 或 DVD-ROM） 或 USB 闪存驱动器上。 答案文件必须命名为 Autounattend.xml。 答案文件必须位于根目录下的媒体。

-   Windows 产品 DVD。

**要从 Windows 产品 DVD 安装窗口**

1.  打开新的计算机。

    **请注意**  
    本示例假定硬盘驱动器上为空。

     

2.  插入 Windows 产品 DVD 和答案文件将包含新计算机的可移动媒体。

    **请注意**  
    当您使用 USB 闪存驱动器时，插入驱动器直接插入计算机的 USB 端口中的主要组。 对于台式计算机，这是通常在计算机的背面。

     

3.  通过按 CTRL + ALT + DEL 键重新启动计算机。 Windows 安装程序 (Setup.exe) 将自动启动。

    默认情况下，Windows 安装程序搜索的驱动器和其他位置，如可移动媒体，以便应答文件，名为 Autounattend.xml 的根本。 即使未显式指定答案文件，将发生这种情况。 有关详细信息，请参阅"隐式搜索的应答文件"和"隐式答案文件搜索顺序" [Windows 安装程序自动化概述](windows-setup-automation-overview.md)中。

4.  安装程序完成后，验证 Windows 应用所有的自定义设置，然后使用**sysprep**命令和**一般化 /**选项重新封装计算机。

    Sysprep 工具删除所有系统特定的信息，并将重置计算机。 下次计算机启动时，您的客户可以接受 Microsoft 软件许可条款并添加特定于用户的信息。

    可选︰ 若要在安装后自动运行 Sysprep 工具，设置 Microsoft Windows 部署 |重新封装应答文件 (Autounattend.xml) 中的组件设置如下所示︰

    `ForceShutdownNow = true, Mode =OOBE`

    可选︰ 若要手动运行 Sysprep 工具，从正在运行的操作系统，下列命令提示符下键入︰

    `c:\windows\system32\sysprep /oobe /shutdown`

有关详细信息，请参阅[Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md)。

## <a name="span-idnextstepsspanspan-idnextstepsspanspan-idnextstepsspannext-steps"></a><span id="Next_Steps"></span><span id="next_steps"></span><span id="NEXT_STEPS"></span>下一步行动


本演练阐释了基本的无人参与的安装，无需任何用户输入。 对新安装操作系统，可以手动添加更多自定义。 如果这是主安装或将映像部署的安装，请关闭计算机。 然后，通过使用部署映像服务和管理 (DISM) 工具或任何第三方映像软件捕获安装映像。

**重要**  
您必须运行**sysprep 一般化 /**命令之前到新计算机的 Windows 映像移动通过任何方法。 这些方法包括图像处理、 硬盘重复和其他方法。 移动或复制到另一台计算机而不运行的 Windows 映像**sysprep 一般化 /**不支持命令，即使新的计算机具有相同的硬件配置。 泛化图像从 Windows 安装删除唯一的信息，以便您可以将该映像应用在不同的计算机上。

下次您启动 Windows 映像，在[specialize](specialize.md)配置阶段运行。 在此配置阶段中，许多组件执行您的新计算机上启动 Windows 映像时，必须执行的操作。 有关详细信息，请参阅[如何配置阶段的工作](how-configuration-passes-work.md)。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[使用 Windows 安装程序配置集](use-a-configuration-set-with-windows-setup.md)

[部署自定义映像](deploy-a-custom-image.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[在 Windows 安装期间添加到 Windows 的设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md)

[向 Windows 安装程序中添加自定义脚本](add-a-custom-script-to-windows-setup.md)

 

 






