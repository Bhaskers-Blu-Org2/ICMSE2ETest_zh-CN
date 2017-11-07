---
title: "Windows 评估服务概述"
description: "Windows 评估服务概述"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 192c0739-dabd-4ff8-9ac8-5bf6e026757f
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 716b3419d98aad9d33d6bc16cae15121d086a813
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-services-overview"></a>Windows 评估服务概述


Windows 评估服务可用于实现自动化调度的从一个中心位置的评估在多台计算机上运行。 它用来查找质量问题并加快问题的解决。 它非常适合用于提供在测试过程中的保持一致性和启用更快地解决问题。

## <a name="how-does-windows-assessment-services-work"></a>Windows 评估服务是如何工作的？


Windows 评估服务已被配置为进行交互并在 Windows 评估服务共享存储资产，如测试计算机，Windows 映像和应答文件的测试框架。 如果它安装在 Windows Server 2012，Windows 部署服务 (Windows DS) 提供动态驱动程序资源调配 (DDP) 和计算机发现和 PXE 基于映像部署用来测试计算机。 完成评估后，结果被复制到服务器和存储在 Windows 评估服务的结果共享，以便他们可以在 Windows 评估服务的客户端 (Windows ASC) 中。 Windows ASC 是使用与 Windows 评估服务进行交互的图形用户界面。

Windows 评估服务和 Windows ASC 使您可以执行下列操作︰

-   从 Windows ASC 的计算机向一台 Windows 评估服务服务器发送作业的多个请求

-   管理计算机库存并评估全部或部分库存中测试计算机

-   使用各种计算机和各种图像来创建项目

-   创建包含一个或多个评估的工作

-   一个或多个测试计算机上运行的作业

-   在服务器释放用于其他用途的测试计算机上运行对评估结果的分析

-   与更多的资源，不是测试的计算机的服务器上运行的评估结果分析

-   重新运行分析的评估结果，使用更新的诊断或符号

-   评估在测试计算机上运行时监视作业状态

-   从服务器的访问结果共享，并进行评审和比较一致地呈现

## <a name="common-scenarios"></a>常见方案


-   将映像应用到一组指定的计算机，这些计算机和图像特征进行比较的计算机上运行的特定的评估。

-   在多台计算机，或在同一台计算机上的多个评估或多台计算机上的多个评估上运行相同的评估。

-   导入到中心来生成 SQL 数据库的多个 Windows 评估服务实验室的结果合并报表。

-   要释放用于其他用途的目标计算机，以指定服务器保存时间运行分析，在充分利用资源的服务器上运行的评估结果的分析和使用已经在服务器上加载的符号。

## <a name="benefits"></a>优点


-   加快的解决质量问题，通过在计算机前的 OEM、 ODM、 IHV 和 ISV 的协作投入生产。

-   在使用 Microsoft 测试、 诊断和调试的专业的 OEM 和 ODM 工厂过程中使用的端到端的测试和验证平台。

-   Oem、 零售商和零售客户的易于识别的质量优势。

## <a name="limitations"></a>限制


-   Windows 评估服务支持在同一时间最多 150 的测试计算机上运行作业。 在同一时间评估 150 多台计算机时，您可能会看到性能有所下降。

-   测试计算机未必须加入到域中。 在域上运行程序加入计算机，WinRM 不授予权限。

## <a name="related-topics"></a>相关的主题


[Windows 评估服务](windows-assessment-services-technical-reference.md)

[Windows 评估服务常见方案](windows-assessment-services-how-to-topics--wastechref.md)

 

 







