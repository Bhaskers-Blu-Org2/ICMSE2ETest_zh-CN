---
title: Device.Connectivity.WSD
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 99dca45759f8de128f6cf24f70a7d4416537903e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.WSD

 - [Device.Connectivity.WSD](#device.connectivity.wsd)
-->

<a name="device.connectivity.wsd"></a>
##Device.Connectivity.WSD

### <a name="deviceconnectivitywsddpws"></a>Device.Connectivity.WSD.DPWS

*设备的使用或与 Web 服务在设备 API (WSDAPI) 进行交互的 Web 服务 (DPWS) 规范遵守设备配置文件*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

它计划使用，或与 Microsoft Windows DPWS 上, 设备 API (WSDAPI)，Web 服务实现进行交互的设备必须实现 DPWS 规范本身。 (WSDAPI)

*设计备注*

在可用的 DPWS 规范

<http://go.microsoft.com/fwlink/?LinkId=109231>

### <a name="deviceconnectivitywsddpwsextensibility"></a>Device.Connectivity.WSD.DPWSExtensibility

*设备配置文件 Web 服务设备必须接受包含扩展性部分消息并处理相应的消息。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

设备配置文件 Web 服务 (DPWS) 设备必须接受扩展 XML 消息。 如果该设备能够理解可扩展部分中的内容，它可能会对其进行处理。

*设计备注*

在可用的 DPWS 规范

<http://go.microsoft.com/fwlink/?LinkId=109231>

### <a name="deviceconnectivitywsdmetadataexchange"></a>Device.Connectivity.WSD.MetadataExchange

*设备配置文件 Web 服务 (DPWS) 设备支持元数据交换*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

DPWS 与设备 API (WSDAPI) 上的 Web 服务交互的设备必须支持元数据交换规范中定义的元数据交换。

*设计备注*

可以在<http://go.microsoft.com/fwlink/?LinkId=109248>获取元数据交换规范

### <a name="deviceconnectivitywsdmetadatavalid"></a>Device.Connectivity.WSD.MetadataValid

*设备与设备 (WSDAPI) 的 Web 服务交互生成元数据 Web 服务符合设备配置文件*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

与 WSDAPI 交互设备必须填充如 2006 年 2 月的 Web 服务规范的设备配置文件中定义的元数据。

*设计备注*

2006 年 2 月的 Web 服务规范的设备配置文件是可用在<http://go.microsoft.com/fwlink/?LinkId=109231>

### <a name="deviceconnectivitywsdschema"></a>Device.Connectivity.WSD.Schema

*将启用网络的设备实现的 Web 服务 (DPWS) 中的设备配置文件必须遵守协议和架构。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

启用网络的设备实现的 Web 服务 (DPWS) 中的设备配置文件必须遵守设备配置文件 Web 服务描述的架构。

该设备还必须引用的命名空间 URI 所述设备配置文件 Web 服务规范。

实现 DPWS 必须遵循为 Web 服务描述语言 (WSDL) 的设备相关联的徽标的设备类。 WSDL 定义服务为网络终结点或端口的集合。 WSDL 规范的 XML 格式的文档提供用于此目的。 设备必须实现 WSDL 1.1 版。

*设计备注*

请参阅 Web 服务描述语言 (WSDL) 1.1 版在<http://www.w3.org/TR/2001/NOTE-wsdl-20010315>

在 Web 服务架构的设备配置文件，请参阅<http://schemas.xmlsoap.org/ws/2006/02/devprof/devicesprofile.xsd。>

查看设备配置文件 Web 服务规范的<http://specs.xmlsoap.org/ws/2006/02/devprof/devicesprofile.pdf。>

其他信息可在 Windows 位置开发工具包在<http://go.microsoft.com/fwlink/?LinkId=109368。>

### <a name="deviceconnectivitywsdwsdiscovery"></a>Device.Connectivity.WSD.WSDiscovery

*设备配置文件，与 Web 服务设备 API (WSDAPI) 上进行交互的 Web 服务 (DPWS) 设备实现 WS-发现*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

DPWS 设备必须实现 WS-发现使用 WSDAPI。

*设计备注*

可以在<http://go.microsoft.com/fwlink/?LinkId=109247>获取 WS-发现规范

