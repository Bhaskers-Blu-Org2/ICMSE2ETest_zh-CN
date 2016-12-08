---
author: Justinha
Description: "DISM 支持的平台"
ms.assetid: c52337e1-19a0-46d9-aa17-c5b704ea1949
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 支持的平台"
ms.openlocfilehash: bdaa8da3b21d6da869b374fc0b35258194fe65aa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-supported-platforms"></a>DISM 支持的平台


部署映像服务和管理 (DISM) 的 Windows 10 版均可在 Windows 10 （家庭、 Pro、 企业和教育） 的桌面版本 Windows 服务器 2016年技术预览和 Windows 10 为 Windows 预安装环境 (WinPE)。

若要处理 Windows 10 映像，您将需要的 DISM 中，否则为可能会损坏图像的 Windows 10 版本。

若要使用 DISM 的 Windows 10 版本到以前版本的 Windows 上，Windows 评估和部署工具包 (ADK)[从本网站](http://go.microsoft.com/fwlink/p/?LinkId=526803)，安装和安装**部署工具**。 然后，开始**部署和图像处理工具环境**运行 DISM 命令。

若要使用以前版本的 Windows PE 的 DISM Windows 10 版本，请参阅[安装 Windows 10 使用早期版本的 Windows PE](copy-dism-to-another-computer.md)。

请注意，不能处理的以前版本的 Windows 映像时始终很 DISM 中的新增功能。 若要了解详细信息，请参阅[DISM 引用](dism-reference--deployment-image-servicing-and-management.md)。

## <a name="span-iddtspdismspanspan-iddtspdismspansupported-platforms"></a><span id="DTSP_DISM"></span><span id="dtsp_dism"></span>支持的平台


主机部署环境是操作系统运行 DISM。 目标图像是正在处理的映像。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">主机部署环境</th>
<th align="left">对于 Windows 10 目标图像︰ Windows 10，10，Windows 或 WinPE</th>
<th align="left">目标图像:、 Windows 8.1，Windows 服务器 2016年技术预览，Windows Server 2012 R2 或 WinPE 5.0 （x86 或 x64）</th>
<th align="left">目标图像︰ Windows 8、 Windows Server 2012 或 WinPE 4.0 （x86 或 x64）</th>
<th align="left">目标图像︰ Windows 7，Windows Server 2008 R2 或 WinPE 3.0 （x86 或 x64）</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Windows 10 （x86 或 x64）</p></td>
<td align="left">支持</td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows--服务器 2016年各种技术的预览，（x86 或 x64）</p></td>
<td align="left">支持</td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8.1 （x86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2012 R2 (x 86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 8 （x86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2012 （x86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows 7 （x86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 8 版本的支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows Server 2008 R2 (x 86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 8 版本的支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows Server 2008 SP2 (x 86 或 x64）</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 8 版本的支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="even">
<td align="left"><p>对于 Windows 10 WinPE x86</p></td>
<td align="left">支持</td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>对于 Windows 10 WinPE x64</p></td>
<td align="left">支持︰ X64 目标仅图像</td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
</tr>
<tr class="even">
<td align="left"><p>WinPE 5.0 x86</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>WinPE 5.0 x64</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持︰ X64 目标仅图像</td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
</tr>
<tr class="even">
<td align="left"><p>WinPE 4.0 x86</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>WinPE 4.0 x64</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持︰ X64 目标仅图像</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
</tr>
<tr class="even">
<td align="left"><p>WinPE 3.0 x86</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持</p></td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 8 版本的支持</p></td>
<td align="left"><p>支持</p></td>
</tr>
<tr class="odd">
<td align="left"><p>WinPE 3.0 x64</p></td>
<td align="left">使用 DISM 的 Windows 10 版本的支持︰ X64 目标仅图像</td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 的 8.1 版本的支持︰ X64 目标仅图像</p></td>
<td align="left"><p>使用 DISM 或更高版本的 Windows 8 版本的支持︰ X64 目标仅图像</p></td>
<td align="left"><p>支持︰ X64 目标仅图像</p></td>
</tr>
</tbody>
</table>

 

不支持可恢复文件系统 （引用）。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[安装 Windows 10 评估和部署工具包 (ADK)](http://go.microsoft.com/fwlink/p/?LinkId=526803)

[DISM 引用 (部署映像服务和管理)](dism-reference--deployment-image-servicing-and-management.md)

[安装 Windows 10 使用早期版本的 Windows PE](copy-dism-to-another-computer.md)

 

 






