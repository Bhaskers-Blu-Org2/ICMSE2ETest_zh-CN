---
author: Justinha
Description: "Copype 命令行选项"
ms.assetid: 3342c1d4-7dff-4e0b-ab86-1f28d5057f12
MSHAttr: PreferredLib:/library/windows/hardware
title: "Copype 命令行选项"
ms.openlocfilehash: 8562546856e643c64b41c505948ef16f1dabe932
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="copype-command-line-options"></a>Copype 命令行选项


**Copype**工具会创建一个包含一组标准的 Windows 预安装环境 (Windows PE) 文件的工作目录。 您可以使用这些文件以自定义映像和 （与**Makewinpemedia**脚本） 创建可引导介质。 有关详细信息，请参阅[Makewinpemedia 命令行选项](makewinpemedia-command-line-options.md)。

## <a name="span-idcopypecommand-lineoptionsspanspan-idcopypecommand-lineoptionsspanspan-idcopypecommand-lineoptionsspancopype-command-line-options"></a><span id="Copype_Command-Line_Options"></span><span id="copype_command-line_options"></span><span id="COPYPE_COMMAND-LINE_OPTIONS"></span>Copype 命令行选项


**Copype**将使用下面的命令行选项。

**Copype.cmd**体系结构 WorkingDirectory

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">命令行选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>体系结构</em></p></td>
<td align="left"><p>将引导文件和 Windows PE 基本映像 (Winpe.wim) 复制到<em>&lt;WorkingDirectory&gt;</em>\Media。</p>
<p>值包括<strong>amd64</strong>、 <strong>x86</strong>或<strong>手臂</strong>。</p>
<p>X86 版本的 Windows PE 可以引导 32 位 （uefi）、 32 位 BIOS 或 BIOS 基于 64 位的个人电脑。</p>
<p>Amd64 版本的 Windows PE 可以引导或者 64 位基于 BIOS 或 64 位基于 UEFI 的计算机。</p>
<p>Windows PE 的 arm 版本可以引导基于 ARM 的 Pc。</p>
<p>关于个人电脑上运行 Windows PE 不同体系结构的详细信息，请参阅[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)。</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>WorkingDirectory</em></p></td>
<td align="left"><p>指定的工作目录<strong>Copype</strong>中创建目录结构并复制 Windows PE 文件的名称。 例如︰</p>
<pre class="syntax" space="preserve"><code>copype amd64 C:\winpe_amd64</code></pre>
<p><strong>Copype</strong>创建如下的目录结构。</p>
<pre class="syntax" space="preserve"><code>&lt;WorkingDirectory&gt;
&lt;WorkingDirectory&gt;\media
&lt;WorkingDirectory&gt;\mount</code></pre>
<p>当<strong>Copype</strong>复制到 Windows PE 基本映像<em>&lt;WorkingDirectory&gt;</em>\Media\Sources 文件夹中，它将从 Winpe.wim 到 Boot.wim 基本映像重命名。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[Makewinpemedia 命令行选项](makewinpemedia-command-line-options.md)

 

 






