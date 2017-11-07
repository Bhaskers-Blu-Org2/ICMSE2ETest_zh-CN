---
author: Justinha
Description: auditSystem
ms.assetid: 86d77a1f-2244-4600-80cd-65930a2cee3d
MSHAttr: PreferredLib:/library/windows/hardware
title: auditSystem
ms.openlocfilehash: 7598b94e9b291a55f6de8d48ab89b9f05cdc11ec
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="auditsystem"></a>auditSystem


**AuditSystem**的配置阶段处理无人参与的 Windows® 安装设置在审核模式下的系统环境中。 立即在[auditUser](audituser.md)配置阶段中，用来在用户上下文中应用设置之前先运行**auditSystem**的配置阶段。 当 Windows 启动到审核模式、 **auditSystem**配置阶段和无人值守的 auditUser Windows 安装程序设置处理。

审核模式使 Oem 和公司可以向主 Windows 映像安装附加的设备驱动程序、 应用程序和其他更新。 使用审核模式，可以维护很少的映像，因为您可以用最小的驱动程序和应用程序集创建参考映像。 在审核模式期间再使用其他驱动程序更新参考映像。 此外，然后您可以测试和向客户发售计算机前 Windows 映像上解决任何问题相关与出现故障或未正确安装的设备。 审核模式是可选的。

下图显示在审核模式下处理后的**auditSystem**配置阶段。

![auditmode 的配置阶段](images/dep-win8-l-auditmode.jpg)

仅在您配置 Windows 安装程序启动到审核模式时， **auditSystem**的配置阶段运行。 在您能够启动到审核模式，通过使用**审核**选项，使用**sysprep**命令或**sysprep**命令与**一般化**和**审核**选项，或者您可以在 Microsoft Windows 部署组件中指定**重新封装**设置。 有关详细信息，请参阅[审核模式概述](audit-mode-overview.md)和[启动到审核模式或 OOBE 的 Windows](boot-windows-to-audit-mode-or-oobe.md)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[配置阶段的工作](how-configuration-passes-work.md)

[auditUser](audituser.md)

[一般化](generalize.md)

[offlineServicing](offlineservicing.md)

[oobeSystem](oobesystem.md)

[专门负责](specialize.md)

[windowsPE](windowspe.md)

 

 






