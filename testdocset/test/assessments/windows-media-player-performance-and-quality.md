---
title: "Windows Media Player 性能和质量"
description: "Windows Media Player 性能和质量"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0c0c1485-ab34-42a4-bcc7-690b09b51347
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: ab3e4c48ddaa355c67c9dcbb8a71cd3d5f4ec19e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-media-player-performance-and-quality"></a>Windows Media Player 性能和质量


Windows Media Player 性能和质量评估启动 Windows Media Player 和播放多个媒体剪辑一个接一个。 此评估服务的重点是播放的品质和稳定中 Windows Media Player，模仿用户观看电影的工作负荷的性能。 产生这一评估的结果可帮助您评估媒体播放功能和性能和质量问题。 这一评估不计算任何查找或暂停功能。 有关所产生的这一评估的结果的详细信息，请参阅[Windows Media Player 性能和质量的评估结果](results-for-the-windows-media-player-performance-and-quality-assessment.md)。

下图说明了评估过程。

![windows 媒体播放器 p 和 q 的流图形](images/dep-win8-8-techref-wmpassessmentflow.jpg)

本主题︰

-   [系统要求](#bkmk-systemrequirements)

-   [设置](#assesssettings)

## <a name="a-href-idbkmk-systemrequirementsasystem-requirements"></a><a href="" id="bkmk-systemrequirements"></a>系统要求


当运行 Windows 8.1 此评估，确保评估预期的电池寿命时，**收集分析跟踪**设置处于未选中状态。 当选中时，此选项会产生不正确的估计。

仅当您需要调查其他与能源有关的问题的其他信息，请启用分析跟踪集合。

您可以在以下操作系统上运行此评估︰

-   Windows 8

-   Windows 10

支持的体系结构包括基于 x86 和基于 x64 的系统。

## <a name="a-href-idassesssettingsasettings"></a><a href="" id="assesssettings"></a>设置


默认情况下，此评估使用推荐的设置。 Microsoft 将定义这些设置，以便跨多个计算机配置或一段时间，在同一台计算机上，您可以比较结果。 当您查看结果时，请运行的信息包括指示评估是否使用推荐的设置的元数据。

下表描述评估建议的设置，值和每个设置的替代值。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>设置</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>使用建议的设置</p></td>
<td><p>指定评估是否使用推荐的设置。 默认情况下，选中此复选框。 若要更改此评估服务的设置，必须首先清除此复选框。</p></td>
</tr>
<tr class="even">
<td><p>内容的路径</p></td>
<td><p>指定的媒体文件的源文件夹。 默认情况下，该文件夹位于<code>..\Content\Streaming Media Assessment</code>。 可以使用的媒体文件的默认位置，或指定另一个文件夹。 如果您提供自己的媒体文件，评估支持网络文件夹的使用。</p></td>
</tr>
<tr class="odd">
<td><p>测试传递类型</p></td>
<td><p>指定评估电源选项。 从下拉列表中选择下列选项之一。 默认情况下，便携式计算机的电源选项是<strong>在交流和直流测试</strong>。</p>
<ul>
<li><p><strong>在交流和直流测试</strong></p></li>
<li><p><strong>仅使用交流电测试</strong></p></li>
<li><p><strong>仅适用于测试在 DC 上</strong></p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>相关的主题


[Windows 评估 Toolkit](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

[Windows Media Player 性能和质量评估结果](results-for-the-windows-media-player-performance-and-quality-assessment.md)

[媒体转换代码性能](media-transcoding-performance.md)

 

 







