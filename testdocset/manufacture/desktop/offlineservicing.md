---
author: Justinha
Description: offlineServicing
ms.assetid: 8c921c85-c986-419c-9f93-bdacd9441abb
MSHAttr: PreferredLib:/library/windows/hardware
title: offlineServicing
ms.openlocfilehash: 12f000093127dcafe144db254fd23d8b8c92e7f3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="offlineservicing"></a>offlineServicing


使用**offlineServicing**配置阶段到脱机映像 Microsoft® Windows® 应用无人参与的安装设置。 在此配置阶段中，您可以添加语言包、 更新，设备驱动程序或其他程序包脱机映像。

在 Windows 安装期间运行的**offlineServicing**配置阶段。 安装程序提取并安装的 Windows 映像，然后执行部署映像服务和管理 (Dism.exe) 工具。 在列出的包`<servicing>`节和设置在`<offlineServicing>`部分中的答案文件应用于脱机 Windows 映像。

此外，可以使用部署映像服务和管理工具使用应答文件应用**offlineServicing**过程中的设置。 有关详细信息，请参阅[Windows 映像使用 DISM 服务](service-a-windows-image-using-dism.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[配置阶段的工作](how-configuration-passes-work.md)

[auditSystem](auditsystem.md)

[auditUser](audituser.md)

[一般化](generalize.md)

[oobeSystem](oobesystem.md)

[专门负责](specialize.md)

[windowsPE](windowspe.md)

 

 






