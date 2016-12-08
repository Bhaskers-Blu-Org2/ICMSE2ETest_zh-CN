---
title: Device.Input.HID
Description: "所有的 HID 设备通过 I2C 连接必须符合 Microsoft HID I2C 协议规范。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 193cc5b46d0229e1a4b85f520c6081014ee30184
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.HID

 - [Device.Input.HID](#device.input.hid)
-->

<a name="device.input.hid"></a>
##Device.Input.HID

### <a name="deviceinputhidi2cprotocolspeccompliant"></a>Device.Input.HID.I2CProtocolSpecCompliant

*所有的 HID 设备通过 I2C 连接必须符合 Microsoft HID I2C 协议规范。*

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

所有隐藏通过 I2C 兼容设备必须遵循 Microsoft 发布的 HID I2C 协议规范的文档。

*设计备注*

Microsoft 发布了 HID I2C 协议规范 （还未提供的链接），请参阅

异常︰ 这一要求是 HID I2C 设备才强制实施，不为 SPB 通用。

### <a name="deviceinputhidusbspecificationcompliant"></a>Device.Input.HID.UsbSpecificationCompliant

*通过 USB 连接的所有 HID 设备必须都符合 USB HID 规范 (1.1 版或更高版本)。*

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

版本 5︰ 定义 WMC AQ 要求

-   用于 WMC AQ 是此要求︰

    -   对于桌面系统的要求

    -   如果便携式计算机系统包括遥控器和接收器的便携式电脑系统的要求。

-   对于非 AQ 系统，这一要求是︰

    -   如果系统 （台式机或笔记本电脑） 包括遥控器和接收器所需。<br/><br/>

-   红外接收器 （仅输入） 和红外收发器 （输入和发出的红外/学习） 与 Windows Media Center 类驱动程序的接口。 在系统中使用电视调谐器，红外收发器必须使用支持所有功能的*遥控器和接收器收发器规格和要求的 Windows Media Center 在 Windows 操作系统*的文档。

-   对于红外接收器使用的 tunerless 系统，只有红外输入和唤醒功能是必需的。 红外学习和发射功能是可选的。

-   DVB-T 解决方案不需要支持学习和发出。 这些功能是可选的。

-   在不使用机顶盒的地方，学习，并发出功能是可选的。

-   在那些支持辅助 10 英尺长的应用程序的区域，使红外接收器/收发器不需要满足红外学习要求。

-   在这些地区支持 DVB-S，Microsoft 强烈建议使用的红外收发器 （输入和发出的红外/学习）。

-   如果发运便携式计算机系统、 红外学习和红外发射是可选的。

-   对于红外接收器 （仅输入） 使用 Microsoft 授权红外线 （ir） 协议和所有红外收发器 （输入和发射器的函数），设备将回到红外波形包络的软件解码红外信号的软件。 无法在硬件中解码红外信号。 唯一的例外是"唤醒从远程"电源键。

-   红外接收器 （仅输入） 允许执行硬件解码红外信号。 （仅输入） 这些红外接收器必须接收并响应任何当前授权 Microsoft 红外线 （ir） 协议。 使用硬件解码红外信号的红外接收器还需要支持"唤醒从远程"功能。 这些设备必须符合远程*控制和接收器收发器规格和要求的 Windows Media Center 在 Windows 操作系统*文档。

*设计备注*

Microsoft 建议标记红外线 （ir） 缆线并为最终用户记录良好。 插入显示红外线 （ir） 控制线和如何连接到数字有线电视或卫星接收器可以帮助防止支持电话的小图示。

