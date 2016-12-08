---
title: "Windows 性能 Toolkit 的新增功能"
description: "Windows 性能 Toolkit 的新增功能"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 3e27707c-fcba-4052-8cd9-bd04760b7439
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 1cd94adaaccae6449803205a6a63722f0bf3deda
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="whats-new-in-the-windows-performance-toolkit"></a>Windows 性能 Toolkit 的新增功能


Windows 性能分析器 (WPA) 形象从 Windows 性能记录器和 Windows 评估控制台跟踪与关系图和表以便可以分析系统和应用程序的性能。 WPA 提供了下列新功能︰

-   分析助手显示有用的内容，以帮助您确定如何以最佳方式使用一个给定的图形、 预设或分析选项卡的窗格。 为分析助手，让您的格式文本支持您设置文本格式以更方便地阅读和分析，以及将链接添加到参考资料、 视频或 web 上的更多详细的帮助页。

-   [WPA 图形的列表](list-of-wpa-graphs.md)供您参考

-   新版本的[文件菜单](introduction-to-the-wpa-user-interface.md)（称为丰富菜单） 切换到经典菜单上的选项

-   时间[矩形查看器](how-to-use-the-rectangle-viewer.md)，您可以直观地显示出了什么问题在屏幕上您的跟踪过程中点

-   [感兴趣的区域](regions-of-interest.md)，您可以突出显示在跟踪中重要的时间范围

-   创建标签，可帮助您更好的[堆栈标记](stack-tags.md)标识调用 stack(s) 中的哪些部分会受到影响

-   支持在单个会话中的多个跟踪

-   恢复配置文件支持

Windows 性能记录器 (WPR) 是一种性能工具，可用来记录系统事件，可以通过使用 WPA 来分析。 WPR 提供了以下新功能︰

-   记录跟踪之后, 现在可以立即打开它在 WPA 通过选择**在 WPA 打开**按钮。

-   直接处理的 CLR 符号，因此不不需要在配置和使用[NGEN 支持](using-clr-40-ngen-pdb-support.md)任何标志

内核跟踪控件 API 参考介绍内核跟踪控件 API 的 WPA 的以前版本中可用。 此 API 是 ETA 事件跟踪 API 的扩展，并支持向后兼容的现有脚本和配置文件。 但是，它已过时，并且应使用当前的版本创建新的配置文件。 没有公共 API 仅供 WPA 的当前版本。 利用此 API，捕获内核堆栈跟踪，合并多个跟踪文件进行分析，并在合并文件中包括系统信息。 有时，函数添加或更新。 本文引用添加了下列新功能︰

-   [StartHeapTrace](startheaptrace.md)

-   [UpdateHeapTrace](updateheaptrace.md)

## <a name="related-topics"></a>相关的主题


[Windows 性能 Toolkit 技术参考](windows-performance-toolkit-technical-reference.md)

 

 







