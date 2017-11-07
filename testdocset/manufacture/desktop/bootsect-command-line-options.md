---
author: Justinha
Description: "Bootsect 命令行选项"
ms.assetid: 2021a0b5-955a-4193-a6e2-9864c047d82d
MSHAttr: PreferredLib:/library/windows/hardware
title: "Bootsect 命令行选项"
ms.openlocfilehash: a1c41bb9b45853d5ab110959d9355a30e083205b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bootsect-command-line-options"></a>Bootsect 命令行选项


Bootsect.exe 更新 Bootmgr 和 NT 加载程序 (**NTLDR**) 之间进行切换的硬盘分区的主启动代码。 您可以使用此工具来还原您的计算机上的启动扇区。 此工具取代了**FixFAT**和**FixNTFS**。

## <a name="span-idbootsectcommandsspanspan-idbootsectcommandsspanspan-idbootsectcommandsspanbootsect-commands"></a><span id="Bootsect_Commands"></span><span id="bootsect_commands"></span><span id="BOOTSECT_COMMANDS"></span>Bootsect 命令


Bootsect 使用下面的命令行选项︰

**bootsect {/ 帮助 | /nt52 | /nt60} {系统 |所有 |&lt;驱动器号︰&gt;} \[/强制\]/mbr**

例如，要应用到标记的卷与 NTLDR 兼容的主启动代码 E，使用下面的命令︰

**bootsect /nt52 e:**

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
<td align="left"><p><strong>/help</strong></p></td>
<td align="left"><p>显示这些用法说明。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/nt52</strong></p></td>
<td align="left"><p>适用与对<strong>SYS</strong>，<strong>所有</strong>，NTLDR 兼容的主启动代码或&lt;驱动器号&gt;。 <strong>SYS</strong>，<strong>所有</strong>安装的操作系统或&lt;驱动器号&gt;必须早于 Windows Vista。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/nt60</strong></p></td>
<td align="left"><p>应用 Bootmgr 对<strong>SYS</strong>，<strong>所有</strong>，与兼容的主启动代码或&lt;驱动器号&gt;。 <strong>SYS</strong>，<strong>所有</strong>安装的操作系统或&lt;驱动器号&gt;必须是 Windows 8、 Windows® 7、 Windows Vista、 Windows Server® 2012年，Windows Server 2008 R2 或 Windows Server 2008。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SYS</strong></p></td>
<td align="left"><p>更新用于启动 Windows 系统分区上的主启动代码。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>ALL</strong></p></td>
<td align="left"><p>更新所有分区的主启动代码。 <strong>全部</strong>选项不一定更新每个卷的启动代码。 相反，此选项将更新启动代码可用作 Windows 启动卷的卷上不包括没有与基础磁盘分区连接的动态卷。 存在此限制是因为启动代码必须位于磁盘分区的开始处。</p></td>
</tr>
<tr class="even">
<td align="left"><p>&lt;驱动器号&gt;</p></td>
<td align="left"><p>更新与此驱动器号关联的卷上的主启动代码。 如果是，将不会更新启动代码︰</p>
<ul>
<li><p>&lt;驱动器号&gt;不与卷相关联</p></li>
<li><p>&lt;驱动器号&gt;都与没有与基础磁盘分区连接的卷相关联。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/force</strong></p></td>
<td align="left"><p>启动代码更新的过程中，强制卸下卷。 您必须谨慎使用该选项。</p>
<p>如果 Bootsect.exe 不能获得独占卷访问权限，文件系统可能会覆盖在下次重新启动之前的启动代码。 Bootsect.exe 总是试图锁定和卸载卷之前每个更新。 <strong>指定/强制</strong>时，强制的卸除将尝试如果初始锁定失败。 锁可以失败，例如，如果目标卷上的文件当前正在由其他程序打开。</p>
<p>登录成功时，强制的卸除将启用独占卷访问权限和可靠的启动代码更新，即使初始锁定失败。 同时，强制的卸除将使无效目标卷上的文件的所有打开句柄。 从打开这些文件的程序，这可能导致意外的行为。 因此，请谨慎使用此选项。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/mbr</strong></p></td>
<td align="left"><p>而无需更改包含<strong>系统</strong>，<strong>所有</strong>，由指定的分区的磁盘的 0 扇区上的分区表中更新主引导记录或&lt;驱动器号&gt;。 使用<strong>/nt52</strong>选项，主引导记录时与早于 Windows Vista 操作系统兼容。 如果使用<strong>/nt60</strong>选项，主启动记录与 Windows 8、 Windows 7、 Windows Vista、 Windows Server 2012，Windows Server 2008 R2 或 Windows Server 2008 兼容。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[BCDboot 命令行选项](bcdboot-command-line-options-techref-di.md)

 

 






