---
title: Device.Input.Digitizer
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 8e01ce2454bd09b575ddabdffa44b74bde6c2c34
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceinputdigitizer"></a>Device.Input.Digitizer
 
 - [Device.Input.Digitizer.Base](#device.input.digitizer.base)
 - [Device.Input.Digitizer.Pen](#device.input.digitizer.pen)
 - [Device.Input.Digitizer.PrecisionTouchpad](#device.input.digitizer.precisiontouchpad)

<a name="device.input.digitizer.base"></a>
## <a name="deviceinputdigitizerbase"></a>Device.Input.Digitizer.Base

### <a name="deviceinputdigitizerbasecontactreports"></a>Device.Input.Digitizer.Base.ContactReports

*数字化仪的可靠性*

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

这一要求以前称为**Device.Digitizer.Touch.NoiseSupression**。

数字化器应仅对应于用户输入的报告数据。 应不报告任何其他数据，通常称为"幻像"或"虚影联系人"。 这适用于这两系统积极接收用户输入和当它不接收用户输入，在交流和直流电源条件下 （如果适用）。

### <a name="deviceinputdigitizerbasehidcompliant"></a>Device.Input.Digitizer.Base.HIDCompliant

*符合标准的 HID 的设备的固件和/或 HID 微型端口驱动程序*

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

这一要求以前称为**设备。Digitizer.Touch.HIDCompliantFirmware**

所有数字化仪所需是人体学接口设备 (HID) 符合并遵守到报表的窗口输入顺序及其各自的用法的规范。

请在使用收件箱 HID 微型端口驱动程序与 3<sup>研发</sup>方 HID 微型端口驱动程序，参阅 Device.Input.Digitizer.Base.ThirdPartyDrivers 的其他信息。

有关实施的详细信息，请参阅︰

报告要求，请参阅在[*http://msdn.microsoft.com/en-us/library/windows/hardware/jj151569.aspx*的主题的集合](http://msdn.microsoft.com/en-us/library/windows/hardware/jj151569.aspx)

通过 I2C 要求 HID，请参阅[*http://msdn.microsoft.com/en-us/library/windows/hardware/Dn642101.aspx*](http://msdn.microsoft.com/en-us/library/windows/hardware/Dn642101.aspx)

通过 USB 要求 HID，请参阅[*http://www.usb.org/developers/devclass\_文档/HID1\_11.pdf*](http://www.usb.org/developers/devclass_docs/HID1_11.pdf)

Bluetooth 要求对 HID，请参阅[*http://developer.bluetooth.org/TechnologyOverview/Documents/HID\_SPEC.pdf*](http://developer.bluetooth.org/TechnologyOverview/Documents/HID_SPEC.pdf)

**业务理由**

人体学接口设备 (HID) 协议是业界公认标准，Microsoft 还要求输入设备。 这一要求保证 Windows 兼容性和可维护性与任何符合标准的数字化解决方案。

### <a name="deviceinputdigitizerbasethirdpartydrivers"></a>Device.Input.Digitizer.Base.ThirdPartyDrivers

*服务和 3<sup>研发</sup>方驱动程序可用性*

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

*适用性:"Windows 桌面"*

如果 Windows 精度触摸板数字化仪利用第三方 HID 微型端口驱动程序，则应为 OEM 传送图像 （和还原图像） 的一部分，Windows Update 上可用。 任何第三方 HID 微型端口驱动程序还应在 WinPE 正常工作。 强烈建议收件箱 HID 微型端口驱动程序利用尽可能实现 Windows 精度触摸板。

特别注意︰ 触摸板可能不推广作为 Windows 精度触摸板除非符合所有适用的兼容性要求。

所有集成 Windows 触摸屏和笔设备应齐全而不使用的任何第三方 HID 微型端口或筛选器驱动程序提供有关联的总线，用于连接。 虽然 Windows 建议随着测试装运设备，OEM 可以选择交付 Windows 10 兼容 HID 微型端口驱动程序，和/或设备已满足所有后提供附加功能的筛选器驱动程序相关联的 HLK 要求包括**Device.Input.Digitizer.Base.ThirdPartyDrivers** ，安装该驱动程序时如果满足所有其他要求。 任何 3<sup>研发</sup>方 HID 微型端口驱动程序在收件箱驱动程序不可用于所选连接，总线实例中使用该驱动程序应为 OEM 传送图像 （和还原图像） 的一部分，Windows Update 上可用。 任何第三方 HID 微型端口驱动程序还应在 WinPE 正常工作。

*适用性:"Windows Mobile"*

如果 Windows 精度触摸板、 集成的触摸或集成的笔数字化器利用第三方 HID 微型端口驱动程序，则应为部分系统 OEM 基支持包 (BSP)。 强烈建议尽可能，使用的收件箱的 HID 微型端口驱动程序。

**业务理由**

这一要求保证数字化器始终是可用的用户输入，而不考虑服务方案和/或干净安装。 在数字化仪可能对某个给定设备的输入的唯一来源的情况

<a name="device.input.digitizer.pen"></a>
## <a name="deviceinputdigitizerpen"></a>Device.Input.Digitizer.Pen

### <a name="deviceinputdigitizerpenaccuracy"></a>Device.Input.Digitizer.Pen.Accuracy

*笔联系准确性*

|                |                            |
|----------------|----------------------------|
| 目标功能 | Device.Input.Digitizer.Pen |

**说明**

与这一要求已合并 Device.Digitizer.Pen.HoverAccuracy 的要求。

当笔尖接触屏幕时，应联系的实际位置和设备的报告之间的增量︰

-   &lt;= 0.5 毫米 （中心） +/-

-   &lt;1 毫米 （内的所有边缘的 3.5 毫米） +/-=

当将鼠标指针悬停 （与提示不在联系人中），物理增量之间的物理位置和什么设备报告应为&lt;+/-1 毫米 （中心） =。

**业务理由**

这一要求保证兼容的 DirectInk 和收件箱笔经验;具体来说︰

-   当笔在联系人屏幕，确保墨迹似乎源于笔尖，并确保对目标小控件的能力。

-   当触笔悬停在屏幕中，确保该光标所在的位置，所以我们认为须准确用户

### <a name="deviceinputdigitizerpenbuffering"></a>Device.Input.Digitizer.Pen.Buffering

*对于总线缓冲，高恢复延迟*

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

这是一项"如果实现"的要求。 活动笔的解决方案，如果某条总线上使用高恢复延迟，如 USB 与选择性挂起或 Bluetooth 应实现能处理输入的报告缓冲区&gt;= 100 毫秒的数据。

输入报告缓冲区的大小 （以字节为单位） = 输入报表大小&times;（100 ms/最大值报告率）

虽然这是以高恢复延迟使用总线的设备的要求，建议使用其他总线的解决方案还实现输入的报告缓冲，避免可能发生的中断处理难题。

**业务理由**

由于主控制器或总线从低功耗状态的恢复时间，设备可能需要实现缓冲，以确保在电源转换过程不丢失任何用户交互数据。

### <a name="deviceinputdigitizerpencontactreports"></a>Device.Input.Digitizer.Pen.ContactReports

*数字化仪的可靠性*

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

这一要求以前称为**Device.Digitizer.Touch.NoiseSupression**

数字化器应仅对应于用户输入的报告数据。 应不报告任何其他数据，通常称为"幻像"或"虚影联系人"。 这适用于这两系统积极接收用户输入和当它不接收用户输入，在交流和直流电源条件下 （如果适用）。

### <a name="deviceinputdigitizerpencustomgestures"></a>Device.Input.Digitizer.Pen.CustomGestures

*自定义运行时系统笔势*

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

无论报告实施，除了唤醒笔势禁止附加自定义运行时笔的笔势。

**业务理由**

这一要求保证与 DirectInk 兼容性。

-   确保没有干扰墨迹书写体验的核心。

-   确保使用收件箱的笔势引擎的兼容性。

### <a name="deviceinputdigitizerpeneraser"></a>Device.Input.Digitizer.Pen.Eraser

*橡皮擦功能可见性︰*

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

集成的 Windows 笔解决方案应有硬件一笔橡皮擦功能符合要求提供的相关协议。 默认情况下，必须启用擦除功能。

Microsoft 将允许活动直到 2016 年 1 月 01，支持单个圆柱式按钮的笔异常︰ 

Microsoft 强烈建议所有笔默认都支持擦除功能。  包含单个的笔杆按钮支持集成的 Windows 笔解决方案将允许不直到 2016 年 1 月 1，橡皮擦功能可见性︰ 发行。  在 2016 年 1 月 1，集成的 Windows 笔解决方案应有硬件一笔橡皮擦功能符合要求提供相关协议和擦除功能必须启用默认情况下。

**业务理由**

此要求确保与笔交互操作直观、 高效。 此实现使软件开发人员能够同时使用橡皮擦实现剩余不可知的橡皮擦功能开发。

注意︰ 启用橡皮擦功能的活动笔提供擦除数字墨水最自然的方法。  启用橡皮擦功能的活动笔还释放应用程序开发人员不必开发 UI 笔的墨迹模式的上下文切换，擦除模式。  因此强烈建议所有笔都支持擦除功能默认情况下。

### <a name="deviceinputdigitizerpenhidcompliant"></a>Device.Input.Digitizer.Pen.HIDCompliant

*HID 标准的设备的固件和/或 HID 微型端口驱动程序*

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

请参阅 Device.Input.Digitizer.Base.HIDCompliant。

### <a name="deviceinputdigitizerpenhoverrange"></a>Device.Input.Digitizer.Pen.HoverRange

*悬停范围*

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

这一要求以前称为 Device.Digitizer.Pen.PenRange

笔数字化器应报告的笔位置，并是*在范围*开始时笔尖为至少 5 毫米远离屏幕。

**业务理由**

这一要求保证兼容性与 DirectInk 以及更具体地说︰

-   确保用户收到屏幕上笔位置和工具上下文的及时的反馈。

-   确保与 Windows palm 拒绝功能的兼容性。

### <a name="deviceinputdigitizerpenjitter"></a>Device.Input.Digitizer.Pen.Jitter

*抖动和线性*

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

从集成的 Windows 笔报告的抖动应为︰

-   移动抖动

    -   &lt;= +/-0.4 毫米 （中心）

    -   &lt;= +/-0.6 毫米 （内的所有边缘的 3.5 毫米）

-   静止的抖动

    -   &lt;= +/-0.3 毫米 （中心）

    -   &lt;= +/-0.5 毫米 （内的所有边缘的 3.5 毫米）

-   将鼠标指针悬停原地抖动&lt;= +/-0.5 毫米 （中心）

**业务理由**

这一要求保证兼容性与 DirectInk 以及更具体地说︰

-   当笔尖接触屏幕是和移动墨迹准确地反映实际笔画的用户

-   笔还保持静止状态 （在与屏幕或鼠标悬停时），并不感觉到用户抖动。

### <a name="deviceinputdigitizerpenlatency"></a>Device.Input.Digitizer.Pen.Latency

*响应延迟*

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

笔数字化器应具有每个以下的响应延迟时间︰

-   冷启动延迟

    -   集成的 Windows 笔应立即响应，一旦显示处于活动状态

    -   冷启动被指时间段的起始应用程序的能力到控制器，控制器准备接受 HID 命令之前

-   向下滞后时间 （空闲） &lt;= 150ms年 （如果实现）

    -   这一要求是适用如果空闲状态电源状态已经实现

    -   向下延迟 （空闲） 定义为在笔使初次接触屏幕时设备处于空闲状态电源状态和具有相关联的报表传送到主机之间的延迟。

-   向下延迟 （活动） &lt;= 35ms （中心）

    -   向下延迟 （活动） 指在笔使初次接触屏幕设备时处于活动状态的电源状态和具有相关联的报表传送到主机之间的延迟。

-   移动延迟&lt;= 30ms （中心）

    -   在运动 （以及接触屏幕） 钢笔尖时，移动滞后时间指物理位置并无关联的笔之间的延迟报告传送到主机

**业务理由**

这一要求保证︰

-   系统电源状态转换后，设备是随时可供用户交互。

-   当笔初始接触屏幕，视觉反馈中的延迟不是感觉大多数用户。

-   笔时接触屏幕和移动、 端到端延迟的墨迹和其他交互不是感觉大多数用户。

### <a name="deviceinputdigitizerpenpressure"></a>Device.Input.Digitizer.Pen.Pressure

*报告的压力*

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

应报告笔数字化器&gt;= 256 级的压力。

应使用对数曲线来报告笔尖上的作用力。 当笔尖接触屏幕，激活力超过了设备应设置报告接头开关。 集成的 Windows 笔最大激活力是&lt;= 20 g。

（对于 256 级的设备） 的理想压力曲线所示图 1 中，但相关的 HLK 测试可确保设备报告的上界和下界所定义范围内的压力。 有更多的压力级别的设备，应应用但缩放到逻辑上报告的级别数的相同的曲线。

**图 1-报告曲线具有 256 压力级别的设备的理想压力**
![非常适合压力报告曲线具有 256 压力级别的设备](images/ideal-pressure-reporting-curve.png)



**业务理由**

这一要求保证兼容性与 DirectInk 以及更具体地说︰

-   保证足够的粒度和表示形式的应用压力变化与墨迹书写时由用户察觉到。

### <a name="deviceinputdigitizerpenreportrate"></a>Device.Input.Digitizer.Pen.ReportRate

*报告频率*

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

这一要求以前称为 Device.Digitizer.Pen.100HzSampleRate

集成的 Windows 笔数字化器应有报告率&gt;= 133 赫兹。

**业务理由**

这一要求保证兼容性与 DirectInk 以及更具体地说︰

-   确保足够的点进行采样来表示在典型的手写速度准确地手写。

### <a name="deviceinputdigitizerpenresolution"></a>Device.Input.Digitizer.Pen.Resolution

*输入的分辨率*

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

这一要求以前称为 Device.Digitizer.Pen.PenResolution

笔数字化器的输入分辨率应为&gt;= 本机显示分辨率或 150 dpi （取较大）。

**业务理由**

这一要求保证了每个像素可以在屏幕上墨迹，并提供了平滑笔经验。

### <a name="deviceinputdigitizerpenthirdpartydrivers"></a>Device.Input.Digitizer.Pen.ThirdPartyDrivers

*服务和 3<sup>研发</sup>方驱动程序可用性*

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

请参阅 Device.Input.Digitizer.Base.ThirdPartyDrivers。

<a name="device.input.digitizer.precisiontouchpad"></a>
## <a name="deviceinputdigitizerprecisiontouchpad"></a>Device.Input.Digitizer.PrecisionTouchpad

### <a name="deviceinputdigitizerprecisiontouchpadaccuracy"></a>Device.Input.Digitizer.PrecisionTouchpad.Accuracy

*准确性*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 精度触摸板应报告绝对数字化器位置&lt;= 2 毫米，从所有联系人的实际位置。

**业务理由**

要求保证精确的 moussing 和 gesturing 的表面。

### <a name="deviceinputdigitizerprecisiontouchpadbuffering"></a>Device.Input.Digitizer.PrecisionTouchpad.Buffering

*对于总线缓冲，高恢复延迟。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这是一项"如果实现"的要求。 USB 或 Bluetooth 连接 Windows 精度触摸板应实现能处理输入的报告缓冲区&gt;= 100 毫秒的数据基于联系人输入报告缓冲区的大小 （以字节为单位） 的设备所支持的最大数量︰

= 最大\#的支持联系人&times;输入报表大小&times;（100 ms/最大值报告率）

而这一要求适用于 USB 和 Bluetooth 设备，建议其他设备也实现输入的报告缓冲，避免可能发生的中断处理难题。

**业务理由**

由于主控制器或总线从低功耗状态的恢复时间，设备可能需要实现缓冲，以确保在电源转换过程不丢失任何用户交互数据。

### <a name="deviceinputdigitizerprecisiontouchpadbuttons"></a>Device.Input.Digitizer.PrecisionTouchpad.Buttons

*物理按钮和按钮报告*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

已经合并到此要求的以下要求︰

-   Device.Input.PrecisionTouchpad.Hardware.ClickpadPress
-   Device.Input.PrecisionTouchpad.Hardware.PressurePadPress

如果 Windows 精度触摸实现外部按钮，而不是 clickpads 或 pressurepads，必须至少两个按钮来表示左和右击按钮。

如果有多个按钮，按钮应被视为一个按钮标志数组。 处理超过前两个按钮 （主和次点击） 应该是驱动程序和/或鼠标集合的角色。

（如果实现） – 同时基于 clickpad 的和非基于 clickpad 的 Windows 精度触摸板应报告按钮关闭状态时所施加的压力超过 150 g-180 g。  这被测试在 140 g-190 g 容许制造差异。

**业务理由**

可点击区域应该可以方便地使用。

如果实现了外部按钮，必须至少两个硬件按钮来表示这两个左和右击以确保设备上有完整的鼠标功能。

### <a name="deviceinputdigitizerprecisiontouchpadcontactreports"></a>Device.Input.Digitizer.PrecisionTouchpad.ContactReports

*数字化仪的可靠性*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为**Device.Digitizer.Touch.NoiseSupression**

数字化器应仅对应于用户输入的报告数据。 应不报告任何其他数据，通常称为"幻像"或"虚影联系人"。 这适用于这两系统积极接收用户输入和当它不接收用户输入，在交流和直流电源条件下 （如果适用）。

### <a name="deviceinputdigitizerprecisiontouchpadcontacttipswitchheight"></a>Device.Input.Digitizer.PrecisionTouchpad.ContactTipSwitchHeight

*联系人提示开关高度*

Windows 精度触摸不应报告联系人&gt;数字化曲面上方 0.5 毫米。

**业务理由**

防止意外发生的联系人激活并有助于避免在键入过程中调用的掌上激活。

### <a name="deviceinputdigitizerprecisiontouchpaddevicetypereporting"></a>Device.Input.Digitizer.PrecisionTouchpad.DeviceTypeReporting

*设备类型*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

按钮是否出现在数字化仪下 Windows 精度触摸必须通过 HID 特征报告报告其设备按钮类型 （例如，压力板，单击键盘）。  没有可单击的数字化器设备必须公开此功能报告。

有关实施的详细信息，请参阅[http://msdn.microsoft.com/en-us/library/windows/hardware/jj126202.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/jj126202%28v=vs.85%29.aspx)*.* 

**业务理由**

基本以确保正确的按钮处理由操作系统执行。

### <a name="deviceinputdigitizerprecisiontouchpaddimensions"></a>Device.Input.Digitizer.PrecisionTouchpad.Dimensions

*尺寸*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

已经用这个合并的要求**Device.Input.PrecisionTouchpad.Hardware.Length**和**Device.Input.PrecisionTouchpad.Hardware.Height** 。

Windows 精度触摸板应为&gt;= 长度 （触摸板的横向度量值） 64 毫米 x &gt;= 32 毫米 （垂直度量单位）。

**业务理由**

精度触摸必须维护的最小大小，以允许用户跨远距离 moussing 和执行多手指手势正确交互。

### <a name="deviceinputdigitizerprecisiontouchpadfingerseparation"></a>Device.Input.Digitizer.PrecisionTouchpad.FingerSeparation

*手指分离*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为 Device.Input.PrecisionTouchpad.Performance.MinSeparation。

Windows 精度触摸板应别名不对齐的 8 毫米或更少的边缘到边缘的最小隔离两个联系人。

**业务理由**

这一要求保证手指计数和位置都能保持在多手指交互过程。

### <a name="deviceinputdigitizerprecisiontouchpadhidcompliant"></a>Device.Input.Digitizer.PrecisionTouchpad.HIDCompliant

*HID 标准的设备的固件和/或 HID 微型端口驱动程序*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

请参阅 Device.Input.Digitizer.Base.HIDCompliant。

### <a name="deviceinputdigitizerprecisiontouchpadinputresolution"></a>Device.Input.Digitizer.PrecisionTouchpad.InputResolution

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 精度触摸板应报告逻辑的最大值，x 成线性正比于触摸板的宽度，并应报告逻辑 y 触摸板的长度成线性比例最多。 触摸板的左上的角应为原点 (0，0)。 所有 Windows 精度触摸板都是至少 300 dpi。因此，对最小大小 Windows 中的精度触摸板的逻辑 x 最大值应&gt;= 767 和逻辑的最大的应 y &gt;= 384。

**业务理由**

这一要求保证了用户可以执行精确的操作和游标定位。

### <a name="deviceinputdigitizerprecisiontouchpadjitter"></a>Device.Input.Digitizer.PrecisionTouchpad.Jitter

*抖动和线性*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Device.Input.Digitizer.PrecisionTouchpad.Linearity 的要求已经合并到此要求。

一个联系人

-   数字化曲面上单固定精度联系人时，Windows 精度触摸不应报告任何抖动。

多个联系人

-   Windows 精度触摸板应报告具有联系人&lt;= 2 毫米的抖动、 数字化器表面上最初放置多个固定的联系人但是联系人在移动并再次变得静止后允许无固定的抖动。

任意数量的联系人

-   Windows 精度触摸板应保持在水平、 垂直和对角线方向跨边缘到边缘差旅报告的所有联系人的 0.5 毫米的线性。

-   内的任一边缘的 3.5 毫米，精度触摸板应保持线性内报告的所有联系人的 1.5 毫米。

-   Windows 精度触摸不应报告任何向后的运动抖动，运动中的联系人。 向抖动被定义为相反方向的联系旅行社联系位置的后续报告。

**业务理由**

确保精度 moussing 和笔势正常工作，并且，在 gesturing 期间暂停不会产生抖动的视觉效果。

### <a name="deviceinputdigitizerprecisiontouchpadlatency"></a>Device.Input.Digitizer.PrecisionTouchpad.Latency

*响应延迟*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

已经合并到此要求的以下要求︰

-   Device.Input.PrecisionTouchpad.Performance.ActiveTouchdownLatency

-   Device.Input.PrecisionTouchpad.Performance.IdleTouchdownLatency

-   Device.Input.PrecisionTouchpad.Performance.PanLatency

触摸下压延迟︰

-   活动︰

    -   Windows 精度触摸应有&lt;= 35 毫秒触摸下压延迟处于活动状态。 触摸下压延迟被指与数字化仪接触和主机接收后续输入的报告之间的时间。

-   空闲︰

    -   Windows 精度触摸应有&lt;= 150 毫秒触摸下压延迟处于空闲状态。

    -   触摸下压延迟被指与数字化仪接触和主机接收后续输入的报告之间的时间。

移动滞后时间︰

-    Windows 精度触摸平移延迟应有&lt;= 70 毫秒。 平移延迟定义为在数字化仪上的移动和接收主机的后续更改之间的时间段。

冷启动延迟︰

-    一旦显示活动正在形成的冷启动的系统上，Windows 精度触摸板应立即响应。 在控制器准备接受 HID 命令之前，冷启动被指到控制器的期间从应用程序的能力。

**业务理由**

此要求确保核心用户体验涉及分路器，moussing，和 gesturing 仍是性能 （即点击按钮、 控件、 超链接等。）。

触摸板设备应随时可供用户输入系统已启动或从低功耗状态，而不考虑其总线连接恢复之后。

平移间接输入设备的延迟的影响上的其他用户体验研究论证比较，以直接输入的设备的平移延迟增加。

### <a name="deviceinputdigitizerprecisiontouchpadminmaxcontacts"></a>Device.Input.Digitizer.PrecisionTouchpad.MinMaxContacts

*联系人计数*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 精度触摸不应报告能够超过 5 特有的联系人的最大支持。 Windows 精度触摸板应报告是能够 （并能胜任） 支持最少的 3 的唯一联系人。

**业务理由**

触摸板的精度要求至少三个手指，以有权访问所有窗口交互。 广泛的可用的交互支持四个或更多的抓手。 Multihand 交互是不适合用于触摸板，因此多 5 联系人支持是不需要的。

### <a name="deviceinputdigitizerprecisiontouchpadreportrate"></a>Device.Input.Digitizer.PrecisionTouchpad.ReportRate

*报告率*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为 Device.Input.PrecisionTouchpad.Performance.ReportRate。

Windows 精度触摸板应报告在&gt;= 125 赫兹 （和不超过 250 赫兹） 当一个联系人位于数字化仪上。 Windows 精度触摸板应报告的所有联系人&gt;= 显示刷新率 + 10 赫兹 （达 125 赫兹） 数字化仪上时多个联系人。

**业务理由**

保持鼠标体验需求和竞争对手产品的性能，在&gt;= 125 赫兹。 笔势性能串联接触要求的后盾直接操作的体验需求，以避免抖动。

### <a name="deviceinputdigitizerprecisiontouchpadselectivereporting"></a>Device.Input.Digitizer.PrecisionTouchpad.SelectiveReporting

*选择报告*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 精度触摸板应支持通过 HID 特征报告主机请求，有选择性地报告数字化器联系人并按下按钮。 请求主机接收报告或者数字化器联系人或按下按钮，或都不可能。 Windows 精度触摸板应优化基于主机的选择及其能源消耗。

**业务理由**

这一要求保证精度触摸板的数字化器正确响应用户配置请求启用/禁用该设备。

### <a name="deviceinputdigitizerprecisiontouchpadthirdpartydrivers"></a>Device.Input.Digitizer.PrecisionTouchpad.ThirdPartyDrivers

*服务和 3<sup>研发</sup>方驱动程序可用性*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

请参阅 Device.Input.Digitizer.Base.ThirdPartyDrivers。

 # <a name="deviceinputdigitizertouch"></a>Device.Input.Digitizer.Touch

### <a name="deviceinputdigitizertouchaccuracy"></a>Device.Input.Digitizer.Touch.Accuracy

*准确性*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

**说明**

这一要求以前称为 Device.Digitizer.Touch.PhysicalInputPosition

触控数字化器应报告以下补助中的所有联系人的位置︰

-   &lt;当联系人位置大于从数字化仪上缘的 3.5 毫米 1 毫米 +/-=

-   &lt;当联系人的位置是在数字化器边的 3.5 毫米内 2 毫米 +/-=

**业务理由**

这一要求保证准确和可靠的触摸交互。

### <a name="deviceinputdigitizertouchbuffering"></a>Device.Input.Digitizer.Touch.Buffering

*对于总线缓冲，高恢复延迟*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这是一项"如果实现"的要求。 一个 Windows 触摸屏通过 USB 连接的解决方案或 Bluetooth 应实现能处理输入的报告缓冲区&gt;= 100 毫秒的基于联系人设备支持的最大数量的数据

输入 （对于单个手指混合报告） 报告缓冲区的大小 （以字节为单位）: = 最大值\#的联系人支持&times;输入报表大小&times;（100 ms/最大值报告率）

虽然这是以高恢复延迟使用总线的设备的要求，建议使用其他总线的解决方案还实现输入的报告缓冲，避免可能发生的中断处理难题。

**业务理由**

由于主控制器或总线从低功耗状态的恢复时间，设备可能需要实现缓冲，以确保在电源转换过程不丢失任何用户交互数据。

### <a name="deviceinputdigitizertouchcontactreports"></a>Device.Input.Digitizer.Touch.ContactReports

*数字化仪的可靠性*

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

这一要求以前称为**Device.Digitizer.Touch.NoiseSupression**

数字化器应仅对应于用户输入的报告数据。 应不报告任何其他数据，通常称为"幻像"或"虚影联系人"。 这适用于这两系统积极接收用户输入和当它不接收用户输入，在交流和直流电源条件下 （如果适用）。

### <a name="deviceinputdigitizertouchcustomgestures"></a>Device.Input.Digitizer.Touch.CustomGestures

*自定义运行时系统笔势*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

允许仅旨在唤醒系统笔势。 设计用户界面元素所使用的自定义笔势被禁止。

**业务理由**

这一要求保证了平台的所有 Windows 设备的维护更一致和可靠的笔势的体验。

### <a name="deviceinputdigitizertouchfingerseparation"></a>Device.Input.Digitizer.Touch.FingerSeparation

*手指分离*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为 Device.Digitizer.Touch.InputSeparation

所有联系人应唯一跟踪并且报告时&lt;= 8 毫米距离边缘到边缘的距离。

**业务理由**

这一要求保证使用 pinch/缩放，多手指分路器，如收件箱笔势的兼容性和并行的手指操作可以可靠地执行。

### <a name="deviceinputdigitizertouchhidcompliant"></a>Device.Input.Digitizer.Touch.HIDCompliant

*HID 标准的设备的固件和/或 HID 微型端口驱动程序*

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

请参阅 Device.Input.Digitizer.Base.HIDCompliant。

### <a name="deviceinputdigitizertouchjitter"></a>Device.Input.Digitizer.Touch.Jitter

*抖动和线性*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为 Device.Digitizer.Touch.DigitizerJitter

静止的抖动不应超过最大&lt;= 0.5 毫米，边缘 +/-和&lt;= +/-内边的 3.5 毫米 1 毫米

移动抖动不应超过最大&lt;= 1 毫米，边缘 +/-和&lt;= +/-2 毫米内边的 3.5 毫米

抖动不允许非文具联系人联系旅行社任何方向相反。

**业务理由**

这一要求保证与收件箱笔势、 操作和墨迹书写的兼容性和更具体地讲:

-   点击小控件的交互使用

-   当操作之后保持静止状态，内容应不抖动。

-   自由格式平移操作用户预期的方向中的内容

-   墨迹书写手指绘画/看上去可接受

### <a name="deviceinputdigitizertouchlatency"></a>Device.Input.Digitizer.Touch.Latency

*响应延迟*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为 Device.Digitizer.Touch.ResponseLatency

触控数字化器应具有响应延迟，如下所示︰

<html>
    <ul>
        <li>
            <p>向下延迟 （活动）&lt;= 35ms年</p>
            <ul>
                <li><p>下压延迟的活动被定义为与数字化仪接触由主机接收后续输入的报告之间的时间段。</p></li>
            </ul>
        </li>
        <li>
            <p>向下滞后时间 （空闲） &lt;= 150ms年</p>
            <ul>
                <li><p>空闲状态下压延迟定义为与数字化仪接触数字化仪连接待机时，主机正在接收后续输入的报告之间的时间段。</p></li>
            </ul>
        </li>
        <li><p>移动滞后时间</p>
            <table>
                <thead>
                    <tr class="header">
                        <th>屏幕尺寸 （对角线）</th>
                        <th>最大延迟</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="odd">
                        <td>&lt;7"</td>
                        <td>&lt;= 35ms</td>
                    </tr>
                    <tr class="even">
                        <td>&gt;= 7"</td>
                        <td>&lt;= 25ms</td>
                    </tr>
                </tbody>
            </table>
        </li>

        <li><p>Move latency is defined as the period between a contact being at a physical position and having that position reported to the host.</p></li>

        <li>
            <p>Cold Boot Latency -</p>
            <ul>
                <li><p>Touch digitizers shall be immediately responsive once the display is active.  Cold boot is defined as the period from application of power to the controller until the controller is ready to accept HID commands.</p></li>
            </ul>
        </li>
    </ul>
    <p><strong>Business Justification</strong></p>
    <p>This requirement ensures the following:</p>
    <ul>
        <li><p>Content sticks close to the physical finger position when under manipulation.</p></li>
        <li><p>Devices are readily available for user interactions after a system power state transition.</p></li>
        <li><p>User interactions involving a tap are responsive even when in a low power state.</p></li>
    </ul>
</html>

### <a name="deviceinputdigitizertouchmincontactcount"></a>Device.Input.Digitizer.Touch.MinContactCount

*最小的同时可报告联系人*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为**Device.Digitizer.Touch.5TouchPointMinimum**。

触控数字化器必须支持至少五个同时触摸触点。

**业务理由**

这一要求保证与收件箱笔势、 辅助工具和第三方应用程序的兼容性。

### <a name="deviceinputdigitizertouchreportrate"></a>Device.Input.Digitizer.Touch.ReportRate

*报告频率*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求以前称为 Device.Digitizer.Touch.ReportingRate

在当前电源状态，触控数字化器报告率应保持显示刷新速率的最小和最大 250 赫兹。 所有的报告应唯一采样。

例如︰

| 显示刷新率 | 触摸屏输入报告率 |
|----------------------|----------------------|
| 60 Hz                 | &gt;= 60 Hz           |
| 120 Hz                | &gt;= 120 Hz          |

**业务理由**

这一要求保证兼容，平滑和无口吃的 gesturing 经验时执行平移和 pinch/缩放交互利用 Windows 直接操作框架。

### <a name="deviceinputdigitizertouchresolution"></a>Device.Input.Digitizer.Touch.Resolution

*输入的分辨率*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

至少，触控数字化器分辨率将是等于本机显示分辨率或更高版本。 集成的触控数字化器中显示的每个像素都需要可触摸屏输入。 每个像素包括像素的边缘和角的显示。
有关验证和测试的这一要求的其他详细信息，请参阅<http://go.microsoft.com/fwlink/?LinkID=234575>

**业务理由**

这一要求保证每个像素可用于触摸交互，并确保可靠和平滑的触控体验。

### <a name="deviceinputdigitizertouchthirdpartydrivers"></a>Device.Input.Digitizer.Touch.ThirdPartyDrivers

*服务和 3<sup>研发</sup>方驱动程序可用性*

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

请参阅 Device.Input.Digitizer.Base.ThirdPartyDrivers。
