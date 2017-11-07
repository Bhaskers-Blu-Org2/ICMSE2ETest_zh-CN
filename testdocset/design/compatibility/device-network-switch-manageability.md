---
title: Device.Network.Switch.Manageability
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 611f7cb905510e8e6ae15a312f8c89d705aaef7a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Network.Switch.Manageability

 - [Device.Network.Switch.Manageability](#device.network.switch.manageability)
-->

<a name="device.network.switch.manageability"></a>
##Device.Network.Switch.Manageability

### <a name="devicenetworkswitchmanageabilitynetworkswitchprofile-if-implemented"></a>Device.Network.Switch.Manageability.NetworkSwitchProfile （如果实现）

*Device.Network.Switch.Manageability.NetworkSwitchProfile*

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

建议的 DTMF 网络切换配置文件定义的 CIM 模型和相关的网络交换机 （包括 CIM 类、 关联、 指示、 方法和属性） 的管理行为。  不必要的数据中心网络交换机实现完整建议的 DMTF 网络切换配置文件，因为满足此可管理性要求所需的功能的子集。  此子集必须远程包括通过实施 CIM 类下面的管理操作，通过 WS-Man. 这一要求是如果实现要求，需满足如果实现了这一要求的功能，如下所示︰

-   获取、 启用和禁用交换机的功能

-   获取、 启用和禁用端口

-   为访问或干线模式设置端口

-   获取，设置端口说明

-   获取一个中继端口 Vlan 的列表

-   获取访问端口 VLAN

-   添加或删除对中继端口 VLAN

-   获取列表的 Vlan

-   启用/禁用的 VLAN

-   创建/删除 VLAN

-   更改 VLAN 名称

-   关闭/重新启动交换机

-   获取、 设置交换机的主机名

-   获取固件版本信息

-   获取，请将标题设置为登录

### <a name="devicenetworkswitchmanageabilitynetworkswitchprofileview"></a>Device.Network.Switch.Manageability.NetworkSwitchProfileView

*这是三层功能的网络交换机必须能够通过 Windows PowerShell 所需状态配置 (DSC) 机制来配置认证是强制性要求。*

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

所需状态配置 (DSC) 使部署和管理的服务和管理的环境中运行这些服务的配置数据。 在<http://technet.microsoft.com/en-us/library/dn249912.aspx>可以找到其他信息。

数据中心第 3 层网络交换机本机基于 OMI 提供商实现一组特定的视图类的定义的 DSC 的体验和需求。 视图类的设计提供了比较完整的网络交换机 CIM 架构的更高级别的基于任务的抽象。 视图类的设计将基于 CIM 标准 DMTF 在此发布<http://www.dmtf.org/sites/default/files/standards/documents/DSP0004_3.0.0.pdf>。

这种声明性的交换机配置的方式确保多个往返行程不是必需的配置，并提供供应商中立的接口来实现的。 此外，它还确保网络交换机不会偏离这一初始配置，从而提高部署的可靠性。

CIM 的视图类的方法极大地简化了初始配置的架构，使上述配置的目标。 交换机供应商可以灵活地选择满足合同由视图类的 DSC 提供它们自己基础实现。

所有类别的可管理性操作将通过都验证，如下所示︰

1.  更改请求的 DSC 文档的托管对象格式文件 (MOF) 文件，是成功接收，并由网络交换机。 此文档指定网络交换机必须转换到所需的状态。

2.  根据网络交换机的目标功能区域，使用不同的方法来验证网络交换机的预期的状态。 相关的要求动员这些分别。

除了上述方式在 DSC 文档的消耗量，交换机还支持枚举和获取功能上的配置元素以便显式枚举或 Get 操作可以调用返回的状态信息的配置元素的开关。

数据中心第 3 层网络交换机提供这一支持本身没有运行在一个单独的设备机箱中的外部配套提供的帮助。
