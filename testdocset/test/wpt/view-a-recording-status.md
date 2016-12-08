---
title: "查看录制状态"
description: "查看录制状态"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: a0df113f-d0be-4560-9f6a-3df9ae93bdd4
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 4d89a23a0160551f08ea4830bff1122158df5a91
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="view-a-recording-status"></a>查看录制状态


开始录制在 Windows 性能记录器 (WPR) 后，可以按照记录的状态，因为据调查。 本文介绍了录制状态。

## <a href="" id="viewstat"></a>


当您通过使用 WPR 用户界面 (UI) 开始录制时，录制状态立即 WPR 在屏幕上显示。 如果您通过使用 WPR 命令行界面启动录制，您可以使用下列方法之一来查看录制状态︰

-   在命令提示符窗口中，键入`wpr –status`。 有关此命令的详细信息，请参阅[WPR 命令行选项](wpr-command-line-options.md#status)。

-   打开 WPR UI。 从 WPR 命令行启动录制的状态将显示为。

有关如何使用这些方法来开始录制 WPR 的详细信息，请参阅[开始录制](start-a-recording.md)和[WPR 命令行选项](wpr-command-line-options.md)。

**请注意**  
如果录制开始通过 WPR WPR 只能显示记录的状态。 它不能显示录制唱片由 Xperf 或其它应用程序启动的状态。

 

录制状态显示以下信息︰

-   **记录时间**︰ 这是录制已运行的时间长度。

-   **缓冲**︰ 这是记录正在使用的缓冲区大小。 它被显示在 MB 和可用缓冲池内存的百分比。

-   **丢弃事件**︰ 丢失事件自启动录制的次数。 有关此问题的详细信息，请参阅[避免丢失事件](avoid-lost-events.md)。

## <a name="related-topics"></a>相关的主题


[会话](sessions.md)

 

 







