---
title: Device.Connectivity.PciConnected
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: bcb3ff8337f1a8061a8371595b9f6ac7f111f86c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.PciConnected

 - [Device.Connectivity.PciConnected](#device.connectivity.pciconnected)
-->

<a name="device.connectivity.pciconnected"></a>
##Device.Connectivity.PciConnected

### <a name="deviceconnectivitypciconnected64bitprefetchablebar"></a>Device.Connectivity.PciConnected.64BitPrefetchableBar

*PCI-X 和 PCI Express 的设备，使用 prefetchable 的内存条，实现 64 位 prefetchable 内存基址寄存器 （条）*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

坐 PCI-X 或 PCI Express 总线上，并使用 prefetchable 内存条必须基于 x64 的系统上实现 64 位 prefetchable 内存条设备。

*设计备注*

请参阅[固件的 Windows 中的 PCI 设备资源的分配](http://www.microsoft.com/whdc/system/bus/pci/PCI-rsc.mspx)

如果设备支持 64 位 prefetchable 内存条，Windows 会尝试分配 4 GB 以上的区域。 在一个 PCI 桥，Windows 将忽略整个设备路径发出从桥在其作用域中定义此方法的引导配置。 桥接器和设备下面要为其分配 4 GB 以上的区域，路径中的所有设备都必须都支持 64 位 prefetchable 条。 如果不是这样，重新平衡代码运行并移动所有资源分配下 4 GB，因为目标是要尽可能开始尽可能多的设备

### <a name="deviceconnectivitypciconnectedconfigurationspacecorrectlypopulated"></a>Device.Connectivity.PciConnected.ConfigurationSpaceCorrectlyPopulated

*PCI 设备的配置空间进行正确填充*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

PCI2.3 描述了系统用来标识和配置连接到总线的每个设备的配置空间。 配置空间标题区域和设备相关地区组成。 配置的每个空间必须具有在 offset0 64 字节的标头。 所有设备注册设备电路用于初始化、 配置和灾难性错误处理必须符合 byte64 和 byte255 之间的空间内。
所有其他设备在正常操作过程中使用的寄存器必须位于正常的 I/O 或者内存空间。 未实现的寄存器或保留寄存器读取必须正常完成并返回零。 写入到保留寄存器通常情况下，必须完成和数据必须被放弃。
设备需要在中断时的所有寄存器必须都是在 I/O 或者内存空间。

### <a name="deviceconnectivitypciconnectedexpresscardimplementsserialnumber"></a>Device.Connectivity.PciConnected.ExpressCardImplementsSerialNumber

*支持 USB 和 PCI Express 接口的单一 ExpressCard 模块实现常见的序列号*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

PCI ExpressCard 机电规范中所述，对单个模块支持 USB 和 PCI Express 接口 ExpressCard 模块必须实现公用的序列号。
这是唯一的方法，Windows 将使用来确定一个模块上的 USB 和 PCI Express 的关系。
 

### <a name="deviceconnectivitypciconnectedinterruptdisablebit"></a>Device.Connectivity.PciConnected.InterruptDisableBit

*PCI 和 PCI-X 设备，这些都符合 PCI 2.3，支持中断禁用位*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有的 PCI 和 PCI-X 设备声称支持的 PCI 本地总线技术指标修订版 2.3 或更高版本，必须支持中断禁用位。

*设计备注*

请参见 PCI 局部总线技术指标修订版 2.3、 部分 6.2.2。

### <a name="deviceconnectivitypciconnectedmsiormsixsupport"></a>Device.Connectivity.PciConnected.MsiOrMsixSupport

*PCI 设备报告 PCI-X 的 PCI 配置空间中的功能和所生成的中断可能支持 MSI 或 MSI X，但不是需要执行此操作*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

作为一部分的 PCI 常规技术指标 2.2 或更高版本，PCI-X 的补充说明，第 3.2 节所有生成中断的 PCI-X 设备必须支持消息告知中断。
MSI 实现 MSI 功能必须配置空间中实现。
对于 MSI-X 实现，必须在配置空间中实现 MSI-X 功能。
但是，正在通过 PCI Express 更换 PCI-X 和许多现有的实现都不支持 MSI 或 MSI X，因为这种要求是正在放松。 MSI 或 MSI-X 支持所声称的任何设备必须这样做，也会失败相关的 WDK 测试。

*设计备注*

消息发出信号中断 PCI-X 设备所需的工业标准规范。 但是，如上所示。

### <a name="deviceconnectivitypciconnectedpciandpcixdevicesarepcicompliant"></a>Device.Connectivity.PciConnected.PciAndPcixDevicesArePciCompliant

*PCI 和 PCI-X 设备，至少，是符合标准的 PCI 2.1*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有 PCI 和 PCI-X 设备必须都符合 PCI 局部总线规范-修订版 2.1 或更高版本。 此要求适用于 X86，IA64 的设备和 x64 系统。

*设计备注*

PCI 局部总线规范-修订版 2.1 或更高版本，请参阅。

### <a name="deviceconnectivitypciconnectedpciexpress"></a>Device.Connectivity.PciConnected.PCIExpress

*PCI Express 要求*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

**1.PCI Express 设备设备驱动程序不会修改 VC 启用设置︰**

设备驱动程序不能修改"VC 启用"位 (PCI Express 基础规范、 Version1.0a、 Section7.11.7、 VC 资源控制寄存器︰ 31 位) 的任何设备的扩展 (非 VC0) 虚拟信道或通道。

**2。** **PCI Express 链接活动状态 L1 退出延迟不能超过 64 祍︰**

PCI Express 之间的链接，复杂的根和设备或桥接器上, 不能有超过 64 微秒的活动状态 L1 退出延迟系统除非链接程序与 PCI Express 的电缆;也就是说，不能 111b 值报告中链接功能寄存器字段 17:15。 请参阅 PCIe 速成版基规范版本 1.0 a、 7.8.6 节。

**3。** **支持固件控制热插拔用途的热插拔 PCI Express 端口\_OSC 控制方法用于启用和禁用**:

所有 PCI Express 热插拔都支持端口控制固件-热-插头必须都支持\_OSC 来启用和禁用固件控制热插拔 PCI 固件规范版本 3.0 中所述的控制方法。 请参见 PCI Express 基础规范、 修订版 1.1，部分 6.7.4。

**4。** **PCI Express 组件在其主界面上实现单个设备编号︰**

每个 PCI Express 组件 （即物理设备） 被限制为 （上游端口），其主界面上实现单个设备数，但它可以实现内设备数达八个独立的功能。 请参见 PCI Express 基规范，Revision1.1 （或更高版本），部分 7.3.1。

**5.PCI Express 设备实现支持 MSI 或 MSI x:**

MSI 的支持是可选的 PCI 2.1、 PCI 2.2 和 PCI 2.3 设备，则需要 PCI Express 设备。 可以作为 MSI 或 MSI-X 可以实现此功能。 请参见 PCI Express 基础规范，Revision1.0a，Section 6.1。

**6**。**复杂的 PCI Express 根支持增强 （内存映射） 的配置空间的访问机制︰**

在 PCI Express 基本规范，修订版 1.1 版 （或更高版本），部分 7.9 复杂根必须支持增强的配置空间的访问机制。

**7。** **可以中断的 PCI Express 设备支持中断禁用位︰**

如果实现一个中断时，PCI Express 设备必须支持 PCI 局部总线规范-Revision2.3 中所描述的中断禁用功能。 这位将禁用该设备或从断言 INTx 函数。 值 0 允许其 INTx 信号的断言。 1 的值将禁用其 INTx 信号的断言。 这位状态时重置为 0

### <a name="deviceconnectivitypciconnectedsubsystemidsrequired"></a>Device.Connectivity.PciConnected.SubsystemIdsRequired

*设备 Id 包括 PCI 子系统 Id*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

SID 和 SVID 字段必须遵守 PCI 本地总线规范 2.3 和实现中的 SID 要求的详细信息在"PCI 设备子系统 Id 和 Windows。
AMR 设备和系统主板上的 MR 设备没有免于 SID 和 SVID 的要求。
SVID 不需要有关 PCIe 到 PCI/PCI-X 的桥梁。

*设计备注*

在<http://go.microsoft.com/fwlink/?LinkId=36804>中看到"PCI 设备子系统 Id 和窗口"。
