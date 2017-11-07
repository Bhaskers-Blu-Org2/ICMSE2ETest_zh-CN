---
title: "对于基本系统诊断的录制"
description: "对于基本系统诊断的录制"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: bfaa08d7-0bb0-4786-a925-dc54c6f78ffc
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 311f23a2af96a3bdb83c49c6e40e48440381c8f2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="recording-for-basic-system-diagnosis"></a>对于基本系统诊断的录制


默认情况下，Windows 性能记录器 (WPR) 运行每个录制的**常规**配置文件。 此配置文件用于记录基本系统问题和性能数据。

在这篇文章︰

-   [常规配置文件设置](#generalpro)

-   [找出持久的性能问题](#sus)

-   [发现的瞬态性能问题](#trans)

## <a name="a-href-idgeneralproageneral-profile-settings"></a><a href="" id="generalpro"></a>常规配置文件设置


**常规**配置文件使用以下收集器︰

**NT 内核记录器收集器**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>缓冲区大小 (KB)</p></td>
<td><p>1024</p></td>
</tr>
<tr class="even">
<td><p>缓冲区数目</p></td>
<td><p>198</p></td>
</tr>
<tr class="odd">
<td><p>系统的关键字</p></td>
<td><p>CpuConfig、 CSwitch、 DiskIO、 DPC、 HardFaults，中断，KernelQueue、 加载程序、 MemoryInfo、 ProcessCounter、 电源、 ProcessThread、 ReadyThread、 SampledProfile、 ThreadPriority</p></td>
</tr>
</tbody>
</table>

 

**WPR\_启动\_WPR 事件收集器**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>属性</th>
<th>值</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>缓冲区大小 (KB)</p></td>
<td><p>1024</p></td>
</tr>
<tr class="even">
<td><p>缓冲区数目</p></td>
<td><p>39</p></td>
</tr>
<tr class="odd">
<td><p>提供程序</p></td>
<td><p>PerfTrack:: 0x04</p>
<p>Microsoft Windows 的令人陶醉的外壳︰ 0x0000000000100000: 0x04</p>
<p>Microsoft Windows 的内核的功耗︰ 0x0000000000000004: 0xff</p>
<p>Microsoft Windows Win32k: 0x0000000000402000: 0xff</p>
<p>Microsoft 的 Windows 的 WLAN 的自动配置︰ 0x0000000000000200: 0xff</p>
<p>.NET 公共语言运行库︰ 0x0000000000000098: 0x05</p>
<p>Microsoft 的 JScript: 0x0000000000000001: 0xff e7ef96be-969f-414f-97 d 7-3ddb7b558ccc: 0x0000000000002000: 0xff</p>
<p>MUI 资源跟踪:: 0xff</p>
<p>Microsoft Windows COMRuntime: 0x0000000000000003: 0xff</p>
<p>Microsoft 的 Windows 的网络的关联:: 0xff</p>
<p>Microsoft Windows RPCSS:: 0x04</p>
<p>Microsoft Windows RPC:: 0x04 a669021c-c450-4609-a035-5af59af4df18:: 0x00</p>
<p>Microsoft Windows 的内核的处理器的功耗:: 0xff</p>
<p>Microsoft 的 Windows 的内核-StoreMgr:: 0xff e7ef96be-969f-414f-97 d 7-3ddb7b558ccc:: 0xff</p>
<p>Microsoft Windows UserModePowerService:: 0xff</p>
<p>Microsoft Windows Win32k:: 0xff</p>
<p>Microsoft Windows ReadyBoostDriver:: 0xff</p></td>
</tr>
</tbody>
</table>

 

有关收集器和提供程序的详细信息，请参阅[收集器](collectors.md)和[提供程序](providers.md)。

## <a name="a-href-idsusaidentify-sustained-performance-issues"></a><a href="" id="sus"></a>找出持久的性能问题


要找出持久的性能问题，您可以运行**常规**配置文件以及其他默认设置。 它们是︰**详细**日志的详细信息并记录到**内存**。 在 WPR 启动录制之后，它将一直持续到停止并保存录制。

## <a name="a-href-idtransaidentify-transient-performance-issues"></a><a href="" id="trans"></a>发现的瞬态性能问题


因为无法预知将发生瞬态性能问题时，您必须运行**常规**配置文件，直到问题调查。

**找出瞬态性能问题**

1.  在 WPR 屏幕上，如果隐藏了选项，单击**其他选项**。

2.  从**性能方案**下拉菜单中，选择**一般**。

3.  从**登录模式**下拉菜单中，选择**内存**。

4.  单击**开始**，然后运行记录，直到问题出现为止。

5.  单击**保存**，然后单击**浏览**以使用一个名称或默认位置以外的位置保存该文件。 默认位置是**\\用户\\%用户名 %\\文档\\WPR 文件**系统驱动器上的文件夹。

6.  输入问题描述。

7.  单击**保存**。

## <a name="related-topics"></a>相关的主题


[WPR 常见方案](windows-performance-recorder-common-scenarios.md)

[性能的方案](performance-scenarios.md)

 

 







