---
author: Justinha
Description: "Microsoft.NET Framework 3.5 部署注意事项"
ms.assetid: c231ba55-4181-47c0-bd16-f63e428f555f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Microsoft.NET Framework 3.5 部署注意事项"
ms.openlocfilehash: 6f8e47e77ffaab1e7a869f91c6a93a48cb773a2a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="microsoft-net-framework-35-deployment-considerations"></a>Microsoft.NET Framework 3.5 部署注意事项


.NET Framework 3.5 不包含默认情况下，在 Windows 10 或 Windows 服务器 2016，但您可以下载并将其部署为应用程序兼容性。 本部分介绍这些部署选项。

**在此部分中︰**

-   [部署.NET Framework 3.5 的需求设置使用组策略功能](deploy-net-framework-35-by-using-group-policy-feature-on-demand-setting.md)
-   [通过使用部署映像服务和管理 (DISM) 部署.NET Framework 3.5](deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism.md)
-   [通过使用 Windows PowerShell 启用.NET Framework 3.5](enable-net-framework-35-by-using-windows-powershell.md)
-   [通过使用控制面板和 Windows 更新 (仅适用于 Windows 8) 启用.NET Framework 3.5](enable-net-framework-35-by-using-control-panel-and-windows-update--windows-8-only.md)
-   [通过使用添加角色和功能向导启用.NET Framework 3.5](enable-net-framework-35-by-using-the-add-roles-and-features-wizard.md)
-   [.NET Framework 3.5 部署错误和解决步骤](net-framework-35-deployment-errors-and-resolution-steps.md)

## <a name="span-idintroductionspanspan-idintroductionspanspan-idintroductionspanintroduction"></a><span id="Introduction"></span><span id="introduction"></span><span id="INTRODUCTION"></span>介绍


Windows 10 或 Windows 服务器 2016年包括.NET Framework 4.6，完整的 Windows 组件支持生成和运行应用程序和 web 服务的下一代。 .NET Framework 提供的托管类型，它们可用于为 Windows 创建 Windows 应用商店应用程序，通过使用 C 子集\#或 Visual Basic。 有关详细信息，请参见[.NET Framework](http://go.microsoft.com/fwlink/p/?linkid=329972)。

需要启用.NET Framework 3.5 的元数据包含在默认的 Windows 映像中**(\\源\\install.wim**)。 实际的二进制文件不是在图像中。 *禁用删除负载*称为此功能状态。

您可以从 Windows Update 或安装媒体中的获得.NET Framework 3.5 负载文件**\\源\\sxs**文件夹。 有关详细信息，请参阅[安装.NET Framework 3.5](http://go.microsoft.com/fwlink/p/?linkid=257556)。 启用了.NET Framework 3.5 功能后，文件从 Windows 更新其他操作系统文件一样提供服务。

如果您升级到 Windows 服务器 2016年的从 Windows 7 （其中包括.NET Framework 3.5.1[默认情况下](http://blogs.msdn.com/b/e7/archive/2009/03/06/beta-to-rc-changes-turning-windows-features-on-or-off.aspx)为 Windows 10） 或 Windows Server 2008 R2 （其安装的.NET Framework 3.5.1 功能），将自动启用.NET Framework 3.5。

如果您有关于此主题的反馈，请访问相应的 Microsoft 论坛︰

-   [Windows IT 专业人员](http://social.technet.microsoft.com/Forums/windows/home?category=w8itpro)
-   [Windows 服务器](http://social.technet.microsoft.com/Forums/windowsserver/home?category=windowsserver)
-   [Windows 应用商店应用程序](http://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps)

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 服务器安装选项](http://go.microsoft.com/fwlink/p/?linkid=251454)

 

 






