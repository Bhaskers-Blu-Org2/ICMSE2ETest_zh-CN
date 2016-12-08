---
title: "体验出的评估的结果"
description: "体验出的评估的结果"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: CE1CE800-D2DB-41DD-B98E-650E5D676C28
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 9238eccf6542ca89483b22c4284dd6b6f1f3c36f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="results-for-the-out-of-box-experience-assessment"></a>体验出的评估的结果


适用于︰ Windows 8.1，Windows 10

此评估衡量关键方面首次启动体验 (OOBE) 通常图像自定义项和应用于 Windows 零售映像软件加载项受影响的持续的时间。 从性能跟踪收集 10 为 Windows 系统的第一次启动过程中使用事件跟踪 Windows (ETW) 获得测量结果。 评估措施第一次登录，以及如智能安装和配置应用程序安装的特定方面的持续的时间。

本主题有助于您理解 OOBE 性能评估所产生的结果。 它还提供如何利用这些结果发现和解决影响 OOBE 体验的问题的指南。

## <a name="metrics"></a>指标


以下指标没有 OOBE 性能评估报告。

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
<td><p>第一个登录时间</p></td>
<td><p>测量的时间以秒为单位进行登录。 这是来自用户提供登录电影开始播放之前的最后一次输入，直到桌面登录影片播放完毕后启动的时间。</p></td>
</tr>
<tr class="even">
<td><p>外壳程序登录框架</p></td>
<td><p>测量的时间以秒为单位的登录 shell 的框架正在初始化其中的部分。</p></td>
</tr>
<tr class="odd">
<td><p>智能安装</p></td>
<td><p>测量的时间以秒为单位的活动设置。</p></td>
</tr>
<tr class="even">
<td><p>提供应用程序安装时</p></td>
<td><p>度量单位是秒为要安装的应用程序资源调配。</p></td>
</tr>
<tr class="odd">
<td><p>运行一次首次登录命令</p></td>
<td><p>测量的时间以秒为单位完成运行执行一次第一次登录命令。</p></td>
</tr>
</tbody>
</table>

 

## <a name="issues"></a>问题


外出时的体验的性能可以通过附加的 CPU 和磁盘 IO 活动由驱动程序、 服务和应用程序期间方案执行受到很大影响。

建议的方法，识别中 OOBE 的性能问题的来源是按照 Windows 评估 Toolkit 使用情况和最佳做法文档中涉及从零售 Windows 映像的 '基准' 系统中收集结果和比较结果时自定义 Windows 映像包含相关的扩展和附加软件 test 系统中收集到的模型。 两种配置的评估结果可以进行比较并排放置在 Windows 评估控制台 (WAC) 来确定指标的最大区别。 单击显示在 WAC ETW 跟踪到的链接将显示相应的性能跟踪 Windows 性能分析器 (WPA)。 WPA 可以用于深入到每个配置的 CPU 和磁盘利用率，同样比较并排的两个配置有助于确定他们使用的 CPU 和磁盘中显示最大增量的过程。

## <a name="related-topics"></a>相关的主题


[评估服务](assessments.md)

[全新安装体验](out-of-box-experience.md)

[Windows 评估 Toolkit](index.md)

 

 







