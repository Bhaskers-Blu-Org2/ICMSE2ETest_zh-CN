---
author: Justinha
Description: "Makewinpemedia 命令行选项"
ms.assetid: b3fc26e8-96a0-4fca-9678-ac895835b7e0
MSHAttr: PreferredLib:/library/windows/hardware
title: "Makewinpemedia 命令行选项"
ms.openlocfilehash: 1801c235255c49c44a8b8b92b20349902c3f8c74
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="makewinpemedia-command-line-options"></a>Makewinpemedia 命令行选项


**Makewinpemedia**工具是新的 Windows 8。 **Makewinpemedia**可用于创建可引导的 Windows 预安装环境 (Windows PE) 介质。 运行**Copype**工具是用于创建可引导介质的先决条件。 **Copype**创建 Windows PE 文件的目录结构并复制所需的 Windows PE 的媒体文件。 有关详细信息，请参阅[Copype 命令行选项](copype-command-line-options.md)和[WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)。

## <a name="span-idmakewinpemediacommand-lineoptionsspanspan-idmakewinpemediacommand-lineoptionsspanspan-idmakewinpemediacommand-lineoptionsspanmakewinpemedia-command-line-options"></a><span id="Makewinpemedia_Command-Line_Options"></span><span id="makewinpemedia_command-line_options"></span><span id="MAKEWINPEMEDIA_COMMAND-LINE_OPTIONS"></span>Makewinpemedia 命令行选项


**Makewinpemedia**工具使用以下的命令行选项。

**Makewinpemedia**{*/ufd* | */iso*}\[ */f* \] * &lt;WorkingDirectory&gt; &lt;DestinationLocation&gt; *

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
<td align="left"><p><strong>/ufd</strong></p></td>
<td align="left"><p>指定要创建的媒体类型的 USB 闪存驱动器。 例如︰</p>
<pre class="syntax" space="preserve"><code>Makewinpemedia /ufd C:\winpe_amd64 F:</code></pre>
<p>其中 F 是 USB 闪存驱动器的驱动器号。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/iso</strong></p></td>
<td align="left"><p>为要创建的媒体类型指定.iso 文件 （CD 或 DVD）。 例如︰</p>
<pre class="syntax" space="preserve"><code>Makewinpemedia /iso C:\winpe_amd64 C:\winpe_x64\winpe_amd64.iso</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/f</strong></p></td>
<td align="left"><p>可选项。 取消格式化 USB 闪存驱动器或覆盖现有.iso 文件之前显示确认消息。 例如︰</p>
<pre class="syntax" space="preserve"><code>Makewinpemedia /ufd /f C:\winpe_amd64 F:</code></pre>
<p>其中 F 是 USB 闪存驱动器的驱动器号。</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>&lt;WorkingDirectory&gt;</em></p></td>
<td align="left"><p>指定工作目录中<strong>Copype</strong>工具创建的 Windows PE 目录结构并复制所需的文件，用于创建可引导的介质的名称。 例如︰</p>
<pre class="syntax" space="preserve"><code>C:\winpe_amd64</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><em>&lt;DestinationLocation&gt;</em></p></td>
<td align="left"><p>如果您使用<strong>/ufd</strong>选项或.iso 文件的名称如果您正在使用<strong>/iso</strong>选项，指定的 USB 闪存驱动器的驱动器号。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[Oscdimg 命令行选项](oscdimg-command-line-options.md)

 

 






