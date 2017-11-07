---
title: "文件处理评估的的结果"
description: "文件处理评估的的结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 9f620d9c-976c-4fdf-ba52-6188b3982305
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 709bdbf4dd47a85147333d5313cb9d96db21ce32
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-file-handling-assessment"></a>文件处理评估的的结果


文件处理评估提供了自动化的方式行使公共文件操作和捕获的指标。 此评估测量同时复制、 移动、 压缩、 解压缩，并删除文件和文件夹在您的计算机上的持续时间和吞吐量。 结果可帮助您了解计算机在这些操作期间执行的程度。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-fileresults)

-   [问题](#bkmk-fileissues)

有关系统要求、 工作负荷和评估设置的详细信息，请参阅[文件处理](file-handling.md)。

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

 

## <a name="a-href-idbkmk-fileresultsametrics"></a><a href="" id="bkmk-fileresults"></a>指标


文件处理评估的结果显示为副本，计算机的性能将移动、 压缩和删除操作。 下表描述了文件处理评估衡量的指标。

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
<td><p>复制持续时间 （以编程方式）</p></td>
<td><p>显示编程复制操作需要完成的秒数。</p></td>
</tr>
<tr class="even">
<td><p>复制期间 (UX 编写脚本)</p></td>
<td><p>显示脚本的复制操作需要完成的秒数。</p></td>
</tr>
<tr class="odd">
<td><p>复制吞吐量 （以编程方式）</p></td>
<td><p>显示吞吐量，以兆字节每秒，以编程方式复制操作。</p></td>
</tr>
<tr class="even">
<td><p>复制吞吐量 (UX 编写脚本)</p></td>
<td><p>显示吞吐量，以兆字节每秒为脚本的复制操作。</p></td>
</tr>
<tr class="odd">
<td><p>删除持续时间 （以编程方式）</p></td>
<td><p>显示编程删除操作所需完成的秒数。</p></td>
</tr>
<tr class="even">
<td><p>删除期间 (UX 编写脚本)</p></td>
<td><p>显示脚本的删除操作所需完成的秒数。</p></td>
</tr>
<tr class="odd">
<td><p>删除文件的吞吐量 （以编程方式）</p></td>
<td><p>显示文件的吞吐量，在第二个，每个文件中以编程方式删除操作。</p></td>
</tr>
<tr class="even">
<td><p>删除吞吐量 （以编程方式）</p></td>
<td><p>显示吞吐量，以每秒兆字节编程删除操作。</p></td>
</tr>
<tr class="odd">
<td><p>删除吞吐量 (UX 编写脚本)</p></td>
<td><p>显示吞吐量，以每秒兆字节的脚本删除操作。</p></td>
</tr>
<tr class="even">
<td><p>文件处理</p></td>
<td><p>概要显示的通用文件操作 （如复制、 移动、 压缩、 和删除） 完成所花费的时间长度。 若要查看为文件处理的详细度量值，请展开结果。</p></td>
</tr>
<tr class="odd">
<td><p>文件组织指标</p></td>
<td><p>显示编程脚本操作 （如复制、 移动、 压缩、 和删除） 完成后，所花费的时间的长度，并包括为每个操作下的吞吐量︰</p>
<ul>
<li><p>复制持续时间 (Programmatic) MinifilterDelay （秒）</p></li>
<li><p>删除期间 (Programmatic) MinifilterDelay （秒）</p></li>
<li><p>移动持续时间 (Programmatic) MinifilterDelay （秒）</p></li>
<li><p>复制吞吐量 (Programmatic) （兆字节 / 秒）</p></li>
<li><p>删除吞吐量 (Programmatic) （兆字节 / 秒）</p></li>
<li><p>移动的吞吐量 (Programmatic) （兆字节 / 秒）</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>移动持续时间 （以编程方式）</p></td>
<td><p>显示编程移动操作所需完成的秒数。</p></td>
</tr>
<tr class="odd">
<td><p>移动持续时间 (UX 编写脚本)</p></td>
<td><p>演示脚本式移动操作所需完成的秒数。</p></td>
</tr>
<tr class="even">
<td><p>移动文件的吞吐量 （以编程方式）</p></td>
<td><p>显示文件的吞吐量，在第二个，每个文件中编程移动操作。</p></td>
</tr>
<tr class="odd">
<td><p>移动文件的吞吐量 (UX 编写脚本)</p></td>
<td><p>显示文件的吞吐量，第二个，每个文件中的脚本移动操作。</p></td>
</tr>
<tr class="even">
<td><p>移动吞吐量 （以编程方式）</p></td>
<td><p>显示吞吐量，以每秒兆字节编程移动操作。</p></td>
</tr>
<tr class="odd">
<td><p>移动的吞吐量 (UX 编写脚本)</p></td>
<td><p>显示吞吐量，以每秒兆字节的脚本移动操作。</p></td>
</tr>
<tr class="even">
<td><p>压缩工期 (UX 编写脚本)</p></td>
<td><p>演示脚本式的压缩操作所需完成的秒数。</p></td>
</tr>
<tr class="odd">
<td><p>Zip 吞吐量 (UX 编写脚本)</p></td>
<td><p>显示吞吐量，以每秒兆字节的脚本压缩操作。</p></td>
</tr>
<tr class="even">
<td><p>联合国压缩工期 (UX 编写脚本)</p></td>
<td><p>显示脚本的提取操作所需完成的秒数。</p></td>
</tr>
<tr class="odd">
<td><p>联合国 Zip 吞吐量 (UX 编写脚本)</p></td>
<td><p>显示吞吐量，以每秒兆字节的脚本提取操作。</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
如果启用**启用微筛选器诊断模式**评估设置，评估结果将包括微筛选器规格。 有关微筛选器的指标和结果的详细信息，请参阅[微筛选器诊断程序](minifilter-diagnostics.md)。

 

## <a name="a-href-idbkmk-fileissuesaissues"></a><a href="" id="bkmk-fileissues"></a>问题


### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

## <a name="related-topics"></a>相关的主题


[文件处理](file-handling.md)

[评估服务](assessments.md)

[连接备用能源效率](connected-standby-energy-efficiency.md)

[创建并运行一个能源效率作业](create-and-run-an-energy-efficiency-job.md)

[微筛选器诊断程序](minifilter-diagnostics.md)

[Windows 评估 Toolkit 技术参考](windows-assessment-toolkit-technical-reference.md)

 

 







