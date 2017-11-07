---
title: Device.Connectivity.Network.VerticalPairing
Description: "要求。 前者的位置技术的根。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: edea4c352a63749cd2dfd0f10ac0be02fcd0424c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.Network.VerticalPairing

 - [Device.Connectivity.Network.VerticalPairing](#device.connectivity.network.verticalpairing)
-->

<a name="device.connectivity.network.verticalpairing"></a>
##Device.Connectivity.Network.VerticalPairing

*前者的位置技术的根*

### <a name="deviceconnectivitynetworkverticalpairingwcn"></a>Device.Connectivity.Network.VerticalPairing.WCN

*作为工作站 (STA) 中运行的 802.11 启用网络的设备必须实现 WCN NET 且符合 802.11 的基本要求。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

802.11 网络启用的设备的操作如工作站 (STA) 必须满足以下要求︰

-   该设备必须实现 WCN NET，符合规范。

-   该设备必须实现 WCN NET 垂直配对扩展并指示它是否支持 PNP-X 传输协议。 如果设备支持 PNP-X 传输协议，它必须确保正确的通用唯一标识符 (UUID) 对齐方式。

-   如果实现 WCN UFD 时，它必须符合规范。

-   如果设备具有能够显示四位或八位号码显示，它必须支持显示动态 Windows 连接现在 (WCN) 针，无需用户干预。 PIN 必须至少两分钟后在 WPS 模型名称属性中设备接收到的"窗口"的值与无线配置服务 (WPS) M2D 消息显示。

-   如果设备没有显示四位或八位号码显示，它必须提供物理标签贴到设备，其中包括 8 位数字的 PIN，清楚地标志 PIN 值作为 PIN (例如，附︰ 12345670)。

-   通过 Wi-fi 联盟，包括 Wi-Fi 认证、 Wi-fi 保护访问 2 (WPA2) 认证和 Wi-Fi 保护安装证书，设备必须经过认证。

*设计备注*

有关实施的详细信息，请参阅<http://go.microsoft.com/fwlink/?LinkId=109371>的 WCN 网络规范和<http://go.microsoft.com/fwlink/?LinkId=109372>的 WCN UFD 规范。

有关详细信息，请参阅"安装 Wi-fi 设备使用位置垂直配对"白皮书在<http://www.microsoft.com/whdc/connect/rally/WiFiVerticalPair.mspx>。

在<http://go.microsoft.com/fwlink/?LinkId=109373>和<http://go.microsoft.com/fwlink/?LinkId=109368>可以找到其他信息。

WCN 网络是必需的。 WCN UFD 是可选的在 Windows 支持的设备，可用于为 Windows XP Service Pack 2 支持 WCN 的功能与向后兼容性。

设备使用 WCN NET 垂直配对扩展名指示 PNP-X 其支持。 该设备必须提供既为 WCN 网络交换提供一个 UUID 和设备 (WSD) 设备文件 UPnP /web 服务或提供 UPnP/WSD 设备 UUID WCN NET 垂直匹配扩展的 TransportUUID 属性中。 提供在 UPnP 或 WSD UUID 必须以小写字母 （也可以用十进制数）。

WSD 实现 WSD UUID 提供的终结点引用的地址，并且必须是窗体的<code>urn:uuid:</code>。 UPnP 实现 UPnP UUID 作为根设备 UUID。

