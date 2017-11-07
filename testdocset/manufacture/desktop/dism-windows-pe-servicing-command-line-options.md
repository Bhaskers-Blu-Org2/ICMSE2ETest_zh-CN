---
author: Justinha
Description: "DISM Windows PE 服务命令行选项"
ms.assetid: d759221d-47ee-4f50-957e-3b978be22dea
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM Windows PE 服务命令行选项"
ms.openlocfilehash: da01f2b9a623d8873295be731e6eb558b72257e0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-windows-pe-servicing-command-line-options"></a>DISM Windows PE 服务命令行选项


您可以装载 Windows 预安装环境 (Windows PE) 映像和添加或删除程序包、 驱动程序和语言包使用相应的驱动程序文件包或国际服务命令。 也有可用于准备 Windows PE 环境，启用分析，请列出程序包并准备部署 Windows PE 映像的 Windows PE 映像的特定命令。

**重要**  
分析功能的 Windows PE 将删除 Windows 8.1 开头。

 

为处理 Windows PE 映像的基本语法如下︰

**DISM.exe** **/图像︰***&lt;路径\_到\_图像\_目录&gt;* \[ **dism\_全局\_选项**\] {**服务\_选项**} \[*&lt;服务\_参数&gt;*\]

除了部署映像服务和管理 (DISM) 的选项，下面的 Windows PE 服务选项可用于脱机映像。

**DISM.exe /Image:***&lt;路径\_到\_图像\_目录&gt;*\[ **/Get-PESettings** | **/Get-Profiling** | **/Get-ScratchSpace** | **/Get-TargetPath** | **/Set-ScratchSpace:***&lt;大小\_的\_ScratchSpace&gt;* | **/Set-TargetPath:***&lt;目标\_路径&gt;* | **/Enable-Profiling** | **/Disable-Profiling** | **/Apply-Profiles:***&lt;路径\_到\_myprofile.txt&gt; *\]

**重要**  
这些选项不能使用 Windows PE 的在线、 正在运行的版本。 您必须指定 Windows PE 映像使用**/图像︰***&lt;路径\_到\_图像\_目录&gt;*选项。

 

下表提供了有关如何在 Windows PE 映像上使用每个 Windows PE 服务选项的说明。 这些选项不是区分大小写的。

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
<td align="left"><p><strong>/ Get PESettings</strong></p></td>
<td align="left"><p>在 Windows PE 映像中显示 Windows PE 设置的列表。 该列表包含当前配置处理状态、 暂存空间设置和目标路径设置。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /Get-PESettings</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 获取分析</strong></p></td>
<td align="left"><p>检索该分析工具的 Windows PE 的启用/禁用状态。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /Get-Profiling</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Get ScratchSpace</strong></p></td>
<td align="left"><p>检索已配置的 Windows PE 系统卷空闲空间量。 此设置表示当在 ramdisk 模式下启动 Windows PE 系统卷上的可写的可用空间量。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /Get-ScratchSpace</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 目标路径获取</strong></p></td>
<td align="left"><p>检索 Windows PE 映像的目标的路径。 目标路径表示在启动时对 Windows PE 映像的根路径。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /Get-TargetPath</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 集-ScratchSpace:</strong><em>&lt;size_of_ScratchSpace&gt;</em></p></td>
<td align="left"><p>设置可用的空闲空间，以兆字节为单位。 有效值为 32、 64、 128、 256 和 512。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /set-ScratchSpace:128</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 设置目标路径︰</strong><em>&lt;目标路径&gt;</em></p></td>
<td align="left"><p>硬盘启动的情况下，此选项设置在该磁盘上的 Windows PE 映像的位置。</p>
<p>设置目标路径时，请注意以下限制︰</p>
<ul>
<li><p>该路径必须至少三个字符且不超过 32 个字符</p></li>
<li><p>该路径必须以字母 （任何信件从 C 到 Z） 开头</p></li>
<li><p>驱动器号后面必须跟 *:\*</p></li>
<li><p>路径的其余部分不能包含任何无效字符，例如 Unicode 字符</p></li>
<li><p>路径必须是绝对的不&quot;。&quot; or &quot;..&quot; 元素</p></li>
<li><p>路径不能包含任何空格或&quot;\\&quot;</p></li>
</ul>
<p>例如︰</p>
<p><strong>Dism /image:C:\test\offline /Set-TargetPath:X: \</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 启用分析</strong></p></td>
<td align="left"><p>启用分析 （文件日志记录），因此您可以创建自己的配置文件。 默认情况下，分析处于禁用状态。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /Enable-profiling</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 禁用分析</strong></p></td>
<td align="left"><p>关闭用于创建配置文件的文件日志记录。</p>
<p><strong>Dism /image:C:\test\offline /Disable-Profiling</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 应用的配置文件︰</strong><em>&lt;path_to_myprofile.txt&gt;</em></p></td>
<td align="left"><p><em>&lt;path_to_myprofiles.txt&gt; </em>必须是逗号分隔的列表模板的文件的名称。</p>
<p>不是自定义配置文件的 Windows PE 映像中删除任何文件。 它还检查对照核心配置文件以确保未删除的自定义应用程序文件和引导所必需的文件的自定义配置文件。 已使用任何配置文件自定义 Windows PE 映像不是可维护性。 但是， <strong>/Get-Profiling</strong>、 <strong>/Get-TargetPath</strong>和<strong>/Get-PESettings</strong>将起作用。 例如︰</p>
<p><strong>Dism /image:C:\test\offline /Apply-Profiles:C:\test\profiles\myprofile.txt</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


Windows PE 命令可用于更改仅在 Windows PE 3.0 及 Windows PE 映像中的国际设置。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows PE 为 Windows 10](winpe-intro.md)

[Wpeutil 命令行选项](wpeutil-command-line-options.md)

[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

 

 






