---
title: Device.BusController.UART
Description: "仅对芯片供应商的要求。 建议使用 SerCXV2 UART 控制器驱动程序。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 60f64db8d7497c59ef986b95f5d340c767802ad5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.UART
 - [Device.BusController.UART](#device.buscontroller.uart)
-->

<a name="device.buscontroller.uart"></a>
##Device.BusController.UART

要求仅适用于芯片供应商。 建议使用 SerCXV2 UART 控制器驱动程序。

### <a name="devicebuscontrolleruartcancellation"></a>Device.BusController.UART.Cancellation

*UART 控制器，控制器驱动程序必须支持读取和写入请求取消。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持以下︰

-   控制器实现必要的逻辑来支持 I/O 取消

### <a name="devicebuscontrolleruartdma"></a>Device.BusController.UART.DMA

*UART 控制器，控制器驱动程序需要适当的 DMA 事务 DMA 支持。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持以下︰

-   外围设备的驱动程序可以发出读并且到 5k 数据大小最大控制器写入请求。

### <a name="devicebuscontrolleruartflowcontrol"></a>Device.BusController.UART.FlowControl

*UART 控制器，控制器驱动程序必须支持流控制的设置打开和关闭。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持以下︰

-   驱动程序实现 IOCTL 支持\_串行\_获得\_HANDFLOW 和 IOCTL\_串行\_设置\_HANDFLOW Ioctl 和流控制设置

### <a name="devicebuscontrolleruartflushfifo"></a>Device.BusController.UART.FlushFIFO

*UART 控制器，控制器驱动程序必须支持刷新 FIFOs。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持刷新先进先出队列的功能。

### <a name="devicebuscontrolleruartguardbuffer"></a>Device.BusController.UART.GuardBuffer

*UART 控制器和关联的控制器驱动程序必须检测和更正的触发缓冲区溢出和下溢。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，不应写入传输缓冲区以外的内存。 例如，如果 1 KB 数据传输缓冲区分配读取，UART 数据传输必须写入 1 KB 缓冲区以外的内存。 针对这一要求，已添加测试来检测传输缓冲区以外的内存已被覆盖。 一旦完成传输，传输缓冲区的所有权传递到测试应用程序。 然后，测试验证传输缓冲区内存并不改变，以确保不会覆盖该缓冲区。

### <a name="devicebuscontrolleruarthcktestability"></a>Device.BusController.UART.HCKTestability

*正确的 ACPI 表信息和 UART 引脚启用 HCK 可测试性，必须公开 UART 控制器的系统。*

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

这一要求的目的是使 UART 控制器为可测试 HCK 框架。

详细信息︰

-   测试控制器必须提供 UART 的外部连接针脚 （Rx，得克萨斯州 RTS、 CTS 和 GND）。

-   描述了 UART HCK 测试外围设备驱动程序和与受测设备的固件中的 UART 控制器的连接。

### <a name="devicebuscontrolleruartidlepowermanagement"></a>Device.BusController.UART.IdlePowerManagement

*UART 控制器，控制器驱动程序必须支持空闲电源管理。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持以下︰

-   对 Dx 状态时 200 ms 控制器中没有挂起 I/O 控制器转换。

### <a name="devicebuscontrolleruartperformance"></a>Device.BusController.UART.Performance

*UART 控制器，控制器驱动程序已测得的波特率相匹配所需的值。*

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

UART 控制器和关联的控制器驱动程序必须符合串行框架测得的波特率匹配所需的值。

### <a name="devicebuscontrolleruartreadwrite"></a>Device.BusController.UART.ReadWrite

*UART 控制器，控制器驱动程序必须支持读/写 Unicode(8 bits) 数据。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，然后从 UART 外围设备中读取数据时支持以下︰

-   支持 IOCTL\_串行\_设置\_行\_控制和 IOCTL\_串行\_获得\_行\_控件并且能够根据数据长度设置 （8 位） 的数据传输。

### <a name="devicebuscontrolleruartstress"></a>Device.BusController.UART.Stress

*UART 控制器，控制器驱动程序可以正确地运行 （和恢复适当的总线错误） 在长时间的压力的情况下。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持以下︰

-   至少 1 小时维持压力测试通过。

### <a name="devicebuscontrolleruartsupportedbaudrates"></a>Device.BusController.UART.SupportedBaudRates

*UART 控制器，控制器驱动程序必须支持基本的波特率 115200 和更快的速度，更高带宽通信。*

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

UART 控制器和关联的控制器驱动程序必须符合串行的框架，并支持以下︰

-   驱动程序支持 IOCTL\_串行\_设置\_波特\_速率和 IOCTL\_串行\_获得\_波特\_率 IOCTL。

-   驱动程序应该会失败，不受支持的波特率的波特率设置，并且可以执行 i/o 操作使用波特速率集。

