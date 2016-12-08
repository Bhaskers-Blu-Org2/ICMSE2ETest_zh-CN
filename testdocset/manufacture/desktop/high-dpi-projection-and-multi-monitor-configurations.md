---
author: Justinha
Description: "高 DPI 投影和多显示器配置"
ms.assetid: 81a96303-5ab5-4002-acac-ab356e2ec829
MSHAttr: PreferredLib:/library/windows/hardware
title: "高 DPI 投影和多显示器配置"
ms.openlocfilehash: 7e3990a2e3b43bf10a6c2ce4df1245519abd501d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="high-dpi-projection-and-multi-monitor-configurations"></a>高 DPI 投影和多显示器配置


很多企业用户对坞站连接，投影，或扩展到辅助显示器桌面等目的使用辅助显示器。

这些方案不会影响 150%和 200%设备的指南，但使用者还使用桌面坞站或辅助监视器 125%显示设备的用户，我们建议[修正模糊文本，IT 专业人员的 Windows 8.1 中](fixing-blurry-text-in-windows-for-it-professionals.md#unaware)所示的 Windows 8 的兼容性模式。 本主题提供了有关兼容设备和投影仪的其他指南。

## <a name="span-idprojectionspanspan-idprojectionspanprojection-experiences"></a><span id="projection"></span><span id="PROJECTION"></span>投影的体验


Windows 8.1 已经优化投影经验的支持。 在以前版本的 Windows 中，高 DPI 设备的用户可能会看到低 DPI 投影仪，太大的内容难以用于呈现在屏幕上获得所有适当的内容。 有两种投影模式︰*复制*和*扩展*。 本部分介绍如何 Windows 支持每一种模式。

### <a name="span-idduplicatemodedefaultforprojectionandtypicallyusedforprojectionspanspan-idduplicatemodedefaultforprojectionandtypicallyusedforprojectionspanspan-idduplicatemodedefaultforprojectionandtypicallyusedforprojectionspanduplicate-mode-default-for-projection-and-typically-used-for-projection"></a><span id="Duplicate_mode__default_for_projection_and_typically_used_for_projection_"></span><span id="duplicate_mode__default_for_projection_and_typically_used_for_projection_"></span><span id="DUPLICATE_MODE__DEFAULT_FOR_PROJECTION_AND_TYPICALLY_USED_FOR_PROJECTION_"></span>重复模式 （通常用于投影和投影默认值）

默认投影模式称为重复模式。 (在四种多监视器的显示模式的列表，请参阅键盘键入**Win + P** ︰**只有电脑屏幕**、**重复的**、**延伸**和**第二个**屏幕。)在重复模式中，便携式计算机的显示器上投影仪上显示相同的内容。 这使得简单的演示者，直接与被显示在屏幕上，特别是对于便携式计算机或 tablet 支持触摸屏输入的内容进行交互。 在此模式下，Windows 将看一看两个显示器，试着找到最常见的解决方法，然后将两个显示器放到该分辨率。 在 Windows 8.1，如果此更改分辨率影响显示的缩放比例，Windows 将然后重新缩放基于新的缩放比例，从而确保最佳投影体验。

### <a name="span-idextendmodetypicalformulti-monitordesktopscenariosspanspan-idextendmodetypicalformulti-monitordesktopscenariosspanspan-idextendmodetypicalformulti-monitordesktopscenariosspanextend-mode-typical-for-multi-monitor-desktop-scenarios"></a><span id="Extend_mode__typical_for_multi-monitor_desktop_scenarios_"></span><span id="extend_mode__typical_for_multi-monitor_desktop_scenarios_"></span><span id="EXTEND_MODE__TYPICAL_FOR_MULTI-MONITOR_DESKTOP_SCENARIOS_"></span>扩展模式 （典型的多显示器桌面方案）

在扩展模式中，投影仪将被视为单独显示在主显示器。 这种模式是典型的用户使用多台监视器或定位方案。 用户可以拖动或将内容移动到单独的显示，通过使用鼠标或触摸板。 这不是默认选项，但是有些用户喜欢 （以为只是一个示例，因为它允许用户将他们的演示文稿中的笔记） 此设置。 在此模式下，Windows 8.1 将为每个显示，适当的比例系数，当用户将内容移至投影仪，Windows 会将放大，相应地再次确保最佳投影体验。

### <a name="span-iditprospanspan-iditprospanwhat-this-means-for-the-it-professional"></a><span id="itpro"></span><span id="ITPRO"></span>这为 IT 专业人员意味着什么

投影情况下，每个监视器扩展是需要为 150%和 200%显示提供可用投影的体验。 在某些情况下，拥有 125%设备的用户可能有不 dpi 正在越模糊，在幻灯片放映时的应用程序的问题。 如何关闭每个应用程序在这些情况下缩放的 DPI 的指导，请参阅[修复模糊文本的 Windows 8.1 面向 IT 专业人员](fixing-blurry-text-in-windows-for-it-professionals.md#unaware)。

**重要**  
投影仪在重复模式下工作最好，如果他们支持的分辨率和类似的设备，将投影的视频模式。 例如，如果在企业主导的便携设备具有 1366 x 768 和 1920 x 1080 显示，使用投影仪应最佳重复模式经验的支持相同的分辨率。

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[面向 IT 专业人员的高 DPI 支持](high-dpi-support-for-it-professionals.md)

 

 






