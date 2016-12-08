---
author: Justinha
Description: "应用使用 DISM 的映像"
ms.assetid: f9e0727d-a210-4efa-85af-5b222c53624e
MSHAttr: PreferredLib:/library/windows/hardware
title: "应用使用 DISM 的映像"
ms.openlocfilehash: 111e495f5841895e85cbc9d85763e4b6cdcee3a3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="apply-images-using-dism"></a>应用使用 DISM 的映像


本主题介绍如何部署到一个或多个目标计算机上使用部署映像服务和管理 (DISM) 工具从参考计算机捕获的图像。 有关配置推荐的硬盘分区的详细信息，请参阅[Configure UEFI/GPT-Based 硬驱动器分区](configure-uefigpt-based-hard-drive-partitions.md)和[Configure BIOS/MBR-Based 硬驱动器分区](configure-biosmbr-based-hard-drive-partitions.md)。

## <a name="span-idbootusingwindowspespanspan-idbootusingwindowspespanspan-idbootusingwindowspespanapply-a-windows-image"></a><span id="BootUsingWindowsPE"></span><span id="bootusingwindowspe"></span><span id="BOOTUSINGWINDOWSPE"></span>将 Windows 映像应用


在目标计算机上，您将创建应用映像的位置的分区结构。 在目标计算机上的分区结构必须匹配参考计算机的分区结构。

如果将映像应用到现有的 Windows 安装的卷时，可能不会删除以前的安装中的文件。 在应用新的映像之前使用 DiskPart 之类的工具格式化该卷。

**要进行分区的硬盘，并应用图像**

1.  目标计算机启动到 Windows PE。 有关详细信息，请参阅[Windows PE (WinPE) 技术参考](winpe-intro.md)。

2.  连接到网络分发共享上存储您的 Windows 映像。 例如，可以使用**net use**命令来执行此操作︰

    ``` syntax
    net use n: \\server\share
    ```

    如果出现提示，请提供网络凭据。

3.  在 Windows PE 命令提示符下键入`diskpart`开始**Diskpart**工具。

4.  创建分区结构使用**Diskpart**工具。 例如︰

    ``` syntax
    select disk 0
    clean
    create partition primary size=3000 id=27
    format quick fs=ntfs label="Recovery"
    assign letter="R"
    create partition primary size=300
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    create partition primary
    format quick fs=ntfs label="Windows"
    assign letter="C"
    exit
    ```

    此示例暂时将这些驱动器号︰ Windows = C，系统 = S 和恢复 = R。 如果有未格式化的硬盘驱动器部署于个人电脑，到末尾的字母，例如 W，以避免驱动器号冲突是一个号更改 Windows 的驱动器号。 不要使用 X，因为 Windows PE 为保留该驱动器号。 重新启动计算机后，Windows 分区分配的字母 C，和其他分区不接收驱动器号。

    建议的分区结构的示例，请参见[Configure BIOS/MBR-Based 硬驱动器分区](configure-biosmbr-based-hard-drive-partitions.md)和[Configure UEFI/GPT-Based 硬驱动器分区](configure-uefigpt-based-hard-drive-partitions.md)。

    **请注意**  
    使用此任务可以自动执行`diskpart /s <script>`命令。 有关详细信息，请参阅[Diskpart 命令行语法](http://go.microsoft.com/fwlink/?LinkId=128458)。

     

5.  使用 DISM 工具将映像应用到 Windows 分区。

    为每个分区应用图像，运行**DISM** **/apply-image** /imageFile:*&lt;图像\_文件&gt;*/索引︰*&lt;索引\_号&gt;*/ApplyDir:*&lt;图像\_路径&gt;*命令。

    ``` syntax
    Dism /apply-image /imagefile:N:\Images\my-windows-partition.wim /index:1 /ApplyDir:C:\
    ```

    **请注意** 如果 DISM /Apply-Image 命令失败，请确保您正在使用的[受支持版本的 DISM](dism-supported-platforms.md)的此 Windows 映像。 例如，要应用 Windows 10 图像，请将需要 DISM 的版本 Windows 10。

     

6.  若要设置基本的系统分区，可以使用 BCDboot 工具以将一组简单的系统文件复制到系统分区。 这些文件包括用来启动 Windows 的引导配置数据 (BCD) 信息︰

    常见的系统分区文件复制并初始化引导配置数据，请使用 BCDboot 工具︰

    ``` syntax
    C:\Windows\System32\bcdboot C:\Windows /l en-US
    ```

    BCDboot 工具有关的详细信息，请参阅[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)。

    **请注意**  
    您可以通过应用图像设置系统分区。 使用**DISM** **/apply-image**命令。 例如︰

    `Dism /apply-image /imagefile:N:\Images\my-system-partition.wim /index:1 /ApplyDir:S:\`

     

您可以设置计算机，重新安装 Windows 映像系统发生故障。 有关详细信息，请参阅[Windows 恢复环境 (Windows RE) 技术参考](windows-recovery-environment--windows-re--technical-reference.md)。

**重要**  
Microsoft 保留分区 (MSR) 和扩展分区均由计算机进行管理。 不适用于这些分区映像。

 

要测试计算机并运到最终用户之前执行其他自定义设置，可以使用审核模式。 有关详细信息，请参阅[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

此外可以执行某些自定义计算机而不启动它。 有关详细信息，请参阅[为应用 Windows 映像提供服务](service-an-applied-windows-image.md)。

**请注意**  
如果您收到的错误消息︰ **Bootmgr 找不到。按下 CTRL + ALT + DEL**，它指示 Windows 无法识别中的活动分区的引导信息。 如果您收到此错误消息，请进行以下检查︰

-   使用 DiskPart 工具检查并确保系统分区被设置为活动状态。

-   检查以确保活动分区包含系统文件。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[捕获硬盘分区使用 DISM 的图像](capture-images-of-hard-disk-partitions-using-dism.md)

[引导到审核模式或 OOBE 的窗口](boot-windows-to-audit-mode-or-oobe.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[应用映像使用脚本](http://go.microsoft.com/fwlink/?LinkId=618399)

 

 






