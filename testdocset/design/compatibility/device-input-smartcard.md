---
title: Device.Input.SmartCard
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 575a08b7cd183f8181c05ca9cb1d16433f8b0676
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceinputsmartcard"></a>Device.Input.SmartCard

 - [Device.Input.SmartCardMiniDriver](#device.input.smartcardminidriver)
 - [Device.Input.SmartCardReader](#device.input.smartcardreader)

<a name="device.input.smartcardminidriver"></a>
## <a name="deviceinputsmartcardminidriver"></a>Device.Input.SmartCardMiniDriver

*对智能卡的微型驱动程序程序*

### <a name="deviceinputsmartcardminidriverdonotstopwhenresourcesareunavailable"></a>Device.Input.SmartCardMiniDriver.DoNotStopWhenResourcesAreUnavailable

*智能卡的驱动程序必须停止系统，如果所需的资源不可用。*

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

如果读取器所需的资源不可用智能卡驱动程序必须不会中断系统操作。

### <a name="deviceinputsmartcardminidriverspecsandcertifications"></a>Device.Input.SmartCardMiniDriver.SpecsAndCertifications

*Windows 智能卡 Minidrivers 必须符合 Windows 智能卡的微型驱动程序版本 5 规范和认证标准。*

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

智能卡 Minidrivers 是可插拔的安全组件，提供基本的 CSP 与智能卡提供安全存储的加密密钥和证书之间一个抽象层。 智能卡 Minidrivers 执行安全包括加密、 解密、 关键设施、 密钥交换和数字签名的加密操作。 智能卡 Minidrivers 还包括其他形式的因素，如 USB 令牌或其他个人受信任的设备。
智能卡 Minidrivers 必须遵守以下规范︰

-   智能卡微型驱动程序规范的 Windows 基础加密服务提供程序 (基 CSP) 和智能卡密钥存储提供程序 (KSP) 版本 5.06 （或更高版本）。

-   智能卡微型驱动程序认证条件，5.06 （或以后） 版本。

智能卡 Minidrivers 必须符合下列基本条件︰

-   如果提交测试设备是智能卡并具有 ISO 7816 ID-1 智能卡板型，它必须经已通过 WHQL 测试要求智能卡的智能卡阅读器。

-   如果该设备是多功能设备，它必须通过每个设备类别的徽标要求如果徽标计划存在。

-   卡微型驱动程序可能不会实现卡微型驱动程序规范中没有指定的附加功能。

-   卡微型驱动程序可能不包含任何特洛伊木马程序或"后门"。

-   卡微型驱动程序可能会向最终用户显示任何 UI。

-   所有加密操作必须发生在设备上。

-   所有加密密钥必须存储在设备上并不能从该设备可导出。

智能卡 Minidrivers 必须遵守在卡微型驱动程序认证条件的下列一般条件︰

-   卡微型驱动程序管理和安装

-   卡微型驱动程序逻辑文件系统要求

-   卡微型驱动程序一般约定

-   卡微型驱动程序内存管理

-   可选的一般要求

智能卡的微型驱动程序必须遵守标准，来控制每个功能中的卡微型驱动程序规范，每个函数导出包括︰

-   功能

-   表现

-   错误处理

智能卡 Minidrivers 必须支持卡微型驱动程序函数的顺序的调用。
智能卡的微型驱动程序可能支持多个智能卡，但必须将证书条件分别传递每个支持的智能卡。

*设计备注*  

请参阅智能卡微型驱动程序规范的 Windows 基础加密服务提供程序 (基 CSP) 和智能卡密钥存储提供程序 (KSP) 中和在<http://msdn.microsoft.com/en-us/windows/hardware/gg487500.aspx>的版本规范。
请参阅智能卡的微型驱动程序认证条件，在<http://msdn.microsoft.com/en-us/windows/hardware/gg487504>。
下表描述了必须在任何给定的 OS 系列支持的最小值和最大的规范版本︰

| 系列操作系统 | 允许的规范版本                                                                         |
|-------------------------|--------------------------------------------------------------------------------------------------------|
| Windows 7 的客户端        | 5,6,7 （任意组合允许如 5 和 7 只、 5 只，7 只、 5 和 6 只，6 至 7 只，等等。） |
| Windows Server 2008     | 5,6,7 （任意组合允许如 5 和 7 只、 5 只，7 只、 5 和 6 只，6 至 7 只，等等。） |
| Windows 8 客户端        | 5,6,7 （任意组合允许如 5 和 7 只、 5 只，7 只、 5 和 6 只，6 至 7 只，等等。） |
| Windows Server 2016     | 5,6,7 （任意组合允许如 5 和 7 只、 5 只，7 只、 5 和 6 只，6 至 7 只，等等。） |

 

### <a name="deviceinputsmartcardminidriversupportmultipleinstancesonasystem"></a>Device.Input.SmartCardMiniDriver.SupportMultipleInstancesOnASystem

*智能卡的驱动程序可以在一个系统上支持同一设备的多个实例。*

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

智能卡驱动程序必须能够正常工作，如果在系统上安装了设备的多个实例。 每个设备实例的功能必须是一致的。 当加载一个单独的实例时，不能减少功能。

<a name="device.input.smartcardreader"></a>
## <a name="deviceinputsmartcardreader"></a>Device.Input.SmartCardReader

### <a name="deviceinputsmartcardreaderpindataentrykeyboardcomplieswithiso"></a>Device.Input.SmartCardReader.PinDataEntryKeyboardCompliesWithIso

*实现一个 PIN 数据输入键盘输入的设备必须符合 ISO。*

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

使用键盘输入 PIN 输入的设备必须符合 ISO 13491-1:1998 银行 — 安全加密设备 （零售） 第 1 部分︰ 概念、 要求和评估方法。
 

### <a name="deviceinputsmartcardreadersmartcardservice"></a>Device.Input.SmartCardReader.SmartCardService

*智能卡插入读卡器后，必须启动智能卡服务。*

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

智能卡插入智能卡阅读器后，必须启动智能卡服务。

**业务理由**

这一要求是所需的智能卡功能的可靠性。

### <a name="deviceinputsmartcardreadersupports258and259bytepackets"></a>Device.Input.SmartCardReader.Supports258And259BytePackets

*读取器必须支持在 T = 0 和 259 字节数据包中 T = 1 258 个字节的数据包。*

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

智能卡读卡器必须支持以下的交换在一次邮件传输︰

-   .258 字节数据包在 T = 0;也就是说，256 的数据字节数再加上两个状态词 SW1 和 SW2。

-   259 个字节数据包中 T = 1;也就是说，254 个字节的信息加上节点地址、 数据包控制字节、 长度和两种错误检测代码字节。

### <a name="deviceinputsmartcardreadersupportsdirectandinverseconvention"></a>Device.Input.SmartCardReader.SupportsDirectAndInverseConvention

*智能卡读卡器必须支持直接和逆约定智能卡。*

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

智能卡读卡器必须支持直接和逆约定智能卡硬件或操作系统的驱动程序。
 

### <a name="deviceinputsmartcardreadersupportsinsertionandremovalmonitor"></a>Device.Input.SmartCardReader.SupportsInsertionAndRemovalMonitor

*读取器必须支持智能卡插入和移除监视器。*

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

智能卡读卡器必须能够检测和报告智能卡插入和移除移除或插入智能卡本身以外的其他任何用户干预。 读取器必须使用中断机制来报告智能卡插入或删除系统。 检测到智能卡插入和移除驱动程序轮询方法不是可接受的方式来满足这一要求。
 

### <a name="deviceinputsmartcardreadersupportsminclockfrequency"></a>Device.Input.SmartCardReader.SupportsMinClockFrequency

*智能卡读卡器必须支持 3.5795 MHz 的小时钟频率。*

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

智能卡读卡器必须支持 3.5795 MHz 的小时钟频率。
 

### <a name="deviceinputsmartcardreadersupportsmindatarateof9600bps"></a>Device.Input.SmartCardReader.SupportsMinDataRateOf9600bps

*Smar 读卡器必须支持 9600 bps 的最小数据速率。*

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

智能卡读卡器必须能够传输数据的 9600 bps 速率或更高版本。

### <a name="deviceinputsmartcardreadersupportsnegotiableandspecificmodes"></a>Device.Input.SmartCardReader.SupportsNegotiableAndSpecificModes

*读取器必须支持按照 ISO/IEC 规范流通和特定模式。*

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

若要支持多协议的智能卡和智能卡的使用更高的数据速率和更高的时钟频率，读取器必须支持流通和特定的模式，按照 ISO/IEC 7816-3 (1997年-12-15)，第 5.4 节和第 7。
ISO 7816-3 的**电源关闭**命令是可选的但需要**重置**命令。
PT 不是必需的。
 

### <a name="deviceinputsmartcardreadersupportsresetcommand"></a>Device.Input.SmartCardReader.SupportsResetCommand

*智能卡读卡器必须支持重置命令。*

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

智能卡读卡器必须支持 T = 0，T = 1 的异步协议所述的硬件或驱动程序。 这两个协议都必须得到充分支持。 智能卡读卡器和驱动程序必须支持卡可以处理这两个协议。 不需非 T = 0，T = 1 协议的支持。
下面的协议规则适用于 T = 1 协议︰

-   传输指将命令发送到智能卡，通过使用一个或多个 T = 1 块并使用某个接收相应的答案或在 ISO/IEC 7816-3 中定义为多个 T = 1 块。

-   用于支持 IFSC 请求的卡，智能卡重置后的第一个传输必须以带有 IFSD 请求，在 ISO/IEC 7816-3，修正 1 节 9.5.1.2。

-    对于不支持 IFSD 请求的卡 （即卡回复与 R 块，表明"其他错误"），传输必须继续与我块。

-   成功的同步请求之后, 必须与其最初开始传输的第一个块与从头开始重新传输。

 

### <a name="deviceinputsmartcardreaderusbccidcomplieswithusbdeviceclassspec"></a>Device.Input.SmartCardReader.UsbCcidCompliesWithUsbDeviceClassSpec

*USB CCID 智能卡读取器必须符合 USB 设备类规范的 USB 芯片/智能卡接口设备。*

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

如果读取器支持 USB 连接，CCID 是必需的。 要确保 USB 智能卡读卡器正常工作的 USB 主机，CCID 的智能卡阅读器必须符合 USB 设备类︰ Integrated Circuit(s) 卡接口设备，1.00 或更高版本的智能卡技术指标。

### <a name="deviceinputsmartcardreaderusbccidissuesnak"></a>Device.Input.SmartCardReader.UsbCcidIssuesNak

*如果一个设备具有无中断数据传输 USB CCID 读者必须发出中断管道上的否认。*

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

除非在状态发生更改，USB CCIDs 必须发出中断管道上的否认。 这样可以防止反复轮询状态的设备的必要性。

*设计备注*

请参阅 USB 设备类规范的 USB 芯片/智能卡接口设备，1.00 或更高版本的修订，第 3 章。 请参阅 USB 规范、 修订版 1.1 版或更高版本、 5.7.4 和 8.5.4 部分。

