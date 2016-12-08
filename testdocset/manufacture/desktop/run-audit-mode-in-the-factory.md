---
author: Justinha
Description: "在工厂中运行审核模式"
ms.assetid: e8262c69-3fae-455e-9cbd-88c486f92094
MSHAttr: PreferredLib:/library/windows/hardware
title: "在工厂中运行审核模式"
ms.openlocfilehash: bb4da88d9308ec72a8e06353a5eb42a210503128
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="run-audit-mode-in-the-factory"></a>在工厂中运行审核模式


在生成的订单方案 Oem 可以引导目标计算机以便审核模式安装的语言特定于客户的应用程序、 驱动程序、 和进行其他配置。

最终装配的电脑后完成完整性测试，以确保正确配置了电脑。

准备好后，启动 Windows PE 或另一个操作系统，您可以将自定义 Windows 映像安装到 PC 电脑。 您可以启动电脑通过 USB 密钥，或者您可以启动从使用 PXE 启动，Windows 部署服务的网络电脑。

我们建议使用 Windows PE 和 DISM 启动 PC 并应用自定义 Windows 映像。

-   [应用使用 DISM 的映像](apply-images-using-dism.md)

-   [对于 Windows 10 WinPE](winpe-intro.md)

-   [Windows 部署服务概述](http://technet.microsoft.com/library/hh831764.aspx)

应用图像之后，您可以启动电脑到审核模式。

-   [审核模式概述](audit-mode-overview.md)

在审核模式下，您可以安装客户请求软件，驱动程序特定于电脑和其他项目。 同时您还可以在审核模式下安装最新的 Windows 更新。 下面的主题转到有关如何安装驱动程序、 语言包和 Windows 更新的更多详细信息︰

-   [设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)

-   [语言包](language-packs-and-windows-deployment.md)

-   [使用 DISM Windows 映像提供服务](service-a-windows-image-using-dism.md)

请记住，安装则将安装在工厂地板增加装配，所花费的时间更多项目，和中 PC。

审核模式安装完成后，您必须运行 sysprep /oobe 以确保最终用户经历的现成的经验，并接受许可协议条款。 应抓住在 Windows 安装程序恢复分区，以帮助用户停留在 PC 到出厂默认值。 通过在工厂中执行此操作，可确保客户进行订单生成自定义项是恢复图像中。

您将需要启动 Windows PE 中，再次以捕获和应用到恢复分区的 Windows 安装到 PC。

下面的主题描述如何创建恢复映像︰

-   [将按钮重置功能的部署](deploy-push-button-reset-features.md)

恢复映像被捕获后，您可以关闭电脑、 框，和运。

根据单位发卷，您可能需要考虑提取一个或多个计算机离线以确保您构建的系统满足质量要求。

 

 





