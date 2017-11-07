---
author: kpacquer
Description: "使用 WIM MMO 图像"
ms.assetid: c995e207-1b89-4d49-ad46-1ccc750737ec
MSHAttr: PreferredLib:/library/windows/hardware
title: "使用 WIM MMO 图像"
ms.openlocfilehash: 1c10013a0543a8345308b166f48bb28d433ef2a2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="working-with-wim-mmos-images"></a>使用 WIM MMO 图像


暂时可以通过 （Windows 图像处理） 的 WIM 映像复制到设备，然后对在易失性 RAM 内存运行该映像的引导。 此功能可用于使用 MMO 设备提供服务。 MMO 有关的详细信息，请参阅[微软制造的操作系统](microsoft-manufacturing-os.md)。 服务使用这种方法的优点是不需要在零售 OS 代码只在维修中使用的保留空间。 最小化的空间所使用的操作系统是低成本的设备中重要的考虑因素。

**重要**  
目前支持的只有 MMO 测试映像。 目前不支持零售签名。

 

## <a name="span-idcreatingawimimagespanspan-idcreatingawimimagespanspan-idcreatingawimimagespancreating-a-wim-image"></a><span id="Creating_a_WIM_Image"></span><span id="creating_a_wim_image"></span><span id="CREATING_A_WIM_IMAGE"></span>创建一个 WIM 映像


创建一个 WIM 映像之前，必须完成以下主题中描述的步骤︰

[MMO 图像定义](mmos-image-definition.md)

此外，请遵循以下原则准备映像，以便它将正常运行时转换为一个 WIM 映像。

-   下面的 XML 显示测试 WIM 映像中可用的 Microsoft 功能示例。

    ``` syntax
    <Microsoft>
      <Feature>MOBILECOREBOOTSH</Feature>
      <Feature>ENABLE_BOOT_KEYS_TEST</Feature>
      <Feature>ENABLE_IP_OVER_USB</Feature>
    </Microsoft>
    ```

    要添加其他功能，例如电池充电 (启用\_MMO\_正在充电) 根据您的需要。 有关 MMO 功能的其他信息，请参阅[MMO 图像定义](mmos-image-definition.md)。

-   不包括访问设备上的其他分区的包。 因为 WIM 已加载并运行在内存中，则不能访问其他分区和操作系统中不能包含引用其他分区的包。

完成前面的主题中的步骤后，使用**ImgToWIM**命令将已签名的 FFU 映像转换为 WIM 映像。 ImgToWim 可执行文件位于 %WPDKCONTENTROOT%\\工具\\bin\\i386。 使用情况汇总如下。

``` syntax
ImgToWIM <FFUFileName> <WIMFileName> 
```

当您输入**ImgToWim**命令时，您应该看到类似于下面的输出。

``` syntax
C:\TestWIM>ImgToWim MMOS.ffu MMOSWim.wim
Reading the image file: MMOS.ffu
ETW Log Path: C:\Users\USER1\AppData\Local\Temp\storage_session_1210.etl
OS Version: Microsoft Windows NT 6.2.9200.0
OpenDiskInternal: Creating empty virtual disk.
No mounted WP disks found.
Storage Service: Created a new image in 0.7 seconds.
AddAccessPath: Mount point for volume MainOS: C:\Users\USER1\AppData\Local\Temp
\oji20cvi.mq5.mnt\.

Creating WIM at 'C:\TestWIM\MMOSWim.wim' ...

Capturing 'MainOS'...
WIM creation complete.
DismountFullFlashImage:[2.87] Cleaning up temporary paths.
CleanupTemporaryPaths: Cleaning up temporary path C:\Users\USER1\AppData\Local\
Temp\oji20cvi.mq5.mnt\.
Storage Service: Dismounting the image in 2.9 seconds.
```

## <a name="span-idbootingfromawimimagespanspan-idbootingfromawimimagespanspan-idbootingfromawimimagespanbooting-from-a-wim-image"></a><span id="Booting_from_a_WIM_Image"></span><span id="booting_from_a_wim_image"></span><span id="BOOTING_FROM_A_WIM_IMAGE"></span>从 WIM 映像引导


使用**WIM** FFUTool 选项启动从 WIM 映像。 使用情况汇总如下。

``` syntax
ffutool -WIM <WIMFileName.wim>
```

要引导从 WIM 映像的设备，请完成以下步骤。

1.  设置闪烁工具的 PC 端。

2.  将设备置于打开设备电源时按住按钮向上卷闪烁模式。 设备处于闪烁模式后，连接到计算机的 USB 数据线。

3.  使用带有**-WIM**选项的**FFUTool**命令启动从 WIM 映像的设备。 它位于 %WPDKCONTENTROOT%\\工具\\bin\\i386。 当您输入**FFUTool-WIM**命令，您会看到与以下内容类似的输出。

    ``` syntax
    C:\> ffutool -wim MMOSWim.wim
    Found device:
    Name:   Contoso.MSM8960.JD301_ATT.3.2.1
    ID:     00000011-f151-a509-0000-000000000000
    Booting WIM: MMOSWim.wim
    WIM transfer completed in 26.550073 seconds.
    ```

Ffutool 将 WIM 操作码发送到该设备，以及信息的图像的大小。 下一步分配的内存缓冲区将包含图像。 Ffutool 将移交给该设备的 WIM 映像。 一旦它完全转移，该设备将启动到内存中的 WIM 映像。

**请注意**  
当前的 MMO WIM 映像可能无法显示旋转光盘图形，但是 MMO 仍正常工作。

 

 

 





