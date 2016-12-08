---
title: "Windows 应用商店应用程序性能评估的结果"
description: "Windows 应用商店应用程序性能评估的结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 1f0cb16e-c4e1-4953-97c3-b20894d6b667
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 91c2511d5d8fd440cd157729c8a8ca189a56e7ca
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-windows-store-app-performance-assessment"></a>Windows 应用商店应用程序性能评估的结果


Windows 应用商店应用程序性能评估服务可帮助您优化您的应用程序更好的客户体验。 评估测量多快的速度应用程序打开并将暂停，并在 PC 上使用的资源量。 可以使用此评估服务可帮助您提高单个应用程序，或可帮助您优化的领料快速、 流畅的应用程序很好地在您的 PC 上运行的 Windows 映像。

本主题有助于您理解 Windows 应用商店应用程序性能评估所产生的结果。 它还提供有关如何使用结果来识别和解决应用程序性能带来负面影响的公共问题的指导。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-metrics)

-   [问题](#bkmk-issues)

有关系统要求和评估设置的详细信息，请参阅[Windows 商店应用程序性能](windows-store-app-performance.md)。

## <a name="a-href-idbkmk-goalsagoals-file"></a><a href="" id="bkmk-goals"></a>目标文件


您可以创建自定义的目标来衡量结果视图中的您改进。 目标文件是会审的工具，可帮助您了解 PC 的性能如何，比较 Pc 业务中。

例如，基本的便携式计算机目标可能不同于为高端桌面计算机设置的目标或者市场预期可能会更改所需的灵活性，可以定义不同类型的目标和时间的推移和技术的关键要求提高的方式中。

度量值是与该指标的目标相比，状态都用颜色编码在结果视图中，如下所示︰

-   浅紫色意味着系统具有出色的用户体验，有没有感觉到的问题。

-   紫色的中等意味着用户体验是容许，可以优化系统。 检查以查看可对系统进行何种改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。

-   深紫色意味着系统有很差的用户体验，并且有重大改进的空间。 检查以查看可对系统进行改进的建议和分析。 这可能是软件更改，更改配置或硬件更改。 您可能需要考虑进行权衡，以便提供 Windows 遇到的高质量。

-   没有颜色的含义有没有定义为度量的目标。

**请注意**  
在 Windows 评估 Toolkit 针对 Windows 8，某些评估包括默认目标文件。 查看使用此版本的工具，结果在第一次使用该默认目标文件。 但是，您还可以定义自定义目标针对 Windows 8 相同的方式，可以为 Windows 8.1 和 Windows 10。

 

您可以设置文件位置的目标并将目标文件添加到该位置之前可用于用户界面应用的自定义目标。 选择目标文件后，它将继续是目标文件，用于打开的任何结果。

可每次只能有一个目标文件。 所有的评估的目标是单个目标文件中设置的。 评估工具将搜索顺序如下目标︰

1.  自定义的目标文件

2.  在结果文件中定义的目标

3.  评估清单中定义的目标

您可以在 %PROGRAMFILES%使用提供了该示例的目标文件\\窗口工具包\\10\\评估和部署工具包\\Windows 评估 Toolkit\\SDK\\样本\\目标来创建目标文件。

**请注意**  
不能包装作业的目标文件，但可以将其存储在供其他用户使用共享。

 

## <a name="a-href-idbkmk-metricsametrics"></a><a href="" id="bkmk-metrics"></a>指标


以下指标将通过 Windows 应用商店应用程序的性能评估报告。

### <a name="total-windows-store-apps"></a>总 Windows 应用商店应用程序

多少的 Windows 应用商店应用程序安装在设备上的计数。

### <a name="windows-store-apps-assessed"></a>评估 Windows 应用商店应用程序

多少的 Windows 应用商店应用程序包括在评估中的计数。

### <a name="windows-store-app-details"></a>Windows 应用商店应用程序详细信息

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>公制</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>热启动︰</p></td>
<td><p>以毫秒为单位，从挂起状态的应用程序所需的时间。</p></td>
</tr>
<tr class="even">
<td><p>冷启动︰</p></td>
<td><p>以毫秒为单位，以打开该应用程序所需的时间。</p></td>
</tr>
<tr class="odd">
<td><p>在投放</p></td>
<td><p>在前十秒后启动该应用程序的资源使用情况。</p></td>
</tr>
<tr class="even">
<td><p>空闲</p></td>
<td><p>不到三十秒后<strong>启动开机自检</strong>期间的交互打开应用程序时的资源使用。</p></td>
</tr>
<tr class="odd">
<td><p>挂起</p></td>
<td><p>时间，以毫秒为单位，所需应用程序进入暂停的状态。</p></td>
</tr>
</tbody>
</table>

 

## <a name="a-href-idbkmk-issuesaissues"></a><a href="" id="bkmk-issues"></a>问题


此评估执行高级的问题分析，并提供到 Windows 性能分析器 (WPA) 标识问题进行故障排除的链接。 在大多数情况下，您可以单击 WPA 分析链接来解决出现的问题。 当 WPA 打开磁盘活动有关的更多详细信息或 CPU 活动可根据问题的类型。 深入分析的问题和建议有关的详细信息，请参阅[In-Depth 分析的常见问题](common-in-depth-analysis-issues.md)。

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

 

 






