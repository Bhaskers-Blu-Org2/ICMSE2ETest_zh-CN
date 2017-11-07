---
author: kpacquer
Description: "以下功能可以用在制造模式下运行的设备。"
ms.assetid: 6f675ace-3f76-4421-8109-16fdf9e469fd
MSHAttr: PreferredLib:/library/windows/hardware
title: "可选功能，用于制造模式"
ms.openlocfilehash: 51da87396efc2459291e971054d3b698f5416722
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="optional-features-for-manufacturing-mode"></a>可选功能，用于制造模式


以下功能可以用在制造模式下运行的设备。

**请注意** 所有的可选功能，附带 10 Windows Mobile 可以使用，太。 有关其他可选功能的详细信息，请参阅[构建映像的可选功能](https://msdn.microsoft.com/library/windows/hardware/dn756780)。

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能 </th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>BCDEDIT</p></td>
<td align="left"><p>将 bcdedit.exe 添加到此图像可查看开发支持。 这不应包括在最终零售图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGMODEBCD</p></td>
<td align="left"><p>添加要启用制造模式中的 OS 映像的完整的 BCD 条目。 您应该删除此设备离开工厂之前。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MFGSTARTUP</p></td>
<td align="left"><p>将 startup.bsc 文件添加到的制造模式图像，需要使用 MOBILECOREBOOTSH 功能时。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGDEVTOOLS</p></td>
<td align="left"><p>向制造模式图像，如 tlist.exe、 sc.exe、 shutdown.exe 有用开发工具的集合。 这不应包括在最终的制造模式图像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MFGTELNETFTP</p></td>
<td align="left"><p>将 Telnet 和 TFTP 服务器添加到制造模式图像。 您可以将其保留在最终图像进行处理，因为它们仅运行时该设备处于制造模式。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGTSHELL</p></td>
<td align="left"><p>TShell 功能向制造模式图像。 您可以使其保持在最终图像处理由于仅运行时该设备处于制造模式。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MOBILECOREBOOTSH</p></td>
<td align="left"><p>使 bootsh 服务 (bootshscv)，以便可以使用 startup.bsc，如 telnet 和 ftp 中的功能。 当指定 MFGTELNETFTP 功能时，这是必需的。 您可以保持其服务由于只运行设备时在制造模式下的图像。</p></td>
</tr>
</tbody>
</table>

 

 

 





