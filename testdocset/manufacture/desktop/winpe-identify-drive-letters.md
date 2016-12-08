---
author: kpacquer
Description: "WinPE︰ 使用脚本确定驱动器号"
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 使用脚本确定驱动器号"
ms.openlocfilehash: 83a508c8406ce390e5452190a6120a9dbd76c999
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-identify-drive-letters-with-a-script"></a>WinPE︰ 使用脚本确定驱动器号

WinPE 驱动器号分配更改硬件检测到的每次启动，并且可以更改。 

您可以使用脚本判断哪些驱动器号是它通过搜索文件或文件夹。

此示例脚本中寻找具有标题为图像的文件夹的驱动器，并将其分配给系统变量: %IMAGESDRIVE%。 

``` syntax
@echo Find a drive that has a folder titled Images.
@for %%a in (C D E F G H I J K L M N O P Q R S T U V W X Y Z) do @if exist %%a:\Images\ set IMAGESDRIVE=%%a
@echo The Images folder is on drive: %IMAGESDRIVE%
@dir %IMAGESDRIVE%:\Images /w
```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="Related_topics"></span>相关的主题

[对于 Windows 10 WinPE](winpe-intro.md)

[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md) 

[WinPE︰ 安装在硬盘上 （平面引导或非 RAM）](winpe-install-on-a-hard-drive--flat-boot-or-non-ram.md) 