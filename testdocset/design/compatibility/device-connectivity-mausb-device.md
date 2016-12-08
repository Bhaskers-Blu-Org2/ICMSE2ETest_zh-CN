---
title: Device.Connectivity.MAUSB.Device
Description: "要求适用于 MA USB 设备。 但是，MA USB 要求是当前可选，并且直到 2017年将不会强制执行。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: cd308bf987203d27936644cec9a6759fe83151e5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Connectivity.MAUSB.Device

 - [Device.Connectivity.MAUSB.Device ](#device.connectivity.mausb.device)
-->

<a name="device.connectivity.mausb.device"></a>
##Device.Connectivity.MAUSB.Device 

以下要求适用于 MA USB 设备。

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

以下表的定义中使用 MA USB 集线器和 MA USB 设备要求的上下文︰

PAL 的 MA USB 设备︰

在马萨诸塞州 USB 规范中，定义 MA USB 设备 PAL，是 MA USB 设备或通过 MA 链接接口管理的传输的 USB 负载的 MA USB 集线器的组成部分。

MA USB 设备后面的集成的 USB 设备︰

由 USB 2.0 或 USB 3.1 规范，除了那些涉及到物理的 USB 媒体指中执行 USB 设备工作正常，MA USB 设备的 USB 设备逻辑块。 为简洁起见，背后 MA USB 设备集成的 USB 设备将被称为集成的 USB 设备

集成的 USB 2.0 集线器后面 MA USB 集线器︰

这是指中执行 USB 设备的功能由 USB 2.0 规范，除了那些涉及到物理的 USB 介质的上游端口要求 MA USB 集线器的 USB 集线器逻辑块。 为简洁起见，集成的 USB 2.0 集线器后面 MA USB 集线器将被称为集成的 USB 2.0 集线器

集成的 USB 3.1 MA USB 集线器背后的中心︰

这是指中执行 USB 设备的功能由 USB 3.1 规范，除了那些涉及到物理的 USB 介质的上游端口要求 MA USB 集线器的 USB 集线器逻辑块。 为简洁起见，集成的 USB 3.1 集线器后面 MA USB 集线器将被称为集成的 USB 3.1 集线器

请注意后面 MA USB 集线器的 USB 2.0 或 USB 3.1 集线器后面的集成 USB 设备所需满足有线 USB 设备 Device.Connectivity.UsbDevices 类别下列出的。

### <a name="deviceconnectivitymausbdevicebulkoutbuffersize"></a>Device.Connectivity.MAUSB.Device.BulkOutBufferSize

*MA USB 设备必须支持至少 64 KB 缓冲区空间每个非 SuperSpeed 批量出终结点和至少 512 KB 缓冲区空间，每个大容量 SuperSpeed Out 终结点*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。


MA USB 设备必须支持这些最小缓冲区大小，以便能可靠地为获得最佳的性能 （吞吐量）。 MA USB 规范 1.0 a 版，6.3.7 一节所述由 MA USB 设备在其终结点响应数据包中报告这些缓冲区大小。

 - SuperSpeed 大容量出-512 KB

 - 非-SuperSpeed 批量出-64 KB

### <a name="deviceconnectivitymausbdevicefunctionsuspendselectivesuspend"></a>Device.Connectivity.MAUSB.Device.FunctionSuspendSelectiveSuspend

*具有集成 3.1 设备在它们后面的 MA USB 设备必须正确实现函数挂起。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 设备从挂起状态恢复时，处于暂挂状态，MA USB 设备被挂起之前，集成 3.1 任何的设备函数将保留在函数挂起状态。 集成的设备从挂起状态恢复时，集成 3.1 设备集成的设备被挂起之前，处于挂起状态的任何函数将保留在函数挂起状态。 从暂停状态恢复的集成的 USB 设备保留设备的 USB 3.0 规范中部分 9.2.5.2 的指定状态信息的最小集合。 MA USB 设备从挂起状态恢复时，集成的 USB 设备正在挂起盯 MA USB 设备被挂起之前，仍处于暂停状态。

### <a name="deviceconnectivitymausbdeviceipmode"></a>Device.Connectivity.MAUSB.Device.IPMode

*MA USB 设备必须实现支持 IP 模式*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 设备必须实现 IP 模式对 MA USB 规范 1.0 a 版，4.5.3.2 部分中指定的支持"的要求为 IP 模式"。

### <a name="deviceconnectivitymausbdeviceisochronousdeviceanddriver"></a>Device.Connectivity.MAUSB.Device.IsochronousDeviceAndDriver

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

-   **集成的 ISO USB 设备和驱动程序提供多个替代设置以支持硬件接口选项的最大的灵活性︰**

    -   如果任何替代设置消耗同步带宽，设备和驱动程序必须提供多个替代设置的每个接口。

-   **集成的 USB 设备和驱动程序不使用同步带宽为备用设置 0:**

    -   Integraetd 的 USB 设备和驱动程序不能使用同步带宽为备用设置 0。 仅当正在使用时，设备必须消耗的带宽。

-   **集成的 USB 同步全速或高速设备使用 USB 总线带宽的 50%以上，提供了替代设置︰**

    -   如果集成 USB 同步全速或高速设备使用 USB 总线带宽的 50%以上，它必须提供的可选设置，允许设备切换到使用少于 50%的总线带宽设置并为设备的特定类 (ex。 如果是照相机，然后它必须继续对视频进行流），即使它可能会在较低的质量模式。
        集成的 USB 设备连接的主机控制器不受这一要求。

-   **集成的 USB 设备接口包含常时等量终结点具有低带宽情况下的至少一个备用接口︰**

    -   集成的 USB 设备必须至少一个可选的接口提供为低带宽 USB 规范 2.0 版或更高版本的修订号、 第 9.6.5 部分中所述。

*设计备注*

请参见通用串行总线规范-修订版 2.0 的第 9.6.5 部分。
如果两个或多个设备连接，使用超过 50%的总线带宽并没有提供其他设置，设备之一工作一次。
请参阅 USB 规范，修订版 2.0 或更高版本，部分 5.6 和 5.7。

### <a name="deviceconnectivitymausbdevicemausbspeccompliance"></a>Device.Connectivity.MAUSB.Device.MAUSBSpecCompliance

*MA USB 设备必须支持 USB-如果符合规范*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 设备必须符合 MA USB 规范 1.0 a 版或更高版本。

### <a name="deviceconnectivitymausbdevicemsoscontainerid"></a>Device.Connectivity.MAUSB.Device.MsOsContainerId

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

如果多功能集成的 USB 设备实现的 Microsoft® 操作系统**ContainerID**描述符，设备执行此操作的 Microsoft 操作系统功能描述符中。 

Microsoft 操作系统**ContainerID**描述符允许 Windows® 以正确检测到集成多功能设备。 该描述符提供所有设备节点显示为**设备和打印机**用户界面 (UI) 中的一个物理对象的一种的方法。

### <a name="deviceconnectivitymausbdevicemustbefunctionalafterresume"></a>Device.Connectivity.MAUSB.Device.MustBeFunctionalAfterResume

*从系统电源状态恢复后，MA USB 设备必须正常工作。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 恢复后 MA USB 设备 PAL 必须处于正常工作状态而无需 MA USB 设备重置。 此外，集成的 USB 设备必须在正常工作状态 USB 恢复后无需 MA USB 设备重置或 USB 设备重置。

不输入及时就绪状态的设备将被标记代码 10 或其他系统。 特定种类的设备不正确响应系统事件，如继续，而且需要上的驱动程序或预期引导精确计时才能正常工作。

### <a name="deviceconnectivitymausbdevicemustnotdisconnectduringsuspend"></a>Device.Connectivity.MAUSB.Device.MustNotDisconnectDuringSuspend

*MA USB 设备或集成的 USB 设备必须断开连接到或从暂停状态恢复时。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 设备必须 MA USB 挂起或恢复期间未断开从主机。

集成的 USB 设备必须断开 USB 挂起/继续或马萨诸塞州 USB 挂起/恢复过程。

### <a name="deviceconnectivitymausbdevicerespondallstringrequests"></a>Device.Connectivity.MAUSB.Device.RespondAllStringRequests

*集成的 USB 设备必须为所有主机发送到索引的字符串请求作出响应。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

集成的 USB 设备必须相应地作出响应字符串主机发送的请求。 如果没有字符串存储在索引查询或请求错误存在，则必须隔栏集成的设备。 集成的设备必须重置本身或停止运行。 这是所述 USB 规范 2.0 版或更高版本的修订，部分 9.6。

### <a name="deviceconnectivitymausbdeviceresponseslimitedbywlengthfield"></a>Device.Connectivity.MAUSB.Device.ResponsesLimitedByWlengthField

*集成的 USB 设备 responss 主机的请求并将 wLength 字段大小有限。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

所有 USB 设备请求都包含并将 wLength 字段。 大小必须通过集成的 USB 设备响应主机请求&lt;= 设备请求并将 wLength 字段定义在 USB 规范中，Revision1.1 或更高版本，部分 9.3.5。
 

### <a name="deviceconnectivitymausbdeviceserialnumbers"></a>Device.Connectivity.MAUSB.Device.SerialNumbers

*USB 序列号由特定的设备类集成的 USB 设备，和在特定设备型号是唯一的。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

必须由以下设备类集成的 USB 设备实现 USB 序列号︰

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
 

### <a name="deviceconnectivitymausbdeviceserialnumbersusevalidcharacters"></a>Device.Connectivity.MAUSB.Device.SerialNumbersUseValidCharacters

*集成的 USB 设备实现制造商定义的序列号必须包含有效的字符。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

USB 的序列号必须是包含有效字符组成的制造商确定 ID 的字符串。 有效的字符定义 Windows 驱动程序工具包中"USB\_设备\_描述符。"

### <a name="deviceconnectivitymausbdevicespeedcapabilitymatch"></a>Device.Connectivity.MAUSB.Device.SpeedCapabilityMatch

*集成的 USB 设备必须枚举以 USB 速度 MA USB 设备速度功能描述符中公布。*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

*集成的 USB 设备必须枚举以 USB 速度 MA USB 设备速度功能描述符中公布。速度功能描述符是 MA USB 设备作为中指定节 6.3.3.1 MA USB 规范 1.0 a 版功能响应的一部分。*

### <a name="deviceconnectivitymausbdevicesupportswifidirectandwsb"></a>Device.Connectivity.MAUSB.Device.SupportsWiFiDirectAndWSB

*MA USB 设备支持 WiFi 直接连接和 WiFi 串行总线*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

网络接口实现 MA USB 设备必须满足以下要求才能可靠地使用收件箱窗口 MA USB 主机︰

-   MA USB 集线器/设备必须支持 Wi-Fi 直接服务 (点到点服务 1.x) 通过 802.11 n / 交流和/或 802.11ad NIC

    -   将有可能进入 ASP2 (Wi-Fi 直接发现并连接)

-   MA USB 集线器/设备必须实现 WSB v0.18&lt;最新&gt;作为广告主

### <a name="deviceconnectivitymausbdevicetcpimplementation"></a>Device.Connectivity.MAUSB.Device.TCPImplementation

*MA USB TCP 实现可靠性*

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

MA USB 设备的 TCP 实现必须满足以下要求才能可靠地使用收件箱窗口 MA USB 主机︰

-   必须禁用 TCP 延迟 ACK 优化。

-   必须禁用 TCP Nagle 算法实现。

-   TCP 必须提供至少 64 KB 的接收缓冲区空间。

### <a name="deviceconnectivitymausbdeviceuseusbclassonlyforcontrollerorhub"></a>Device.Connectivity.MAUSB.Device.UseUsbClassOnlyForControllerOrHub

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

MA USB 要求是当前可选，并且直到 2017年将不会强制执行。

没有预定义的类的设备通常错误地使用类 USB。 例如，USB 鼠标使用类 HID，而 USB 智能卡使用类智能卡读取器。 保留类 USB 主控制器和根或外部 USB 集线器。 如果供应商有没有 Windows 定义的类，但使用 USB 总线的设备，它必须定义自己的类或类的 GUID。 与 USB 设备的类型关联的安装程序类不使用总线类型，必须使用。 安装程序类"USB"(ClassGuid = {36fc9e60-c465-11cf-8056-444553540000}) 是保留 （包括马萨诸塞州 USB 主机 PAL） 的 USB 主控制器和根或外部 USB 集线器。 它必须不用于其它设备类别。

 
*设计备注*

Microsoft 提供的大多数设备类型的系统定义的安装程序类。 系统定义的安装程序类 Guid 被在 Windows 驱动程序工具包，"Devguid.h"。
如果您选择了错误的类，该设备出现在错误的位置在设备管理器和 Windows Vista 用户界面。 不正确地使用此类可能会导致设备驱动程序出现故障的硬件兼容性测试。
针对将出现的 Windows 类 Guid，请查看 Windows 驱动程序工具包，"System-Supplied 设备安装程序类": <http://msdn.microsoft.com/en-us/library/ff553419.aspx>。

