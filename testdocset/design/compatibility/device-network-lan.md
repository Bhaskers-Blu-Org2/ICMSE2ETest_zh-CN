---
title: Device.Network.LAN
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 4e1db4ead7da5faa52774f43a41e3a5fee3aaf8f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicenetworklan"></a>Device.Network.LAN

 - [Device.Network.LAN.10GbOrGreater](#device.network.lan.10gborgreater)
 - [Device.Network.LAN.AzureStack](#device.network.lan.azurestack)
 - [Device.Network.LAN.Base](#device.network.lan.base)
 - [Device.Network.LAN.ChecksumOffload](#device.network.lan.checksumoffload)
 - [Device.Network.LAN.CS](#device.network.lan.cs)
 - [Device.Network.LAN.DCB](#device.network.lan.dcb)
 - [Device.Network.LAN.GRE](#device.network.lan.gre)
 - [Device.Network.LAN.IPsec](#device.network.lan.ipsec)
 - [Device.Network.LAN.KRDMA](#device.network.lan.krdma)
 - [Device.Network.LAN.LargeSendOffload](#device.network.lan.largesendoffload)
 - [Device.Network.LAN.PM](#device.network.lan.pm)
 - [Device.Network.LAN.RSC](#device.network.lan.rsc)
 - [Device.Network.LAN.RSS](#device.network.lan.rss)
 - [Device.Network.LAN.SRIOV](#device.network.lan.sriov)
 - [Device.Network.LAN.SRIOV.VF](#device.network.lan.sriov.vf)
 - [Device.Network.LAN.TCPChimney](#device.network.lan.tcpchimney)
 - [Device.Network.LAN.VMMQ](#device.network.lan.vmmq)
 - [Device.Network.LAN.VMQ](#device.network.lan.vmq)
 - [Device.Network.LAN.VXLAN](#device.network.lan.vxlan)
 - [Device.Network.LAN](#device.network.lan)

<a name="device.network.lan.10gborgreater"></a>
## <a name="devicenetworklan10gborgreater"></a>Device.Network.LAN.10GbOrGreater

10 GB 或更多局域网要求 

### <a name="devicenetworklan10gborgreatercloudstress"></a>Device.Network.LAN.10GbOrGreater.CloudStress
实现 GRE 封装包任务减轻的以太网设备必须符合规范

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

此要求适用于所有认证服务器的以太网设备。  此测试可验证以太网设备可以满足数据中心云的压力要求。 满足这一要求的以太网设备还必须符合规范和支持下列功能︰

所有的网络适配器必须支持以下 Device.Network.LAN 功能。  

- 基 (要求 100MbOrGreater 至 SupportIEEE8023)
- ChecksumOffload
- LargeSendOffload
- RSS

对于实现的任何新功能的 WS2016 的 Nic 10gb 或更高版本操作系统的所有驱动程序 （即 NDKPI 2.0、 VMMQ、 VxLAN 任务卸载、 NVGREv2 任务卸载、 MTU 为 HNV，PacketDirect） 还必须提供与基本 10 千兆以太网 NIC 配置文件的 PC （私有云模拟器） 测试 4 节点群集配置。


<a name="device.network.lan.azurestack"></a>
## <a name="devicenetworklanazurestack"></a>Device.Network.LAN.AzureStack

_定义了局域网网卡 (NIC) 支持基于 Microsoft Azure 堆栈私有云解决方案中必须满足的要求_

### <a name="devicenetworklanazurestackbasicfunction"></a>Device.Network.LAN.AzureStack.BasicFunction

_在 Microsoft Azure 堆栈解决方案中使用的 LAN 卡的基本要求_ 

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

通过下表来捕获 Microsoft Azure 堆栈 LAN 网卡 (Nic) 的要求。

<table>
    <tr><th>功能</th><th>要求 ></th></tr>
    <tr><td>Device.Network.LAN.10GbOrGreater</td><td>Device.Network.LAN.10GbOrGreater.CloudStress</td></tr>
    <tr><td>Device.Network.LAN.VXLAN</td><td>Device.Network.LAN.VXLAN.VXLANPacketTaskOffloads</td></tr>
    <tr><td>Device.Network.LAN.VMQ</td><td>Device.Network.LAN.VMQ.VirtualMachineQueues</td></tr>
    <tr><td>Device.Network.LAN.VMMQ</td><td>Device.Network.LAN.VMMQ.VirtualMachineMultipleQueues</td></tr>
    <tr><td rowspan="5">Device.Network.LAN.RSS</td><td>Device.Network.LAN.RSS.RSS</td></tr>
    <tr><td>Device.Network.LAN.RSS.SetHashFunctionTypeAndValue</td></tr>
    <tr><td>Device.Network.LAN.RSS.SupportIndirectionTablesSizes</td></tr>
    <tr><td>Device.Network.LAN.RSS.SupportToeplitzHashFunction</td></tr>
    <tr><td>Device.Network.LAN.RSS.SupportUpdatesToRSSInfo</td></tr>
    <tr><td>Device.Network.LAN.MTUSize</td><td>Device.Network.LAN.MTUSize</td></tr>
    <tr><td>Device.Network.LAN.LargeSendOffload</td><td>Device.Network.LAN.LargeSendOffload.LargeSendOffload</td></tr>
    <tr><td>Device.Network.LAN.KRDMA</td><td>Device.Network.LAN.KRDMA.KRDMA</td></tr>
    <tr><td>Device.Network.LAN.GRE</td><td>Device.Network.LAN.GRE.GREPacketTaskOffloads</td></tr>
    <tr><td>Device.Network.LAN.DCB</td><td>Device.Network.LAN.DCB.DCB</td></tr>
    <tr><td>Device.Network.LAN.ChecksumOffload</td><td>Device.Network.LAN.ChecksumOffload.ChecksumOffload</td></tr>
    <tr><td rowspan="12">Device.Network.LAN.Base</td><td>Device.Network.LAN.Base.100MbOrGreater</td></tr>
    <tr><td>Device.Network.LAN.Base.32MulticastAddresses</td></tr>
    <tr><td>Device.Network.LAN.Base.AdvProperties</td></tr>
    <tr><td>Device.Network.LAN.Base.AnyBoundary</td></tr>
    <tr><td>Device.Network.LAN.Base.IPv4AndIPv6OffloadParity</td></tr>
    <tr><td>Device.Network.LAN.Base.NDISCalls</td></tr>
    <tr><td>Device.Network.LAN.Base.NDISRequirements</td></tr>
    <tr><td>Device.Network.LAN.Base.PacketFiltering</td></tr>
    <tr><td>Device.Network.LAN.Base.PreserveOSServices</td></tr>
    <tr><td>Device.Network.LAN.Base.PriorityVLAN</td></tr>
    <tr><td>Device.Network.LAN.Base.ShortPacketPadding</td></tr>
    <tr><td>Device.Network.LAN.Base.SupportIEEEE8023</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

### <a name="devicenetworklanazurestackcloudstress"></a>Device.Network.LAN.AzureStack.CloudStress

_网络控制器用于 Microsoft Azure 堆栈的解决方案必须符合本规范_ 

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

私有云解决方案构成了紧密集成的软件和硬件组件，以提供高性能的可恢复性。 中的任何组件 （软件、 硬件、 驱动程序、 固件等） 的问题会危害解决方案，并会破坏任何私有云的有关服务级别协议 (SLA) 所做的承诺。 

许多这些问题都只能在云高强度的专用模拟出来后。 私有云模拟器 (PC) 使您可以验证您的组件在云方案并确定此类问题。 它通过创建 VM 工作负载、 调度管理操作 （负载平衡、 软件/硬件维护），和在私有云上注入故障 （没有计划的硬件/软件故障） 来模拟实时数据中心/私有云。 

为遵守此规范，控制器必须通过个人电脑测试运行的网络控制器-AzureStack 上的 4 节点群集配置的配置文件。

### <a name="devicenetworklanazurestackfirmwareupdate"></a>Device.Network.LAN.AzureStack.FirmwareUpdate

_网络控制器用于 Microsoft Azure 堆栈的解决方案必须符合本规范_ 

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

设备驱动程序和固件更新工具必须满足如 Device.DevFund.Server.Nano 中所述的 Nano 服务器兼容性要求


<a name="device.network.lan.base"></a>
## <a name="devicenetworklanbase"></a>Device.Network.LAN.Base

*局域网的要求*

### <a name="devicenetworklanbase100mborgreater"></a>Device.Network.LAN.Base.100MbOrGreater

*以太网设备必须支持 100 Mb 或更高版本的链接速度。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备必须能够存在于 100 Mb 或更高的速度。

### <a name="devicenetworklanbase32multicastaddresses"></a>Device.Network.LAN.Base.32MulticastAddresses

*以太网设备必须支持至少 32 个多路广播地址的筛选。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备必须支持筛选的 32 个或更多址广播地址。 

设计备注︰ 请参阅 Windows 驱动程序工具包，"多播"。 请参阅 Windows 驱动程序工具包、"NdisReadNetworkAddress"和"MAC 地址"。

### <a name="devicenetworklanbaseadvproperties"></a>Device.Network.LAN.Base.AdvProperties

*以太网设备必须保护高级的属性，并提供完整的可配置性通过高级属性。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备必须遵循标准化的注册表关键字用于控制在 MSDN 上所述的高级的功能。  标准化的 Microsoft 和专用关键字从恶意值，还必须保护设备。

### <a name="devicenetworklanbaseanyboundary"></a>Device.Network.LAN.Base.AnyBoundary

*以太网设备必须能够传输数据包从缓冲区在所有边界上对齐。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

在奇数字节、 字、 双字或其他边界缓冲区中开始是否指缓冲区对齐方式。 设备必须能够传输的数据包与任何数据包片段在奇数字节边界上开始。 为了提高性能，必须到双字边界上的相邻缓冲区收到数据包。

### <a name="devicenetworklanbaseipv4andipv6offloadparity"></a>Device.Network.LAN.Base.IPv4AndIPv6OffloadParity

*实施减轻的以太网设备必须为 IPv4 和 IPv6 因此以一致的方式执行。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

实现由以太网设备需要以一致的方式，操作而不考虑所使用的 IP 协议，减轻了网络。 无奇偶校验卸载允许 Windows 客户跨 IPv4 和 IPv6 有一致和可预测的体验。

### <a name="devicenetworklanbasendiscalls"></a>Device.Network.LAN.Base.NDISCalls

*只有 NDIS 库或 WDF 的系统调用，必须使以太网设备。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备的驱动程序必须进行唯一的 NDIS 或 WDF 调用。 不允许有任何的其它内核模式组件的调用。 

设计备注︰ 请参阅 Windows 驱动程序工具包、"NDIS"和"WDF。"

### <a name="devicenetworklanbasendisrequirements"></a>Device.Network.LAN.Base.NDISRequirements

*以太网设备必须符合 Windows 驱动程序工具包中的 NDIS 要求。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有的以太网设备驱动程序必须符合 NDIS 指定 Windows 驱动程序工具包中。 

设计备注︰ 请参阅 Windows 驱动程序工具包，"NDIS。"

### <a name="devicenetworklanbasepacketfiltering"></a>Device.Network.LAN.Base.PacketFiltering

*以太网设备必须支持数据包筛选。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

微型端口驱动程序必须支持 Windows 驱动程序工具包中的所有筛选器类型。 注︰ 应被执行筛选硬件/固件中。

### <a name="devicenetworklanbasepreserveosservices"></a>Device.Network.LAN.Base.PreserveOSServices

*以太网设备微型端口驱动程序的驱动程序/软件必须禁用 OS 服务。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备微型端口驱动程序的驱动程序/软件必须禁用 OS 服务。 某些设备往往对闭合服务如文库筛选引擎 (BFE)。 这使系统易受攻击缺乏安全功能。

### <a name="devicenetworklanbasepriorityvlan"></a>Device.Network.LAN.Base.PriorityVLAN

*实现链路速度大于或等于千兆位的以太网设备必须实现优先级和 VLAN 标签根据 IEEE 802.1 q 规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现链接速度大于或等于千兆位的以太网设备。 如果以太网设备未实现链接速度千兆位或更高版本，则这一要求不适用于。 以太网设备和驱动程序必须支持的插入和删除的优先级和 VLAN 标记。

### <a name="devicenetworklanbaseshortpacketpadding"></a>Device.Network.LAN.Base.ShortPacketPadding

*以太网设备必须板短数据包使用持续数据。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

就填充添加到短的以太网数据包使该数据包的大小最小的 IEEE 802.3 部分 4.2.3.3，数据包大小之前必须初始化为零或 8 位重复模式传输数据包。 802.3 以太网规格需要比之前到线路上传输的数据包进行填充最大最小尺寸的最小数据包大小短的数据包。 802.3 以太网规格不指定填充内容;但是，Microsoft 还要求为零或为解决安全问题的另一个常量值的空白。 某些驱动程序填充的数据包使用来自先前发送的数据包;这种做法是不可接受的。 

设计备注︰ 建议新的解决方案来实现零填充。 但是，有些设备在硬件中实现填充使用 0xffs，解决了安全问题。

### <a name="devicenetworklanbasesupportieeee8023"></a>Device.Network.LAN.Base.SupportIEEEE8023

*以太网设备必须遵守 IEEE 802.3。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有 802.3 以太网设备必须实施和遵守 IEEE 802.3 规格。

<a name="device.network.lan.checksumoffload"></a>
## <a name="devicenetworklanchecksumoffload"></a>Device.Network.LAN.ChecksumOffload

*网络要求*

### <a name="devicenetworklanchecksumoffloadchecksumoffload"></a>Device.Network.LAN.ChecksumOffload.ChecksumOffload

*以太网设备必须实现校验和减轻。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

 

发送和接收 IPv4 和 IPv6 的 TCP 校验和清除

发送和接收 ipv4 的 IP 校验和清除

为 IPv4 和 IPv6 的发送和接收 UDP 校验和卸载

对 TCP 校验和标准化的关键字的支持是必需的。

校验和减轻的以太网设备实现必须公开 NDIS 枚举关键字。

 

<a name="device.network.lan.cs"></a>
## <a name="devicenetworklancs"></a>Device.Network.LAN.CS

*连接待机性能的计算机 （也称为平台） 支持低功耗的活动状态，并宣称支持的操作系统使用适当的 ACPI 标志该状态 (低\_电源\_S0\_空闲\_能够) 在 FADT 中。它还应满足一个平台连接，备用的所有 Windows 认证要求。此节指定有线 LAN （以太网） 连接备用要求。*

### <a name="devicenetworklancsnetworkwake"></a>Device.Network.LAN.CS.NetworkWake

*有线的 LAN （以太网） 设备集成到系统中连接待机状态或坞站随系统必须支持网络唤醒模式。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

下面列出了具体的要求︰

唤醒局域网模式︰

有线的 LAN 设备和驱动程序都必须的支持至少三十二 （32） 位图图案的 128 字节大小的最小值。 这种模式类型指的是灵活的位图模式 (NDIS\_PM\_WOL\_数据包。NdisPMWoLPacketBitmapPattern) 和没有其他模式类型。

唤醒数据包︰

有线的 LAN 设备及其驱动程序必须支持数据包唤醒。 对此唤醒数据包类型的支持是必需的并且不会将其包括在 32 位图图案要求。

唤醒数据包指示︰

有线的 LAN 设备和驱动程序都需要支持唤醒数据包指示所有网络唤醒数据包并且可以缓存，并指明导致唤醒的完整的网络数据包。 请注意，这将取代连接待机功能的设备的 Device.Network.LAN.PM.WakePacket 要求。

设计备注︰

请参阅 MSDN 上的电源管理规范。

### <a name="devicenetworklancspresenceoffload"></a>Device.Network.LAN.CS.PresenceOffload

*有线的 LAN （以太网） 设备集成到系统中连接待机状态或坞站随系统必须支持卸载功能的网络状态。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

此功能支持是必需的。 下面列出了具体的要求︰

ARP 协议卸载︰

规定在 MSDN 上的电源管理规范，有线的 LAN 设备必须实现 ARP 卸载。 具体来说，必须卸载响应到 ARP 请求 (操作 = 1） 通过使用 ARP 应答响应 (操作 = 2） 根据 RFC 826 (<http://tools.ietf.org/html/rfc826>) 中的定义。

NS 协议卸载︰

有线的 LAN 设备必须实现 IPv6 NS 卸载 MSDN 上的电源管理规范中定义。 特别是，卸载必须响应相邻节点请求 (操作 = 135) 通过与 NS 广告响应 (操作 = 136) 根据 RFC 4861 (<http://tools.ietf.org/html/rfc4861>) 中的定义。 我们要求至少 2 ND 卸载请求支持。 每个请求可以有 2 的目标地址。 它们应公布在 NDIS 的值\_PM\_CAPABILITIES::NumNSOffloadIPv6Addresses 是数量的请求，没有地址数。 因此，如果它们所支持的最小的 2 请求，它们应公布 2。 字段的名称错误，而将在下一步修复 NDIS 释放。

微型端口必须根据 Rfc 描述 IPv6 相邻节点搜索和相邻节点请求协议实现了上述的协议。

### <a name="devicenetworklancsreliablecsconnectivity"></a>Device.Network.LAN.CS.ReliableCSConnectivity

*支持连接备用系统上的 LAN 设备必须提供可靠的连接，连接待机状态。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

D0 的工作电源状态和低功耗状态 D2/D3 虽然在连接待机 (CS) 之间无缝地过渡有线的 LAN 设备。 有线的局域网设备维护 OSI 层 2 链接在 CS 中的连接。 有线的 LAN 设备上匹配的唤醒模式唤醒。 有在 CS 中没有虚假的唤醒。 唤醒数据包将被传输而不会延迟或缓冲。 对 IPv4 和 IPv6 在 CS 中的将锁定屏幕应用程序保持连接与控制通道或推式通知的触发器。

在低功耗状态的精确 D 值取决于基础的总线类型。 例如，网络适配器的 USB，SDIO 总线以其低功耗状态，同时在 PCI 网络适配器使用 D2 或 PCIe 总线使用 D3 状态。

其他信息

例外情况-不适用于非 AOAC 功能的设备

### <a name="devicenetworklancswakeevents"></a>Device.Network.LAN.CS.WakeEvents

*有线的 LAN （以太网） 设备集成到系统中连接待机状态或坞站随系统必须支持各种唤醒触发器。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

下面列出了具体的要求︰ 唤醒媒体连接︰ 必须公布有线以太网设备和媒体支持远程唤醒连接在 MSDN 上规范中定义。 媒体断开连接在唤醒︰ 有线以太网设备必须公布，并支持远程唤醒媒体断开在 MSDN 上规范中定义。

设计备注︰ 请参阅 MSDN 上的电源管理规范。

### <a name="devicenetworklancswakereasondetection"></a>Device.Network.LAN.CS.WakeReasonDetection

*有线的 LAN （以太网） 设备集成到系统中连接待机状态或坞站随系统必须支持唤醒原因检测。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

下面列出了具体的要求︰ 唤醒原因支持︰ 有线以太网设备必须包括唤醒原因支持 NDIS 符合\_状态\_PM\_唤醒\_原因在 MSDN 上的文档。  当唤醒由接收的网络数据包时，需要网卡可捕获，并指示导致操作系统唤醒整个数据包。 

设计备注︰ 请参阅 MSDN 上的电源管理规范。

<a name="device.network.lan.dcb"></a>
## <a name="devicenetworklandcb"></a>Device.Network.LAN.DCB

*局域网的要求*

###  <a name="devicenetworklandcbdcb"></a>Device.Network.LAN.DCB.DCB

*实现数据中心桥接 (DCB) 的以太网设备必须符合 DCB 规范*。

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于支持数据中心桥接 (DCB) 的以太网设备。

实现数据中心桥接 (DCB) 的以太网设备必须符合以下要求︰

 - MaxNumTrafficClasses 必须介于 3 和 8 的包容。
 - MaxNumEtsCapableTrafficClasses 必须至少为 2。
 - MaxNumPfcEnabeldTrafficClasses 必须至少为 1。
 - ETS 必须得到支持。
 - PFC 必须得到支持。
 - 严格的优先级必须得到支持。
 - iSCSI CNAs 必须支持分类元素用于 iSCSI 通信 （TCP 端口 860 和 3260，源和目标端口）。
 - FCoE CNAs 必须支持分类元素 FCoE 通信 （0x8906 的以太网类型）。

设计备注

请参阅在<http://msdn.microsoft.com/en-us/library/windows/hardware/hh451635.aspx>桥规范数据中心。

<a name="device.network.lan.gre"></a>
## <a name="devicenetworklangre"></a>Device.Network.LAN.GRE

*局域网的要求*

### <a name="devicenetworklangregrepackettaskoffloads"></a>Device.Network.LAN.GRE.GREPacketTaskOffloads

*实现 GRE 封装包任务减轻的以太网设备必须符合规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于以太网设备实现封装 GRE 数据包任务减轻。 实现封装 GRE 数据包任务减轻的以太网设备必须符合规范和内部/外部 IPv4/IPv6 标头的所有组合的都支持封装的卸载以下任务︰

 - 发送校验和 （IPv4、 TCP、 UDP）
 - 接收校验和 （IPv4、 TCP、 UDP）
 - LSOv2
 - VMQ

<a name="device.network.lan.ipsec"></a>
## <a name="devicenetworklanipsec"></a>Device.Network.LAN.IPsec

*局域网的要求*

### <a name="devicenetworklanipsecipsec"></a>Device.Network.LAN.IPsec.IPsec

*实施 IPsec 任务卸载功能的以太网设备必须支持所需的模式和协议。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

支持 IPsec 任务卸载功能的以太网设备必须支持以下︰ 版本︰ IPsec 任务卸载 v2 NDIS 版本︰ 6.1、 6.20 6.30。

以太网设备支持 IPsec 卸载 Windows 8 的任务必须使用 NDIS 6.30。 模式︰

- IPv4 和 IPv6 传输  

- IPv4 和 IPv6 TunnelProtocol: ESPCrypto 算法︰

- 必须实现︰ AES-GCM （128 或更高版本）

- 可以实现其他算法，如 http://technet.microsoft.com/en-us/library/dd125380(v=WS.10).aspxCoexistence: Ethernet devices that support IPsec task offload and any the following offload technologies: 中所述

- 大量发送卸载-接收端扩展

- 校验和清除。必须实现它们共存的方式，以便使用 IPsec 卸载任务不排除利用其他卸载技术实现为每个 IPsec 模式。

<a name="device.network.lan.krdma"></a>
## <a name="devicenetworklankrdma"></a>Device.Network.LAN.KRDMA

*局域网的要求*

### <a name="devicenetworklankrdmakrdma"></a>Device.Network.LAN.KRDMA.KRDMA

*实现 NetworkDirect 内核模式接口 (NDKPI) （即内核模式 RDMA，kRDMA） 的设备必须符合网络直接内核模式接口 (NDKPI) 规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于以太网设备实现的网络直接内核模式接口 (NDKPI) 规范。 实现网络直接内核模式接口 (NDKPI) （即内核模式 RDMA） 的设备必须符合网络直接内核模式接口 (NDKPI) 规范。 2.0 版已自 7 月 2014年当前的规范。  提交符合 NDKPI 规范的版本 1.2 将接受直到 2016 年 12 月 31，但不能使用 Windows 服务器 2016年的超收敛方案。  有效的 2017 年 1 月 1，仅 NDKPI 版本 2.0 兼容设备将被接受。  针对 Microsoft Azure 堆栈 (MAS) AQ 徽标不 AQ 报送必须支持 NDKPI 2.0 版。

NDKPI 2.0 版介绍了三种操作模式︰

- 模式 1，支持本机模式操作模式
- 模式 2，一种模式，支持 NIC_Switch vPorts NDKPI 
- 模式 3，在取景器驱动程序支持公开的 NDKPI 模式

10 的 Windows 客户端驱动程序只需支持模式 1。

Windows 服务器 2016年和 MAS 驱动程序必须支持模式 1 和 2。

*设计备注*

请参见网络直接内核模式接口 (NDKPI) 规范 （版本 2.0）。

<a name="device.network.lan.largesendoffload"></a>
## <a name="devicenetworklanlargesendoffload"></a>Device.Network.LAN.LargeSendOffload

*网络要求*

### <a name="devicenetworklanlargesendoffloadlargesendoffload"></a>Device.Network.LAN.LargeSendOffload.LargeSendOffload

*以太网设备必须实现大量发送卸载。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备必须支持以下任务卸载︰

大量发送卸载版本 2 为 IPv4 和 IPv6。

*设计备注*

请参阅 Windows 驱动程序工具包，"NDIS。"

### <a name="devicenetworklanmtusize"></a>Device.Network.LAN.MTUSize

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

以太网设备必须支持巨型帧。 在用户界面中的 MTU 值必须包含 14 字节的以太网标头大小。 "* JumboPacket"标准化的 Windows 注册表中关键字当前用于设置的 MTU 大小和应予保留为使用受支持的值被 1514年、 4088 和 9014 可枚举值。

### <a name="devicenetworklanmtusizeencapoverhead"></a>Device.Network.LAN.MTUSize.EncapOverhead

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

New 关键字将添加称为"*EncapOverhead"的类型是数字，默认值为 0，最大值为 480 和步长增量的大小为 32。此值将考虑由于如 VXLAN 和 NVGRE 的虚拟网络覆盖封装的以太网帧中的开销。MTU 大小因此将由除在这种情况可能是这两个关键字值的总和， *JumboPacket + * EncapOverhead 将超过某些硬件上界的 nic。

实施减轻 GRE 或 VxLAN 的设备还必须结合这一要求。

<a name="device.network.lan.pm"></a>
## <a name="devicenetworklanpm"></a>Device.Network.LAN.PM

*局域网的要求*

### <a name="devicenetworklanpmpowmgmtndis"></a>Device.Network.LAN.PM.PowMgmtNDIS

*实现网络存在减轻的以太网设备必须符合在 NDIS 程序的电源管理规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备必须实现 ARP 卸载 MSDN 上的电源管理规范中定义。 具体来说，必须卸载响应到 ARP 请求 (操作 = 1） 通过使用 ARP 应答响应 (操作 = 2） 作为 RFC 826 中定义。

以太网设备必须实现 IPv6 NS 卸载 MSDN 上的电源管理规范中定义。 特别是，卸载必须响应相邻节点请求 (操作 = 135) 通过以 NS 广告来 (操作 = 136) 在 RFC 4861 中定义。 设备必须支持至少 2 NS 减轻，每个都有多达 2 目标 IPv6 地址。

设计备注

请参阅 MSDN 上的电源管理规范。

请参阅 RFC 826 处<http://go.microsoft.com/fwlink/?LinkId=108718>。

例外情况的这一要求的例外情况包括︰ PC 卡，cardbus 启动设备和总线的电源运行时的外部 USB 网络设备。 有超过 1 千兆比特的传输速度的设备。 使用光纤光纤介质的设备。

 

### <a name="devicenetworklanpmwakeonlanpatterns"></a>Device.Network.LAN.PM.WakeOnLANPatterns

*以太网设备必须符合规范的局域网模式实现唤醒。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

实现必须遵守网络设备类电源管理参考技术指标。 因为 Windows 会使用最多 8 个模式支持至少八 （8） 位图图案需要以太网设备和驱动程序。 神奇的数据包唤醒支持是必需的不包括在 8 位图图案要求。

*设计备注*

在 MSDN 上的电源管理规范的实现详细信息。

异常的这一要求的例外情况包括︰ PC 卡，cardbus 启动设备和总线的电源运行时的外部 USB 网络设备。 有超过 1 千兆比特的传输速度的设备。 使用光纤光纤介质的设备。 注︰ 如果设备实现在 LAN 上的唤醒它必须实现它正确地根据这一要求而不考虑该设备是否在例外列表。

 

### <a name="devicenetworklanpmwakepacket"></a>Device.Network.LAN.PM.WakePacket

*以太网设备实现唤醒数据包检测必须遵守网络设备类电源管理参考技术指标。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

以太网设备实现唤醒数据包检测必须遵守网络设备类电源管理参考技术指标。 实现必须符合 Windows WDK 中讨论的网络设备类电源管理引用规范。 网卡需要捕获至少第 128 个字节的数据包，从而导致网络唤醒并生成操作系统状态指示。

*设计备注*

请参阅 WDK，网络设备类电源管理参考技术指标。

<a name="device.network.lan.rsc"></a>
## <a name="devicenetworklanrsc"></a>Device.Network.LAN.RSC

*局域网的要求*

### <a name="devicenetworklanrscrsc"></a>Device.Network.LAN.RSC.RSC

*实现接收段合并 (RSC) 的以太网设备必须符合 RSC 规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

实现接收段合并 (RSC) 的以太网设备必须符合 RSC 规范，并要求 IPv4 和 IPv6 支持。

*设计备注*

NDIS 版本︰ 6.30

<a name="device.network.lan.rss"></a>
## <a name="devicenetworklanrss"></a>Device.Network.LAN.RSS

*局域网的要求*

### <a name="devicenetworklanrssrss"></a>Device.Network.LAN.RSS.RSS

*实现 RSS 的以太网设备*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

服务器 Sku 除 SR IOV 取景器驱动程序之外的所有设备上需要 RSS 支持。

RSS 支持是可选的在客户端 Sku。

实现 RSS 的以太网设备必须支持︰

 - 哈希类型︰ IPv4、 TCP IPv4、 IPv6 和 TCP IPv6
 - （适用于微型的 NDIS 6.20 版本及以上） 的多个处理器组

（这取决于链接速度） 的队列的数目︰

 - 少于 10 千兆位︰ 2
 - 10 千兆位或更高版本︰ 8
 - SR IOV 取景器驱动程序 （独立于链接速度）︰ 2
 - 间接寻址 （这取决于链接速度） 的表大小︰
 - 少于 10 千兆位︰ 64
 - 10 千兆位或更高版本︰ 128
 - SR IOV 取景器驱动程序 （独立于链接速度）︰ 16
 - SR IOV PF 驱动程序 （独立于链接速度）︰ 64
 - 实现所有标准化的 RSS 关键词
 - \*RSS
 - \*NumRSSQueues

消息发出信号中断扩展 (MSI-X) 在 PCI 3.0 版规范中定义。 对于链接速度小于 10 千兆位的设备，该设备必须有 1 MSI-X 向量 2 RSS 硬件队列的支持。 设备的 10 千兆位或更高版本，该设备必须有每个 RSS 硬件队列 MSI-X 向量。 例如，如果设备具有 10 千兆比特的链接速度并且宣称支持 8 个 RSS 硬件队列然后它必须具有至少 8 MSI-X 向量硬件中。

*设计备注*

请参阅 RSS 关键词标准化规范<http://msdn.microsoft.com/library/windows/hardware/ff570864.aspx>。

此外，该设备必须分配系统中有 Cpu 上的 MSI-X 表项。 对于<http://msdn.microsoft.com/library/windows/hardware/ff566491.aspx>的更多详细信息，请参阅 MSI-X 一 NDIS 文档节。

### <a name="devicenetworklanrsssethashfunctiontypeandvalue"></a>Device.Network.LAN.RSS.SetHashFunctionTypeAndValue

*实现 RSS 的以太网设备必须在指定的每个数据包上设置哈希函数、 哈希类型和哈希值。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 RSS 的以太网设备。 如果以太网设备未实现 RSS，此要求不适用。 如果网络设备支持 RSS，所有数据包的 RSS 实施可以说无法计算哈希，RSS 实现必须返回完整的 32 位哈希值的哈希函数和哈希类型，为每个接收的数据包，则表明。 它没有错误，没有收到任何数据包能够生成的哈希函数，它必须清除哈希类型。 宏 NET\_缓冲区\_列表\_设置\_希\_类型，净\_缓冲区\_列表\_设置\_希\_函数及网络\_缓冲区\_列表\_设置\_希\_值必须用于设置相关联的值。

*设计备注*

MSDN 页面的详细信息，请参阅︰ <http://msdn.microsoft.com/en-us/library/windows/hardware/ff570726.aspx>。 请参阅 Windows 驱动程序工具包，"指示 RSS 接收数据"。

### <a name="devicenetworklanrsssupportindirectiontablessizes"></a>Device.Network.LAN.RSS.SupportIndirectionTablesSizes

*实现 RSS 的以太网设备必须支持特定的间接寻址表大小。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 RSS 的以太网设备。 如果以太网设备未实现 RSS，此要求不适用。 网络设备是否支持 RSS，RSS 实现必须支持间接寻址表大小为 2，直到达到支持的最大的间接寻址表大小的每个电源。  例如，如果 128 是最大的间接寻址表的大小，微型端口必须接受规模 2、 4、 8、 16、 32、 64 或 128 的间接寻址表。 查找到间接寻址表中查找目标 CPU 必须通过使用所指定的最后一个值只有最低有效位设置在 OID\_GEN\_接收\_比例\_NumberOfLsbs 变量的参数。 RSS 的实现必须支持主机协议栈将 NumberOfLsbs 设置为 1 到 7，包括之间的任何值。

*设计备注*

请参阅 Windows 驱动程序工具包，"OID\_GEN\_接收\_比例\_参数。"

### <a name="devicenetworklanrsssupporttoeplitzhashfunction"></a>Device.Network.LAN.RSS.SupportToeplitzHashFunction

*实现 RSS 的以太网设备必须支持 Toeplitz 哈希函数。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 RSS 的以太网设备。 如果以太网设备未实现 RSS，此要求不适用。 如果网络设备支持 RSS，RSS 实现必须至少支持 Toeplitz 哈希函数的公布与能够生成哈希的数据包类型 (示 OID\_GEN\_接收\_比例\_功能)。 这包括支持 40 个字节的 HashSecretKey 长度。

*设计备注*

请参阅 Windows 驱动程序工具包，"哈希函数的 RSS。" 此外，对<http://msdn.microsoft.com/en-us/library/windows/hardware/ff570725.aspx>的详细信息，请参考 MSDN

### <a name="devicenetworklanrsssupportupdatestorssinfo"></a>Device.Network.LAN.RSS.SupportUpdatesToRSSInfo

*实现 RSS 的以太网设备必须支持对 RSS 信息随时更新。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 RSS 的以太网设备。 如果以太网设备未实现 RSS，此要求不适用。 在任何网络设备是否支持 RSS 的时候，它必须支持设置 OID\_GEN\_接收\_比例\_参数，包括更新的间接寻址表、 NumberOfLsbs、 SecretKey 和 HashInformation （哈希函数和哈希类型）。 RSS 实现可以投递数据包顺序从先前的状态转换为新状态的过程，并且可以执行硬件重置如果更改 HashInformation、 SecretKey 或 NumberOfLsbs。 它必须执行硬件重置只间接寻址表内容被更改。

*设计备注*

请参阅 Windows 驱动程序工具包，"OID\_GEN\_接收\_比例\_参数。"

<a name="device.network.lan.sriov"></a>
## <a name="devicenetworklansriov"></a>Device.Network.LAN.SRIOV

*网络要求*

### <a name="devicenetworklansriovsriov"></a>Device.Network.LAN.SRIOV.SRIOV

*实施单个根 I/O 虚拟化 (SR IOV) 的以太网设备必须支持所需的功能。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

驱动程序必须使用取景器驱动程序 PCIe 配置空间请求到 PF 的 Microsoft 软件后的通道。

在 INF 文件中必须是的默认初始交换机配置信息。

PF INF 必须设置为"ndis5"UpperRange 和 LowerRange 为"以太网"。

在 INF 中不能包含\*SriovPreferred 关键字。

合并后的筛选器必须设置在 NDIS\_REECIVED\_筛选器\_功能。

SR IOV 网卡必须包括虚拟以太网网桥 (VEB)。

如果 VF 微型支持 RSS，必须能够支持独立的 RSS 希对于每个函数，物理或虚拟 NIC。

PF 和取景器的微型端口驱动程序必须能够通过局域网徽标测试。

不能删除默认 vPort;在取景器上的非默认的 vPorts 可以被删除。

如果禁用 SRIOV，NIC 和微型端口必须作为标准的以太网卡。

SRIOV NIC 还必须公布并实施 VMQ。 队列对未分配给 IOV 为可供 VMQ。

在报表上的连接介质，VF 微型端口必须准备接受通信。

VF 微型端口必须指定"ndisvf"UpperRange 和 LowerRange 的"iovvf"。

*设计备注*

请参阅单根 I/O 虚拟化技术指标。

<a name="device.network.lan.sriov.vf"></a>
## <a name="devicenetworklansriovvf"></a>Device.Network.LAN.SRIOV.VF

*网络要求*

### <a name="devicenetworklansriovvfvf"></a>Device.Network.LAN.SRIOV.VF.VF

*实施单个根 I/O 虚拟化 (SR IOV) 的以太网设备必须支持所需的功能。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

对于 SRIOV 取景器适配器要求

驱动程序必须使用取景器驱动程序 PCIe 配置空间请求到 PF 的 Microsoft 软件后的通道。

如果 VF 微型支持 RSS，网卡必须能够在 PFs 可以支持相同数量的 RSS。

所有的 NDIS 设备必须符合于 NDIS 6.x 版 Windows 驱动程序工具包中指定应该取景器设备。

VF 微型端口必须指定"ndisvf"UpperRange 和 LowerRange 的"iovvf"。

如果 VF 微型端口实现接收段合并 (RSC)，它必须符合 RSC 规范并要求 IPv4 和 IPv6 支持。

在报表上的连接介质，VF 微型端口必须准备接受通信。

*设计备注*

请参阅单根 I/O 虚拟化技术指标。

<a name="device.network.lan.tcpchimney"></a>
## <a name="devicenetworklantcpchimney"></a>Device.Network.LAN.TCPChimney

*TCP 烟囱要求*

### <a name="devicenetworklantcpchimneycomplywithndis"></a>Device.Network.LAN.TCPChimney.ComplyWithNDIS

*实现 TCP 烟囱的以太网设备必须符合最新的 NDIS 微型端口驱动程序模型。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 TCP 烟囱的以太网设备。 如果以太网设备未实现 TCP 烟囱，此要求不适用。 该设备的 TCP 烟囱部分必须遵守在连接的 TCP 烟囱规范。

*设计备注*

请参阅 Windows 驱动程序工具包，"网络设备和协议"。

### <a name="devicenetworklantcpchimneycomplywithtcpipprotocol"></a>Device.Network.LAN.TCPChimney.ComplyWithTCPIPProtocol

*实现 TCP 烟囱的以太网设备必须符合 IETF 标准 Rfc 的 TCP/IP 协议族，并表现为 Microsoft Windows （主机） TCP/IP 协议实现。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 TCP 烟囱的以太网设备。 如果以太网设备未实现 TCP 烟囱，此要求不适用。 这些关键字"必须"，"禁"、"必需的"、"下"、"不应"、"必须"、"不应该"、"推荐"、"可能"，和"可选"的这一要求将被解释 RFC 2119 中所述。 TCP 烟囱网卡必须实现 TCP/IP 协议族这样︰ 1。 TCP/IP 协议实现符合 IETF 标准 Rfc 和 2。 TCP/IP 协议实现行为的 Microsoft Windows TCP/IP 协议实现的方式相同。 这一要求指定的 Rfc 必须由 TCP 烟囱 NIC，并阐明在 RFC 不明确的情况下的预期的行为。 表 1 列出了 TCP 烟囱网卡必须实现 Rfc。

<html>
    <table>
        <thead>
            <tr class="header">
                <th>描述性名称</th>
                <th>规范</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>传输控制协议 Rfc</td>
                <td>
                    <p>
RFC 793-传输控制协议<br />
RFC 813-窗口和 TCP 确认策略<br />
RFC 1122\* -要求的互联网主机的通讯层的整个第 4.2 节                    </p>
                    <p>RFC 1323-TCP 高性能扩展</p>
                    <p>RFC 2923\* -TCP 路径 MTU 发现问题</p>
                    <p>RFC 2988\* -计算 TCP 的 RTO</p>
                    <p>RFC 3465\*的相应字节计数</p>
                </td>
            </tr>
            <tr class="even">
                <td>TCP 拥塞控制</td>
                <td>
                    <p>RFC 2581\* -TCP 拥塞控制</p>
                    <p>RFC 2582\* -对 TCP 的快速恢复为.alg 的新 Reno 修改</p>
                    <p>RFC 3042-有限的传输</p>
                </td>
            </tr>
            <tr class="odd">
                <td>TCP 丢失恢复</td>
                <td>
                    <p>RFC 2018\* -TCP 选择性确认选项</p>
                    <p>RFC 3517\* -保守选择性确认 (SACK)-基于 TCP 的丢失恢复算法</p>
                </td>
            </tr>
            <tr class="even">
                <td>TCP 安全</td>
                <td>RFC tcpm-tcpsecure-09\* -为盲人窗口中攻击提高 TCP 的稳定性</td>
            </tr>
            <tr class="odd">
                <td>互联网协议 v4 Rfc\*\*</td>
                <td>RFC 791，RFC 894，RFC 1042，RFC 1191，RFC 1122-整个部分 3.2</td>
            </tr>
            <tr class="even">
                <td>互联网协议 v6 Rfc\*\*</td>
                <td>RFC 1752，RFC 1981，RFC 2374、 RFC 2460，RFC 2461、 RFC 2675，RFC 2711 RFC 3122，RFC 3513</td>
            </tr>
            <tr class="odd">
                <td>
                    <p>\*-有的 RFC，这必须遵守的相关的说明。 它们如下所示。\*\*</p>
                    <p>TCP 烟囱 Nic 必须的实现的 IP 设置整个相关的 Rfc。 相反，必须遵循 Internet 协议 RFC 实现 TCP 烟囱驱动程序工具包的准则。</p>
                </td>
                <td></td>
            </tr>
        </tbody>
    </table>
</html>

表 1-Rfc TCP 烟囱网卡必须实现 RFC 所说明的列表。 以下说明必须跟在 TCP 烟囱 NIC 的 TCP/IP 实现 RFC 11221。 4.2.3.4 一节指定应作为一种避免愚蠢的窗口综合症的方法实现了 Nagle 算法。 TCP 烟囱网卡必须实现 Nagle 算法和实现必须遵循此伪代码︰。 在发送一段时，必须以实现 SWS 避免的第一阶段︰

```
Send(){..If (BytesToSend &gt; MSS ||BytesToSend &gt; MaxSndWnd /2 ||BytesToSend &gt;= BytesInCurReq ||ForceOutput){BeginSend();}else{StartSwsTimer();}                ...               

...
```

<html>
    <dl>
        <dt><i>BytesToSend</i></dt>
        <dd>
            <p>可以发送当前所允许的可用字节数发送窗口。</p>
        <dd>
        <dt><i>MSS</i></dt>
        <dd>
            <p>最大段</p>
        <dd>
        <dt><i>SizeMaxSndWnd</i></dt>
        <dd>
            <p>最大接收窗口，不断公布的 TCP 对等方。</p>
        <dd>
        <dt><i>BytesInCurReq</i></dt>
        <dd>
            <p>留在当前的字节发送请求。</p>
        <dd>
        <dt><i>ForceOutput</i></dt>
        <dd>
            <p>一个变量，确定是否该段必须发送，由于 SWS 计时器过期为例。 红色线条指定必须实现 SWS 避免偏离。</p>
        <dd>
    </dl>
</html>
     
**注意**&nbsp;&nbsp;&nbsp;发送时的而不是在发送请求由主机 TCP/IP 堆栈的下放时，此伪代码定义的行为。 Microsoft TCPIP 堆栈背离上述方法中的 SWS 算法的原因是︰

1. CWND 可以增长以字节为单位。 更确切地说，未约束 CWND 放大或缩小以 MSS 或推边界的倍数。 由于 Windows 中的 TCP 实现实现相应字节计数 (RFC 3465)，这一点是更进一步加强。

2. 发布数据的 TCP 应用程序要发送以便它不能保证对准的 MSS 大小取决于推边界。

3. 由于\#1， \#2 很可能 TCP 状态机来到达一个临界点，此时一个 MSS 已被放在网络上并且没有子 MSS 段的发送，如果将完成到推边界的数据块。

    一。 在这种情况下，为 TCP 发送此一子 MSS 要完成应用程序的缓冲区中直到推边界传输段的有利。 为什么很有利，若要这样做的原因是因为数据将传递给接收应用程序比到信如果遵循 SWS 算法更快。 同时，差不重新引入任何 SWS 首先解决的问题。

4. 4.2.2.17 一节所述 TCP 烟囱网卡必须使用连接 RTT 为触发器发送零窗口探测器，然后呈指数方式增加连续探测器之间的时间间隔。 此外，该探测器必须包含 1 个新字节的数据。

5. <!--edit: List item 5 is as it appears in the Word version, but this needs help. -->TCP 烟囱网卡必须支持至少两个重组孔填充。 RFC 20181。 TCP 烟囱 NIC 可能实现 RFC 2018。 如果 TCP 烟囱 NIC 实现 RFC 2018，然后它也必须实现 RFC 3517.2。 TCP 烟囱 NIC，不正确地实现 RFC 2018 必须处理纯 ACK 数据包，包含 SACK 块的 RFC 793.25811 RFC 第 3 节中所述。 TCP 烟囱网卡必须能够转换从使用慢启动算法在第 3.1 节规定使用拥塞避免算法。 此外，它必须实现拥塞窗口 (cwnd) = 缓慢而不是拥塞窗口构建的启动阈值 (ssthresh)&gt;慢启动 Threshold.RFC 25821。 TCP 烟囱网卡必须使用下面的等式所述 RFC 2582 点 1:SsThresh 在部分 3-= 最大值 (2\*mss，min(cwnd,window\_advertised\_by\_peer)/2) RFC 29231。 TCP 烟囱 NIC 无需实现 RFC 2923 中列出的建议。 相反，TCP 烟囱网卡必须上载允许主机堆栈执行黑洞检测状态机的 TCP 连接。 Windows 驱动程序工具包的详细信息，请参阅。RFC 29881。 有关背景信息，请参阅 RFC 1122 部分 4.2.3.1 和 RFC 2988。 TCP 烟囱网卡必须实现 RTO 计算使用下面的算法，这次要下限定的例外情况是 RFC 2988 相同︰ 函数 CalculateRto 第一、 byRef srtt、 byRef rttvar (m） rttSample = 最小值 (m，30 秒)，如果是第一 thenrttvar = m/2srtt = melse 请注意，rttvar 的计算第一次，使用旧的 srttrttvar 值 = (3/4) \* rttvar + (1/4) \* abs (srtt-rttSample) srtt = (7/8)\*srtt + (1/8) \* rttSampleend ifCalculateRto srtt + 4 = \* rttvarCalculateRto = 最小 (CalculateRto六十年代) CalculateRto = 最大值 (CalculateRto，除了) 红色捕获从 RFC 的偏差中的两行。 具体而言，应计算 RTT 值时，TCP 烟囱 NIC，有一个上限。RFC 34651。 第 2.1 节介绍在拥塞避免 CWND 变化。 TCP 烟囱网卡必须使用下面的公式来计算期间拥塞避免的 CWND: / / L is 4CWnd + = 最大值 ((MaxMss\*最小 (MaxMss \* L、 BytesAcked)) /CWnd，1) 请注意，是否 BytesAcked 始终为 1 上面的公式将成为最大 ((MaxMss, MaxMss)/Cwnd，1) 等效于在 RFC 2581 2 公式。 2。 在 RFC 3465 2.3 节讨论的限制中，机械、 CWND 增加选择过程缓慢开始和拥塞避免，控制算法的进取。 TCP 烟囱网卡必须使用值 4 L 以使其展现出的 Windows TCP/IP 协议实现相同的行为。RFC tcpm-tcpsecure-091。     TCP 烟囱 Nic 必须遵循 3、 4 和 5 的 RFC (http://tools.ietf.org/html/draft-ietf-tcpm-tcpsecure-12) 的 TCP 安全 internet 草稿的各节中介绍的安全指南。 2。     TCP 烟囱 NICSs 应按照所述 WDK Windows 具体的实现细节。

设计备注︰ 请参阅 Rfc 在<http://go.microsoft.com/fwlink/?LinkId=36702>的完整文本。

### <a name="devicenetworklantcpchimneyhandlesoutoforderdata"></a>Device.Network.LAN.TCPChimney.HandlesOutOfOrderData

*实现 TCP 烟囱的以太网设备必须正确处理的无序的数据方案。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

实现 TCP 烟囱的以太网设备必须正确处理无序的数据方案如下所述︰ 

1. 如果任何内容后翼片 inorder 重组队列中放置，必须通过放弃其所有内容刷新重组队列。

2. 如果 TCP 烟囱 NIC 存储 OOO FIN 重组队列中，然后它必须存储 OOO 数据或以外其他 OOO FIN OOO FIN 重组队列中。 如果它收到 OOO 数据或将导致此类冲突的 OOO FIN 段，然后将 TCP 烟囱网卡必须删除该段，并通过放弃其所有内容刷新重组队列。

### <a name="devicenetworklantcpchimneyimplementsufficientlygranulartimers"></a>Device.Network.LAN.TCPChimney.ImplementSufficientlyGranularTimers

*实现 TCP 烟囱的以太网设备必须实现足够精确的计时器。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 TCP 烟囱的以太网设备。 如果以太网设备未实现 TCP 烟囱，此要求不适用。 TCP 烟囱网卡必须计时器 （网卡的硬件上实现） 不够精确粒度访问和扭曲，以致它可以正确地提高 TCP/IP 状态机。 计时器间隔必须为 10 毫秒或更好的 （低于 10 毫秒），并且必须相当于什么通用 CPU 计时器提供倾斜的计时器。

### <a name="devicenetworklantcpchimneyneighborstateobjtimestampscomplywithwdk"></a>Device.Network.LAN.TCPChimney.NeighborStateObjTimestampsComplyWithWDK

*根据在 Windows 驱动程序工具包的详细信息实现了邻居状态对象的时间戳。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

TCP 烟囱维护使用相邻节点状态的每个对象的时间戳，并对每个传入和传出数据包执行对时间戳检查，必须确保实现 TCP 烟囱的网络设备。

*设计备注*

请参阅 Windows 驱动程序工具包，"OID\_TCP\_减轻负担。

### <a name="devicenetworklantcpchimneysupport1024connections"></a>Device.Network.LAN.TCPChimney.Support1024Connections

*实现 TCP 烟囱的以太网设备必须支持至少 1024年连接并不公布更多减轻容量比硬件的支持。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 TCP 烟囱的以太网设备。 如果以太网设备未实现 TCP 烟囱，此要求不适用。 实现 TCP 烟囱的以太网设备必须支持至少 1024年连接并不公布更多减轻容量比硬件的支持。

### <a name="devicenetworklantcpchimneysupport64bitaddresses"></a>Device.Network.LAN.TCPChimney.Support64bitAddresses

*实现 TCP 烟囱的以太网设备都必须支持 64 位地址。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于实现 TCP 烟囱的以太网设备。 如果以太网设备未实现 TCP 烟囱，此要求不适用。 如果该设备使用 PCI，它必须支持 64 位地址。64 位数据支持不是必需的。


<a name="device.network.lan.vmmq"></a>
## <a name="devicenetworklanvmmq"></a>Device.Network.LAN.VMMQ

*定义实现虚拟机的多个队列的以太网设备的要求。*

### <a name="devicenetworklanvmmqvirtualmachinemultiplequeues"></a>Device.Network.LAN.VMMQ.VirtualMachineMultipleQueues

*实现虚拟机的多个队列的以太网设备的要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

实现必须遵守虚拟机的多个队列引用规范。


<a name="device.network.lan.vmq"></a>
## <a name="devicenetworklanvmq"></a>Device.Network.LAN.VMQ

*局域网的要求*

### <a name="devicenetworklanvmqvirtualmachinequeues"></a>Device.Network.LAN.VMQ.VirtualMachineQueues

*实现虚拟机队列的以太网设备必须遵守可编程计算机队列引用规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

实现必须遵守可编程计算机队列引用规范。

必须支持至少四个队列使用筛选器。 建议至少 16 队列使用筛选器的支持。 所需队列的数目将 16 按 2009 年 12 月 1 日的 10 千兆位部件。 包含默认队列，队列所需的数目了。

MSI-X 支持 (NDIS\_接收\_筛选器\_MSI\_X\_支持) 是必需的︰ 

| 队列       | Msi-x 队列比 |
|--------------|-----------------------|
| 1 到 16 个      | 1:1                   |
| 17 64        | 1:2 (最小值为 16)          |
| 65 无限 | 1:16 (最小值 32)         |

筛选︰

为 VLAN 的硬件支持 (NDIS\_接收\_筛选器\_MAC\_头\_VLAN\_ID\_支持) 是可选的。 如果实现，每个 VM 队列 (NumVlansPerVMQueue) 的 Vlan 必须是&gt;= 1

对 MAC 筛选在硬件支持 (NDIS\_接收\_筛选器\_MAC\_头\_目标\_地址\_支持) 是必需的。

支持 NDIS\_接收\_筛选器\_测试\_头\_等于\_支持是必需的。

MAC 头筛选器 (MaxMacHeaderFilters) 的最大数量必须是&gt;= 队列的数目

总的 MAC 地址 (NumTotalMacAddresses) 必须是&gt;= 队列的数目

每个 VM 队列 (NumMacAddressesPerVMQueue) 的 MAC 地址必须是&gt;= 1

每个队列接收指示必须支持 (NDIS\_接收\_队列\_参数\_PER\_队列\_接收\_表示)

只需要 Windows Server 2012，动态 VMQ 支持。

设计备注

实现详细信息包含在 ProgrammableMachine 队列指定 NDIS 程序中，连接网站<http://msdn.microsoft.com/en-us/library/windows/hardware/ff571034.aspx>

<a name="device.network.lan.vxlan"></a>
## <a name="devicenetworklanvxlan"></a>Device.Network.LAN.VXLAN

### <a name="devicenetworklanvxlanvxlanpackettaskoffloads"></a>Device.Network.LAN.VXLAN.VXLANPacketTaskOffloads

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求只适用于以太网设备实现 VXLAN 封装包任务减轻。 实现 VXLAN 封装包任务减轻的以太网设备必须符合规范和内部/外部 IPv4/IPv6 标头的所有组合的都支持封装的卸载以下任务︰

 - 发送校验和 （IPv4、 TCP、 UDP）
 - 接收校验和 （IPv4、 TCP、 UDP）
 - LSOv2
 - VMQ

<a name="device.network.lan"></a>
## <a name="devicenetworklan"></a>Device.Network.LAN

### <a name="devicenetworklancloudstress"></a>Device.Network.LAN.CloudStress

*实现 GRE 封装包任务减轻的以太网设备必须符合规范。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

此要求适用于所有认证服务器的以太网设备。 此测试可验证以太网设备可以满足数据中心云的压力要求。 满足这一要求的以太网设备还必须符合规范和支持下列功能︰

 - 所有的网络适配器必须支持下面的 Devie.Networking.LAN 功能，并通过私有云压力测试

 - 基 (要求 100MbOrGreater 至 SupportIEEE8023)

 - ChecksumOffload

 - LargeSendOffload

 - RSS

 - 对于小型云准备好部署的网络适配器必须支持的所有上述功能和

 - 有的 10g 或更高的速度

 - MTUSize

 - NVGRE

 - VXLAN

 - VMQ

对于大的云准备好部署的网络适配器必须支持的所有上述功能和

 - PacketDirect

 - DCB

 - KRDMA （iWARP 或可穿绕的 RoCE）

 - SRIOV

其他信息;

 - 1GigE Nic，如果它们不支持所有所需的功能将不被授予徽标的服务器

 - 1GigE Nic，如果他们支持所需的全部功能将服务器授予徽标

 - 1GigE Nic，即使它们所支持的一些高级功能对于云就绪的 Nic，列出不会授予云就绪其他资格

 - 0GigE 和上面的 Nic，如果它们不支持所有必需的功能，而不考虑它们所支持的任何其他功能将不会授予徽标

 - 10GigE 并支持所需的全部功能，但不要不支持所需的云就绪列为 10GigE Nic 的小型云功能的所有 Nic，上面会被授予徽标

 - 10GigE 和上面 Nic，小云 Nic 的支持所需的所有功能，以及所有的功能，将被授予云就绪额外的限定，对于较小的云部署提供支持

 - 10GigE 和上面 Nic，大云 Nic 的支持所需的所有功能，以及所有的功能，将被授予云就绪额外的限定，对于较大的云部署提供支持
