---
title: Device.Connectivity.UsbDevices
Description: "通过 USB，包括 USB 集线器，但非 USB 控制器连接的所有设备的要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 7c2d24859b1a1228e81c3ee197b8768d4d10ac21
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.UsbDevices

 - [Device.Connectivity.UsbDevices](#device.connectivity.usbdevices)
-->

<a name="device.connectivity.usbdevices"></a>
##Device.Connectivity.UsbDevices

*适用于通过包括 USB 集线器的 USB 连接的所有设备。不适用于 USB 控制器。*

### <a name="deviceconnectivityusbdevicesdebugcomplieswithdebugspec"></a>Device.Connectivity.UsbDevices.DebugCompliesWithDebugSpec

*USB 调试设备必须遵守 USB2 调试设备规格。*

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

USB 设备通过 USB 2.0 用于调试时必须遵守 USB2 调试设备功能要求，其中包括设备框架、 命令和其他运营要求的详细信息。

### <a name="deviceconnectivityusbdevicesdebugcomplieswithdebugspecusb3"></a>Device.Connectivity.UsbDevices.DebugCompliesWithDebugSpecUSB3

*USB 3.0 调试电缆必须符合 USB 3.0 规范。*

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

对于 USB 3.0 主机调试设计的 USB 电缆必须遵守通用串行总线 3.0 规范，部分 5.5.2。

### <a name="deviceconnectivityusbdevicesdeviceattachlessthan100ms"></a>Device.Connectivity.UsbDevices.DeviceAttachLessThan100ms

*至少 100 毫秒后必须响应信号设备连接的 USB 设备。*

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

当 USB 设备已发出信号设备附加，操作系统提供 100 毫秒的恢复时间间隔。 该设备必须在该时间间隔结束作出响应。 在 USB 规范、 Revision2.0、 7.1.7.3 一节对此进行了描述。 这一要求保证电气和机械连接是稳定的在所连接的设备将被重置之前。

### <a name="deviceconnectivityusbdevicesfunctionsuspendselectivesuspend"></a>Device.Connectivity.UsbDevices.FunctionSuspendSelectiveSuspend

*USB 3.0 设备正确必须实现函数挂起和选择性挂起。*

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

设备从选择性挂起状态恢复时之前设备是有选择地, 处于挂起状态的任何函数挂起仍停留在函数挂起状态。 设备必须放置所有设备功能函数中的挂起状态。 设备必须选择性挂起状态报告中。

SuperSpeed 设备忽略该设备\_远程\_唤醒功能选择器。

在函数中所有函数的 SuperSpeed 设备时挂起状态和端口\_U2\_超时字段进行编程到 0xFF，该设备在 10 毫秒 (ms) 链接处于非活动状态后触发 U2。 有关详细信息，请参阅 USB 3.0 规范 9.2 节。

设备，继续与选择性挂起状态保留在指定节 9.2.5.2 作为 USB 3.0 规范的设备状态信息的最小集合。
 

### <a name="deviceconnectivityusbdevicesinternaldevicesmustsupportsuspend"></a>Device.Connectivity.UsbDevices.InternalDevicesMustSupportSuspend

*所有内部连接的 USB 设备必须前往选择性挂起后活动的时间。*

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

所有内部连接的 USB 设备必须能够进入挂起状态之后这些设备的设备驱动程序启动的 USB 选择性挂起的进程。 第三方，对应用系统的内部设备的驱动程序必须实现 USB 选择性挂起。

属于这些设备类别的设备可以选择不支持 USB 选择性挂起︰

-   打印机

-   扫描程序

-   传真

### <a name="deviceconnectivityusbdevicesisochronousdeviceanddriver"></a>Device.Connectivity.UsbDevices.IsochronousDeviceAndDriver

*等时 USB 设备和驱动程序要求*

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

**1.ISO USB 设备和驱动程序提供多个替代设置以支持硬件接口选项的最大的灵活性︰**

如果任何替代设置消耗同步带宽，设备和驱动程序必须提供多个替代设置的每个接口。

**2.USB 设备和驱动程序不使用同步带宽为备用设置 0:**

设备和驱动程序不能使用同步带宽为备用设置 0。 仅当正在使用时，设备必须消耗的带宽。

**3.USB 同步全速或高速设备使用 USB 总线带宽的 50%以上，提供了替代设置︰**

如果 USB 同步全速或高速设备使用 USB 总线带宽的 50%以上，它必须提供的可选设置，允许设备切换到使用不少于 50%的总线带宽的设置，并为设备的特定类 (ex。 如果是照相机，然后它必须继续对视频进行流），即使它可能会在较低的质量模式。
连接的主机控制器的设备不受这一要求。

**4.USB 接口包含常时等量终结点使用的设备具有低带宽情况下的至少一个备用接口︰**

USB 设备必须至少一个可选的接口提供为低带宽 USB 规范 2.0 版或更高版本的修订号、 第 9.6.5 部分中所述。

*设计备注*

请参见通用串行总线规范-修订版 2.0 的第 9.6.5 部分。
如果两个或多个设备连接，使用超过 50%的总线带宽并没有提供其他设置，设备之一工作一次。
请参阅 USB 规范，修订版 2.0 或更高版本，部分 5.6 和 5.7。
 

### <a name="deviceconnectivityusbdevicesmsoscontainerid"></a>Device.Connectivity.UsbDevices.MsOsContainerId

*USB 设备实现 Microsoft 操作系统容器 ID 描述符必须正确实现。*

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

如果 Microsoft® 操作系统**ContainerID**描述符实现了多功能的 USB 设备，该设备执行此操作 Microsoft 操作系统功能描述符中。 

Microsoft 操作系统**ContainerID**描述符允许 Windows® 正确检测机等多功能设备。 该描述符提供所有设备节点显示为**设备和打印机**用户界面 (UI) 中的一个物理对象的一种的方法。

### <a name="deviceconnectivityusbdevicesmustbefunctionalafterresume"></a>Device.Connectivity.UsbDevices.MustBeFunctionalAfterResume

*从系统电源状态恢复后，连接的 USB 设备必须正常工作。*

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

不输入及时就绪状态的设备将被标记代码 10 或其他系统。 特定种类的设备不正确响应系统事件，如继续，而且需要上的驱动程序或预期引导精确计时才能正常工作。 设备必须能够在恢复时重置端口不起作用，但也必须要保持如果出现重置功能。
设备必须保持连接状态 (USB 规范 2.0，部分 9.1) 来配置和设备必须处于已配置状态之前也许使用其功能 （亦即设备是可用容量）。 这是每个 USB 规范 2.0 9.1 和 9.2.6.2 部分与"后重置端口或将其恢复，USB 系统软件预期将提供 10 毫秒的"恢复"间隔之前连接到端口的设备需要响应的数据传输。 该设备可能会忽略任何数据传输恢复时间间隔内。"

*说明︰*

是否或不发出重置端口从系统电源状态恢复后，设备必须正常工作。

### <a name="deviceconnectivityusbdevicesmustnotdisconnectduringsuspend"></a>Device.Connectivity.UsbDevices.MustNotDisconnectDuringSuspend

*USB 设备必须从上游端口断开时进入或继续从选择性挂起。*

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

USB 设备必须断开从上游端口在选择性挂起的进程。

若要测试此要求，我们将转到选择性挂起状态，然后继续该设备的设备。 在此过程中，我们将观察的上游端口的端口状态位并验证该设备不会在这段时间断开。 我们将重复此过程多种时间。
 

### <a name="deviceconnectivityusbdevicesmustresumewithoutforcedreset"></a>Device.Connectivity.UsbDevices.MustResumeWithoutForcedReset

*所有的 USB 设备时从休眠，休眠状态，恢复正常工作或不强制重置 USB 主机控制器的情况下重新启动。*

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

所有的 USB 设备时从休眠，休眠状态，恢复正常工作或不强制重置 USB 主机控制器的情况下重新启动。

*设计备注*  

注册表项时在 Windows 7 中正常工作的设备不需要记录下 kb ForceHCResetOnResume: <http://support.microsoft.com/kb/928631>。
请注意，一组已知的当前现有设备执行操作需要强制重设时，应保持，这将重置时恢复这些设备的操作系统列表中介绍这些设备。 这一要求的目的是确保该列表必须重置起来后继续不会增长的设备与该设备的正确可以处理休眠状态转换无重置。
在重置后的整个 USB 主控制器结果显著增加时所需的所有 USB 设备后系统恢复，因为有可能只有一个设备 0 一次变得可用，此枚举具有要序列化的总线上的所有 USB 设备。 我们也知道，重置主机控制器可能会导致非法 SE1 信号状态某些主机控制器，这反过来又会导致挂起或总线放置一些 USB 设备上。 此外，设备都无法保持任何私有状态在睡眠恢复为该状态将重置在丢失。

### <a name="deviceconnectivityusbdevicesmustsignalattachwithin500ms"></a>Device.Connectivity.UsbDevices.MustSignalAttachWithin500ms

*设备必须附加在 500 毫秒内，系统恢复后发出信号。*

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

系统从休眠状态恢复后，集线器驱动程序将获取该设备连接到该端口的状态。 如果未显示设备连接，如集线器驱动程序将等待 500 毫秒 (ms) 集线器驱动程序再次查询的端口状态。 如果在该时间内显示为连接设备，中心将不需要重新枚举即插即用和播放，这将导致更好的用户体验的设备。 这一要求已经存在总线供电的设备中 USB 规范。 要求将现在还适用于自供电的设备。

### <a name="deviceconnectivityusbdevicesmustsupportsuspend"></a>Device.Connectivity.UsbDevices.MustSupportSuspend

*在经过的无活动期后必须支持挂起 USB 总线供电的所有 USB 设备。*

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

总线供电的设备的设备驱动程序启动的 USB 选择性挂起的进程。 设备可以从任何通电状态进入挂起状态。 该设备必须开始过渡到挂起状态后超过 3.0 ms 其上游对开总线线上看到持续空闲状态。 在挂起状态，设备必须唯一签发暂停不超过 10 毫秒它所有端口上的总线处于非活动状态后总线从当前 USB 规范、 修订版 2.0、 7.1.7.6、 6 9.1.1.6 和 9.2.6.2 部分中所述。

有关 USB 选择性挂起中嵌入式 USB 设备的说明可在以下要求︰ Device.Connectivity.UsbDevices.InternalDevicesMustSupportSuspend。

澄清有关 USB 选择性挂起 Windows RT 系统中的可以找到以下要求︰ Device.Connectivity.UsbDevices.MustSupportSuspendOnRT。

### <a name="deviceconnectivityusbdevicesrespondallstringrequests"></a>Device.Connectivity.UsbDevices.RespondAllStringRequests

*USB 设备必须为所有主机发送到索引的字符串请求作出响应。*

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

USB 设备必须相应地作出响应字符串主机发送的请求。 如果没有字符串存储在索引查询或请求错误存在，设备必须停顿。 不，设备必须重置自身或者停止正常运行。 这是所述 USB 规范 2.0 版或更高版本的修订，部分 9.6。

### <a name="deviceconnectivityusbdevicesresponseslimitedbywlengthfield"></a>Device.Connectivity.UsbDevices.ResponsesLimitedByWlengthField

*USB 设备响应主机请求并将 wLength 字段大小有限。*

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

所有 USB 设备请求都包含并将 wLength 字段。 大小必须通过 USB 设备响应主机请求&lt;= 设备请求并将 wLength 字段定义在 USB 规范中，Revision1.1 或更高版本，部分 9.3.5。
 

### <a name="deviceconnectivityusbdevicesserialnumbers"></a>Device.Connectivity.UsbDevices.SerialNumbers

*USB 串行数字特定设备类实现，并且在特定设备型号是唯一的。*

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

必须为以下设备类实现 USB 序列号︰

-   Bluetooth （类代码 0xE0，子类 0x01，协议 0x01）

-   通信设备类 （类代码 0x02）

-   大容量存储 （类代码 0x08）

-   扫描/成像 （类代码 0x06）

-   打印 （类代码为 0x07）

-   主机网络适配器和设备线适配器 （子类 02 类代码 0xE0）

USB 的序列号是可选的其他所有的设备类别。    此外，如果该设备的模型实现了序列号，同一模型的所有设备必须都具有唯一的序列号。

*设计备注*

USB 设备类的详细信息的详细信息，请参阅"定义 1.0 类代码"处︰ <http://go.microsoft.com/fwlink/?LinkId=40497>。
序列号实现的详细信息，请参阅 USB 规范 2.0 版或更高版本的修订，部分 9.6。
 

### <a name="deviceconnectivityusbdevicesserialnumbersusevalidcharacters"></a>Device.Connectivity.UsbDevices.SerialNumbersUseValidCharacters

*USB 设备实现制造商定义的序列号必须包含有效的字符。*

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

USB 的序列号必须是包含有效字符组成的制造商确定 ID 的字符串。 有效的字符定义 Windows 驱动程序工具包中"USB\_设备\_描述符。"

### <a name="deviceconnectivityusbdevicessuperspeedonconnectviausb3port"></a>Device.Connectivity.UsbDevices.SuperSpeedOnConnectViaUsb3Port

*如果在上游 SuperSpeed 终止，设备必须始终连接的 USB 3.0 端口上，永远不会连接到 USB 2.0 端口。*

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

在一个 USB 3.0 的集线器，两个下游端口、 USB 2.0 端口和 Superspeed 端口共享相同的连接器。 当 SuperSpeed (即非集线器) 设备插入到此类连接器，该设备必须始终连接的 SuperSpeed 端口上。 设备必须永远不会连上 USB 2.0 端口。

若要测试这种要求，软件将验证 USB 3.0 端口状态位显示已连接的设备和 USB 2.0 端口状态位不会显示已连接的设备。 

"连接"的定义，请参阅第 2 部分的 USB 3.0 规范下"连接"。

### <a name="deviceconnectivityusbdevicestestedusingmicrosoftusbstack"></a>Device.Connectivity.UsbDevices.TestedUsingMicrosoftUsbStack

*USB 设备必须经微软 xHCI 安装堆栈。*

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

必须使用 Microsoft 的可扩展的主机控制器接口 (xHCI) 堆栈的 Windows 系统上安装并启用测试所有 USB 设备 （低、 全、 高和超级速度）。

**注意︰**在 USB-如果出于测试目的安装了自测试特定的 USB 测试堆栈，这是预期的和可以接受。

### <a name="deviceconnectivityusbdevicesusbifcertification"></a>Device.Connectivity.UsbDevices.UsbifCertification

*USB 设备必须通过 USB IF 测试或者是 USB 如果认证。*

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

USB 设备必须通过 USB 实现论坛 （如果） 测试或者是 USB-如果认证。

USB C PD 能够设备、 集线器和 chargers 版本 1.1 的 USB 类型 C 规范或更高版本和修订版本 2.0 1.1 版的 PD 规范或更高版本，必须实现，必须使用 USB 根据认证的 PD 硅-IF 的 USB C 产品测试矩阵。

有关详细信息，请参阅白皮书 Windows 徽标工具包 USB-如果测试︰

-   <http://www.microsoft.com/whdc/connect/usb/wlk-usb-if-testing.mspx>

### <a name="deviceconnectivityusbdevicesusbtypecaltmodecertification"></a>Device.Connectivity.UsbDevices.USBTypeCAltModeCertification

*与他们各自组织认证类型 C 备用模式时 USB 设备。*

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

如果 USB 类型 C 设备支持备用模式标准和行业组拥有标准，它具有相应的证书，设备必须使用 USB 该行业组通过认证的 PD 硅-如果。

例如，如果 USB 类型 C 设备的 PD 硅支持 USB 和 PD DisplayPort 备用模式，然后该硅必须由 VESA DisplayPort 功能，此外到 USB-如果由于 USB 和 PD 的功能。

证书的特定于供应商的备选模式不是必需的。

### <a name="deviceconnectivityusbdevicesusbtypeccertifiedcables"></a>Device.Connectivity.UsbDevices.USBTypeCCertifiedCables

*随附缆线附带的 USB 类型 C 设备认证电缆*

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

如果设备是 USB 类型 C，附带一条电缆或适配器、 电缆和/或适配器必须 USB-如果认证。

此外，如果 USB 类型 C 电缆或适配器用于备用模式标准和行业组拥有标准具有相应证书，电缆或适配器必须获得该证书。

### <a name="deviceconnectivityusbdevicesusbtypecaltmodedevicecompat"></a>Device.Connectivity.UsbDevices.USBTypeCAltModeDeviceCompat

*USB 类型 C 替换模式设备兼容性*

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

只有一个 USB 端口，连接到下游的对开端口 (DFP) 备用模式设备还必须提供 USB 功能等价于它的替代模式。

例如，Thunderbolt 备用模式 USB-C 存储设备必须能够作为 USB 大容量存储设备通过 USB 2.0 或 USB 3.0。

注意︰ 替换模式适配器不需要提供 USB 功能等价于它的替代模式。 例如，DisplayPort 或 MHL 备用模式 USB-C 适配器不需要还支持通过 USB 2.0 或 USB 3.0 工作视频协议。

### <a name="deviceconnectivityusbdevicesuseusbclassonlyforcontrollerorhub"></a>Device.Connectivity.UsbDevices.UseUsbClassOnlyForControllerOrHub

*第三方 INF 文件包含类"USB"仅当设备是 USB 主机控制器、 一个根目录或一个外部集线器。*

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

没有预定义的类的设备通常错误地使用类 USB。 例如，USB 鼠标使用类 HID，而 USB 智能卡使用类智能卡读取器。 保留类 USB 主控制器和根或外部 USB 集线器。 如果供应商有没有 Windows 定义的类，但使用 USB 总线的设备，它必须定义自己的类或类的 GUID。 与 USB 设备的类型关联的安装程序类不使用总线类型，必须使用。 安装程序类"USB"(ClassGuid = {36fc9e60-c465-11cf-8056-444553540000}) 保留为 USB 主控制器和根或外部 USB 集线器。 它必须不用于其它设备类别。

 
*设计备注*

Microsoft 提供的大多数设备类型的系统定义的安装程序类。 系统定义的安装程序类 Guid 被在 Windows 驱动程序工具包，"Devguid.h"。
如果您选择了错误的类，该设备出现在错误的位置在设备管理器和 Windows Vista 用户界面。 不正确地使用此类可能会导致设备驱动程序出现故障的硬件兼容性测试。
针对将出现的 Windows 类 Guid，请查看 Windows 驱动程序工具包，"System-Supplied 设备安装程序类": <http://msdn.microsoft.com/en-us/library/ff553419.aspx>。

### <a name="deviceconnectivityusbdeviceswirelessusbobtainswusblogofromusbif"></a>Device.Connectivity.UsbDevices.WirelessUsbObtainsWusbLogoFromUsbif

*无线 USB 设备或主机必须获得认证的无线 USB 徽标的 USB-如果。*

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

所有的无线 USB 设备必须获得认证的无线 USB 徽标的 USB-如果。

### <a name="deviceconnectivityusbdeviceswirelessusbwimediaalliace"></a>Device.Connectivity.UsbDevices.WirelessUsbWiMediaAlliace

*经认证的无线 USB 设备或主机必须通过所有必需的 WiMedia 联盟符合性测试。*

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

无线 USB 设备必须通过 WiMedia 联盟无线电法规遵从性测试。

