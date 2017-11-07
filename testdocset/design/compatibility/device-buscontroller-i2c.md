---
title: Device.BusController.I2C
Description: "仅用于 I2C 控制器芯片供应商的要求。 系统制造商可能会有选择地运行这些测试，但可能需要硬件自定义。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 32b50a6eb2c7911f4639b2dc51de8bdd9bb1f0ff
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.I2C
 - [Device.BusController.I2C](#device.buscontroller.i2c)
-->

<a name="device.buscontroller.i2c"></a>
##Device.BusController.I2C

*这些要求仅适用于 I2C 控制器芯片供应商。系统制造商可能会有选择地运行这些测试，但可能需要硬件自定义。*

### <a name="devicebuscontrolleri2ccancellationofio"></a>Device.BusController.I2C.CancellationOfIO

*I2C 控制器，控制器驱动程序必须支持输入/输出请求的取消。*

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

I2C 控制器关联的控制器驱动程序必须符合 SPB 框架和支持以下︰

-   驱动程序实现 SPB 读/写序列 I/O 请求取消逻辑。

### <a name="devicebuscontrolleri2cclockstretching"></a>Device.BusController.I2C.ClockStretching

*I2C 控制器，控制器驱动程序必须支持外围时钟拉伸。*

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

I2C 控制器关联的控制器驱动程序必须符合 SPB 框架和支持以下︰

-   控制器可以维持至少 2 秒钟读、 写和顺序 I/O 期间外围控股时钟。

### <a name="devicebuscontrolleri2chcktestability"></a>Device.BusController.I2C.HCKTestability

*系统具有 I2C 控制器必须公开正确 ACPI 表信息和 I2C 引脚启用 HCK 可测试性。*

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

这一要求的目的是使控制器为可测试 HCK 框架。

详细信息︰

-   测试控制器必须提供 I2C 外部连接针脚 （SCL，SDA 和 GND）。

-   更新 ACPI 正确描述 HCK 测试外围设备驱动程序和与受测 I2C 控制器的连接。

-   当运行 HCK 测试时，必须禁用相同的 I2C 控制器测试其他外围设备。

### <a name="devicebuscontrolleri2cidlepowermanagement"></a>Device.BusController.I2C.IdlePowerManagement

*I2C 控制器，控制器驱动程序必须支持空闲电源管理。*

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

I2C 控制器关联的控制器驱动程序必须符合 SPB 框架和支持以下︰

-   当多个屏幕时在 1 秒钟的空闲时间，控制器应该转到 D3 状态。

-   控制器应该转到 D3 状态后空闲超过 100 毫秒屏幕时是关闭的。

-   控制器采用少于 75 毫秒 (50 + 25 到时间的计时器精度的帐户) 从 D3 状态恢复为 D0 状态。

### <a name="devicebuscontrolleri2clockunlockioctl"></a>Device.BusController.I2C.LockUnlockIOCTL

*I2C 控制器，控制器驱动程序必须支持锁定/解锁 IOCTL。*

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

如果支持停止条件，则必须符合 SPB 框架和支持以下的 I2C 控制器和关联的控制器驱动程序︰

-   支持任意数量的内部锁定/取消锁定对读/写操作。

-   取消锁定调用时生成的启动条件的锁定/解锁序列中的第一个 I/O、 后续 I/O，重新启动条件和停止条件。

### <a name="devicebuscontrolleri2cnack"></a>Device.BusController.I2C.NACK

*I2C 控制器，控制器驱动程序必须支持外围 NACK。*

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

I2C 控制器关联的控制器驱动程序必须符合 SPB 框架和支持以下︰

-   控制器可以检测地址 NACK 总线条件并返回状态\_NO\_SUCH\_请求的设备。

-   控制器可以在写入操作期间检测到设备 NACK，完成状态请求\_成功，并且信息字节设置为小于用途已被写入的字节数。

-   控制器可以写操作的序列 IOCTL 时检测设备 NACK，完成状态请求\_成功，并且信息字节设置为小于什么意要写入的字节数。

### <a name="devicebuscontrolleri2cspbread"></a>Device.BusController.I2C.SPBRead

*I2C 控制器，控制器驱动程序必须正确支持 SPB 读操作。*

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

I2C 控制器和关联的控制器驱动程序必须符合 SPB 框架和支持下，从 I2C 外围设备中读取数据时︰

-   必须支持读取标准 (100 Kbps)、 快 (400 kbps) 和快速 (1 Mbps) 加外围的目标。 高速度 (3.4 MHz) 是可选的但必须通过 I2C 所有 HCK 要求，如果实现 I2C 控制器和控制器驱动程序。

-   必须支持读取大小从 1 到 4096 字节 （4 千字节）。

-   大于 4 千字节的大小必须成功或失败，此时状态\_不\_支持。

-   SPB 读映射到开始日期、 读取数据、 NACK 和停止 I2C 条件。

-   失败的读取请求状态的任何受支持的数据大小\_无效\_参数，会导致总线的任何活动。

### <a name="devicebuscontrolleri2cspbsequenceioctl"></a>Device.BusController.I2C.SPBSequenceIOCTL

*I2C 控制器，控制器驱动程序必须正确支持 SPB 序列 IOCTL。*

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

I2C 控制器关联的控制器驱动程序必须符合 SPB 框架和支持以下︰

-   支持任何任意的 I/O 序列︰ 读写、 读写写入时，读取读取和复杂组合如读的读-写-写入时

-   SPB IOCTL 序列映射到开始，I/O 序列 1、 Restart...I/O 序列 N、 停止 I2C 条件。

-   控制器需要检查顺序，并确定它是否支持或失败，此时状态\_无效\_在前导致总线的任何活动。

-   支持任何有效的参数 (例如，DelayInUs) 和内存格式 （简单、 MDL、 缓冲区列表等） 按照 SPB 的定义。

### <a name="devicebuscontrolleri2cspbwrite"></a>Device.BusController.I2C.SPBWrite

*I2C 控制器，控制器驱动程序必须正确支持 SPB 写入操作。*

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

I2C 控制器和关联的控制器驱动程序必须符合 SPB 框架并写入 I2C 外设时支持以下︰

-   必须支持写入标准 (100 Kbps)、 快 (400 kbps) 和快速 (1 Mbps) 加外围的目标。 高速度 (3.4 MHz) 是可选的但必须通过 I2C 所有 HCK 要求，如果实现 I2C 控制器和控制器驱动程序。

-   必须支持编写大小从 1 到 4096 字节 （4 千字节）。

-   大于 4 千字节的大小必须成功或失败，此时状态\_不\_支持。

-   SPB 写映射到开始、 写入数据和停止 I2C 条件。

-   故障状态的任何受支持的数据大小写请求\_无效\_参数，会导致总线的任何活动。

### <a name="devicebuscontrolleri2cstress"></a>Device.BusController.I2C.Stress

*I2C 控制器，控制器驱动程序必须正常运行，并从总线挂起或在长时间的压力情况下的故障恢复。*

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

I2C 控制器关联的控制器驱动程序必须符合 SPB 框架和支持以下︰

-   支持总线恢复外围挂起 （监视程序机制）。

-   保持 1 小时以上的多个目标的压力。
