---
author: Justinha
Description: What's New in Windows PE
ms.assetid: db434eb7-ef16-4edc-af6a-f0057c86a56e
MSHAttr: PreferredLib:/library/windows/hardware
title: What's New in Windows PE
ms.openlocfilehash: b9c3b6d71ea70261617bc2a6ceee9350f59d47b2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-windows-pe"></a>是什么在 Windows PE 中新


本主题描述 Windows 预安装环境 (Windows PE/WinPE) 的新的和更改的功能，并将其与以前版本的 Windows PE 和 MS-DOS 进行比较。

## <a name="span-idnewandchangedfunctionalityspanspan-idnewandchangedfunctionalityspanspan-idnewandchangedfunctionalityspannew-and-changed-functionality"></a><span id="New_and_Changed_Functionality"></span><span id="new_and_changed_functionality"></span><span id="NEW_AND_CHANGED_FUNCTIONALITY"></span>新建和更改的功能


下表比较的特性和功能，与以前的 Windows PE 版本︰

<table>
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能</th>
<th align="left">Windows PE 为 Windows 10</th>
<th align="left">Windows PE 5.0</th>
<th align="left">Windows PE 4.0</th>
<th align="left">Windows PE 3.x</th>
<th align="left">Windows PE 2.x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>操作系统部署</p></td>
<td align="left"><p>Windows 10、 Windows 8.1、 Windows Server 2012 R2、 Windows 8，Windows Server 2012，Windows 7 或 Windows Server 2008 R2。</p></td>
<td align="left"><p>Windows 8.1、 Windows Server 2012 R2、 Windows 8，Windows Server 2012，Windows 7 或 Windows Server 2008 R2。</p>
<p>不支持︰ Windows Vista 或 Windows Server 2008。</p></td>
<td align="left"><p>Windows 8，Windows Server 2012，Windows 7，Windows Server 2008 R2，Windows Vista 中或 Windows Server 2008。</p></td>
<td align="left"><p>Windows 7，Windows Server 2008 R2，Windows Vista 中或 Windows Server 2008。</p></td>
<td align="left"><p>Windows Vista 或 Windows Server 2008</p></td>
</tr>
<tr class="even">
<td align="left"><p>脚本用来部署 Windows PE</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>CopyPE 使用 Windows ADK 的更新。</p>
<p>MakeWinPEMedia 添加以创建 USB 闪存驱动器或 ISO 文件更容易。</p></td>
<td align="left"><p>包括 CopyPE 和 Oscdimg 工具。</p></td>
<td align="left"><p>包括 CopyPE 和 Oscdimg 工具。</p>
<p>Windows PE 2.1: Oscdimg 工具更新，可以支持更大的图像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>脚本撰写工具</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>.NET Framework 可选组件重命名为 WinPE_NetFx。</p>
<p>PowerShell 可选组件重命名为 WinPE_PowerShell。</p>
<p>Winpeshl.ini 允许您启动应用程序的命令行参数用引号括起来。 有关详细信息，请参阅[Winpeshl.ini 引用︰ 启动 WinPE 时启动应用程序](winpeshlini-reference-launching-an-app-when-winpe-starts.md)。</p></td>
<td align="left"><p>.NET framework 4.5 可选组件添加 (WinPE_NetFx4)。</p>
<p>PowerShell 3.0 的可选组件添加 (WinPE_PowerShell3)。</p></td>
<td align="left"><p>包含的命令行脚本工具。</p></td>
<td align="left"><p>包含的命令行脚本工具。</p></td>
</tr>
<tr class="even">
<td align="left"><p>图像捕获和服务工具</p></td>
<td align="left"><p>DISM 支持 Windows 10 和 Windows 图像处理和配置设计器 (ICD) 的功能。</p></td>
<td align="left"><p>DISM 支持 Windows 8.1 和 Windows Server 2012 R2 的图像，但不支持 Windows Vista 或 Windows Server 2008 的图像。 更多的信息，请参阅[DISM 的部署映像服务和管理技术参考的窗口](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)。</p></td>
<td align="left"><p>映像捕获工具附带新<code>dism /Capture-image</code>和<code>dism /Apply-image</code>的命令。</p>
<p>不支持服务的 Windows 8.1 或 Windows Server 2012 R2 图像。</p></td>
<td align="left"><p>[DISM 的部署映像服务和管理技术参考 Windows](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)添加。 DISM 是一个命令行工具，可用于自定义 Windows 或 Windows PE 映像。</p>
<p>PEImg 和 Pkgmgr 工具不支持 Windows PE 3.0。</p>
<p>ImageX 可用作捕获和应用映像的可选的应用程序。</p>
<p>不支持服务的 Windows 8.1 或 Windows Server 2012 R2 图像。</p></td>
<td align="left"><p><strong>PEImg</strong>用于对服务的 Windows PE 映像。</p>
<p>Windows PE 2.0 映像运行<strong>PEImg /prep</strong>后，图像不能修改。</p>
<p>ImageX 是作为用于捕获和应用映像的可选应用程序可用。</p>
<p><strong>Pkgmgr</strong>用于安装、 删除或更新 Windows 脱机映像中的程序包。</p>
<p>不支持服务的 Windows 8.1 或 Windows Server 2012 R2 图像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>优化 Windows PE</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>将配置信息提取功能。</p>
<p>默认的空闲空间量是 Pc 具有 1 GB 以上的 RAM 为 512 MB。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>较小的默认大小。 Windows PE 3.0 默认图像包含只有最少的资源来支持大多数部署方案。 您可以通过使用部署映像服务和管理 (DISM) 添加可选组件。</p>
<p>新<code>dism /apply-profiles</code>命令，您可以进一步减少到 Windows PE 3.0 图像的内容，只支持一组给定的应用程序所必需的那些文件。</p></td>
<td align="left"><p>Windows PE 2.1︰ 直接从硬盘引导到 RAM 磁盘不支持。</p>
<p>Windows PE 2.1︰ 可写 RAM 驱动器︰ Windows PE 时从只读介质引导，会自动创建可写的 RAM 磁盘 （驱动器 X） 并为通用的存储分配 32 兆字节 (MB) RAM 磁盘。 您可以使用<strong>PEImg /scratchspace</strong>自定义的大小，以兆字节为单位。 有效值为 32、 64、 128、 256 和 512。</p></td>
</tr>
<tr class="even">
<td align="left"><p>文件管理</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>文件管理发现和恢复添加可选组件未加密的卷中删除文件。</p></td>
<td align="left"><p>Windows PE 3.1︰ 基本映像包含到 4k/512e 驱动器支持相关的改进。</p></td>
<td align="left"><p>没有 4k/512e 驱动器的支持。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Memory</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>支持的最大值︰</p>
<ul>
<li><p>x 86: 64 GB</p></li>
<li><p>64: 4 TB x</p></li>
</ul></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>支持的最大值︰</p>
<ul>
<li><p>x 86: 4 GB</p></li>
<li><p>64: 128 GB x</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>虚拟化</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>Windows PE 3.0 包括所有 Hyper-V 驱动程序，显示驱动程序除外。 这样，Windows PE 运行在虚拟机管理程序。 支持的功能包括海量存储、 鼠标集成和网络适配器。</p></td>
<td align="left"><p>不受支持。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>网络连接</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>为启用网络设备通过 USB 实现 RNDIS 规范添加可选的远程网络驱动程序接口规范 (RNDIS) 功能。</p></td>
<td align="left"><p>Windows PE 3.1 基本映像包含 RNDIS 的二进制文件。</p>
<p>Windows PE 3.0︰[修补程序](http://support.microsoft.com/kb/972831)适用于 802.1 X (LAN) 的支持。</p>
<p>Windows PE 3.1 作为可选组件包括 802.1 X 二进制文件。 此包文件的名称是 WinPE Dot3Svc.cab。</p></td>
<td align="left"><p>支持 IPv4 和 IPv6。 不支持其它协议，如网间数据包交换/已排序数据包交换 (IPX/SPX)。</p>
<p>Windows PE 2.1︰[修补程序](http://support.microsoft.com/kb/975483)适用于 802.1 X (LAN) 的支持。</p></td>
</tr>
<tr class="even">
<td align="left"><p>恢复</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>WinRE 配置实用程序添加 (winrecfg.exe) 以支持脱机操作系统配置 Windows RE。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>支持 Windows 恢复环境 (Windows RE)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>安全性</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>安全启动的资源调配和管理 BitLocker 和受信任的平台模块添加的可选组件。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>支持 BitLocker 和受信任的平台模块。</p></td>
</tr>
<tr class="even">
<td align="left"><p>体系结构</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>支持 x86、 x64，以及基于 ARM 的 Pc。</p></td>
<td align="left"><p>情况没有变化。</p></td>
<td align="left"><p>支持 x86、 x64 和基于 Itanium 的计算机。</p></td>
</tr>
</tbody>
</table>

 

若要查看正在运行的 Windows PE 版本，请键入`regedit`并找到以下注册表项︰ **HKEY\_本地\_机\\软件\\Microsoft\\Windows NT\\CurrentVersion\\WinPE**。

## <a name="span-idcomparisonwithms-dosspanspan-idcomparisonwithms-dosspanspan-idcomparisonwithms-dosspancomparison-with-ms-dos"></a><span id="Comparison_with_MS-DOS"></span><span id="comparison_with_ms-dos"></span><span id="COMPARISON_WITH_MS-DOS"></span>使用 MS-DOS 的比较


Windows PE 是类似于 MS-DOS。 它还支持下列功能︰

-   NTFS 5。*x*文件系统，包括动态卷的创建和管理。

-   TCP/IP 网络和文件共享 （仅用于客户端）。

-   32 位或 64 位的 Windows 设备驱动程序。

-   Windows 应用程序编程接口 (API) 的子集。

-   CD、 DVD 和 USB 闪存驱动器。

-   Windows 部署服务服务器。

-   图像管理和维护 (DISM)。

-   Hyper-V 驱动程序 （除所有驱动程序显示驱动程序）。 这样，Windows PE 运行在虚拟机监控程序。 支持的功能包括海量存储、 鼠标集成和网络适配器。

-   可选支持 PowerShell、 Windows 管理规范 (WMI)、 Windows 数据访问组件 (Windows DAC)，以及 HTML 应用程序 (Hta)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

 

 






