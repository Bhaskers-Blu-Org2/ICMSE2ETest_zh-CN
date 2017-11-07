---
title: "Windows 性能 Toolkit"
description: "Windows 性能 Toolkit Windows 评估和部署工具包中包含，包含产生深入的性能配置文件的 Windows 操作系统和应用程序的性能监视工具。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ef3d3649-4d0e-4207-833c-f58130aca12f
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: d2951093c53630f877b476afa62f4689c6f4c63f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-performance-toolkit"></a>Windows 性能 Toolkit


Windows 性能 Toolkit [Windows 评估和部署工具包](http://go.microsoft.com/fwlink/p/?LinkId=526740)中包含，包含产生深入的性能配置文件的 Windows 操作系统和应用程序的性能监视工具。 本文档讨论 Windows 性能记录器 (WPR) 和 Windows 性能分析器 (WPA)。

## <a name="windows-performance-toolkit"></a>Windows 性能 Toolkit


Windows 性能 Toolkit 包含两个独立的工具︰ Windows 性能记录器 (WPR) 和 Windows 性能分析器 (WPA)。 此外前, 一个命令行工具 Xperf 维护支持。 但是，Xperfview 不再受支持。 必须打开和分析通过使用 WPA 的所有录制。

对于运行 Windows 性能 Toolkit 的系统要求如下︰

-   Windows 性能记录器 (WPR): Windows 8 或更高版本。

-   Windows 性能分析器 (WPA): Windows 8 或更高版本 Microsoft.NET framework 4.5 或更高版本。

### <a name="windows-performance-recorder"></a>Windows 性能记录器

WPR 是一个功能强大的记录工具，创建跟踪 Windows 事件 (ETW) 录制。 可以通过用户界面 (UI) 或从命令行运行 WPR。 WPR 提供内置的配置文件，可用于选择要记录的事件。 或者，您还可以创作自定义配置文件的 XML 中。 WPR 还可以调用并通过使用**WPRControl**应用程序编程接口 (API) 来控制。 关于 WPRControl API 的详细信息，请参阅[WPRControl API 参考](http://go.microsoft.com/fwlink/p/?linkid=223235)。

有关的详细的演练和基本过程，请参阅[WPR 快速入门](wpr-quick-start.md)。 WPR UI 的完整文档，请参阅[WPR 功能](http://go.microsoft.com/fwlink/p/?linkid=223236)。 有关命令行选项的参考，请参阅[WPR 命令行选项](http://go.microsoft.com/fwlink/p/?linkid=223233)。 有关分步过程，请参阅[WPR 帮助主题](http://go.microsoft.com/fwlink/p/?linkid=223237)。 主要方案的讨论，请参阅[WPR 方案](windows-performance-recorder-common-scenarios.md)。 有关完整的参考资料，包括记录配置文件 XML 参考和旧式 Xperf 参考，请参阅[WPR 参考](http://go.microsoft.com/fwlink/p/?linkid=223245)。

### <a name="windows-performance-analyzer"></a>Windows 性能分析器

WPA 是一种功能强大的分析工具，结合丰富的图形功能非常灵活的用户界面和数据表格可以透视，并具有完整文本搜索功能。 WPA 提供**问题**窗口来浏览任何确定的根本原因。

有关的详细的演练和基本过程，请参阅[WPA 快速入门指南](wpa-quick-start-guide.md)。 WPR UI 的完整文档，请参阅[WPA 功能](http://go.microsoft.com/fwlink/p/?linkid=223251)。 有关分步过程，请参阅[WPA 操作方法主题](http://go.microsoft.com/fwlink/p/?linkid=223252)。 有关的主要方案的扩展讨论，请参阅[WPA 方案](windows-performance-analyzer-common-scenarios.md)。

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
<td><p>[Windows 性能 Toolkit 的新增功能](whats-new-in-the-windows-performance-toolkit.md)</p></td>
<td><p>描述此版本中提供的新功能。</p></td>
</tr>
<tr class="even">
<td><p>[Windows 性能记录器](windows-performance-recorder.md)</p></td>
<td><p>提供了有关 WPR 完整文档。 在 MSDN，这包括完整的命令行和可扩展标记语言 (XML) 参考。</p></td>
</tr>
<tr class="odd">
<td><p>[Xperf 命令行参考](http://go.microsoft.com/fwlink/?LinkId=234381)</p></td>
<td><p>为完成 Xperf 的参考资料。</p></td>
</tr>
<tr class="even">
<td><p>[内核跟踪控件 API 参考](kernel-trace-control-api-reference.md)</p></td>
<td><p>介绍了内核跟踪控制 API，ETA 事件跟踪 API 支持向后兼容的现有脚本和配置文件的扩展名。</p></td>
</tr>
<tr class="odd">
<td><p>[Windows 性能分析器](windows-performance-analyzer.md)</p></td>
<td><p>提供完全文档 WPA，使您能够分析 WPR 或者从评估平台创建的录制。</p></td>
</tr>
<tr class="even">
<td><p>[Windows 性能逐步式指南](windows-performance-step-by-step-guides.md)</p></td>
<td><p>提供说明如何执行实验，针对常见的性能情况。</p></td>
</tr>
</tbody>
</table>

 

 

 






