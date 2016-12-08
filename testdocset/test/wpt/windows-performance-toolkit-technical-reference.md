---
title: "Windows 性能 Toolkit 技术参考"
description: "Windows 性能 Toolkit Windows 评估和部署工具包中包含，包含产生深入的性能配置文件的 Windows 操作系统和应用程序的性能监视工具。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: f12f69dc-5b82-4a25-b829-a64365fafebc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 7410c883826eeb541593f9b9a07f4ae852d8e88c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-performance-toolkit-technical-reference"></a>Windows 性能 Toolkit 技术参考


Windows 性能 Toolkit [Windows 评估和部署工具包](http://go.microsoft.com/fwlink/p/?LinkId=526740)中包含，包含产生深入的性能配置文件的 Windows 操作系统和应用程序的性能监视工具。 本文档讨论 Windows 性能记录器 (WPR) 和 Windows 性能分析器 (WPA)。

## <a name="windows-performance-xperf-command-line"></a>Windows 性能 Xperf 命令行


Windows 性能 Toolkit 包含两个独立的工具︰ Windows 性能记录器 (WPR) 和 Windows 性能分析器 (WPA)。 此外前, 一个命令行工具 Xperf 维护支持。 但是，Xperfview 不再受支持。 必须打开和分析通过使用 WPA 的所有录制。

对于运行 Windows 性能 Toolkit 的系统要求如下︰

-   Windows 性能记录器 (WPR): Windows 8 或更高版本。

-   Windows 性能分析器 (WPA): Windows 8 或更高版本 Microsoft.NET framework 4.5 或更高版本。

您可以通过访问[Windows 内部程序](https://insider.windows.com/)下载 Windows 性能 Toolkit。

## <a name="contents"></a>内容


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>节</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[Windows 性能 Toolkit](index.md)</p></td>
<td><p>概述了常规 WPR 和 WPA。</p></td>
</tr>
<tr class="even">
<td><p>[Windows 性能 Toolkit 的新增功能](whats-new-in-the-windows-performance-toolkit.md)</p></td>
<td><p>描述此版本中提供的新功能。</p></td>
</tr>
<tr class="odd">
<td><p>[Windows 性能记录器](windows-performance-recorder.md)</p></td>
<td><p>提供了有关 WPR 完整文档。 在 MSDN，这包括完整的命令行和可扩展标记语言 (XML) 参考。</p></td>
</tr>
<tr class="even">
<td><p>[Xperf 命令行参考](http://go.microsoft.com/fwlink/?LinkId=234381)</p></td>
<td><p>为完成 Xperf 的参考资料。</p></td>
</tr>
<tr class="odd">
<td><p>[内核跟踪控件 API 参考](kernel-trace-control-api-reference.md)</p></td>
<td><p>介绍了内核跟踪控制 API，ETA 事件跟踪 API 支持向后兼容的现有脚本和配置文件的扩展名。</p></td>
</tr>
<tr class="even">
<td><p>[Windows 性能分析器](windows-performance-analyzer.md)</p></td>
<td><p>提供完全文档 WPA，使您能够分析 WPR 或者从评估平台创建的录制。</p></td>
</tr>
</tbody>
</table>

 

 

 






