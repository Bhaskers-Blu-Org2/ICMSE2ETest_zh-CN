---
author: Justinha
Description: "启用或禁用使用 DISM 的 Windows 功能"
ms.assetid: a5280bba-7808-4752-92ca-7605a9ea29f0
MSHAttr: PreferredLib:/library/windows/hardware
title: "启用或禁用使用 DISM 的 Windows 功能"
ms.openlocfilehash: 231846d0c9ed29ed9fd7877dac2766166a6a9f62
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enable-or-disable-windows-features-using-dism"></a>启用或禁用使用 DISM 的 Windows 功能


部署映像服务和管理 (DISM) 工具是一个命令行工具，用于修改 Windows® 图像。 您可以使用 DISM 启用或禁用直接从命令提示符下或通过将答案文件应用于映像的 Windows 功能。 您可以启用或禁用 Windows 功能在 WIM 或 VHD 文件，脱机或联机上运行的操作系统。

## <a name="to-mount-an-offline-image-for-servicing"></a>若要装载脱机映像以便进行处理

1.  使用管理员权限打开命令提示符。

2.  若要从安装了 Windows 评估和部署工具包 (Windows ADK) 使用 DISM，找到 Windows ADK 服务文件夹并导航至该目录。 默认情况下，DISM 安装在 c:\\程序文件 (x86)\\窗口工具包\\10.0\\评估和部署工具包\\部署工具\\Windows 10 c︰ 中\\程序文件 (x86)\\窗口工具包\\8.1\\评估和部署工具包\\部署工具\\在 Windows 8.1and c:\\程序文件 (x86)\\窗口工具包\\8.0\\评估和部署工具包\\部署工具\\Windows 8 中。

    DISM 中有︰

    -   Windows 10
    -   Windows 8.1
    -   Windows 8
    -   Windows 服务器 2016年技术预览
    -   Windows Server 2012 R2
    -   Windows Server 2012
    -   对于 Windows 10 的 Windows 预安装环境 (WinPE)
    -   WinPE 5.0
    -   WinPE 4.0

    您可以安装 DISM 和其他部署映像工具，如 Windows 系统映像管理器 (Windows SIM)，在另一台支持 Windows ADK 操作系统。 有关详细信息，请参阅[DISM 支持的平台](dism-supported-platforms.md)。

3.  使用`/Get-ImageInfo`选项来检索名称或要修改的映像的索引号。 索引或名称值时需要指定图像文件的大多数操作。

    例如，在命令提示符下键入︰

    ``` syntax
    Dism /Get-ImageInfo /ImageFile:C:\test\images\install.wim
    ```

4.  装入脱机 Windows 映像。 例如，键入︰

    ``` syntax
    Dism /Mount-Image /ImageFile:C:\test\images\install.wim /Name:"Base Windows Image" /MountDir:C:\test\offline
    ```

## <a name="to-find-available-windows-features-in-an-image"></a>若要查找图像中可用的 Windows 功能

1.  列出所有可用的操作系统中的功能。 例如，键入︰

    ``` syntax
    Dism /online /Get-Features
    ```

    若要处理脱机映像，指定已装载的映像目录的位置。 例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Get-Features
    ```

    您可以使用`>featurelist.txt`命令的输出重定向到名为功能列表的文本文件。

2.  查看功能，以找到您想要启用、 禁用、 删除或还原功能的列表。

3.  使用`/Get-FeatureInfo`列出有关信息的特定的功能感兴趣。 例如，键入︰

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

## <a name="to-enable-windows-features"></a>若要启用 Windows 功能

1.  使图像中的某个特定功能。 您可以使用`/All`若要启用所有父功能在同一命令中的参数。 例如，键入︰

    ``` syntax
    Dism /online /Enable-Feature /FeatureName:TFTP /All
    ```

    若要处理脱机映像，指定已装载的映像目录的位置。 例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Enable-Feature /FeatureName:TFTP /All
    ```

2.  可选︰ 获取已启用该功能的状态。 例如，键入︰

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    如果**Enble 挂起**状态，您必须启动图像才能完全启用该功能。

## <a name="to-restore-removed-windows-features"></a>若要还原删除 Windows 功能

1.  使图像中的某个特定功能。 如果未指定源，DISM 看在指定所需的文件启用此功能的详细信息，请参阅[配置 Windows 修复源](configure-a-windows-repair-source.md)所需的组策略的默认位置。

    如果在默认位置找不到文件，DISM 将所需的文件与 Windows 更新 (WU)。 您可以使用`/LimitAccess`参数，以防止 DISM 联系 WU。

    如果您指定多个`/Source`参数，将这些文件收集从第一个位置找到它们的位置和位置的其余部分将被忽略。

    例如，键入︰

    ``` syntax
    Dism /Online /Enable-Feature /FeatureName:TFTP /Source:Z:\sources\SxS /Source:C:\test\mount\windows /LimitAccess
    ```

    若要处理脱机映像，指定已装载的映像目录的位置。 例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Enable-Feature /FeatureName:TFTP /Source:C:\test\mount\windows
    ```

2.  可选︰ 获取已启用该功能的状态。 例如，键入︰

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    如果状态是**EnablePending**，您必须引导映像才能完全启用该功能。

## <a name="to-disable-windows-features"></a>若要禁用 Windows 功能

1.  禁用映像中的某个特定功能。 例如，键入︰

    ``` syntax
    Dism /online /Disable-Feature /FeatureName:TFTP
    ```

    若要处理脱机映像，指定已装载的映像目录的位置。 例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Disable-Feature /FeatureName:TFTP
    ```

2.  可选︰ 使用`DISM /GetFeatureInfo`以获取状态的已禁用的功能。 例如，键入︰

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    如果状态是**DisablePending**，您必须以完全禁用该功能引导映像。

## <a name="to-remove-windows-features-for-on-demand-installation"></a>若要删除为按需安装的 Windows 功能

1.  但不从图像中移除功能清单映像中删除特定的功能。 此选项只用于服务窗口 10、 Windows 8.1、 Windows 8、 Windows 服务器 2016年技术预览、 Windows Server 2012 R2 或 Windows Server 2012。 有关详细信息，请参阅[配置 Windows 修复源](configure-a-windows-repair-source.md)。

    例如，键入︰

    ``` syntax
    Dism /online /Disable-Feature /FeatureName:TFTP /Remove
    ```

    若要处理脱机映像，指定已装载的映像目录的位置。 例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Disable-Feature /FeatureName:TFTP /Remove
    ```

2.  可选︰ 使用`DISM /GetFeatureInfo`以获取状态的已禁用的功能。 例如，键入︰

    ``` syntax
    Dism /online /Get-FeatureInfo /FeatureName:TFTP
    ```

    状态为**已禁用**。 从 Windows 10 开始，负载不会从 Windows 客户端 Sku 支持按钮重置。 有效负载从 Windows 服务器 Sku。

## <a name="to-enable-or-disable-windows-features-by-using-dism-and-an-answer-file"></a>若要启用或禁用使用 DISM 和答案文件的 Windows 功能

1.  在 Windows SIM 中，通过单击**文件**菜单上的**选择 Windows 映像**，并在下拉列表中，指定编录文件类型 (.clg) 打开一个现有的目录，或通过单击**工具**菜单上**创建编录**创建新目录。

2.  展开**Windows 映像**窗格中的目录，然后展开**包**。

3.  展开**的基础**上，然后右键单击**Microsoft Windows 基础程序包**。

4.  单击**添加到答案文件**。

5.  单击您想要启用或禁用的功能**已启用**或**已禁用**。 单击箭头以选择相反的选择。

    您可能必须展开以查看所有其子项。 如果启用了其子级之一，必须启用父。

    **请注意**  
    您无法还原或使用无人参与的应答文件删除 Windows 功能的即需即装功能。

6.  在主菜单上，单击**工具**，然后单击**验证答案文件**。

7.  更正任何错误将显示在**邮件**窗格中，并保存答案文件。

8.  在命令提示符下，键入以下命令，以将无人参与的答案文件应用于映像。

    ``` syntax
    Dism /online /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

    若要处理脱机映像，指定已装载的映像目录的位置。 例如，键入︰

    ``` syntax
    Dism /Image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml
    ```

## <a name="to-commit-changes-on-an-offline-image"></a>提交在脱机映像上的更改

-   提交更改并卸载映像。 例如，键入︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\test\offline /Commit
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

[DISM 无人参与服务命令行选项](dism-unattended-servicing-command-line-options.md)

[配置 Windows 修复源](configure-a-windows-repair-source.md)

 

 






