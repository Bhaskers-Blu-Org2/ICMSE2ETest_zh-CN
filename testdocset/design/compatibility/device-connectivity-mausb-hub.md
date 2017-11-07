---
title: Device.Connectivity.MAUSB.Hub
Description: "要求适用于 MA USB 集线器。 但是，MA USB 要求是当前可选，并且直到 2017年将不会强制执行。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 5afa1d76015e624c36d7ad7565c44d827d2ae1c5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.MAUSB.Hub

 - [Device.Connectivity.MAUSB.Hub ](#device.connectivity.mausb.hub)
-->

<a name="device.connectivity.mausb.hub"></a>
##Device.Connectivity.MAUSB.Hub 

以下要求适用于 MA USB 集线器

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

### <a name="deviceconnectivitymausbhubbulkoutbuffersize"></a>Device.Connectivity.MAUSB.Hub.BulkOutBufferSize

*MA USB 集线器必须支持至少 64 KB 缓冲区空间每个非 SuperSpeed 批量出终结点和至少 512 KB 缓冲区空间，每个大容量 SuperSpeed Out 终结点*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 集线器必须支持这些最小缓冲区大小，以便能可靠地为获得最佳的性能 （吞吐量）。 这些缓冲区大小报告其端点的响应数据包中的 MA USB 集线器的 MA USB 规范 1.0 a 版，6.3.7 一节所述。

-   SuperSpeed 大容量出-512 KB

-   非 SuperSpeed 批量出-64 KB

### <a name="deviceconnectivitymausbhubidentifynumofuseraccessibleports"></a>Device.Connectivity.MAUSB.Hub.IdentifyNumOfUserAccessiblePorts

*MA USB 集线器必须正确识别和报告的用户可以访问的端口号。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

集成的 USB 2.0/3.1 中心必须向用户提供准确计数，中心支持的公开面向下游的端口数的操作系统及其集线器描述符中包含详细信息。 请参阅 USB 规范、 修订版 2.0、 Section11.23，以及 USB 3.0 规范、 部分 10.14。

### <a name="deviceconnectivitymausbhubipmode"></a>Device.Connectivity.MAUSB.Hub.IPMode

*MA USB 集线器必须实现支持 IP 模式*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 集线器必须实现为 MA USB 规范 1.0 a 版，4.5.3.2 部分中指定的 IP 模式支持"要求的 IP 模式"

### <a name="deviceconnectivitymausbhubmausbspeccompliance"></a>Device.Connectivity.MAUSB.Hub.MAUSBSpecCompliance

*MA USB 集线器必须为 USB-如果符合规范*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 集线器必须符合 MA USB 规范 1.0 a 版或更高版本。

### <a name="deviceconnectivitymausbhubsupportsuspend"></a>Device.Connectivity.MAUSB.Hub.SupportSuspend

*MA USB 集线器必须支持暂停，和下游设备必须不放置总线集线器从休眠恢复时。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USBhubs 必须支持 MA USB 挂起。 MA USB 集线器恢复从后挂起状态，下游连接的所有设备的集成的 USB 2.0/3.1 集线器，及未删除时中心已挂起，必须存在。

集成的 USB 2.0/3.1 集线器必须支持 USB 挂起。 集成的 USB 2.0/3.1 集线器恢复从 USB 挂起，下游连接的所有设备后的集成的 USB 2.0/3.1 集线器及未删除而集成的 USB 2.0/3.1 集线器已挂起，必须存在。

### <a name="deviceconnectivitymausbhubsupportswifidirectandwsb"></a>Device.Connectivity.MAUSB.Hub.SupportsWiFiDirectAndWSB

*MA USB 集线器支持 WiFi 直接连接和 WiFi 串行总线*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

网络接口实现 MA USB 集线器必须满足以下要求才能可靠地使用收件箱窗口 MA USB 主机。

-   MA USB 集线器/设备必须支持 Wi-Fi 直接服务 (点到点服务 1.x) 通过 802.11 n / 交流和/或 802.11ad NIC

    -   将有可能进入 ASP2 (Wi-Fi 直接发现并连接)

-   MA USB 集线器/设备必须实现 WSB v0.18&lt;最新&gt;作为广告主

### <a name="deviceconnectivitymausbhubtcpimplementation"></a>Device.Connectivity.MAUSB.Hub.TCPImplementation

*MA USB TCP 实现可靠性*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 集线器的 TCP 实现必须满足以下要求才能可靠地使用收件箱窗口 MA USB 主机︰

-   必须禁用 TCP 延迟 ACK 优化。

-   必须禁用 TCP Nagle 算法实现。

-   TCP 必须提供至少 64 KB 的接收缓冲区空间。

### <a name="deviceconnectivitymausbhubusb3hubcomplieswithusb3spec"></a>Device.Connectivity.MAUSB.Hub.Usb3HubCompliesWithUsb3Spec

*集成的 USB 3.1 集线器是符合 USB 3.1 规范。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

集成的 USB 3.1 集线器必须符合**通用串行总线 (USB) 3.1 规范。 

集成的 USB 3.1 集线器必须︰

-   通过 USB-如果互操作性测试

-   通过 Usb 3.1 法规遵从性测试套件

-   通过 USB 3.1 CV 测试

### <a name="deviceconnectivitymausbhubusb3reportportstatusbitscorrectly"></a>Device.Connectivity.MAUSB.Hub.Usb3ReportPortStatusBitsCorrectly

*集成的 USB 3.1 集线器始终必须报告根据 USB 3.1 规范正确的端口状态位。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

对当前堆栈中大量无效的端口状态的位组合中心报告将被忽略。 任何无效的端口状态位组合将被视为错误。 尤其是，检查将执行这些操作︰

-   重置端口

-   挂起和继续执行端口

-   系统恢复

集成的 USB 3.1 集线器不应该报告虚假更改中断。

