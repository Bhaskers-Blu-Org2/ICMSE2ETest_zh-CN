---
author: Justinha
Description: "高 DPI 和 Windows 8.1"
ms.assetid: e330d659-35f0-4178-b504-1e5a3bd169ca
MSHAttr: PreferredLib:/library/windows/hardware
title: "高 DPI 和 Windows 8.1"
ms.openlocfilehash: f69dedf30719c3869ac5067e7abe6f034a6f5611
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="high-dpi-and-windows-81"></a>高 DPI 和 Windows 8.1


本主题介绍 DPI 和显示缩放的主要概念，并描述 Windows 8.1 中的新增功能。

**本主题︰**

-   [主要概念](#key)

-   [有关 DPI 的新增功能](#newdpi)

## <a name="span-idkeyspanspan-idkeyspankey-concepts"></a><span id="key"></span><span id="KEY"></span>主要概念


### <a name="span-idwhatisdpispanspan-idwhatisdpispanspan-idwhatisdpispanwhat-is-dpi"></a><span id="What_is_DPI"></span><span id="what_is_dpi"></span><span id="WHAT_IS_DPI"></span>DPI 是什么

以每英寸点数 (DPI)） 是一个线性英寸的显示器中的像素数的物理测量。 DPI 是一个函数的显示分辨率和大小;高 DPI，将导致更高的分辨率或大小较小和较低的分辨率或更大的大小会降低 DPI。 当显示具有较高 DPI 时，像素是更小和更仔细地在一起，以显示用户界面 (UI) 和其他显示的内容比预期小。

### <a name="span-idscalespanspan-idscalespanwhat-are-windows-scale-factors"></a><span id="scale"></span><span id="SCALE"></span>Windows 比例因素有哪些？

Windows® 可以确保一切按指示应用程序 （包括 Windows 桌面外壳程序） 可调整比例因子及其内容显示可用且一致的大小在屏幕上。 这个数字取决于显示 DPI，以及其他因素的影响显示用户的角度看。 几乎所有桌面显示和最新的便携式计算机显示器处于 95 110 DPI; 范围对于这些设备，没有扩展是必需的并且 Windows 设置 100%缩放比例。 但是，有大量的新设备，特别是在高级便携式计算机和平板市场，具有较高显示与超过 200 DPI。 对于这些设备，Windows 设置更高的缩放比例，以确保用户体验舒适可查看。

### <a name="span-idusersspanspan-idusersspanwhy-this-matters-to-users"></a><span id="users"></span><span id="USERS"></span>为什么这样重要的用户

用户通常花时间阅读并在 Windows 设备上工作，因此非常重要，以确保它们看的设备最适合他们的舒适。 因此，很重要的 Windows 最可读的方式呈现内容，以便减轻眼睛疲劳，工作效率不会受到影响。 随着显示技术的提高，这可能是交付在高 DPI 显示器的组合和更好的在窗口缩放。 Windows 8 提供了自动调整以更好地适应较新的、 更密集的 DPI 显示器的默认缩放的功能。

### <a name="span-identerprisesspanspan-identerprisesspanwhy-this-matters-to-enterprises"></a><span id="enterprises"></span><span id="ENTERPRISES"></span>为什么这样重要的企业

随着 Windows 设备改进，高密度显示将成为企业环境中大放异彩。 企业也正在朝着更流动的劳动力，在会议中使用便携式计算机到项目、 坞站解决方案时在办公桌前。 为了确保最佳的工作效率，企业用户应该不需要管理如何锁定他们的屏幕的投影，或者看出他们坞站解决方案展示他们的工作区时坐在桌前。 Windows 8 自动执行此操作对于大多数用户，但那里保留某些边缘情况下，这可能需要在企业环境中的 IT 专业人员来帮助支持。 本主题描述 Windows 自动执行的正确的事，在大多数情况下，以及在 IT 可能需要介入，并帮助用户解决。

## <a name="span-idnewdpispanspan-idnewdpispanwhats-new-about-dpi"></a><span id="newdpi"></span><span id="NEWDPI"></span>有关 DPI 的新增功能


### <a name="span-iddisplayhardwaremarketchangesspanspan-iddisplayhardwaremarketchangesspanspan-iddisplayhardwaremarketchangesspandisplay-hardware-market-changes"></a><span id="Display_hardware_market_changes"></span><span id="display_hardware_market_changes"></span><span id="DISPLAY_HARDWARE_MARKET_CHANGES"></span>显示硬件市场变化

随着高 DPI 显示。 Windows 可用设备期间和之后 2013年定期将功能都远大于内容已被以前可用的 DPIs。 13"和 1366 x 768 的分辨率与便携式计算机，而将为 3200 x 1800 处 13" 上看到的屏幕分辨率。 对于这些无法使用的膝上型电脑，窗口缩放将不得不转向从 100%（13.3 英寸 1366 x 768） 125%（13.3 英寸 1600 x 900），150%（10.6 英寸 1920 x 1080） 或 200%（13.3 英寸 2560 x 1440）。 在 Windows 8 之前, 只有 100%、 125%和 150%已自动设置以匹配显示;在 Windows 8 中添加 200%支持。

### <a name="span-idwindows81changesspanspan-idwindows81changesspanspan-idwindows81changesspanwindows-81-changes"></a><span id="Windows_8.1_changes"></span><span id="windows_8.1_changes"></span><span id="WINDOWS_8.1_CHANGES"></span>更改 Windows 8.1

Windows 8 将包括大量的*表 1 Windows 8.1 DPI 更改*所示为高 DPI，特定的功能更改︰

**表 1 Windows 8.1 DPI 更改**

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能</th>
<th align="left">Windows 8</th>
<th align="left">Windows 8.1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>支持缩放 200%</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>每个监视器 DPI</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>扩展现有 DPI 感知的应用程序</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>每个监视器 DPI 感知的应用程序</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>查看距离默认合并 DPI 计算</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>注销可用 DPI 更改</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>每个监视器 DPI 识别 Internet Explorer</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="even">
<td align="left"><p>自动 DPI 配置的远程桌面</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
</tr>
</tbody>
</table>

 

上述功能的前两对 Windows 8 的可用性的最大的影响。 在更多的详细信息︰

1.  **提高了 200%缩放支持︰**Windows 8.1 标识高 DPI 显示设备在动态的基础上，并以本机方式支持最多有 200%的缩放比例。 Windows 8 只在第一次启动，期间确定高 DPI 显示，并且只支持而无需用户自定义缩放比例达 150%。 此功能确保购买与高 DPI 显示高级便携式计算机的用户将自动接收使内容很容易地看到所需的 200%缩放。

2.  **每个监视器 DPI:**Windows 8.1 设置不同的缩放比例，针对不同的显示器，并可以进行适当缩放内容。 Windows 8 只设置应用于所有显示单个的缩放比例。 此功能可确保使用者项目或停靠其设备，与传统的 100%缩放投影仪和桌面监视器显示正常高 DPI 设备 （即 150%和 200%缩放膝上型计算机） 的用户规模在这些屏幕上的内容。

### <a name="span-idhowthesechangesimpactenterpriseusersspanspan-idhowthesechangesimpactenterpriseusersspanspan-idhowthesechangesimpactenterpriseusersspanhow-these-changes-impact-enterprise-users"></a><span id="How_these_changes_impact_enterprise_users"></span><span id="how_these_changes_impact_enterprise_users"></span><span id="HOW_THESE_CHANGES_IMPACT_ENTERPRISE_USERS"></span>这些更改如何影响企业用户

用户在具有 100%缩放的便携式计算机上，Windows 8.1 功能变化没有任何影响。 对于用户获得具有高 DPI 的新设备，Windows 8.1 提供的重要优势。

有可能某些用户将获得设备位于中间，采用窗口缩放的 125%。 这些设备可以要求用户或 IT 专业人员对其进行正确的配置或更新/调整应用程序以改进易用性。 本主题的故障排除部分可帮助 IT 专业人员识别这些系统，这些应用程序，并采取适当的缓解策略。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[面向 IT 专业人员的高 DPI 支持](high-dpi-support-for-it-professionals.md)

 

 






