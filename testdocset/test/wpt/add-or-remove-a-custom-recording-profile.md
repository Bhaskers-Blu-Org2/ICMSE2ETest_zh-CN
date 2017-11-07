---
title: "添加或删除自定义录制配置文件"
description: "添加或删除自定义录制配置文件"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0fc967f2-9acb-42ac-b4dc-463c6971fd13
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: e683ace937b830da9057aec2647a6bfd2b07affc
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="add-or-remove-a-custom-recording-profile"></a>添加或删除自定义录制配置文件


本过程描述了如何在 Windows 性能记录器 (WPR) 用户界面 (UI) 中添加自定义录制的配置文件。 有关如何从命令行启动录制的信息，请参阅[WPR 命令行选项](wpr-command-line-options.md)。

**若要添加记录的配置文件**

1.  在 WPR 屏幕上，如果隐藏了选项，单击**其他选项**。

2.  单击**添加配置文件**。

3.  导航到包含配置文件的位置，选择.wprp 文件，然后单击**打开**。 WPR 将添加到配置文件之前会验证.wprp 文件的架构。

4.  重复步骤 2 和 3 中添加额外的配置文件。 最多 64 配置文件可用于单个录制。

您添加的配置文件将显示在**自定义尺寸**下。

**删除录制配置文件**

1.  在 WPR 屏幕上，如果隐藏了选项，单击**其他选项**。

2.  右键单击您要删除，然后单击**删除配置文件**的自定义配置文件。

**删除配置文件**按钮是自定义的配置文件都存在时才可见。 您只能删除自定义配置文件︰ 您不能删除内置的配置文件。

## <a name="related-topics"></a>相关的主题


[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

[编写配置文件记录](authoring-recording-profiles.md)

 

 







