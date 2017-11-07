---
title: "Windows Media Player 性能和质量评估结果"
description: "Windows Media Player 性能和质量评估结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 2503b5ce-6b01-4a49-b3a3-8c4b84419152
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 13e7eee0a0127080a112e351ae2a45bf9b94da42
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-windows-media-player-performance-and-quality-assessment"></a>Windows Media Player 性能和质量评估结果


Windows Media Player 性能和质量评估启动 Windows Media Player，并在多个媒体剪辑一个播放后，另一个用来评估媒体播放功能并捕获性能和质量指标。 评估结果包括在用户体验中的音频和视频失灵或检测视觉或听觉缺陷的数量指标。 重点是播放的在质量和性能稳定的 Windows Media Player，模仿用户观看电影的工作负荷中。 这一评估不计算任何查找或暂停功能。

本主题︰

-   [目标文件](#bkmk-goals)

-   [指标](#bkmk-wmpmetrics)

-   [问题](#bkmk-wmpissues)

有关评估、 系统要求以及评估设置的详细信息，请参阅[Windows Media Player 性能和质量](windows-media-player-performance-and-quality.md)。

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

 

## <a name="a-href-idbkmk-wmpmetricsametrics"></a><a href="" id="bkmk-wmpmetrics"></a>指标


结果显示在计算机上的性能和质量的 Windows Media Player 播放有关的信息。 下表提供了 Windows Media Player 播放评估捕获每个指标的简单描述。

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
<td><p>总的音频坠落</p></td>
<td><p>在播放期间记录的音频坠落的总数。</p></td>
</tr>
<tr class="even">
<td><p>总的音频故障</p></td>
<td><p>在播放期间记录的音频故障总数。</p>
<div class="alert">
<strong>请注意</strong>  
<p>一个小故障是用户体验中的任何检测视觉或听觉缺陷。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>总的音频挨饿</p></td>
<td><p>在播放过程中，出现了音频挨饿总次数。</p>
<div class="alert">
<strong>请注意</strong>  
<p>音频数据不能足够快的速度阅读，以跟上呈现或撰写的文件时发生音频挨饿。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td><p>总 DWM 失灵</p></td>
<td><p>桌面窗口管理器 (DWM) 导致播放失灵总次数。 DWM 涉及组合中播放。</p></td>
</tr>
<tr class="odd">
<td><p>总的 MF 数据下降</p></td>
<td><p>在播放过程中删除了 Microsoft 媒体基础数据的时间总数。 有关此媒体平台的详细信息，请参阅[MSDN: Microsoft 媒体基础](http://go.microsoft.com/fwlink/?LinkId=232723)。</p></td>
</tr>
<tr class="even">
<td><p>总增强视频故障</p></td>
<td><p>总增强型数据速率 (EDR) 视频遇到的故障在播放期间记录了。</p></td>
</tr>
</tbody>
</table>

 

详细信息可为每个度量。 若要查看该信息，请选择 (ETL) 文件的链接。 ETL 文件将自动打开附加分析在 Windows® 性能分析器 (WPA)。

## <a name="a-href-idbkmk-wmpissuesaissues"></a><a href="" id="bkmk-wmpissues"></a>问题


Windows Media Player 播放评估不显示问题或提出建议。 这一评估的最佳使用是比较两个或多个计算机的 Windows Media Player 播放性能。

### <a name="the-assessment-reports-an-exit-code-of-0x80050006"></a>评估报告的退出代码为 0x80050006

维护任务已注册的电脑上，但尚未完成之前运行的评估时，将发生此错误。 为维护任务通常会影响评估指标，这样可以防止运行，这样的评估。

要解决此问题，请执行以下任一操作︰

1.  确保计算机已连接到网络和交流电源供电运行。 手动启动，请使用以下命令从提升提示符挂起的维护任务︰

    `rundll32.exe advapi32.dll,ProcessIdleTasks`

2.  禁用定期和空闲状态维护任务，并在运行评估之前停止所有的维护任务。

## <a name="related-topics"></a>相关的主题


[Windows Media Player 性能和质量](windows-media-player-performance-and-quality.md)

[Windows 评估 Toolkit](index.md)

[评估服务](assessments.md)

[媒体转换代码性能](media-transcoding-performance.md)

 

 







