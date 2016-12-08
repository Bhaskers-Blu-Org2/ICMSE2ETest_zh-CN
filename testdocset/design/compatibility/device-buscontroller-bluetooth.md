---
title: Device.BusController.Bluetooth
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: ba1aeb4d788cacf839032c3e1131730c897b4e1c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicebuscontrollerbluetooth"></a>Device.BusController.Bluetooth

 - [Device.BusController.Bluetooth.Base](#device.buscontroller.bluetooth.base)
 - [Device.BusController.Bluetooth.NonUSB](#device.buscontroller.bluetooth.nonusb)
 - [Device.BusController.Bluetooth.USB](#device.buscontroller.bluetooth.usb)

<a name="device.buscontroller.bluetooth.base"></a>
## <a name="devicebuscontrollerbluetoothbase"></a>Device.BusController.Bluetooth.Base

### <a name="devicebuscontrollerbluetoothbase4lespecification"></a>Device.BusController.Bluetooth.Base.4LeSpecification

*Bluetooth 控制器必须支持 Bluetooth 4.0 规范要求。*

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

这些要求是客户端系统"如果实现"并应用仅当客户端系统支持 Bluetooth。

*Bluetooth 控制器必须遵守法规遵从性 Bluetooth 版本 4.0 规范中列出的基本速率 (BR) 和低能耗 (LE) 的组合核心配置控制器部分和主机控制器接口 (HCI) 核心配置需求。*

*"Bluetooth 无线电硬件应限定为"控制器子系统"和可以另外限定为"组件"Bluetooth 特别兴趣组通过。*

### <a name="devicebuscontrollerbluetoothbaselestatecombinations"></a>Device.BusController.Bluetooth.Base.LeStateCombinations

*Bluetooth 控制器必须支持最小的一组 LE 状态组合。*

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

Bluetooth 控制器必须允许指标 LE 状态组合 (允许在部分\[音量 6\]部件 B、 Bluetooth 4.0 版规范部分 1.1.1): 只以下的状态并不需要得到支持︰

-   支持的 0x0000000000800000 主动扫描状态和启动状态组合。

-   0x0000000004000000 被动扫描状态，并支持从属角色组合。

-   0x0000000008000000 活动扫描状态，并支持从属角色组合。

### <a name="devicebuscontrollerbluetoothbaselewhitelist"></a>Device.BusController.Bluetooth.Base.LeWhiteList

*Bluetooth 控制器必须支持 LE 白名单最小的 25 项。*

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

Bluetooth 控制器必须支持至少 25 项低能耗 (LE) 的远程设备的白名单中。

### <a name="devicebuscontrollerbluetoothbasemicrosoftbluetoothstack"></a>Device.BusController.Bluetooth.Base.MicrosoftBluetoothStack

*Bluetooth 控制器必须使用 Microsoft 的 Bluetooth 堆栈进行测试。*

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

Bluetooth 控制器硬件认证提交时必须经微软 Bluetooth 堆栈。

### <a name="devicebuscontrollerbluetoothbasehciextensions-if-implemented"></a>Device.BusController.Bluetooth.Base.HCIExtensions （如果实现）

*Microsoft 定义 HCI 的广告和 RSSI 监视硬件卸载的扩展支持。*

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

支持 Microsoft 的无线电收发器定义 Bluetooth HCI 扩展必须符合规范，并通过相关的 HLK 测试。 技术指标的详细信息位于 MSDN。 请参阅下面的链接

[https://msdn.microsoft.com/en-us/library/windows/hardware/dn917903.aspx。](https://msdn.microsoft.com/en-us/library/windows/hardware/dn917903.aspx)

### <a name="devicebuscontrollerbluetoothbasenobluetoothlefilterdriver"></a>Device.BusController.Bluetooth.Base.NoBluetoothLEFilterDriver

*不允许 Bluetooth LE 筛选器驱动程序在 BTHLEENUM 上加载。SYS。*

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

若要确保在整个 Windows 应用商店应用程序使用 Bluetooth LE (GATT) WinRT API 的统一体验，筛选器驱动程序应加载在 BTHLEENUM 上。SYS。

### <a name="devicebuscontrollerbluetoothbaseonoffstatecontrollableviasoftware"></a>Device.BusController.Bluetooth.Base.OnOffStateControllableViaSoftware

*Bluetooth 控制器的开/关状态必须为可以通过软件控制。*

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

Bluetooth 控制器时启用"关闭"无线电、 应断电以其最低支持的电源状态，没有传输/接收应该采取的地方。 Windows 将通过卸载的收件箱协议驱动程序和他们的孩子，提交 HCI 终止 Bluetooth 活动\_重置到控制器中，然后又将控制器设置为 D3 逻辑电源状态时，它允许根据无线电关闭的电源总线驱动程序的命令。 如果总线支持的方法可用来打开无线电，无线电可以被完全关闭。 我们将不支持任何其他供应商的软件控制组件。

在重新打开无线电设备，Windows Bluetooth 堆栈应恢复为 D0，它允许重新启动设备总线驱动程序的设备。 Windows Bluetooth 堆栈应再重新初始化控制器的 Bluetooth 组件。

只应为内部 Bluetooth 4.0 控制器启用 Bluetooth 无线电管理 Windows 8.1 中。

### <a name="devicebuscontrollerbluetoothbasescatternet"></a>Device.BusController.Bluetooth.Base.Scatternet

*Bluetooth 主控制器必须支持 Bluetooth scatternet。*

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

Bluetooth 主控制器必须支持至少两个并发 piconets (也称为 scatternet)。 主控制器也必须能够允许主机加入本地无线电收发器时，piconet 的主机请求连接到现有的 piconet 的设备。 Bluetooth 系统、 2.1 版 + 增强数据速率 (EDR) （基带规范），部分 8.6.6 的规范描述了这一要求。 

设计备注︰ scatternet 支持应遵循定义 Bluetooth 特殊兴趣组 (SIG) 的增强的 scatternet 支持勘误表。

### <a name="devicebuscontrollerbluetoothbasesimultaneousbredrandletraffic"></a>Device.BusController.Bluetooth.Base.SimultaneousBrEdrAndLeTraffic

*Bluetooth 控制器必须支持并行的 BR EDR 和 LE 通信。*

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

Bluetooth 控制器必须允许基本速率 BR/增强数据速率 (EDR) 和低能耗 (LE) 无线电收发器同时使用。

### <a name="devicebuscontrollerbluetoothbasespecificinformationparameters"></a>Device.BusController.Bluetooth.Base.SpecificInformationParameters

*Bluetooth 主控制器必须实现特定的信息参数，以提供准确的信息，有关主机控制器的功能。*

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

制造商会修复的信息参数，提供了有价值的信息，有关 Bluetooth 设备和主机控制器的功能。 Bluetooth 主控制器必须实现 HCl\_读\_本地\_版本\_信息命令和 HCI\_读\_本地\_支持\_功能命令 Bluetooth 系统、 2.1 版 + 增强数据速率 (EDR) 部分 E 的说明中所述部分 7.4。 所需的支持包括报告的受支持的版本和功能的机制。

### <a name="devicebuscontrollerbluetoothbasesupportsbluetooth21andedr"></a>Device.BusController.Bluetooth.Base.SupportsBluetooth21AndEdr

*Bluetooth 控制器必须支持 Bluetooth 2.1 + EDR 规范要求。*

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

Bluetooth 主控制器必须遵守 Bluetooth 系统版本 2.1 + 增强数据速率 (EDR) 的规范中列出的要求。

### <a name="devicebuscontrollerbluetoothwidebandspeech-if-implemented"></a>Device.BusController.Bluetooth.WidebandSpeech （如果实现）

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
</td></tr></table>

**说明**

宽带语音启用高清晰度语音质量 （音频的采样率而不是仅 8 KHz 16 KHz） 在 Windows 设备用户通信通过外围还支持宽带语音 Bluetooth 时的电话录音。

这意味着 Bluetooth 无线电收发器，必须在所定义的 Bluetooth SIG[免提配置文件 (HFP) 1.6 规范](https://www.bluetooth.org/docman/handlers/downloaddoc.ashx?doc_id=238193)和[核心版本 4.1](https://www.bluetooth.org/DocMan/handlers/DownloadDoc.ashx?doc_id=282159) Bluetooth 规范中包含[核心规范附录 (CSA) 2](https://www.bluetooth.org/docman/handlers/downloaddoc.ashx?doc_id=245127)的硬件支持宽带语音。 至少，它必须使用至少一个 Bluetooth SIG 定义的宽带语音编码解码器 (目前为 mSBC)。

**业务理由︰**

我们希望用户在 Windows 上使用 Bluetooth 外围设备时遇到最佳可能的质量的音频。 宽带语音正成为支持 HFP 配置文件的外围设备的标准。 我们的竞争对手已经支持它

<a name="device.buscontroller.bluetooth.nonusb"></a>
## <a name="devicebuscontrollerbluetoothnonusb"></a>Device.BusController.Bluetooth.NonUSB

*Bluetooth 控制器-NonUSB 连接无线电收发器*

### <a name="devicebuscontrollerbluetoothnonusbperformance"></a>Device.BusController.Bluetooth.NonUSB.Performance

*Bluetooth 非 USB 控制器必须达到至少 700 kbps 的吞吐量。*

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

Bluetooth 非 USB 控制器必须达到至少 RFCOMM 层 700 kbps 的吞吐量。

### <a name="devicebuscontrollerbluetoothnonusbscosupport"></a>Device.BusController.Bluetooth.NonUSB.ScoSupport

*非 USB 连接 Bluetooth 控制器必须用于 SCO 的旁带通道。*

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

为了确保高质量的音频体验，所有非 USB 连接 Bluetooth 控制器必须使用 SCO (如对 I2S PCM/接口的 SCO) 旁带通道。

<a name="device.buscontroller.bluetooth.usb"></a>
## <a name="devicebuscontrollerbluetoothusb"></a>Device.BusController.Bluetooth.USB

*Bluetooth 控制器的 USB 连接无线电收发器*

### <a name="devicebuscontrollerbluetoothusbscodatatransportlayer"></a>Device.BusController.Bluetooth.USB.ScoDataTransportLayer

*Bluetooth 主控制器必须支持 Bluetooth 2.1 + EDR 规范中规定 SCO 数据传输层。*

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

Bluetooth 主控制器必须遵守与同步连接方向 (SCO)-详列 Bluetooth 系统、 2.1 版 + 增强数据速率 (EDR) 一部分的规范的 USB 要求部分 3.5。
