---
title: "Windows 事件跟踪"
description: "Windows 事件跟踪"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 5130d144-de4d-4b6e-bfe9-e17aaddff7d0
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 80c1487927a74b014f3fff4b08c6c848bba32207
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="event-tracing-for-windows"></a>Windows 事件跟踪


事件跟踪 Windows (ETW) 基础结构的 Windows 性能 Toolkit 提供了基础。 这些工具提供一的组隐藏的复杂性直接使用 ETW 应用程序编程接口 (Api) 的程序。

本文提供了高级别的 ETW 简介。 ETW 有关的详细信息，请参阅[事件跟踪](http://go.microsoft.com/fwlink/p/?linkid=213103)。

ETW 可以一致、 简单获取内核和应用程序事件。 您可以启用或禁用事件捕获任何时候无需重新启动系统或过程。 Windows 性能分析器 (WPA) 呈现 ETW 收集集中易于理解的图形和表的信息。

您可以捕获并显示所选的事件非 invasively 识别和诊断系统和应用程序性能问题。 您可以启用或禁用动态跟踪的事件。 Windows 性能记录器 (WPR) 使用 ETW 来收集和组织关键的系统信息。 WPR 充当会话控制器中，启动和停止会话以及选择要记录的 ETW 事件。

WPA 使用 ETW 会话中生成的所有事件提供程序的事件跟踪日志 (ETL) 文件。 内核和应用程序事件可以提供关于系统操作的大量详细信息。 几乎每个内核事件，会影响整个系统的性能是已定义且可用的 WPA。

## <a name="related-topics"></a>相关的主题


[Windows 性能 Toolkit](index.md)

 

 







