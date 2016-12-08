---
author: Justinha
Description: "裸露金属的重置恢复︰ 在部署新设备的过程创建恢复媒体"
ms.assetid: 2244bddf-8f49-41db-949a-2fbe9e224003
MSHAttr: PreferredLib:/library/windows/hardware
title: "裸露金属的重置恢复︰ 在部署新设备的过程创建恢复媒体"
ms.openlocfilehash: 2164c1933902642ad544299c69956b637b9e9d18
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bare-metal-resetrecovery-create-recovery-media-while-deploying-new-devices"></a>裸露金属的重置恢复︰ 在部署新设备的过程创建恢复媒体


恢复介质 （裸机恢复） 帮助将 Windows 设备恢复到出厂状态时，即使用户需要替换硬驱或完全擦除驱动器清洗。

您可以与您提供给客户使用相同的 Windows 映像部署设备使用的新设备包括该媒体。

**请注意**  
-   必须配置计算机固件 /BIOS，以便计算机可以从介质 （USB 驱动器或 DVD 驱动器） 启动。
-   USB 闪存驱动器或 DVD 恢复介质必须有足够的空间用于 Windows 映像。
-   如果 Windows 映像大于 32 GB 或更大的是媒体正在使用 （例如，Dvd 的 4.7 GB），您需要[的拆分的 Windows 映像的文件跨越多个 Dvd](split-a-windows-image--wim--file-to-span-across-multiple-dvds.md)。

 

若要创建可引导 USB 恢复驱动器的个人设备，请参阅[创建 USB 恢复驱动器](http://go.microsoft.com/fwlink/p/?linkid=296450)。

## <a name="span-idcreatemediaspanspan-idcreatemediaspanspan-idcreatemediaspancreate-a-bootable-windows-re-image"></a><span id="CreateMedia"></span><span id="createmedia"></span><span id="CREATEMEDIA"></span>创建可引导的 Windows RE 映像


若要创建与 PC 可以包括恢复介质，您必须︰

-   Windows 映像 (Install.wim)。 您可以使用基本的 Windows 映像或自定义的恢复图像。
-   Windows RE 工具图像 (Winre.wim)。 可以从 Windows 映像中，提取基本 Windows RE 工具图像，也可以使用[自定义的 Windows RE 映像](customize-windows-re.md)。

**步骤 1︰ 打开部署和成像工具环境**

1.  下载并安装[Windows 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/?LinkId=526803)。
2.  在技术人员计算机上︰ 单击**开始**，并且类型**部署**。 用鼠标右键单击**部署和图像处理工具环境**，然后选择**以管理员身份运行**。

**步骤 2︰ 从 Windows 映像中提取 Windows RE 映像**

1.  将 Windows 映像进行安装︰

    ``` syntax
    md c:\mount\Windows

    Dism /Mount-Image /ImageFile:D:\sources\install.wim /Index:1 /MountDir:C:\mount
    ```

2.  Windows RE 映像复制。

    ``` syntax
    md C:\Images

    xcopy C:\mount\Windows\System32\Recovery\winre.wim C:\Images\winre.wim /h
    ```

3.  卸载 Windows 映像︰

    ``` syntax
    Dism /Unmount-Image /MountDir:C:\mount\winre /Discard
    ```

**步骤 3︰ 创建 Windows RE 文件的工作文件夹**

1.  对于 Windows RE，基于 Windows PE 创建一个文件夹结构︰

    ``` syntax
    copype amd64 C:\resetmedia_amd64
    ```

    *amd64*所在系统的体系结构，您将创建介质。

2.  默认的 Windows PE 启动映像 (Boot.wim) 替换 Windows RE 工具图像。

    ``` syntax
    xcopy C:\MyImages\winre.wim C:\resetmedia_amd64\media\sources\boot.wim /h
    ```

**步骤 4︰ 添加 Windows 映像**

-   将 Windows 映像复制到工作文件夹。

    ``` syntax
    copy D:\sources\install.wim C:\resetmedia_amd64\media\sources\install.wim
    ```

    其中*d:\\源\\install.wim*是基本的 Windows 映像或自定义按钮重置恢复映像。

**步骤 5︰ 可选︰ 添加裸机恢复配置脚本**

-   如果您使用自定义的分区布局，裸机恢复配置将脚本添加到工作文件夹中，在\\源。 有关详细信息，请参阅[裸机重置/恢复︰ 启用您用户创建介质](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md)。

    ``` syntax
    copy E:\Recovery\RecoveryImage\ResetConfig.xml C:\resetmedia_amd64\media\sources\ResetConfig.xml

    copy E:\Recovery\RecoveryImage\ResetPartitions-UEFI.txt C:\resetmedia_amd64\media\sources\ResetPartitions-UEFI.txt
    ```

## <a name="span-idcreatebootablemediaspanspan-idcreatebootablemediaspanspan-idcreatebootablemediaspancreate-bootable-media"></a><span id="Create_bootable_media"></span><span id="create_bootable_media"></span><span id="CREATE_BOOTABLE_MEDIA"></span>创建可引导介质


**若要创建可引导的 USB 闪存驱动器︰**

1.  USB 闪存驱动器上安装 Windows RE:

    ``` syntax
    Makewinpemedia /ufd C:\resetmedia_amd64 F:
    ```

    其中*F*是 USB 闪存驱动器的驱动器号。

2.  USB 闪存驱动器与一个描述性的名称的标签︰

    文件资源管理器中，在驱动器中，用鼠标右键单击并选择**重命名**，键入**完整 PC 恢复**。

**若要创建可启动的 DVD:**

1.  创建 DVD 图像文件︰

    ``` syntax
    Makewinpemedia /iso C:\resetmedia_amd64 C:\resetmedia_amd64\RecoveryImage.iso
    ```

2.  插入 DVD。
3.  文件资源管理器中定位到`C:\resetmedia_amd64`，用鼠标右键单击`RecoveryImage.iso`，然后单击**刻录光盘映像**。

## <a name="span-idtestthebaremetalrecoveryfeaturesspanspan-idtestthebaremetalrecoveryfeaturesspanspan-idtestthebaremetalrecoveryfeaturesspantest-the-bare-metal-recovery-features"></a><span id="Test_the_bare_metal_recovery_features"></span><span id="test_the_bare_metal_recovery_features"></span><span id="TEST_THE_BARE_METAL_RECOVERY_FEATURES"></span>测试的裸机恢复功能


1.  在空硬盘的 PC 上，插入新的恢复媒体。
2.  启动电脑，按下某个键打开固件引导菜单，然后选择相应的启动设备。
3.  在**Windows RE 工具**菜单中，选择一种键盘布局，例如，**我们**。
4.  单击**疑难解答** &gt; **重置您的 PC** &gt; **下一步**

    **请注意**  
    如果您要在同一台 PC，测试并不清理硬盘，可能提示您选择一个驱动器。 选择窗口 10。

     

    选择**是，对驱动器重新分区** &gt; **只是删除我的文件** &gt; **重置**。

    Windows 使用的恢复映像置到其原始状态的计算机。

## <a name="span-idlarge-scaledeploymentspanspan-idlarge-scaledeploymentspanspan-idlarge-scaledeploymentspanlarge-scale-deployment"></a><span id="Large-Scale_Deployment"></span><span id="large-scale_deployment"></span><span id="LARGE-SCALE_DEPLOYMENT"></span>大规模部署


如果您正在部署与您的计算机的 USB 密钥，可以使用上述步骤在 USB 上创建基本的 Windows 恢复媒体副本。 执行最终的自定义项的图像后，可以引导到 Windows PE 中，计算机和更新 USB 恢复介质上的 install.wim 图像。

可能可以通过附加在 USB 闪存驱动器上，将 Windows 映像，而不是重新捕获 Windows 映像以整个节省制造时间。 如果这样做，则还必须更新 ResetConfig.xml 配置文件元素︰`RestoreFromIndex`相应的索引号。 有关详细信息，请参阅[附加到现有图像使用 DISM 卷映像](append-a-volume-image-to-an-existing-image-using-dism--s14.md)和[ResetConfig XML 参考](resetconfig-xml-reference-s14.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[裸机重置/恢复︰ 使用户可以创建媒体](bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space.md)

[点击式重新设置概述](push-button-reset-overview.md)

[ResetConfig XML 参考](resetconfig-xml-reference-s14.md)

[REAgentC 命令行选项](reagentc-command-line-options.md)

 

 






