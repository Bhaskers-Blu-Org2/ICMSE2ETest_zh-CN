---
title: Device.BusController.SdioController
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 042f9f773fd88cf0a97b4b6c855fff35d59014a7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.SdioController
 - [Device.BusController.SdioController](#device.buscontroller.sdiocontroller)
-->

<a name="device.buscontroller.sdiocontroller"></a>
##Device.BusController.SdioController

### <a name="devicebuscontrollersdiocontrollercomplywithindustryspec"></a>Device.BusController.SdioController.ComplyWithIndustrySpec

*SDIO 控制器必须符合行业标准。*

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

安全数字 I/O (SDIO) 主机控制器必须遵守 PCI 2.3 或更高的要求，以便对该接口。 PCI 配置寄存器和接口的信息，请参阅 SD 主机控制器规范版本 1.0，附录 a。

### <a name="devicebuscontrollersdiocontrollerwdfkmdfdriver"></a>Device.BusController.SdioController.WdfKmdfDriver

*SDIO 控制器驱动程序必须是 WDF KMDF 实现。*

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

必须为该驱动程序的实现中使用 Windows 驱动程序框架 (WDF) 的内核模式驱动程序框架编写 SDIO 控制器驱动程序。

