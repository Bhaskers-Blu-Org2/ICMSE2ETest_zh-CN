---
title: "详细信息级别"
description: "详细信息级别"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 8a1de1e7-dea5-4ab2-b707-2a1ee109b0f1
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f1061098643d678b3dab7a72349f27f674af2f84
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="detail-level"></a>详细信息级别


Windows 性能记录器 (WPR) 录制配置文件控制录制的所有方面。 对于 WPR 每个配置文件，您必须选择详细信息级别。 可用的级别是**光**和**详细**。 计时声音录制主要用于**光**详细信息级别。 **详细**详细程度提供了进行分析所需的详细的信息。 内置的配置文件支持**详细**和**指示灯**的详细信息级别。

默认情况下，在两个 WPR 用户界面 (UI) 和 WPR 命令行选择的**详细**级别。

在创作自定义配置文件，我们建议您首先定义简易版和详细的版本相同的.wprp 文件中。 这些文件可以包含最多四个配置文件定义︰ 一个用于每个详细信息级别和日志记录模式组合。

## <a name="related-topics"></a>相关的主题


[WPR 功能](wpr-features.md)

[记录模式](logging-mode.md)

[3.配置文件定义](3-profile-definitions.md)

[更改明细数据级别](change-the-detail-level.md)

[编写配置文件记录](authoring-recording-profiles.md)

 

 







