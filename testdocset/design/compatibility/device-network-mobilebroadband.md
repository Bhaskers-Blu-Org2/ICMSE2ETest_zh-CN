---
title: Device.Network.MobileBroadband
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 0925ce9bd92ec4e19423ca607add7ec77b7abd6b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicenetworkmobilebroadband"></a>Device.Network.MobileBroadband

 - [Device.Network.MobileBroadband.CDMA](#device.network.mobilebroadband.cdma)
 - [Device.Network.MobileBroadband.FirmwareUpdater](#device.network.mobilebroadband.firmwareupdater)
 - [Device.Network.MobileBroadband.GSM](#device.network.mobilebroadband.gsm)

<a name="device.network.mobilebroadband.cdma"></a>
## <a name="devicenetworkmobilebroadbandcdma"></a>Device.Network.MobileBroadband.CDMA

*移动宽带*

### <a name="devicenetworkmobilebroadbandcdmacomplywithbasereq"></a>Device.Network.MobileBroadband.CDMA.ComplyWithBaseReq

*移动宽带设备，必须符合下列基本要求。*

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

移动宽带设备，必须符合下列基本要求︰

-   必须符合 Windows 驱动程序工具包中的 NDIS 6.30 和 Microsoft 移动宽带驱动程序模型规范要求。

-   必须遵守电源管理规范。

-   必须符合指定的各种类别的移动宽带驱动程序模型规范中的设备的各种操作的性能目标。

-   移动宽带设备驱动程序必须实现和符合的 NDIS 6.30 和 Microsoft 移动宽带驱动程序模型规范。 必须实现在移动宽带驱动程序模型规范中指定的所有建议的实现。 请注意，Microsoft 的 MB 类驱动程序是符合上述要求。 网络设备类电源管理引用规范 2.0 版中所述，移动宽带设备必须支持电源管理策略。 设备必须在各种操作系统的电源管理操作后正常工作。 设备必须满足移动宽带驱动程序模型规范中描述的性能目标。

*设计备注*

有用的链接︰ 移动宽带驱动程序模型规范<http://msdn.microsoft.com/en-us/library/ff560543.aspx>网络设备类电源管理引用规范<http://download.microsoft.com/download/1/6/1/161ba512-40e2-4cc9-843a-923143f3456c/netpmspc.rtf>

### <a name="devicenetworkmobilebroadbandcdmafwcomplywithmbspec"></a>Device.Network.MobileBroadband.CDMA.FWComplyWithMBSpec

*基于 USB 接口的 CDMA 类的移动宽带设备固件必须符合 usb-如果的移动宽带接口模型规范。*

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

基于 USB 接口的 CDMA 类的移动宽带设备的固件实现必须符合 usb-如果的移动宽带接口模型 (MBIM) 规范。 没有其他的 IHV 驱动程序所需的设备的功能和设备必须使用微软移动宽带 (MB) 类驱动程序实现。

设备固件还必须遵守 MBIM 勘误表\*以及 MBIM 1.0 规范。 在特定的需要符合 MBIM 勘误表中的下列项目︰

 - MEFD （MB 的扩展功能描述符）︰ 设备操作员特定固件必须报告鉴定设备的运营商的移动网络运营商按照要求正确的 MTU 大小。

 - \*USB-如果链接 NCM DWG 成员仅对可访问的。 它获得批准后，将发布此勘误表。

更多详细信息︰

移动宽带接口型号规格︰ <http://www.usb.org/developers/devclass_docs/MBIM10.zip>

移动宽带驱动程序型号规格︰ <http://msdn.microsoft.com/library/windows/hardware/ff560543.aspx>

### <a name="devicenetworkmobilebroadbandcdmaidentitymorphing"></a>Device.Network.MobileBroadband.CDMA.IdentityMorphing

*移动宽带设备必须支持标识变形。*

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

基于 USB 协议的移动宽带设备必须支持标识变形。 设备固件中实现这一要求使设备制造商要充分利用 Microsoft 的收件箱中 Windows 8 MB 类驱动程序以及对前代的 Windows 操作系统版本 7 及以下使用他们自己的驱动程序的灵活性。 在下面的其他信息一节中提供了指向相关的规范。 附加信息︰ 标识变形指标︰ 请参阅 MSDN。

### <a name="devicenetworkmobilebroadbandcdmaloopback"></a>Device.Network.MobileBroadband.CDMA.Loopback

*基于 USB 协议的移动宽带设备必须实现性能和负载一致性测试环回功能。*

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

基于 USB 协议的移动宽带设备必须在设备固件中实现环回功能规范中所述。 请注意，因为它是一个在性能关键路径，环回功能仅测试数据数据包。 设备必须通过环回测试的性能要求。

具体来说，设备必须能够支持组合的 100 Mbps 吞吐量 (50 Mbps 上行链路 / 50 Mbps 下行线) 或以上，达 5%的丢失率。 在下面的其他信息一节中提供了指向相关的规范。

附加信息︰

环回设备固件实现指南︰ <http://msdn.microsoft.com/en-us/library/windows/hardware/hh975390.aspx>

MB 微型端口驱动程序的性能要求︰ <http://msdn.microsoft.com/en-us/library/windows/hardware/ff557193.aspx>

### <a name="devicenetworkmobilebroadbandcdmamulticarrierfunctionality"></a>Device.Network.MobileBroadband.CDMA.MultiCarrierFunctionality

*支持多载体功能的移动宽带设备必须支持多运营商的功能。*

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

支持多载体功能的移动宽带设备必须支持多载波的功能，还应执行以下︰

-   必须满足移动宽带驱动程序模型规范中提供的多载波性能要求。

-   必须保持在总线上时更改主供应商。

-   必须成功通过涵盖所有设备可以连接到的另一个手机类技术的所有适用的徽标测试。

-   支持多承运人功能的移动宽带设备必须满足移动宽带驱动程序模型规范中指定的多载波性能要求。 移动宽带设备支持多载波功能必须执行总线/设备重新枚举或电源重置更改家庭提供程序时导致 windows 即插即用重新枚举该设备。 如果该设备是能够支持 GSM 和 CDMA 蜂窝移动通信技术，则设备必须执行 GSM 以及 CDMA 徽标测试。 为此要正确介绍，徽标测试执行的位置必须位于至少一个 GSM 和一个 CDMA 蜂窝移动通信技术的覆盖范围。

### <a name="devicenetworkmobilebroadbandcdmareliablecsconnectivity"></a>Device.Network.MobileBroadband.CDMA.ReliableCSConnectivity

*支持连接备用系统上的无线 WAN 设备必须提供可靠的连接，在连接待机状态。*

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

该设备无缝过渡 D0 和 D3 之间热状态而在连接待机 (CS)。 设备维护在 CS 中的 L2 和 l3 高速连接。 设备唤醒根据匹配的唤醒模式。 有在 CS 中没有虚假的唤醒。 唤醒数据包传递而不会延迟或缓冲。 在 IPv4 和 IPv6 上将 RealTimeCommunication 应用程序保持在 CS 连接。

### <a name="devicenetworkmobilebroadbandcdmasupportusbselectivesuspend"></a>Device.Network.MobileBroadband.CDMA.SupportUSBSelectiveSuspend

*基于 USB 的移动宽带设备必须支持实现 USB 选择性挂起的窗口。*

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

基于 USB 的移动宽带设备必须支持 Windows 实现 USB 选择性挂起 (SS)。 没有另外的 USB SS 方案被允许。

### <a name="devicenetworkmobilebroadbandcdmasupportwakeonmb"></a>Device.Network.MobileBroadband.CDMA.SupportWakeOnMB

*移动宽带设备类的移动宽带功能上都必须支持以下唤醒。*

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

移动宽带设备类的移动宽带功能上都必须支持以下唤醒。

-   设备必须支持 32 个 128 字节的位图的唤醒模式。

-   设备必须唤醒上注册状态更改的系统。

-   设备必须唤醒媒体上的系统连接。

-   设备必须唤醒上媒体断开连接的系统。

-   GSM 和 CDMA 类设备必须唤醒设备上接收传入的 SMS 消息的系统。

-   设备支持 USSD 必须唤醒在接收 USSD 消息系统。

-   设备必须支持唤醒数据包指示。 NIC 应缓存导致唤醒硬件并安装操作系统时准备好接收的传入数据包。

移动类别的设备必须支持唤醒移动宽带。 设备应唤醒系统上面提到的事件。 注意该唤醒 USSD 是必需的只有当设备报告它支持 USSD;否则，它是可选的。 有关 SMS，请参阅以下 MSDN 文档以了解更多信息并注册状态唤醒事件。

1. NDIS\_状态\_WWAN\_注册\_状态

2. NDIS\_状态\_WWAN\_SMS\_接收

<a name="device.network.mobilebroadband.firmwareupdater"></a>
## <a name="devicenetworkmobilebroadbandfirmwareupdater"></a>Device.Network.MobileBroadband.FirmwareUpdater

*移动宽带*

### <a name="devicenetworkmobilebroadbandfirmwareupdaterfirmwareupgrade"></a>Device.Network.MobileBroadband.FirmwareUpdater.FirmwareUpgrade

*基于 USB 接口的 GSM 和 CDMA 的符合 Microsoft 的固件更新平台的移动宽带设备的类必须实现固件 ID 设备服务和对设备的固件负载更新 UMDF 基于的固件更新驱动程序。*

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

基于 USB 接口的 GSM 和 CDMA 移动宽带设备符合 Microsoft 的固件更新平台类必须到设备的固件负载更新中实现固件 ID 设备服务 （可在 MSDN 上即将发布） 和基于 UMDF 固件更新驱动程序 （指导原则和很快在 MSDN 上发布的示例）。

其他信息

<a name="device.network.mobilebroadband.gsm"></a>
## <a name="devicenetworkmobilebroadbandgsm"></a>Device.Network.MobileBroadband.GSM

*移动宽带*

### <a name="devicenetworkmobilebroadbandgsmcomplywithbasereq"></a>Device.Network.MobileBroadband.GSM.ComplyWithBaseReq

*移动宽带设备，必须符合下列基本要求。*

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

移动宽带设备，必须符合下列基本要求︰

-   必须符合 Windows 驱动程序工具包中的 NDIS 6.30 和 Microsoft 移动宽带驱动程序模型规范要求。

-   必须遵守电源管理规范。

-   必须符合指定的各种类别的移动宽带驱动程序模型规范中的设备的各种操作的性能目标。

-   移动宽带设备驱动程序必须实现和符合的 NDIS 6.30 和 Microsoft 移动宽带驱动程序模型规范。 所有建议中移动宽带驱动程序模型规范需要实现指定的实现。 请注意，Microsoft 的 MB 类驱动程序是符合上述要求。 网络设备类电源管理引用规范 2.0 版中所述，移动宽带设备必须支持电源管理策略。 设备必须在各种操作系统的电源管理操作后正常工作。 设备必须满足移动宽带驱动程序模型规范中描述的性能目标。

*设计备注*

有用的链接︰ 移动宽带驱动程序模型规范<http://msdn.microsoft.com/en-us/library/ff560543.aspx>网络设备类电源管理引用规范<http://download.microsoft.com/download/1/6/1/161ba512-40e2-4cc9-843a-923143f3456c/netpmspc.rtf>

### <a name="devicenetworkmobilebroadbandgsmeapsim"></a>Device.Network.MobileBroadband.GSM.EAPSIM

*GSM 的移动宽带设备支持 GSM 订户身份模块 (EAP-SIM) 的可扩展身份验证协议方法的类必须支持 EAP-SIM RFC 4186 中定义。*

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

支持 EAP-SIM 的 GSM 设备必须支持 EAP-SIM RFC 4186 中定义。

### <a name="devicenetworkmobilebroadbandgsmfwcomplywithmbspec"></a>Device.Network.MobileBroadband.GSM.FWComplyWithMBSpec

*基于 USB 接口的移动宽带设备固件必须符合 usb 类 GSM-IF 的移动宽带接口模型规范。*

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

基于 USB 接口的移动宽带设备的固件实现必须符合 usb 类 GSM-IF 的移动宽带接口模型 (MBIM) 规范。 没有其他的 IHV 驱动程序所需的设备的功能和设备必须使用微软移动宽带 (MB) 类驱动程序实现。

设备固件还必须遵守 MBIM 勘误表\*以及 MBIM 1.0 规范。 在特定的需要符合 MBIM 勘误表中的下列项目︰

-   MEFD （MB 的扩展功能描述符）︰ 设备操作员特定固件必须报告鉴定设备的运营商的移动网络运营商按照要求正确的 MTU 大小。

\*USB-如果链接 NCM DWG 成员仅对可访问的。 它获得批准后，将发布此勘误表。

更多详细信息︰

移动宽带接口型号规格︰ <http://www.usb.org/developers/devclass_docs/MBIM10.zip>

移动宽带驱动程序型号规格︰ <http://msdn.microsoft.com/library/windows/hardware/ff560543.aspx>

### <a name="devicenetworkmobilebroadbandgsmidentitymorphing"></a>Device.Network.MobileBroadband.GSM.IdentityMorphing

*移动宽带设备必须支持标识变形。*

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

基于 USB 协议的移动宽带设备必须支持标识变形。 设备固件中实现这一要求使设备制造商要充分利用 Microsoft 的收件箱中 Windows 8 MB 类驱动程序以及对前代的 Windows 操作系统版本 7 及以下使用他们自己的驱动程序的灵活性。 在下面的其他信息一节中提供了指向相关的规范。

附加信息︰ 标识变形指标︰ 请参阅 MSDN。

### <a name="devicenetworkmobilebroadbandgsmloopback"></a>Device.Network.MobileBroadband.GSM.Loopback

*基于 USB 协议的移动宽带设备必须实现性能和负载一致性测试环回功能。*

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

基于 USB 协议的移动宽带设备必须在设备固件中实现环回功能规范中所述。 请注意，因为它是一个在性能关键路径，环回功能仅测试数据数据包。 设备必须通过环回测试的性能要求。 具体来说，设备必须能够支持组合的 100 Mbps 吞吐量 (50 Mbps 上行链路 / 50 Mbps 下行线) 或以上，达 5%的丢失率。

在下面的其他信息一节中提供了指向相关的规范。

附加信息︰

环回设备固件实现指南︰ <http://msdn.microsoft.com/en-us/library/windows/hardware/hh975390.aspx>

MB 微型端口驱动程序的性能要求︰ <http://msdn.microsoft.com/en-us/library/windows/hardware/ff557193.aspx>

### <a name="devicenetworkmobilebroadbandgsmmulticarrierfunctionality"></a>Device.Network.MobileBroadband.GSM.MultiCarrierFunctionality

*支持多载体功能的移动宽带设备必须支持多运营商的功能。*

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

支持多载体功能的移动宽带设备必须支持多载波的功能，并还应执行以下︰

必须满足移动宽带驱动程序模型规范中提供的多载波性能要求。

必须保持在总线上时更改主供应商。

必须成功通过涵盖所有设备可以连接到的另一个手机类技术的所有适用的徽标测试。

支持多承运人功能的移动宽带设备必须满足移动宽带驱动程序模型规范中指定的多载波性能要求。 移动宽带设备支持多载波功能必须执行总线/设备重新枚举或电源重置更改家庭提供程序时导致 windows 即插即用重新枚举该设备。 如果该设备是能够支持 GSM 和 CDMA 蜂窝移动通信技术，则设备必须执行 GSM 以及 CDMA 徽标测试。 为此要正确介绍，徽标测试执行的位置必须位于至少一个 GSM 和一个 CDMA 蜂窝移动通信技术的覆盖范围。

 

### <a name="devicenetworkmobilebroadbandgsmmultiplepdpcontext"></a>Device.Network.MobileBroadband.GSM.MultiplePDPContext

*多个 PDP 上下文支持*

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

使用此功能，Windows 应用程序可以通过不同的 PDP 上下文 （虚拟通道） 移动网络中进行通信。 移动操作员使用不同的 PDP 上下文创建与众不同的体验和创新的服务。 第三方应用程序开发人员可以使用此功能来生成高质量 VOIP 和视频流经验与移动运营商合作。

设备固件能够多个 PDP 上下文需要符合[MBIM 规范](http://www.usb.org/developers/devclass_docs/MBIM10.zip)。 具体来说，设备固件应该支持 MBIM 规范的第 10.5.12.1 部分所述多个 IP 数据流。 这包括支持所有 Cid 的控制实现和 IP 数据流的完全支持多个 PDP 上下文。

设备固件必须支持使用 windows 8 双载体 （IPv4 和 IPv6） PDP 上下文的总数。

这包括用于因特网连接的 1 和 7 其他运算符应用程序。

设备不要求公开其内部，固件管理用于 SMS 的 PDP 上下文和 windows 的任何其他管理上下文。

设备固件应该能够利用主机操作系统的 PDP 上下文中已经是内部管理，妥善处理其固件中的设备招标。

设备固件应该继续抽象 SMS PDP 上下文并穿下用载体无论 SMS Cid。

### <a name="devicenetworkmobilebroadbandgsmreliablecsconnectivity"></a>Device.Network.MobileBroadband.GSM.ReliableCSConnectivity

*支持连接备用系统上的无线 WAN 设备必须提供可靠的连接，在连接待机状态。*

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

该设备无缝过渡 D0 和 D3 之间热状态而在连接待机 (CS)。 设备维护在 CS 中的 L2 和 l3 高速连接。 设备唤醒根据匹配的唤醒模式。 有在 CS 中没有虚假的唤醒。 唤醒数据包传递而不会延迟或缓冲。 在 IPv4 和 IPv6 上将 RealTimeCommunication 应用程序保持在 CS 连接。

### <a name="devicenetworkmobilebroadbandgsmsupportfastdormancy"></a>Device.Network.MobileBroadband.GSM.SupportFastDormancy

*GSM 移动宽带设备的类必须支持快速休眠机制由 3GPP 版本 8 中。*

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

按照修订版本 8 中的 3GPP 定义移动宽带设备必须实现快速休眠机制。  快速非活跃状态是一个电池寿命节约机制，UE （用户设备） 设备，允许请求将它们放入低功耗通道网络设备。 UE 发送信令连接发布指示 (SCRI) （UE 通过网络发送） IE"信号连接发布指示原因"存在，并且已设置为"UE PS 数据请求会话结束"。

### <a name="devicenetworkmobilebroadbandgsmsupportusbselectivesuspend"></a>Device.Network.MobileBroadband.GSM.SupportUSBSelectiveSuspend

*基于移动宽带设备必须支持的 Windows 实现 USB 选择性挂起 USB。*

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

基于移动宽带设备必须支持 USB Windows 实现 USB 选择性挂起 (SS)。 没有另外的 USB SS 方案被允许。

### <a name="devicenetworkmobilebroadbandgsmsupportwakeonmb"></a>Device.Network.MobileBroadband.GSM.SupportWakeOnMB

*移动宽带设备类的移动宽带功能上都必须支持以下唤醒。* 

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

移动宽带设备类的移动宽带功能上都必须支持以下唤醒。

-   设备必须支持 32 个 128 字节的位图的唤醒模式。

-   设备必须唤醒上注册状态更改的系统。

-   设备必须唤醒媒体上的系统连接。

-   设备必须唤醒上媒体断开连接的系统。

-   GSM 和 CDMA 类设备必须唤醒设备上接收传入的 SMS 消息的系统。

-   设备支持 USSD 必须唤醒在接收 USSD 消息系统。

-   设备必须支持唤醒数据包指示。 NIC 应缓存导致唤醒硬件并安装操作系统时准备好接收的传入数据包。

移动宽带设备类必须支持移动宽带的唤醒。 设备应唤醒系统上面提到的事件。 注意该唤醒 USSD 是必需的只有当设备报告它支持 USSD;否则，它是可选的。 有关 SMS，请参阅以下 MSDN 文档以了解更多信息并注册状态唤醒事件。

1.  NDIS\_状态\_WWAN\_注册\_状态

2.  NDIS\_状态\_WWAN\_SMS\_接收

### <a name="devicenetworkmobilebroadbandgsmussd"></a>Device.Network.MobileBroadband.GSM.USSD

*实现非结构化的补充服务数据 (USSD) 的移动宽带设备的 GSM 类必须支持 USSD 基于移动宽带驱动程序模型。*

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

Windows 移动宽带驱动程序模型更新以包括发送和接收 USSD 邮件的完全支持。 实现 USSD 的设备必须支持 USSD 基于移动宽带驱动程序模型。

