---
author: kpacquer
Description: "闪烁的工具"
ms.assetid: ac04af30-84ef-4d09-9c6f-5b9c01f9a2a0
MSHAttr: PreferredLib:/library/windows/hardware
title: "闪烁的工具"
ms.openlocfilehash: 0dd3a1876cffe2c402c93998dc18812bc5c90033
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="flashing-tools"></a>闪烁的工具


每个制造商都有不同的技术和工具，它们将用来制造和服务窗口 10 移动设备。 最佳专业技能相关制造位于那些生成 OEM 制造系列。 这意味着 OEM 需要确定哪些闪烁，制造工艺更适合它们。 OEM 服务中心可能有独特的需要，还会影响闪烁工具的选择。 OEM 需要确定如何进行测试和验证选定的工具和流程符合他们的成本、 质量和其他独特的生产目标。

OEM 使用 Microsoft 提供的图像处理工具创建刷新为设备的 FFU OS 映像。

## <a name="span-idflashingtoolscomparisonspanspan-idflashingtoolscomparisonspanspan-idflashingtoolscomparisonspanflashing-tools-comparison"></a><span id="Flashing_tools_comparison"></span><span id="flashing_tools_comparison"></span><span id="FLASHING_TOOLS_COMPARISON"></span>闪烁工具比较


OEM 可能需要开发一个自定义的闪烁工具，为了满足设备的生命周期。 闪烁的其他选项有 OEM 在决定使用它们之前应该了解的局限性。

下表总结了闪烁的工具选项。

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">方案</th>
<th align="left">Microsoft FFU 工程工具</th>
<th align="left">OEM 自定义 FFU 工具</th>
<th align="left">SoC 提供制造闪烁工具</th>
<th align="left">团伙的程序员</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>工程设计和开发</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>无</p></td>
</tr>
<tr class="even">
<td align="left"><p>制造</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
</tr>
<tr class="odd">
<td align="left"><p>服务中心</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>是</p></td>
<td align="left"><p>否</p></td>
<td align="left"><p>不适用</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idoemcustomflashingtoolspanspan-idoemcustomflashingtoolspanspan-idoemcustomflashingtoolspanoem-custom-flashing-tool"></a><span id="OEM_custom_flashing_tool"></span><span id="oem_custom_flashing_tool"></span><span id="OEM_CUSTOM_FLASHING_TOOL"></span>OEM 自定义闪烁工具


若要创建一个闪烁的制造工具，OEM 必须开发自己的工具定制为他们制造环境和设备。

根据 Oem 要求，闪烁的工具可能还需要解决许多[域服务方案](field-service-scenarios.md)所述的方案。

有关详细信息，请参阅[开发自定义 OEM 闪烁工具](developing-custom-oem-flashing-tools.md)。

## <a name="span-idsocprovidedmanufacturingflashingtoolspanspan-idsocprovidedmanufacturingflashingtoolspanspan-idsocprovidedmanufacturingflashingtoolspansoc-provided-manufacturing-flashing-tool"></a><span id="SoC_provided_manufacturing_flashing_tool"></span><span id="soc_provided_manufacturing_flashing_tool"></span><span id="SOC_PROVIDED_MANUFACTURING_FLASHING_TOOL"></span>SoC 提供制造闪烁工具


SoC 提供制造闪烁的工具的信息，请与 SoC 提供程序。

## <a name="span-idgangprogrammerspanspan-idgangprogrammerspanspan-idgangprogrammerspangang-programmer"></a><span id="Gang_programmer"></span><span id="gang_programmer"></span><span id="GANG_PROGRAMMER"></span>团伙的程序员


有大量的选项供 OEM 快闪存储二进制映像。 OEM 可以使用其独特的闪烁工具以及团伙程序员技术制造该设备，如果他们发现的那些选项更适合于他们的环境。

如果 OEM 使用团伙程序员，他们需要开发一个自定义工具将 FFU 图像转换为原始的二进制图像。 转换工具将需要︰

1.  在团伙程序员所期望的格式打开原始的二进制文件。

2.  在 FFU 文件中读取和分析[FFU 图像格式](ffu-image-format.md)中所指定的文件数据。

3.  写出在 FFU 块中引用数据\_数据\_到原始文件的条目元素。

4.  当没有更多的项目时，写出任何元数据或填充所需的原始格式，然后关闭原始二进制文件。

## <a name="span-idffutoolsupportlimitationsspanspan-idffutoolsupportlimitationsspanspan-idffutoolsupportlimitationsspanffutool-support-limitations"></a><span id="FFUTool_support_limitations"></span><span id="ffutool_support_limitations"></span><span id="FFUTOOL_SUPPORT_LIMITATIONS"></span>FFUTool 支持限制


Microsoft 提供了 FFUTool 全闪存更新 (FFU) 技术设计的工程开发和测试目的;不支持在生产中使用。 每个 OEM 必须确定 FFUTool 是否适合在他们服务的中心环境中使用。

## <a name="span-idffutoolknownissuesspanspan-idffutoolknownissuesspanspan-idffutoolknownissuesspanffutool-known-issues"></a><span id="FFUTool_known_issues"></span><span id="ffutool_known_issues"></span><span id="FFUTOOL_KNOWN_ISSUES"></span>FFUTool 已知问题


使用 FFUTool 有大量明显汇总如下的限制。

### <a name="span-idusbhubactivitymaycauseflashingfailuresspanspan-idusbhubactivitymaycauseflashingfailuresspanspan-idusbhubactivitymaycauseflashingfailuresspanusb-hub-activity-may-cause-flashing-failures"></a><span id="USB_hub_activity_may_cause_flashing_failures"></span><span id="usb_hub_activity_may_cause_flashing_failures"></span><span id="USB_HUB_ACTIVITY_MAY_CAUSE_FLASHING_FAILURES"></span>USB 集线器活动可能会引起闪烁的故障

据悉某些 USB 集线器闪烁时，甚至会导致可靠性问题中由于硬件干扰到流式 FFU 数据序列的设备。

不能连接和断开连接时出现闪烁的其它连接的设备多台设备共享一个 USB 集线器。 这暴露出某些 USB 控制器与一个已知的硬件问题。 有关详细信息，请参阅[KB908673](http://support.microsoft.com/kb/908673)。 闪烁的设备时，应不会拔出 USB 设备。

### <a name="span-idusbcablelengthislimitedto3feetspanspan-idusbcablelengthislimitedto3feetspanspan-idusbcablelengthislimitedto3feetspanusb-cable-length-is-limited-to-3-feet"></a><span id="USB_cable_length_is_limited_to_3_feet"></span><span id="usb_cable_length_is_limited_to_3_feet"></span><span id="USB_CABLE_LENGTH_IS_LIMITED_TO_3_FEET"></span>USB 电缆长度不能超过 3 英尺

当使用 USB 电缆超过 3 英尺 （.91 米），或者如果您闪烁的安装程序中包含连续总到超过 3 英尺的电缆，闪烁可能不太可靠。 这是因为在更长的电缆数据传输的硬件限制。

### <a name="span-idflashingtimeperphonespanspan-idflashingtimeperphonespanspan-idflashingtimeperphonespanflashing-time-per-phone"></a><span id="Flashing_time_per_phone"></span><span id="flashing_time_per_phone"></span><span id="FLASHING_TIME_PER_PHONE"></span>每个电话的闪烁时间

您将需要评估是否每个设备的闪烁时间能够满足其目标，为您制造的行。

 

 





