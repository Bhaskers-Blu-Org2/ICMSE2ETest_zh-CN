---
author: kpacquer
Description: "域服务方案"
ms.assetid: 064509f8-902d-4ac8-85d9-7a405512d762
MSHAttr: PreferredLib:/library/windows/hardware
title: "域服务方案"
ms.openlocfilehash: b0d4e51602e55b4939c3b8597277e3c20b209674
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="field-service-scenarios"></a>域服务方案


方案可以帮助识别域服务过程中的安全漏洞。 应该检查每个方案，以验证安全解决方案已由 OEM。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>设备翻新过</p></td>
<td align="left"><p>移动运营商和 Oem 可以使用多种方法来翻新设备。 客户退回手机对移动运营商出于某种原因时发生第一个翻新方案。 在这种情况下，设备通常运送到它们与当前的 OEM 映像的 reflashed 位置区域 OEM 服务中心。</p>
<p>第二个翻新方案客户有问题设备的操作时发生。 客户将设备返回到移动运营商商店和商店助理运行基本诊断。 关联可以尝试重置为出厂设置的电话或通过使用由 Microsoft (FFU) 或 OEM 提供的闪烁工具刷新操作系统的设备。 如果此操作失败，商店助理可以决定将设备发送到 OEM 服务的中心。 设备离开移动运营商的控制，并返回到 OEM 之前，某些机制，用于删除所有客户数据。</p>
<p>在 OEM 服务中心设备的更新是第三个翻新方案。 可以使用任何工具 OEM 服务中心配有 reflashed 设备。 一些 Oem 将使用 OS 级别闪烁技术，意味着它们不能刷新设备，如果断开调制解调器级引导加载程序或软件。 其他人将能够刷新的调制解调器和操作系统分区。</p></td>
</tr>
<tr class="even">
<td align="left"><p>电话故障诊断</p></td>
<td align="left"><p>字段测试和诊断功能的应用程序可以使用的移动电话操作员存储、 移动运营商服务中心和 OEM 服务的中心在两个不同方案中的一部电话上执行特定的测试。</p>
<p>客户用设备遇到困难并运行诊断测试时收集的信息，在报告的问题时的第一个故障排除方案。</p>
<p>第二种情况是当移动运营商或 OEM 服务中心，以期建立设备的质量状态。 该方案是以上故障排除方案中的更一般形式。 这是因为可能有多个原因比会触发需要诊断和测试的零售电话的客户问题。 例如，若要执行域质量措施，测试无法启动进行随机样本测试。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>工程闪烁</p></td>
<td align="left"><p>硅片供应商和 Oem 工程人员需要访问闪烁在手机的硬件和软件的开发过程中的技术。 这种情况下通常受 JTAG、 基于 UEFI 的闪烁或 OEM 特定闪烁技术等低级别技术支持。 选择何种技术取决于正在处理的问题、 开发流程和支持工具。 闪烁选项粒度变化;较低级别工具具有更灵活地选择哪些分区可以刷新。</p></td>
</tr>
<tr class="even">
<td align="left"><p>工程诊断</p></td>
<td align="left"><p>硅片供应商和 Oem 的工程人员在手机的硬件和软件的开发过程中需要访问诊断技术。 这些方案通常由 SV 或将禁用零售设备的 OEM 提供的技术支持。 一些 SV 技术提供了一组广泛的功能 — — 包括支持读取和写入闪存的功能 — — 运设备之前，必须禁用的。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>移动运营商试验</p></td>
<td align="left"><p>可能需要 flash 支持移动运营商试验设备的操作系统映像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>生产制造</p></td>
<td align="left"><p>闪烁在制造电话的过程而异 OEM。 一些 Oem 使用团伙程序员，可以一次; 闪烁的单位数其他人使用此文档中所述的闪烁技术。 闪烁的过程的详细信息，请参阅[闪烁工具](flashing-tools.md)。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>返工制造</p></td>
<td align="left"><p>一些 Oem 就地进行返工失败制造质量控制的电话有的过程。 因为完全装配设备，它不可能使用团伙程序员;这种重复工作可以完成使用 tethered 闪烁技术类似于客户返回翻新方案。</p></td>
</tr>
<tr class="even">
<td align="left"><p>Remanufacturing</p></td>
<td align="left"><p>可能有需要重新调整用途，为不同地区或移动运营商的现有电话库存现有操作系统替换为一个自定义为新的市场。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[制造](index.md)

 

 






