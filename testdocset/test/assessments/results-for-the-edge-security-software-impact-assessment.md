---
title: "边缘安全软件影响评估的的结果"
description: "边缘安全软件影响评估的的结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 47dd67f5-e980-4bb0-a17b-2e4aa241b752
ms.openlocfilehash: ffdb2c74e59809ad059aaa9e53f321a3fc7df6e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-edge-security-software-impact-assessment"></a>边缘安全软件影响评估的的结果


适用于︰ Windows 10

边缘安全软件影响评估度量方面的 Microsoft 边缘通常受到反恶意软件。 评估测量启动的影响，并浏览 Microsoft 边缘的时间。

本主题有助于您理解边安全软件影响评估所产生的结果。

本主题︰

-   [指标](#metrics)

-   [问题](#issues)

## <a name="metrics"></a>指标


以下指标没有边安全软件影响评估报告。

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
<td><p>边缘启动和导航</p></td>
<td><p>时间 （毫秒） Microsoft 边缘应用程序启动并已提供所请求的 URL。</p></td>
</tr>
<tr class="even">
<td><p>应用程序激活</p></td>
<td><p>以毫秒为单位为 Microsoft 边缘应用程序激活的时间。</p></td>
</tr>
<tr class="odd">
<td><p>创建选项卡</p></td>
<td><p>若要在 Microsoft 边缘创建的选项卡 （毫秒） 的时间。</p></td>
</tr>
<tr class="even">
<td><p>可用的页面</p></td>
<td><p>时间 （毫秒） 的页后，可以对用户是可见的。</p></td>
</tr>
<tr class="odd">
<td><p>在页面可用页面加载完成后</p></td>
<td><p>以毫秒为单位完全加载页面可见页面后的时间。 只显示完全加载之前，该页是否可用。</p></td>
</tr>
</tbody>
</table>

 

## <a name="issues"></a>问题


建议的方法，识别性能问题的来源是按照 Windows 评估 Toolkit 使用情况和最佳做法文档中涉及从零售 Windows 映像的"基准"系统中收集结果和比较结果时自定义 Windows 映像包含相关的扩展和附加软件 test 系统中收集到的模型。

两种配置的评估结果可以进行比较并排放置在 Windows 评估控制台 (WAC) 来确定指标的最大区别。 单击显示在 WAC ETW 跟踪到的链接将显示相应的性能跟踪 Windows 性能分析器 (WPA)。 WPA 可以用于深入到每个配置的 CPU 和磁盘利用率，同样比较并排的两个配置有助于确定他们使用的 CPU 和磁盘中显示最大增量的过程。

## <a name="related-topics"></a>相关的主题


[边缘安全软件影响](edge-security-software-impact.md)

[Windows 评估 Toolkit 技术参考](windows-assessment-toolkit-technical-reference.md)

[评估服务](assessments.md)

 

 







