---
title: Device.BusController.NFC
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: b75a40f52f87087c798d80afe740ae0540693b2a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicebuscontrollernfc"></a>Device.BusController.NFC

 - [Device.BusController.NFC](#device.buscontroller.nfc)
 - [Device.BusController.NFC.NearFieldProximity](#device.buscontroller.nfc.nearfieldproximity)
 - [Device.BusController.NFC.RadioManagement](#device.buscontroller.nfc.radiomanagement)
 - [Device.BusController.NFC.SecureElement.HCE](#device.buscontroller.nfc.secureelement.hce)
 - [Device.BusController.NFC.SmartCard](#device.buscontroller.nfc.smartcard)
 - [Device.BusController.NFC.SecureElement.UICC](#device.buscontroller.nfc.secureelement.uicc)

<a name="device.buscontroller.nfc"></a>
## <a name="devicebuscontrollernfc"></a>Device.BusController.NFC

强烈建议的 IHV 的 NFC 客户机驱动程序接口使用创建[Microsoft NFC 类扩展 (CX)](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905534.aspx)。 此接口将从 6 月 2017 年开始强制性。

<a name="device.buscontroller.nfc.nearfieldproximity"></a>
## <a name="devicebuscontrollernfcnearfieldproximity"></a>Device.BusController.NFC.NearFieldProximity

任何技术实现 GUID\_DEVINTERFACE\_在 NFP 的设备驱动程序要求中指定 NFP 设备驱动程序接口被定义为 NFP 提供程序，必须满足所有近域近似 DDI 实现要求[规范](https://msdn.microsoft.com/en-us/library/windows/hardware/jj866064.aspx)中的布局方式。

### <a name="devicebuscontrollernfcnearfieldproximityattribute"></a>Device.BusController.NFC.NearFieldProximity.Attribute

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

NFP 提供程序必须支持大消息的大小不小于 10 KB 和传输速率不小于每秒 16 KB。

### <a name="devicebuscontrollernfcnearfieldproximityevent"></a>Device.BusController.NFC.NearFieldProximity.Event

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

NFP 提供程序必须使客户端能够接收后到达或出发的近因设备的 DeviceArrived 和 DeviceDeparted 事件。

### <a name="devicebuscontrollernfcnearfieldproximityndef"></a>Device.BusController.NFC.NearFieldProximity.NDEF

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

NFP 提供程序必须支持通过 NFC 论坛 NDEF 规格 1.0 版中定义的 NDEF 协议。

### <a name="devicebuscontrollernfcnearfieldproximitypeertopeer"></a>Device.BusController.NFC.NearFieldProximity.PeerToPeer

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

NFP 提供程序必须支持传输并接收数据通过 NFC 论坛定义逻辑链接控制协议 (LLCP) 1.1 版和简单 NDEF 交换协议 (SNEP) 1.0 版。

### <a name="devicebuscontrollernfcnearfieldproximitypublish"></a>Device.BusController.NFC.NearFieldProximity.Publish

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

NFP 提供程序必须支持发布和传送消息。

### <a name="devicebuscontrollernfcnearfieldproximityreliability"></a>Device.BusController.NFC.NearFieldProximity.Reliability

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

NFP 提供程序必须可靠地读取和写入标签。

### <a name="devicebuscontrollernfcnearfieldproximitysubscribe"></a>Device.BusController.NFC.NearFieldProximity.Subscribe

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

NFP 提供程序必须能够接收并将邮件传递到订阅的客户端。

### <a name="devicebuscontrollernfcnearfieldproximitytagoperation"></a>Device.BusController.NFC.NearFieldProximity.TagOperation

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

NFP 提供程序必须能够读取、 写入和格式标记，以及一组标记为只读。

<a name="device.buscontroller.nfc.radiomanagement"></a>
## <a name="devicebuscontrollernfcradiomanagement"></a>Device.BusController.NFC.RadioManagement

无线电管理 DDI 允许调用方的 NFC 设备驱动程序来设置近程无线电的 NFC 设备的电源状态。 NFC 设备驱动程序必须实现中定义的 DDIs[无线电管理 DDI 文档。](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905577.aspx)

### <a name="devicebuscontrollernfcradiomanagementbase"></a>Device.BusController.NFC.RadioManagement.Base

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

NFC 设备驱动程序必须能够设置附近的电源状态和 NFC 设备的安全元素无线电收发器。

<a name="device.buscontroller.nfc.secureelement.hce"></a>
## <a name="devicebuscontrollernfcsecureelementhce-if-implemented"></a>Device.BusController.NFC.SecureElement.HCE （如果实现）

安全元素 DDI 允许 NFC 设备驱动程序的调用方进行枚举时，相互通信，并配置可从设备访问的安全元素。 

任何技术实现 GUID\_DEVINTERFACE\_NFCSE 设备驱动程序接口安全元素 DDI 文档中指定为 NFC 安全元素的提供程序定义和必须满足所有安全元素 DDI 实现[规范](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905485.aspx)中的布局方式。 

安全元素 DDI 允许主机卡仿真 (HCE) 基于安全元素。 与 HCE，数据被直接路由到主机 CPU 上运行的应用程序。

### <a name="devicebuscontrollernfcsecureelementhcebase"></a>Device.BusController.NFC.SecureElement.HCE.Base

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

支持基于 HCE 卡仿真 NFC 安全元素提供程序必须能够配置侦听模式下的路由表，报告给 HCE 基于应用程序的 NFCC 功能和路由数据。

### <a name="devicebuscontrollernfcsecureelementhceevent"></a>Device.BusController.NFC.SecureElement.HCE.Event

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

支持基于 HCE 卡仿真 NFC 安全元素提供程序必须支持的事件的客户端订阅，必须能够引发事件以指示发作 HCE 被激活和停用。

### <a name="devicebuscontrollernfcsecureelementhcereliability"></a>Device.BusController.NFC.SecureElement.HCE.Reliability

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

支持基于 HCE 卡仿真必须能够可靠地路由数据到主机或其他安全元素适当地基于当前 NFC 安全元素提供程序侦听模式路由表配置***.***

<a name="device.buscontroller.nfc.smartcard"></a>
## <a name="devicebuscontrollernfcsmartcard"></a>Device.BusController.NFC.SmartCard

智能卡 DDI 允许 NFC 设备驱动程序的调用方执行低级别智能卡 NFC 非接触式智能卡上的操作。 这包括侦听读取元数据，如 ATR、 UID 和历史字节信息，执行特定的 NFC 卡用于为某些非 ISO14443 4 兼容卡的低级别基元命令翻译 Apdu Apdu 以及支持上的读/写操作的智能卡的卡到达/出发通知。

任何技术实现 GUID\_DEVINTERFACE\_智能卡\_智能卡 DDI 文档中指定的读卡器设备驱动程序接口定义为智能卡读取器提供程序，并且必须满足所有中的布局方式的智能卡 DDI 实现要求[规范。](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905602.aspx)

### <a name="devicebuscontrollernfcsmartcardattribute"></a>Device.BusController.NFC.SmartCard.Attribute

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

智能卡读卡器提供程序必须能够获取和设置智能卡的属性。

### <a name="devicebuscontrollernfcsmartcarddataexchange"></a>Device.BusController.NFC.SmartCard.DataExchange

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

智能卡读卡器提供程序必须能够根据支持非接触式智能卡与 PC/SC 标准进行通信。 它必须包括对 PC/SC 透明模式的支持。 支持非接触式智能卡包括︰ MIFARE 经典 （可选） MIFARE Ultralight、 Topaz、 宝石、 ISO14443-A/B、 Felica、 ISO15693。

### <a name="devicebuscontrollernfcsmartcardstate"></a>Device.BusController.NFC.SmartCard.State

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

智能卡读卡器提供程序必须能够获取和设置非接触式智能卡的状态。

<a name="device.buscontroller.nfc.secureelement.uicc"></a>
## <a name="devicebuscontrollernfcsecureelementuicc-if-implemented"></a>Device.BusController.NFC.SecureElement.UICC （如果实现）

安全元素 DDI 允许 NFC 设备驱动程序的调用方进行枚举时，相互通信，并配置可从设备访问的安全元素。

任何技术实现 GUID\_DEVINTERFACE\_NFCSE 设备驱动程序接口安全元素 DDI 文档中指定为 NFC 安全元素的提供程序定义和必须满足所有安全元素 DDI 实现[规范](https://msdn.microsoft.com/en-us/library/windows/hardware/dn905485.aspx)中的布局方式。

### <a name="devicebuscontrollernfcsecureelementuiccemulation"></a>Device.BusController.NFC.SecureElement.UICC.Emulation

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

支持基于 UICC 卡仿真 NFC 安全元素提供程序必须能够相互通信和配置 UICC 和必须的独占访问权授予客户端来管理卡仿真模式。

### <a name="devicebuscontrollernfcsecureelementuiccenumeration"></a>Device.BusController.NFC.SecureElement.UICC.Enumeration

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

支持基于 UICC 卡仿真 NFC 安全元素提供程序必须能够列举所有可以从设备访问的安全元素。

### <a name="devicebuscontrollernfcsecureelementuiccevent"></a>Device.BusController.NFC.SecureElement.UICC.Event

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

支持基于 UICC 卡仿真 NFC 安全元素提供程序必须支持的事件的客户端订阅并必须能够引发事件以指示如事务外部的读取器实例。

### <a name="devicebuscontrollernfcsecureelementuiccreliability"></a>Device.BusController.NFC.SecureElement.UICC.Reliability

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

支持基于 UICC 卡仿真 NFC 安全元素提供程序必须能够可靠地开启 / 关闭的卡仿真模式。
