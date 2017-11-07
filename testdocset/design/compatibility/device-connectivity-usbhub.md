---
title: Device.Connectivity.UsbHub
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: effccc706b2391dacdc81899d840b1eee1b02092
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.UsbHub

 - [Device.Connectivity.UsbHub](#device.connectivity.usbhub)
-->

<a name="device.connectivity.usbhub"></a>
##Device.Connectivity.UsbHub

*仅适用于 USB 集线器的需求*

### <a name="deviceconnectivityusbhubidentifynumofuseraccessibleports"></a>Device.Connectivity.UsbHub.IdentifyNumOfUserAccessiblePorts

*一个 USB 集线器必须正确识别并报告的用户可以访问的端口号。*

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

USB 集线器必须向用户提供准确计数，中心支持的公开面向下游的端口数的操作系统及其集线器描述符中包含详细信息。 请参阅 USB 规范、 修订版 2.0、 Section11.23，以及 USB 3.0 规范、 部分 10.14。 根集线器不受这一要求。

### <a name="deviceconnectivityusbhubsupportsuspend"></a>Device.Connectivity.UsbHub.SupportSuspend

*USB 集线器都必须支持选择性挂起状态，和下游设备必须不放置总线时中心继续与选择性挂起。*

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

USB 集线器都必须支持选择性挂起状态，如所述 USB 规范和其他徽标计划的要求。 中心继续与选择性后挂起状态，所有已连接的设备的集线器，下游和程序没有删除时中心已挂起，必须存在。

### <a name="deviceconnectivityusbhubusb3hubcomplieswithusb3spec"></a>Device.Connectivity.UsbHub.Usb3HubCompliesWithUsb3Spec

*USB 3.0 集线器是符合 USB 3.0 规范。*

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

USB 3.0 集线器必须符合**通用串行总线 (USB) 3.0 规范。 

USB 3.0 集线器必须︰

-   通过 USB-如果互操作性测试

-   通过 Usb 3.0 的法规遵从性测试套件

-   通过 USB 3.0 CV 测试

### <a name="deviceconnectivityusbhubusb3reportportstatusbitscorrectly"></a>Device.Connectivity.UsbHub.Usb3ReportPortStatusBitsCorrectly

*USB 3.0 集线器始终必须报告了 USB 3.0 规范按照正确的端口状态位。*

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

对当前堆栈中大量无效的端口状态的位组合中心报告将被忽略。 任何无效的端口状态位组合将被视为错误。 尤其是，检查将执行这些操作︰
 

-   重置端口

-   挂起和继续执行端口

-   系统恢复

集线器不应该报告虚假更改中断。 集线器应该完成端口状态中断传输，而无需更改报告。

### <a name="deviceconnectivityusbhubusbtypechubcompat"></a>Device.Connectivity.UsbHub.USBTypeCHubCompat

*USB 集线器类型 C 兼容性*

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

这样一个端口可以映射到任意方向的附加的即插即用 USB 类型 C 集线器必须使用它们的 SuperSpeed 端口复用器。 这样，连接了 USB C 设备中任何一个不带用户界面的影响方向和丢失状态。

如果 USB 类型 C 中心旨在回上游主机提供的电能，其上游端口必须作为充电 UFP。 此外，如果数据 DFP 作为最初解析其上游端口，则必须启动数据角色交换;如果电源接收器作为最初解析其上游端口，则必须启动角色换用电源。
