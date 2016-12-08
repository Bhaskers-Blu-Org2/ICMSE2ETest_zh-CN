---
title: Device.Network.Switch.AzureStack
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: cf99e469935f2283c32c795f473765f51ecde98e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
## <a name="devicenetworkswitchazurestack"></a>Device.Network.Switch.AzureStack

*基于私有云解决方案在 Microsoft Azure 堆栈中使用的网络交换机的要求*

<a name="device.network.switch.azurestack.basicfunction"></a>
### <a name="devicenetworkswitchazurestackbasicfunction"></a>Device.Network.Switch.AzureStack.BasicFunction

*网络交换机的 Microsoft Azure 堆栈解决方案中使用的基本要求*

<table><tr><td>适用于</td><td>Windows 服务器 2016 x64</td></tr></table>

**说明**

私有云的 Microsoft Azure 堆栈解决方案必须满足的物理交换机的基础架构的要求。 本部分列举的要求。 

Microsoft Azure 堆栈网络环境假定可恢复性和可扩展性的书脊/叶 CLOS 网络配置︰ 

- 叶交换机提供了 Microsoft Azure 堆栈解决方案中的计算和存储服务器的连接。 
- 书脊交换机提供其他叶交换机和连接到客户网络边界设备之间的连接。

这些脊柱和叶开关必须提供第 3 层 (L3) 形式的路由转发和边界网关协议 (BGP) 支持 IP 级连接。

注︰ 物理和逻辑配置的详细信息超出了此要求枚举的范围，并将包含在"Microsoft Azure 堆栈体系结构文档"。

除了 Microsoft Azure 堆栈下面列举的要求都需要验证以确保配置并正确路由 RDMA 的 NIC 和物理交换机。

**要求**

下表中捕获 Azure 堆栈 Microsoft 私有云解决方案的物理交换机基础结构需求。

<table>
    <tr><th>功能</th><th>要求</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td rowspan="2">Device.Network.Switch.Manageability</td><td>Device.Network.Switch.Manageability.NetworkSwitchProfile</td><td>如果实现</td></tr>
    <tr><td>Device.Network.Switch.Manageability.NetworkSwitchProfileView</td><td>如果实现</td></tr>
</table>

下表描述了 Microsoft Azure 堆栈切换要求周围的定向思维。

<table>
    <tr><th colspan="2">开关特性</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td>OSI 层支持</td><td>L2 和 L3 交换机的所有端口</td><td>是否必需</td></tr>
    <tr><td>端口速度</td><td><p>访问交换机/计算节点︰ 最小的 10 千兆以太网</p><p>每个访问聚合交换机开关︰ 最小的 10 Gb 以太网</p></td><td>是否必需</td></tr>
    <tr><td>吞吐量</td><td>L2 和 L3 的所有端口上的通讯的线速率</td><td>是否必需</td></tr>
    <tr><td>端口的功能</td><td>L2 和 L3 交换机的所有端口</td><td>是否必需</td></tr>
    <tr><td>寻址协议</td>
        <td><p>必须支持 IPv4 和 IPv6 通信。</p> 
            <p>IPv6 支持可实现以下的 IETF 标准中的必须语句是必需的︰</p>
            <ul>
                <li>RFC 2460:"Internet 协议版本 6 (IPv6)"</li>
                <li>RFC 2461:"邻居发现 IP 版本 6 (IPv6)"</li>
                <li>RFC 2462:"IPv6 无状态地址自动配置"</li>
                <li>RFC 2463:"为 Internet 协议版本 6 (IPv6) 的 Internet 控制消息协议 (ICMPv6) 规范。"</li></ul>
            <p>交换机必须支持至少 12000 IPv6 主机路由。</p></td>
            <td>是否必需</td></tr>
</table>

<table>
    <tr><th colspan="2">路由和交换</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td>L3 协议</td>
        <td><p>ECMP</p>
            <p>BGP (IETF RFC 4271)-基于 ECMP︰ 目前，BGP 用于提供访问交换机和聚合交换机间的容错能力。</p>
            <p>在下面的 IETF 标准，实现系统必须支持必须语句︰</p>
            <ul>
                <li>RFC 2545:"BGP-4 多协议扩展用于 IPv6 域间路由"</li>
                <li>RFC 4760:"多协议扩展的 BGP-4"</li>
                <li>RFC 4893:"四个八位位组作为 BGP 支持数字空间"</li>
                <li>RFC 4456:"BGP 路由反射︰ 完全替代网格内部 BGP (IBGP)"</li>
                <li>RFC 4724:"BGP 的正常重新启动机制"</li></ul></td>
            <td>是否必需</td></tr>
    <tr><td>L2 的协议</td><td>LLDP</td><td>是否必需</td></tr>
    <tr><td>覆盖的协议</td><td>VLAN – 隔离的各种类型的通信。</td><td>是否必需</td></tr>
    <tr><td></td><td>802.1 q 干线</td><td>是否必需</td></tr>
    <tr><td>通信量筛选</td><td>需要最少的 ACL 或 VRF 支持</td><td>是否必需</td></tr>
</table>

<table>
    <tr><th colspan="2">链接控件</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td>服务质量</td>
        <td><p>增强的通信选择 (802.1Qaz)</p>
            <p>基于优先级的流量控制 （802.1 p/Q 和 802.1Qbb）</p></td>
        <td>是否必需</td></tr>
</table>

<table>
    <tr><th colspan="2">可用性和冗余</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td>开关的可用性</td><td>多机箱配合 NIC 成组的链路聚合</td><td>是否必需</td></tr>
    <tr><td></td><td>VRRP [假定将堆叠交换机或路由器是高度可用]</td><td>是否必需</td></tr>
</table>

<table>
    <tr><th colspan="2">管理</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td>启动/启动</td><td>启动、 启动和操作继续进行，无需网络交换机管理员的干预。</td><td>是否必需</td></tr>
    <tr><td>监视</td><td>SNMP v1or SNMP v2</td><td>是否必需</td></tr>
    <tr><td>SNMP Mib</td><td>MIB II (RFC 1213)、 LLDP、 界面 MIB (RFC 2863)，如果 MIB、 IP MIB、 IP-进 MIB、 Q-网桥 MIB、 网桥 MIB、 LLDB MIB、 实体 MIB、 MIB-IEEE8023-延隔时间</td><td>是否必需</td></tr>
    <tr><td>流程监视</td><td><p>端口镜像</p><p>IPFIX</p></td><td>如果实现</td></tr>
    <tr><td>日志记录事件 /</td><td>系统日志 （适用于事件和变更检测）</td><td>如果实现</td></tr>
    <tr><td></td><td>陷阱 （设备必须支持多个陷阱目标）。</td><td>是否必需</td></tr>
</table>

<table>
    <tr><th colspan="2">访问</th><th>Microsoft Azure 堆栈认证</th></tr>
    <tr><td>用户</td><td><p>多用户支持，包括通过基于 ACL 的或基于角色的凭据加密 (RBAC) 访问控件</p><p>用户活动的审核</p></td><td>是否必需</td></tr>
    <tr><td>设备访问权限</td><td>SSHv2</td><td>是否必需</td></tr>
    <tr><td>使用证书</td><td>设置为可吊销或 CA</td><td>是否必需</td></tr>
    <tr><td>身份验证</td><td>半径</td><td>是否必需</td></tr>
    <tr><td>远程访问</td><td>交换机的虚拟接口</td><td>是否必需</td></tr>
</table>

开关也应支持 IEEE 802.1 X 身份验证标准。

**第三方 Hyper-V 交换机扩展**

第三方扩展切换 Hyper-V 为该支持捕获筛选，或 Microsoft Azure 堆栈解决方案中不支持网络通信的转发。  
