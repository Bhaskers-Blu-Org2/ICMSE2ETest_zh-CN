---
title: Device.Network.DevFund
Description: "网络要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: adedb3c206935035180c7925189d21db06e717e7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Network.DevFund

 - [Device.Network.DevFund](#device.network.devfund)
-->

<a name="device.network.devfund"></a>
##Device.Network.DevFund

*网络要求*

### <a name="devicenetworkdevfundndisversion"></a>Device.Network.DevFund.NdisVersion

*NDIS 设备必须符合 Windows 驱动程序工具包中的 NDIS 6.x 要求。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有的 NDIS 设备必须符合 NDIS 6.x 版 Windows 驱动程序工具包中指定。

*设计备注*

请参阅 Windows 驱动程序工具包，"NDIS。"

### <a name="devicenetworkdevfundnpos"></a>Device.Network.DevFund.NPOS

*网络设备必须支持无暂停上挂起 (NPOS)。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

NDIS 微型端口驱动程序必须支持客户端 Sku （功能在服务器 Sku 的支持是可选的） 上的否暂停上挂起 (NPOS)。

*设计备注*

请参阅否暂停上挂起规范。

### <a name="devicenetworkdevfundselectivesuspend"></a>Device.Network.DevFund.SelectiveSuspend

*NDIS 设备必须满足选择性挂起的要求。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

NDIS 设备必须满足选择性挂起的要求。

