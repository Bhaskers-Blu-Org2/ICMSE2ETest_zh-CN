---
author: Justinha
Description: "修复 Windows 映像"
ms.assetid: 4ca60b08-6801-4af4-a504-3e88ec0c8fb8
MSHAttr: PreferredLib:/library/windows/hardware
title: "修复 Windows 映像"
ms.openlocfilehash: 52018e0c3885bdbaa78e35246300e093d54297f4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="repair-a-windows-image"></a>修复 Windows 映像


修复使用 DISM 的 Windows 映像。 您可以修复脱机 Windows 映像的 WIM 或 VHD 文件中或联机的 Windows 映像。 在线的 Windows 映像也会自我修复，如果它成为 unserviceable。 此操作的修复源是同一个源，用于根据需要的功能由组策略设置。 有关详细信息，请参阅[配置 Windows 修复源](configure-a-windows-repair-source.md)。 当使用 DISM 工具来修复联机或脱机映像时，可以使用带*/Source*参数*/RestoreHealth*参数来指定要用于搜索所需的文件的其他修复源位置。

为联机映像快速检查，您可能无法使用该命令︰`sfc /scannow`扫描和修复文件。

对于可以修复存储问题的更广泛检查，使用`DISM /Cleanup-Image`。

**以检查图像是否可以修复**

1.  扫描的图像，以检查有损坏。 此操作将需要几分钟。 例如，在命令提示符处，键入以下命令︰

    ``` syntax
    Dism /Online /Cleanup-Image /ScanHealth
    ```

2.  检查以查看是否检测到任何损坏的图像。 例如，在命令提示符处，键入︰

    ``` syntax
    Dism /Online /Cleanup-Image /CheckHealth
    ```

当您使用*/CheckHealth* sfc 参数时，DISM 工具将报告的图像是否正常、 可修复的或无维修。 如果该图像是不可修复的应该放弃该图像并再次启动。 如果图像是可以修复，可以使用*/RestoreHealth*参数来修复图像。

**若要修复图像**

-   */RestoreHealth*参数用于修复图像。 例如，修复脱机映像使用已装载的映像作为修复源，在命令提示符处，键入以下命令︰

    ``` syntax
    Dism /Image:C:\offline /Cleanup-Image /RestoreHealth /Source:c:\test\mount\windows
    ```

    或者，若要修复联机映像使用一些自己的源而不 Windows 更新，请键入︰

    ``` syntax
    Dism /Online /Cleanup-Image /RestoreHealth /Source:c:\test\mount\windows /LimitAccess
    ```

    如果不指定*/Source*修复文件，则使用的即需即装功能的默认位置。 有关详细信息，请参阅[配置 Windows 修复源](configure-a-windows-repair-source.md)。 如果您指定多个*/Source*，从发现和位置的其余部分将被忽略的第一个位置复制文件。 可以使用*/LimitAccess*来防止 DISM 工具使用 Windows 更新作为修复源或备份修复源在线图像。

## <a name="span-idrepairingimagesduringservicingspanspan-idrepairingimagesduringservicingspanspan-idrepairingimagesduringservicingspanrepairing-images-during-servicing"></a><span id="Repairing_images_during_servicing"></span><span id="repairing_images_during_servicing"></span><span id="REPAIRING_IMAGES_DURING_SERVICING"></span>在服务期间修复图像


在某些情况下，图像可以使用 DISM 对其进行修改时已损坏。 使用*/Cleanup-MountPoints*来修复它。 此命令不会卸载已装载的映像，也不会删除图像，可以使用 /Remount-Image 命令来恢复。

``` syntax
Dism /Cleanup-Mountpoints
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[使用系统文件检查器工具来修复系统文件缺失或损坏](http://go.microsoft.com/fwlink/p/?LinkId=717888)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

[配置 Windows 修复源](configure-a-windows-repair-source.md)

 

 






