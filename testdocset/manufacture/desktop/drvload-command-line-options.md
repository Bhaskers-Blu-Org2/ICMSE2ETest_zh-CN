---
author: Justinha
Description: "Drvload 命令行选项"
ms.assetid: d4e6f566-2763-4774-876e-24357f223a52
MSHAttr: PreferredLib:/library/windows/hardware
title: "Drvload 命令行选项"
ms.openlocfilehash: 32563a0b5adb184293b81dda0c4b8d87e3f0a029
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="drvload-command-line-options"></a>Drvload 命令行选项


Drvload 工具引导的 Windows 预安装环境 (Windows PE) 映像添加全新的驱动程序。 它将一个或多个驱动程序.inf 文件作为输入。 将驱动程序添加到脱机 Windows PE 映像，使用部署映像服务和管理 (DISM) 工具。 有关详细信息，请参阅[添加和删除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)。

如果驱动程序.inf 文件需要重新启动，Windows PE 将忽略此请求。 如果驱动程序.sys 文件需要重新启动，然后无法使用 Drvload 添加驱动程序。 有关详细信息，请参阅[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)和[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)。

添加使用 Drvload 工具驱动程序被标记为该设备的首选驱动程序。 如果您在 Windows 安装过程中添加了更新的驱动程序，驱动程序使用 Drvload 添加优先。

## <a name="span-iddrvloadcommand-lineoptionsspanspan-iddrvloadcommand-lineoptionsspanspan-iddrvloadcommand-lineoptionsspandrvload-command-line-options"></a><span id="Drvload_Command-Line_Options"></span><span id="drvload_command-line_options"></span><span id="DRVLOAD_COMMAND-LINE_OPTIONS"></span>Drvload 命令行选项


下面的命令行选项都可用于 Drvload。

**drvload***inf\_路径*\[,*inf\_path* \[...\]\] \[**/?**\]

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/?</strong></p></td>
<td align="left"><p>显示用法信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>inf_path</em></p></td>
<td align="left"><p>指定驱动程序.inf 文件的路径。 该路径可以包含环境变量。</p></td>
</tr>
</tbody>
</table>

 

如果未安装任何驱动程序，然后 Drvload 将返回非零状态 （%错误等级 %）。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

 

 






