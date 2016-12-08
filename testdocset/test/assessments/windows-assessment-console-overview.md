---
title: "评估 Windows 控制台概述"
description: "评估 Windows 控制台概述"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 12afc4f2-74be-41d9-ac09-a9e7c7d79d37
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 7179a0c85674b02d22c06a63219e7228ce73c26c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-assessment-console-overview"></a>评估 Windows 控制台概述


评估 Windows 控制台和评估窗口评估 Toolkit 的一部分安装。 评估 Windows 控制台是一个 GUI，您可以使用来发现评估和预定义的组评估服务，以创建新的作业，作业更改现有作业、 运行作业，以及管理作业结果。 作业是在一台计算机同时运行的一个或多个评估 （以及它们的设置） 的集合。 作业的结果常常包括诊断和修正信息帮助您确定需要进一步调查和纠正措施的区域。 有关如何使用 Windows 评估控制台的详细信息，请参阅[Windows 评估控制台的分步指南](windows-assessment-console-step-by-step-guide.md)。

评估是.xml 和促使一组特定的状态在计算机、 测量和记录活动，并保留记录的结果的二进制文件的组合。 您可以查看可用的评估，以确定您想要评估。 然后，可以添加到作业评估或配置的预定义的作业包括评估和满足您的需要的设置。 个人评估有关的详细信息，请参阅[评估](assessments.md)。

本主题︰

-   [系统要求](#asmt-sysreq)

-   [优点](#asmt-benefits)

-   [限制](#asmt-limitations)

-   [常见方案](#asmt-scenarios)

## <a name="a-href-idasmt-sysreqasystem-requirements"></a><a href="" id="asmt-sysreq"></a>系统要求


评估 Windows 控制台可以安装在以下操作系统之一︰

-   Windows 8

-   Windows 10

**请注意**  
必须在特定操作系统上运行一些评估。 关于个人评估的系统要求的详细信息，请参阅[评估](assessments.md)。

 

此外，Windows 评估控制台文件的安装位置的系统分区必须有不少于 200 兆字节 (MB) 的可用磁盘空间来进行评估。 这一要求，则需要为跟踪 Windows 事件 (ETW)，所有的评估使用的功能。 通过时间、 评估结果和日志文件可能会消耗大量的磁盘空间。

## <a name="a-href-idasmt-benefitsabenefits"></a><a href="" id="asmt-benefits"></a>优点


评估 Windows 控制台具有下列优点︰

-   一个可用于评估计算机的 GUI 调查问题、 审查的建议，并比较结果。

-   有些作业结果提供附加信息的链接可以帮助您提高计算机以及直接链接到 Windows 性能分析器 (WPA)，以便可以追踪溯源问题的原因。

-   在详细信息视图中，几个结果进行比较的能力和数百个摘要视图中的结果进行比较的能力。 有关详细信息，请参阅[将结果进行比较](compare-results.md)。

-   包装作业并将其保存在 USB 闪存驱动器上，然后在另一台计算机上运行的能力。 有关详细信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。

-   从其他位置，如可移动媒体或网络共享将结果导入默认结果库的能力。

-   预定义的作业，很容易找到并运行。

-   如果您已修改了其恢复建议的评估设置的能力。

-   若要恢复默认的模板设置，如果您已修改预定义的作业能力。

-   若要自定义包括评估和您想要使用的设置的作业能力。

-   可以使用相同的方式使用该工具包提供的评估与在 Windows 评估控制台中，在评估平台兼容的自定义评估。 有关详细信息，请参阅[注册自定义的评估](register-and-unregister-custom-assessments.md)。

    **请注意**  
    一组公共的 Api 可用于创建和扩展与评估平台兼容的评估。 有关详细信息，请参阅[MSDN︰ 评估执行引擎](http://go.microsoft.com/fwlink/?LinkId=236367)。

     

## <a name="a-href-idasmt-limitationsalimitations"></a><a href="" id="asmt-limitations"></a>限制


这些限制将应用于评估 Windows 控制台︰

-   评估 Windows 控制台以一台计算机评估一次。 有关远程同时评估多台计算机的详细信息，请参阅[Windows 评估服务](windows-assessment-services-technical-reference.md)。

-   评估 Windows 控制台不能安装在一台服务器上，不用来评估服务器计算机。

-   评估 Windows 控制台不能安装在 Windows 直角 但是，可以打包作业，然后在 Windows RT 运行它，如果评估支持基于 ARM 的处理器。 不是所有的评估支持在基于 ARM 的处理器上运行。 有关详细信息，请参阅[打包作业和运行它在另一台计算机上](package-a-job-and-run-it-on-another-computer.md)。 关于评估的系统要求的详细信息，请参阅[评估](assessments.md)。

## <a name="a-href-idasmt-scenariosacommon-scenarios"></a><a href="" id="asmt-scenarios"></a>常见方案


评估 Windows 控制台和评估履行一般行业需要的计算机评估以统一的方式，根据具体的情形。 它们适用于这些访问群体︰

-   系统构建者想要衡量主要的质量指标，并对他们构建的系统的各种组件组合的效果

-   计算机审阅和分析师希望以一致的方式来测量性能、 可靠性和功能

这些方案中，通常使用 Windows 评估控制台︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>方案</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>黑匣子</p></td>
<td><p>运行预定义的作业并检查任何异常值或标识驱动程序、 内存使用情况或其他领域的问题的结果，评估地址。</p></td>
</tr>
<tr class="even">
<td><p>结果的比较</p></td>
<td><p>预定义的作业，或者单个评估建议的评估设置，请在运行支持的操作系统的任何计算机的运行。 使用 Windows 评估控制台打包在另一台计算机上运行该作业。 在另一台计算机上运行该作业后，将结果导入到默认结果库。 可以将任何基于 Windows 10 的计算机与所有其他受支持的操作系统来确定差异的结果进行比较。</p></td>
</tr>
<tr class="odd">
<td><p>清理计算机</p></td>
<td><p>在<em>干净的计算机</em>（包括操作系统的计算机） 上运行评估来建立基线系统的结果。 有关说明，请参阅[创建基线结果](create-baseline-results-for-comparing-windows-images.md)。</p></td>
</tr>
<tr class="even">
<td><p>已添加的硬件或软件组件</p></td>
<td><p>干净的计算机系统中添加新的硬件或软件，然后重新运行清理计算机结果与结果进行比较评估。 有关说明，请参阅[创建基线结果](create-baseline-results-for-comparing-windows-images.md)。</p></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[评估 Windows 控制台的常见方案](windows-assessment-console-common-scenarios.md)

[评估服务](assessments.md)

[评估平台命令行语法](assessment-platform-command-line-syntax.md)

 

 







