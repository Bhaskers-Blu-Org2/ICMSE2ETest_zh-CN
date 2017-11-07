---
title: Device.DevFund
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 67d234ecc15fb386f3719de6f0b8a2d29f3c46b1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicedevfund"></a>Device.DevFund

 - [Device.DevFund.CDA](#device.devfund.cda)
 - [Device.DevFund.DeviceGuard](#device.devfund.deviceguard)
 - [Device.DevFund.DriverFramework.KMDF](#device.devfund.driverframework.kmdf)
 - [Device.DevFund.DriverFramework.UMDF](#device.devfund.driverframework.umdf)
 - [Device.DevFund.Firmware](#device.devfund.firmware)
 - [Device.DevFund.HALExtension](#device.devfund.halextension)
 - [Device.DevFund.INF](#device.devfund.inf)
 - [Device.DevFund.Memory](#device.devfund.memory)
 - [Device.DevFund.Reliability](#device.devfund.reliability)
 - [Device.DevFund.Reliability.3rdParty](#device.devfund.reliability.3rdparty)
 - [Device.DevFund.Reliability.Interrupts](#device.devfund.reliability.interrupts)
 - [Device.DevFund.ReliabilityDisk](#device.devfund.reliabilitydisk)
 - [Device.DevFund.Rollback](#device.devfund.rollback)
 - [Device.DevFund.Security](#device.devfund.security)
 - [Device.DevFund.Server](#device.devfund.server)
 - [Device.DevFund.Server.Nano](#device.devfund.nano)
 - [Device.DevFund.Server.PCI](#device.devfund.server.pci)
 - [Device.DevFund.StaticTools](#device.devfund.statictools)

<a name="device.devfund.cda"></a>
## <a name="devicedevfundcda"></a>Device.DevFund.CDA

*自定义驱动程序访问权限的应用程序使用。*

### <a name="devicedevfundcdaapplication"></a>Device.DevFund.CDA.Application

*自定义驱动程序访问*

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

如果设备驱动程序支持执行自定义驱动程序访问特权的应用程序，它必须声明一个受限的接口。 

通过声明一个受限的接口，必须满足以下要求︰
 

-   断言此设备驱动程序提供的设备 io 控制接口旨在通过访问 Windows 10 上使用 CreateDeviceAccessInstance() 和 IDeviceIoControl() 的硬件功能的应用程序容器中运行特权的应用程序进行访问。   

<!-- -->

-   不能直接从应用程序容器打开受限的接口。

设备驱动程序声明一个接口限制通过设置 DEVPKEY\_DeviceInterface\_属性仅限于在该接口上的真。  

<a name="device.devfund.deviceguard"></a>
## <a name="devicedevfunddeviceguard"></a>Device.DevFund.DeviceGuard

*所有的内核驱动程序必须生成与<http://aka.ms/DeviceGuard>兼容*

### <a name="devicedevfunddeviceguarddrivercompatibility"></a>Device.DevFund.DeviceGuard.DriverCompatibility

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 10 提供了一个称为[设备监护](http://aka.ms/DeviceGuard)程序将使组织能够锁定的方式提供新的和未知的恶意软件变种的高级恶意软件防护设备以及高级持久威胁 (APTs) 的新功能。 设备保护可以使用硬件技术和虚拟化来隔离代码完整性 (CI) 决策函数，从 Windows 操作系统的其余部分。 当使用基于虚拟化的安全隔离代码完整性，可以成为可执行内核内存的唯一方法是通过代码完整性验证。 这意味着，内核内存页永远不能写和可执行文件 (W + X) 并不能直接修改可执行代码。

[Windows 硬件认证的网络日志](http://go.microsoft.com/fwlink/p/?LinkId=627463)中有详细信息。

Sys 文件必须设置以下属性

| CompanyName             | 公司名称                           |
|-------------------------|----------------------------------------|
| FileDescription         | 驱动程序文件中的产品说明 |
| OriginalFilename        | 原始文件名                     |
| 产品名称             | 产品名称                           |
| 与\_FIXEDFILEINFO:      | &nbsp; |
| &nbsp;&nbsp;&nbsp;FileVer                 | 文件版本号                    |
| &nbsp;&nbsp;&nbsp;ProdVer                 | 产品版本号                 |

您可以在[MSDN 上的 VERSIONINFO 资源](https://msdn.microsoft.com/en-us/library/windows/desktop/aa381058.aspx)上找到更多详细信息。

<a name="device.devfund.driverframework.kmdf"></a>
## <a name="devicedevfunddriverframeworkkmdf"></a>Device.DevFund.DriverFramework.KMDF

*驱动程序框架要求的 KMDF*

### <a name="devicedevfunddriverframeworkkmdfreliability"></a>Device.DevFund.DriverFramework.KMDF.Reliability

*内核模式驱动程序框架 (KMDF) 驱动程序必须设计为可实现最高可靠性和稳定性，不要"泄漏"资源，如内存和 KMDF 对象。*

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

内核模式驱动程序框架 (KMDF) 驱动程序必须负责地使用缓冲池内存。 驱动程序将传递到设备驱动程序接口 (DDIs) 的句柄必须符合该模式的参数。 驱动程序的状态必须是与**WDFREQUEST**对象和**WDFQUEUE**对象的使用保持一致。
驱动程序注册事件回调函数必须遵循中断请求等级 (IRQL) 限制。

*设计备注*

有关开发满足这一要求的驱动程序的详细信息，请访问下面的网站︰ <http://msdn.microsoft.com/en-us/library/aa973499.aspx>
<http://www.microsoft.com/whdc/driver/wdf/KMDF.mspx>可以启用以下工具来验证这一要求的所有 KMDF 驱动程序︰

-   Windows® 驱动程序基础 (WDF) 验证程序。

-   处理跟踪。 将所有 KMDF 对象上启用跟踪句柄。

-   增强的 1.9 KMDF 框架驱动程序的验证程序。 增强的验证程序是用于框架 1.9 版的新功能。 此工具可通过使用 EnhancedVerifierOptions 注册表值来启用。 若要启用增强的验证程序，为驱动程序的参数设置以下注册表值\\Wdf 键︰

```
HKLM\\System\\CurrentControlSet\\Services\\\\Parameters\\Wdf
EnhancedVerifierOptions   REG\_DWORD  1
VerifierOn                REG\_DWORD  1
TrackHandles              MULTI\_SZ        \*
```

-   驱动程序验证程序。 若要启用驱动程序验证程序，请使用下面的命令︰

<blockquote>
<b>验证程序 /flags 0xfb /driver</b>
</blockquote>

运行该命令将在驱动程序验证程序下的 KMDF 驱动程序与除低资源模拟标志设置的所有标志。 有关驱动程序验证程序的详细信息，请访问下面的网站︰ http://msdn.microsoft.com/en-us/library/ff545448.aspx 在 Windows 徽标工具包，WDF 可以运行测试来验证这一要求。

### <a name="devicedevfunddriverframeworkkmdfwdfproperinf"></a>Device.DevFund.DriverFramework.KMDF.WDFProperINF

*必须正确地构建 Windows 驱动程序框架 (WDF) 驱动程序 INF 文件。*

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

<ul>
<li><p>Windows 驱动程序的基础 (WDF) 驱动程序包中的所有信息 (INF) 文件必须正确地都调用 WDF 特定部分。 正确结构化的 INF 部分有助于确保正确地安装驱动程序。 但是，即使安装了驱动程序，则效果不佳或错误地配置节可以驱动程序或设备的操作过程导致不可预知的问题。 这些问题可以通过以下设置 WDF INF 准则来防止。<br />
为了满足这一要求，所有 WDF INF 文件必须都具有下列项目︰</p></li>
<li><p>共同安装程序部分，如下︰</p></li>
<code>[DDInstall.Coinstallers]<br />
CopyFiles=<br />
AddReg=<br />
 </code></li>

<li><p>WDF 部分，如下︰</p>

<p>内核模式驱动程序框架 (KMDF) 的驱动程序︰</p>
<code>[DDInstall.Wdf]<br />
KmdfService= &lt;ServiceName&gt;, &lt;Kmdf\_Install&gt;<br />
[Kmdf\_Install]<br />
KmdfLibraryVersion=
<br />
</code>

<p>用户模式驱动程序框架 (UMDF) 的驱动程序︰</p>
<code>[DDInstall.Wdf]<br />
UmdfService=&lt;ServiceName&gt;,&lt;Umdf\_Install&gt;<br />
UmdfServiceOrder=<br />
UmdfDispatcher [Only for USB Drivers and Drivers with file handle I/O targets]=<br />
UmdfImpersonationLevel[optional]=<br/><br/>
[Umdf\_Install]<br/>
UmdfLibraryVersion=<br />
DriverCLSID=<br />
ServiceBinary=<br />
<br />
 </code>
</li>

<li><p>所有 UMDF 驱动程序 INF 文件必须都有一个 WUDFRD 服务安装部分，如下︰</p>

<code>[WUDFRD\_ServiceInstall]<br />
DisplayName = &quot;Windows Driver Foundation - User-mode Driver Framework<br />
Reflector&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WUDFRd.sys<br />
LoadOrderGroup = Base<br />
<br />
 </code>
</li>

<li><p>使用 WinUSB 驱动程序的所有 WDF 驱动程序必须都具有下面的服务安装设置︰</p>

<code>[WinUsb\_ServiceInstall]<br />
DisplayName = &quot;WinUSB Driver&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WinUSB.sys<br />
<br />
 </code>
</li>

<li><p>服务名、 硬件 Id (HWIDs)，显示的名称，并不从 WDF 示例粘贴 UMDF 的类标识符 (Clsid)。</p></li>
</ul>

<p><em>设计备注︰</em><br />
有关特定于 WDF 的 INF 设置的详细信息，请访问以下网站︰<br />
<a href="http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx" class="uri">http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx</a><br />
http://msdn.microsoft.com/en-us/library/ff560526.aspx<br />
http://msdn.microsoft.com/en-us/library/ff560526.aspx</p>


<a name="device.devfund.driverframework.umdf"></a>
##Device.DevFund.DriverFramework.UMDF

*驱动程序框架要求的 UMDF*

### <a name="devicedevfunddriverframeworkumdfreliability"></a>Device.DevFund.DriverFramework.UMDF.Reliability

*用户模式驱动程序框架 (UMDF) 的驱动程序必须是安全、 稳定、 可靠，并且不存在应用程序兼容性问题。*

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

若要帮助确保用户模式驱动程序框架 (UMDF) 的所有驱动程序符合安全标准、 稳定、 可靠，并且不存在应用程序兼容性问题，驱动程序不能有任何对象泄漏。
可以通过启用对象跟踪诊断对象泄漏。 如果发生内存泄漏，请将引用计数跟踪设置设为"打开"。 此设置将记录的历史记录为"添加引用的"和"版本的引用"计数。

这些功能可以通过以下注册表值设置为"打开":
```
HKLM\\Software\\Microsoft\\WindowsNT\\CurrentVersion\\WUDF\\Services\\{193a1820-d9ac-4997-8c55-be817523f6aa}
TrackObjects REG\_DWORD 1
TrackRefCounts REG\_DWORD 1
```

UMDF 驱动程序还必须满足以下要求︰

-   驱动程序不得尝试使用无效句柄。

-   驱动程序必须正确使用临界区和文件锁定。 锁测试的主要目的是帮助确保应用程序正确使用临界区。

-   驱动程序不会导致堆内存损坏。

-   驱动程序必须正确使用虚拟地址空间操作功能，如**VirtualAlloc**、 **VirtualFree**和**MapViewOfFile**。

-   驱动程序必须隐藏使用结构化的异常处理的访问冲突。

-   驱动程序必须正确使用线程本地存储功能。

-   驱动程序必须正确使用 COM。

在驱动程序开发和测试过程可以验证驱动程序，通过堆启用 Microsoft® 应用程序验证工具把手、 锁、 内存、 异常和 UMDF 主机进程 (即 WUDFHost.exe) 的传输层安全性 (TLS) 设置满足这些要求的合作伙伴。
有关详细信息，请参阅*开发驱动程序的 Windows 驱动程序基础*图书在下面的网站︰ <http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx>。

*设计备注*

应用程序验证工具将帮助您检查 UMDF 驱动程序广泛，有助于确保稳定和可靠的驱动程序。
对于所有的 UMDF 驱动程序，驱动程序的可靠性测试执行时将启用应用程序验证工具。

应用程序验证工具可以从以下 Microsoft 网站︰ http://www.microsoft.com/downloads/en/details.aspx?FamilyID=c4a25ab9-649d-4a1b-b4a7-c9d8b095df18。

若要启用应用程序验证工具 WUDFHost.exe，运行下面的命令︰ appverif-启用手柄锁堆内存 COM 异常 TLS-为 WUDFHost.exe。

有关 UMDF 的详细信息，请访问下面的网站︰ <http://www.microsoft.com/whdc/driver/wdf/UMDF.mspx>。

### <a name="devicedevfunddriverframeworkumdfwdfproperinf"></a>Device.DevFund.DriverFramework.UMDF.WDFProperINF

*必须正确地构建 Windows 驱动程序框架 (WDF) 驱动程序 INF 文件。*

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

Windows 驱动程序的基础 (WDF) 驱动程序包中的所有信息 (INF) 文件必须正确地都调用 WDF 特定部分。 正确结构化的 INF 部分有助于确保正确地安装驱动程序。 但是，即使安装了驱动程序，则效果不佳或错误地配置节可以驱动程序或设备的操作过程导致不可预知的问题。 这些问题可以通过以下设置 WDF INF 准则来防止。

为了满足这一要求，所有 WDF INF 文件必须都具有下列项目︰

<ul>
<li><p>共同安装程序部分，如下︰</p></li>
<li><code>[DDInstall.Coinstallers]<br />
CopyFiles=<br />
AddReg=<br />
<br />
 </code></li>

<li><p>WDF 部分，如下︰</p>

<p>内核模式驱动程序框架 (KMDF) 的驱动程序︰</p>
<code>[DDInstall.Wdf]<br />
KmdfService= &lt;ServiceName&gt;, &lt;Kmdf\_Install&gt;<br />
[Kmdf\_Install]<br />
KmdfLibraryVersion=</code>
<p>用户模式驱动程序框架 (UMDF) 的驱动程序︰</p>
<code>[DDInstall.Wdf]<br />
UmdfService=&lt;ServiceName&gt;,&lt;Umdf\_Install&gt;<br />
UmdfServiceOrder=<br />
UmdfDispatcher [Only for USB Drivers and Drivers with file handle I/O targets]=<br />
UmdfImpersonationLevel[optional]=<br /><br />
[Umdf\_Install]<br />
UmdfLibraryVersion=<br />
DriverCLSID=<br />
ServiceBinary=<br />
 </code>
</li>

<li><p>所有 UMDF 驱动程序 INF 文件必须都有一个 WUDFRD 服务安装部分，如下︰</p></li>
<li><code>[WUDFRD\_ServiceInstall]<br />
DisplayName = &quot;Windows Driver Foundation - User-mode Driver Framework<br />
Reflector&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WUDFRd.sys<br />
LoadOrderGroup = Base<br />
<br />
 </code></li>

<li><p>使用 WinUSB 驱动程序的所有 WDF 驱动程序必须都具有下面的服务安装设置︰</p>

<code>[WinUsb\_ServiceInstall]<br />
DisplayName = &quot;WinUSB Driver&quot;<br />
ServiceType = 1<br />
StartType = 3<br />
ErrorControl = 1<br />
ServiceBinary = %12%\WinUSB.sys<br />
<br />
 </code>
</li>

<li><p>服务名、 硬件 Id (HWIDs)，显示的名称，并不从 WDF 示例粘贴 UMDF 的类标识符 (Clsid)。</p></li>
</ul>

<p><em>设计备注</em><br />
有关特定于 WDF 的 INF 设置的详细信息，请访问以下网站︰<br />
<a href="http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx" class="uri">http://www.microsoft.com/whdc/driver/wdf/wdfbook.mspx</a><br />
http://msdn.microsoft.com/en-us/library/ff560526.aspx<br />
http://msdn.microsoft.com/en-us/library/ff560526.aspx</p>


<a name="device.devfund.firmware"></a>
##Device.DevFund.Firmware

*驱动程序软件包要求的固件更新软件包*

### <a name="devicedevfundfirmwareupdatedriverpackage"></a>Device.DevFund.Firmware.UpdateDriverPackage

*这些要求适用于任何进行审批和签名提交到 Microsoft 的固件更新驱动程序软件包。*

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

除了标准的驱动程序的要求，以下要求适用于驱动程序的固件更新软件包︰

-   固件包必须有效载荷只有一个资源的更新。

-   固件包必须是可配置 （请参阅 Device.DevFund.INF。\* 有关更多详细信息）。

-   之后成功固件升级中的固件版本。该资源的驱动程序包、 资源版本 （在 ESRT) 和上次尝试的版本 （在 ESRT) 的 INF 文件必须匹配。

-   固件包中的二进制文件的名称不得与任何先前的固件版本冲突。

-   成功的固件升级不能减少或消除系统中的任何设备的功能。

<a name="device.devfund.halextension"></a>
## <a name="devicedevfundhalextension"></a>Device.DevFund.HALExtension

### <a name="devicedevfundhalextensionhal"></a>Device.DevFund.HALExtension.HAL

*这些要求适用于 MS 提交供批准和签署的 HAL 扩展。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 10 移动 ARM</p>
</td></tr></table>

**说明**

除了标准的驱动程序的要求，以下要求适用于 HAL

-   HAL 扩展应该无缝地使用系统 HAL。

-   HAL 扩展应正确地签名。

<a name="device.devfund.inf"></a>
## <a name="devicedevfundinf"></a>Device.DevFund.INF

*INF restictions*

### <a name="devicedevfundinfaddreg"></a>Device.DevFund.INF.AddReg

*当使用 AddReg 指令，每个 AddReg 条目都必须指定为注册表根 HKR。*

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

HKR （含义"相对根目录"） 是可以引用位于 AddReg 在 INF 文件中的节中的唯一注册表根标识符。 其他根标识符，包括 HKCR、 HKCU、 HKLM 和 HKU，禁止 AddReg 节中使用。 旨在进行设备安装和配置只用于 AddReg 指令。

*设计备注*

INF 文件 AddReg 节中声明的所有注册表项必须都使用注册表根值，作为相对根标识符 (HKR)，除非显式异常存在这一要求中所述。

下面的示例演示注册的 COM 对象使用 AddReg 指令。 生成此示例，也可以自定义的所有对象的参数︰
```
\[COMobj.AddReg\]
HKCR,CLSID\\{&lt;CLSID&gt;},,,"&lt;MFT DLL description&gt;"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,,%REG\_EXPAND\_SZ%,"%%SystemRoot%%\\System32\\mftxyz.dll"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,ThreadingModel,,"Both"
```

COM 与对它们的使用的详细信息的注册表项的完整列表可以在 MSDN 中找到︰ http://msdn.microsoft.com/en-us/library/ms694355.aspx。

下面的示例演示使用 AddReg 指令 MFT 筛选器的注册︰
```
\[MFT.AddReg\]
HKCR,CLSID\\{&lt;CLSID&gt;},,,"&lt;MFT DLL description&gt;"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,,%REG\_EXPAND\_SZ%,"%%SystemRoot%%\\System32\\mftxyz.dll"
HKCR,CLSID\\{&lt;CLSID&gt;}\\InprocServer32,ThreadingModel,,"Both"
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,InputTypes,%REG\_BINARY%,76,45,87,2d,5e,23,...
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,OutputTypes,%REG\_BINARY%,22,5e,23,46,43,10,...
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,,%REG\_SZ%,"MFT Friendly Name"
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,MFTFlags,%REG\_DWORD%, 0x00000004
HKCR,MediaFoundation\\Transforms\\&lt;CLSID&gt;,Attributes,REG\_BINARY%, 41,46,4d,
HKCR,MediaFoundation\\Transforms\\Categories\\&lt;MFTCategoryGUID&gt;\\&lt;CLSID&gt;
HKLM,SOFTWARE\\Microsoft\\Windows Media Foundation\\ByteStreamHandlers\\audio/xyz,&lt;CLSID&gt;,,"XYZ Stream Handler"
```

此外，注册时的解码或编码 HMFT，以下注册表项之一还必须设置︰

```
DECODE HMFT
HKLM,SOFTWARE\\Microsoft\\Windows Media Foundation\\HardwareMFT,EnableDecoders, %REG\_DWORD%, 1
```

```
ENCODE HMFT
HKLM,SOFTWARE\\Microsoft\\Windows Media Foundation\\HardwareMFT,EnableEncoders, %REG\_DWORD%, 1
```

Mft 中的更多详细信息可以在 MSDN 中找到︰ <http://msdn.microsoft.com/en-us/library/windows/desktop/ms703138.aspx>。

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。 请注意，有此要求，以满足注册的组件对象模型 (COM) 对象和媒体基础变换 (MFT) 使用 AddReg 指令一些例外情况。 参考设计备注部分的这一要求的其他详细信息。</p>
</tr>
</table>


### <a name="devicedevfundinfaddservice"></a>Device.DevFund.INF.AddService

*INF 文件只能安装驱动程序相关的服务。*

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

INF AddService 指令只能引用相关的驱动程序的服务。 不是驱动程序相关的如 Microsoft Win32 服务，服务不能被引用，或者安装使用的 INF 文件。

*设计备注*

INF AddService 指令服务-安装的部分只能指定服务类型类型的代码如下︰

-   服务\_驱动程序

-   服务\_内核\_驱动程序

-   服务\_文件\_系统\_驱动程序

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
</tr>
</table>


### <a name="devicedevfundinfclassinstall32"></a>Device.DevFund.INF.ClassInstall32

*INF 文件无需定义一个 ClassInstall32 部分中的自定义类安装程序。*

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

INF 文件不能指定一个 ClassInstall32 部分中的自定义类安装程序。 因此，驱动程序软件包不能在设备安装过程中执行一个自定义类的安装程序。

*设计备注*

开发人员应使用现有的收件箱设备安装程序类之一为其设备。 如果有必要可以定义新的设备安装程序类，新的安装程序类无法采用类别安装程序作为设备安装过程的一部分。 下面的示例演示一个 INF ClassInstall32 部分，定义一个自定义类的安装程序，并因此符合此要求。

```
\[ClassInstall32.ntx86\]            ; Declare a ClassInstall32 section for the x86
                                                ; architecture.
AddReg=SetupClassAddReg    ; Reference to the ClassInstall32 AddReg section.

; Place additional class specific directives here

\[SetupClassAddReg\]                ; Declare a class specific AddReg section.

; Device class specific AddReg entries appear here.

; The next line defines the class installer that will be executed when
; installing devices of this device-class type. Defining a registry entry
; of this type is no longer supported and the driver package fails to meet
; this device fundamental requirement.
**\[HKR,,Installer32,,"class-installer.dll,class-entry-point"\] **
```

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
</tr>
</table>



### <a name="devicedevfundinfcomplexdevicematching"></a>Device.DevFund.INF.ComplexDeviceMatching

*不支持 INF 指令相关的复杂的设备匹配逻辑。*

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

INF 文件不支持匹配逻辑的复杂设备。 具体而言，将不支持指定 DeviceID 不应安装，当匹配的硬件 Id 或 CompatibleID 中的 DDInstall 部分中，存在的设备的能力。

*设计备注*

不可能在 INF 文件中引用下面的 INF 指令︰

-   ExcludeID

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
</tr>
</table>


### <a name="devicedevfundinfddinstallcoinstallers"></a>Device.DevFund.INF.DDInstall.CoInstallers

*INF 文件不能引用任何辅助安装程序 DDInstall.CoInstallers 部分中。*

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

INF 文件不能引用任何辅助安装程序 DDInstall.CoInstallers 部分中。 因此，驱动程序包在设备安装过程中不能执行任何合用安装服务。

*设计备注*

在设备安装过程中，禁止合用安装服务的执行。 下面的示例演示注册的特定于设备的共同安装程序和设备类共同安装程序。 在 INF 文件中不允许使用两种类型的合用安装服务并包含将导致无法满足要求。
特定于设备的共同安装程序的示例︰

```
; Registering one or more device-specific co-installers requires adding
; adding a REG\_MULTI\_SZ value using an AddReg directive. The following
; shows the general form for registering a device-specific co-installer.
;  :
;  :
\[DestinationDirs\]         ; Destination dir for the co-installer dll
XxxCopyFilesSection = 11           ; DIRID\_for %WINDIR%\\System32 dir
                                   ; Xxx = driver or device prefix
;  :
;  :
\[XxxInstall.OS-platform.CoInstallers\]       ; Define co-installers section
CopyFiles = XxxCopyFilesSection             ; Copy files directive
AddReg = Xxx.OS-platform.CoInstallers\_AddReg        ; Add registry directive

\[XxxCopyFilesSection\]              ; Define the co-installer copy files
XxxCoInstall.dll                   ; section

\[Xxx.OS-platform.CoInstallers\_AddReg\]       ; Define the co-installer AddReg
                                            ; section

; The next line defines the co-installer that will be executed when
; installing this device. Defining a registry entry of this type is no
; longer supported and the driver package fails to meet this device
; fundamental requirement.
**HKR,,CoInstallers32,0x00010000,"XxxCoInstall.dll, \\**
**  XxxCoInstallEntryPoint"**
Device-class co-installer example:
\[Xxx.OS-platform.CoInstallers\_AddReg\]       ; Define the co-installer AddReg
                                            ; section

; Similar format to the device-specific co-installer example, except the
; registry location is under HKLM. The next line defines the co-installer
; executed after any installation operations complete for the given device
; setup class GUID. Defining a registry entry of this type is no
; longer supported and the driver package fails to meet this device
; fundamental requirement.
**HKLM,System\\CurrentControlSet\\Control\\CoDeviceInstallers, \\**
**{SetupClassGUID}, 0x00010008,"DevClssCoInst.dll\[,DevClssEntryPoint\]"**
```

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
</tr>
</table>



### <a name="devicedevfundinfdeviceconfigonly"></a>Device.DevFund.INF.DeviceConfigOnly

*INF 文件中不能引用 INF 指令没有直接关系到设备的配置。*

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

提供配置功能之外是什么配置的硬件设备所需的 INF 指令不再受支持。 INF 文件和驱动程序软件包中的所有支持文件都必须使用仅对设备的安装和配置。

*设计备注*

不可能在 INF 文件中引用下面的 INF 指令︰

1.  RegisterDlls
2.  UnregisterDlls
3.  ProfileItems
4.  UpdateInis
5.  UpdateIniFields
6.  Ini2Reg

请注意，RegisterDlls 指令不再可以在 INF 文件中声明，尽管仍有可能注册组件对象模型 (COM) 和媒体基础变换 (MFT) 对象从使用 AddReg 指令的 INF 文件。 AddReg 指令在 HKLM 注册表配置单元下允许 COM/MFT 注册信息和密钥的声明。 有关为此目的 AddReg 指令的使用信息，请参阅 Device.DevFund.INF.AddReg Windows 硬件认证要求。

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
<td>
</tr>
</table>


 

### <a name="devicedevfundinfdeviceresourceconfig"></a>Device.DevFund.INF.DeviceResourceConfig

*INF 基于设备资源配置和在 INF 文件中不能执行非 PnP 相关的配置。*

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

INF 文件不能用于执行设备资源配置或非 PnP 相关的配置任务。 不再支持多种 INF 指令和各节。

*设计备注*

在 INF 文件中不能引用以下的 INF 部分和指令︰

-   \[DDInstall.LogConfigOverride\]节

-   LogConfig

-   \[DDInstall.FactDef\]节

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
</td>
</tr>
</table>



### <a name="devicedevfundinffilecopyrestriction"></a>Device.DevFund.INF.FileCopyRestriction

*INF 基于文件的复制限制*

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

文件复制的目标位置将受到限制，以防止在系统上的适当位置安装驱动程序驱动程序包。

*设计备注*

当使用 CopyFiles 指令，指定文件的目标目录必须是下面的 DIRID 值中的一个︰

-   11 (对应于 %WINDIR%\\System32 目录) 

-   12 (对应于 %WINDIR%\\System32\\驱动程序目录)

这些表示为相应 DIRID 的目标目录将是一个有效的副本文件的位置。

<table>
<tr>
<th>异常</th>
<td>
<p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p>
</td>
</tr>
</table>



### <a name="devicedevfundinffileorregistrymodification"></a>Device.DevFund.INF.FileOrRegistryModification

*删除或修改现有的文件、 注册表项和/或服务不允许从一个 INF 文件内。*

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

删除或修改注册表项、 服务和文件的 INF 文件指令不再受支持。

*设计备注*

不可能在 INF 文件中引用下面的 INF 指令︰

-   DelReg
-   DelService
-   DelPropertry
-   BitReg
-   DelFiles
-   RenFiles

<table>
<tr>
<th>异常</th>
<td><p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p></td>
</tr></table>

### <a name="devicedevfundinfinstallmanagement"></a>Device.DevFund.INF.InstallManagement

*使用一个 INF 文件安装的文件的管理仅限于系统。*

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

以独占方式由 Windows 管理到使用的 INF 文件的系统上安装的任何文件。 插即用 (PnP) 防止直接修改 INF 中引用的文件的应用程序。

*设计备注*

INF 文件中必须包含设置为值 1 中的 PnpLockDown 指令\[版本\]部分。 这将显示，如下所示在 INF 文件中︰

```
\[Version\]
; Other Version section directives here.
PnpLockDown=1
```

<table>
<tr>
<th>异常</th>
<td><p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p></td>
</tr></table>

### <a name="devicedevfundinflegacysyntax"></a>Device.DevFund.INF.LegacySyntax

*在 INF 文件中无法进行传统的服务配置。*

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

不再支持使用传统的 INF 语法的服务配置。

*设计备注*

在 INF 文件中不能引用 INF 服务安装部分的以下指令︰

-   LoadOrderGroup

<table>
<tr>
<th>异常</th>
<td><p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p></td>
</tr></table>

### <a name="devicedevfundinftargetosversion"></a>Device.DevFund.INF.TargetOSVersion

*TargetOSVersion 修饰的 INF 文件中不能包含 ProductType 标志或 SuiteMask 标志。*

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

在\[制造商\]INF 文件，修饰用于标识该驱动程序包的目标操作系统 TargetOSVersion 部分。 ProductType 标志或 SuiteMask 标志，不能包含 TargetOSVersion 修饰。

*设计备注*

在 Windows 7 和更早的操作系统版本中，TargetOSVersion 修饰格式如下︰

```
nt[Architecture].[OSMajorVersion][.[OSMinorVersion][.[ProductType][ \
  .[SuiteMask]]]]
```

从开始 Windows 8，ProductType 字段和 SuiteMask 字段不再 TargetOSVersion 修饰中的有效字段。

<table>
<tr>
<th>异常</th>
<td><p>这是 Windows 10 移动 （ARM、 ARM64，x86） 的要求但建议 Windows 10 (x64 x86) 桌面版本 （家庭、 Pro、 企业和教育） 和 Windows 服务器 2016年技术预览 x64。 它将要求将来对这些体系结构。</p></td>
</tr></table>

<a name="device.devfund.memory"></a>
##Device.DevFund.Memory

*相关的内存配置的要求*

### <a name="devicedevfundmemorydriverfootprint"></a>Device.DevFund.Memory.DriverFootprint

*驱动程序必须占用有限的内存需求量。*

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

驱动程序必须占用小于或等于在内存中下大小非分页的代码页︰

-   未分页的代码页

| 驱动程序类型 | 图形驱动程序 | 所有其他驱动程序类型 |
|-------------|------------------|------------------------|
| x86/ARM     | &lt;= 10 MB      | &lt;= 1.66 MB          |
| x64         | &lt;= 10 MB      | &lt;= 5.45 MB          |

-   **驱动程序锁定分配**（包括 MDL 分配和连续的内存分配）

    -   12 MB 的这两种体系结构的所有驱动程序类型。

-   **非页面缓冲池**-为 Windows 10 中，驱动程序必须占用小于或等于下列非页面缓冲池的大小，在内存中︰

| 驱动程序类型 | 图形驱动程序 | 所有其他驱动程序类型 |
|-------------|------------------|------------------------|
| x86/ARM     | 6 MB             | 4 MB                   |
| x64         | 10 MB            | 7 MB                   |

-   遥测基于阈值︰ X86/ARM – 4 MB 涵盖第 80 百分点，X64 – 7 MB 介绍了 76th 个百分点值从池中分配示例

*设计备注*

相应的测试将检查的大小，以 mb 为单位的驱动程序未分页的代码页。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td><p>驱动程序的非分页内存使用情况构成了在系统的整个生存期内存利用率方面的固定的成本。 这些贡献显著地朝着总的操作系统内存占用量，和大多数驱动程序会在内存中始终存在。 优化内存的驱动程序将提供改进的用户体验和更好的总体系统响应能力由于更好的用户应用程序的内存的可用性。</p>
<p>非分页的驱动程序的占地面积缩减直接提高了基线内存消耗，从而提高可伸缩性的操作系统。 针对 Windows 8 的当前 WHCK 测试涵盖驱动程序锁定分配 （MDL/连续内存分配） 和非页面缓冲驱动程序代码。 非分页池使用是现有的测试未覆盖的只非分页的驱动程序的占地面积方面。</p></td>
</tr>
</table>

### <a name="devicedevfundmemorynxpool"></a>Device.DevFund.Memory.NXPool

*驱动程序的所有池分配都必须在 NX 池中。*

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

必须在非可执行文件 (NX) 池中进行驱动程序池分配。

*设计备注*

引入了一种新型的非页面缓冲池是一个非可执行文件 (NX) 池。 由于非可执行文件，它本质上是与可执行非分页 (NP) 池，相比更安全并更好地防止溢出攻击。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td><p>将分配移动到非可执行文件池，无管理系统二进制文件的可执行代码的攻击面最小化。</p></td>
</tr>
</table>


<a name="device.devfund.reliability"></a>
##Device.DevFund.Reliability

*可靠性测试包含以前的 DEVFUND 测试的内容。*

### <a name="devicedevfundreliabilitybasicreliabilityandperformance"></a>Device.DevFund.Reliability.BasicReliabilityAndPerformance

*驱动程序被设计为可实现最高可靠性和稳定性，不要"泄漏"资源，例如内存。*

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

驱动程序组件不会导致系统崩溃或泄漏资源。 这些资源包括但不是限于以下︰

-   Memory
-   图形设备接口 (GDI) 或用户对象
-   内核对象，例如文件、 mutex、 信号量，并且设备句柄
-   关键部分
-   磁盘空间
-   打印机句柄

*设计备注*

为了提高可靠性和 Windows 驱动程序的稳定性，一系列的通用驱动程序质量测试受到所有驱动程序。 这些测试包括︰

<dl>
<dt>嵌入的签名验证测试</dt>
<dd><p>此项测试确认启动开始驱动程序嵌入的签名。</p></dd>

<dt>设备安装文件系统一致性检查</dt>
<dd><p>此测试验证系统的资源已被覆盖在一个设备/驱动程序的安装过程。</p></dd>

<dt>设备安装其他设备稳定性的检查</dt>
<dd><p>此项测试确认没有设备或驱动程序，除接受测试，设备已经受到设备 / 驱动程序安装或共同安装过程。</p></dd>

<dt>PCI 根端口意外删除测试</dt>
<dd><p>此测试中移除 PCI 根端口的设备 （如果适用）。</p></dd>

<dt>PNP （禁用和启用） 与 IO 之前和之后</dt>
<dd><p>此测试执行基本 I/O 和基本 PNP 禁用/启用测试设备上。</p></dd>

<dt>重新安装与 IO 之前和之后</dt>
<dd><p>此测试卸载和重新安装测试设备的驱动程序，运行在这些设备上的 I/O。</p></dd>

<dt>睡眠与 PNP （禁用和启用） 与 IO 之前和之后</dt>
<dd><p>此测试周期通过各种睡眠状态的系统，每个睡眠状态周期前后在测试设备上执行 I/O 和基本 PNP （禁用/启用）。</p></dd>

<dt>睡眠与 IO 之前和之后</dt>
<dd><p>此测试周期通过各种睡眠状态的系统，在每个睡眠状态周期前后在设备上执行 I/O。</p></dd>

<dt>睡眠与 IO 期间</dt>
<dd><p>此测试周期通过各种睡眠状态的系统，在每个睡眠状态周期在设备上执行 I/O。</p></dd>

<dt>插驱动程序测试</dt>
<dd><p>此测试试验测试驱动程序中的 PnP 相关的代码路径。</p></dd>

<dt>设备路径 Exerciser 测试</dt>
<dd><p>这包括一组测试，每个点的致力于提供一个不同的条目或 I/O 接口。 这些测试旨在评估一个驱动程序，而不是其功能的可靠性。</p></dd>

<dt>混乱的测试</dt>
<dd><p>此运行即插即用测试 （禁用/启用、 重新平衡、 删除/重新启动、 意外删除和 DIF 删除） 和驱动程序模糊化测试并行测试设备同时在相同的时间周期和所有受支持的休眠状态 （S1、 S2、 S3、 S4 和连接待机） 测试系统的测试。</p></dd>
</dl>

与使用标准设置启用驱动程序验证程序将运行所有这些测试。

此外，将在所有适用工具包测试启用驱动程序验证程序。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td><p>电源管理使用情况、 即插即用的错误以及 IO 相关的错误导致了较差的最终用户体验和可能会导致系统挂起、 崩溃和失败。 这些测试有助于识别一些常见的驱动程序问题。</p></td>
</tr>
</table>


### <a name="devicedevfundreliabilitybasicsecurity"></a>Device.DevFund.Reliability.BasicSecurity

*设备驱动程序必须正确地处理各种用户模式以及内核的内核 (DEVFUND 0004) 的 I/O 请求。*

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

连接驱动程序的可靠性和安全性。 可靠的驱动程序保护系统免遭恶意攻击。
通过对设备驱动程序运行的设备路径 Exerciser 测试将验证法规遵从性。 设备路径 Exerciser 包含一套测试中，每个点的致力于提供一个不同的条目或 I/O 接口。 这些测试旨在评估一个驱动程序，而不是其功能的可靠性。

在测试期间，设备路径 Exerciser 通常发送类似调用驱动程序的几十万连续不断地。 调用包含不同数据访问方法、 有效和无效的缓冲区长度和地址和排列的函数参数，包括空格、 字符串和字符可能会被误解的缺陷分析或错误处理例程。

设备驱动程序必须遵守 Windows 驱动程序工具包中所定义的可靠性准则。 所有用户模式 I/O 请求和内核为内核的 I/O 请求必须可以正确都处理，有助于确保安全设备和驱动程序。

设计备注︰

潜在的安全漏洞包括故障检查缓冲区溢出，无法处理从用户模式错误数据和意外词条的误操作点到驱动程序。 如果无法识别和未更正保留这样的漏洞，恶意程序可以可能发出的拒绝服务攻击或否则绕过系统的安全性。

有关其他信息，请参阅 Windows 驱动程序工具包中的"创建可靠和安全的驱动程序"和"创建可靠内核模式驱动程序"主题。

### <a name="devicedevfundreliabilitybootdriverembeddedsignature"></a>Device.DevFund.Reliability.BootDriverEmbeddedSignature

*启动驱动程序必须是使用嵌入式签名的自签名。*

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

所有启动开始驱动程序必须嵌入的都签名使用从商业证书颁发机构软件发行者的证书 (SPC)。 SPC 必须是有效的内核模块。 驱动程序必须通过自我签名的驱动程序提交前嵌入的签名。

*设计备注*

有关如何嵌入签名启动开始驱动程序的详细信息，请参阅第 6 步︰ 发布和签名的驱动程序通过使用嵌入式签名图像文件"在下面的网站︰ <http://go.microsoft.com/fwlink/?LinkId=237093>

此文件是嵌入签名后，可以使用 SignTool 来验证签名。 检查的结果来验证内核策略的 SPC 证书链的根是"Microsoft 代码验证根"。 下面的命令行验证 toaster.sys 文件上的签名︰

<blockquote>
<b>signtool 验证 /kp /v amd64\\toaster.sys</b>
</blockquote>

```
Verifying: toaster.sys

SHA1 hash of file: 2C830C20CF15FCF0AC0A4A04337736987C8ACBE3

Signing Certificate Chain:

Issued to: Microsoft Code Verification Root

Issued by: Microsoft Code Verification Root

Expires: 11/1/2025 5:54:03 AM

SHA1 hash: 8FBE4D070EF8AB1BCCAF2A9D5CCAE7282A2C66B3

Successfully verified: toaster.sys

Number of files successfully Verified: 1

Number of warnings: 0

Number of errors: 0
```

在 Windows 徽标工具包，将使用嵌入的签名验证测试测试这一要求。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>启动驱动程序必须嵌入的签名后才可启动过程正常工作。</p>
</tr>
</table>


### <a name="devicedevfundreliabilitydriverinstalluninstallreinstall"></a>Device.DevFund.Reliability.DriverInstallUninstallReinstall

*设备和驱动程序安装/卸载-安装/重新-installation 必须完成没有任何错误。这包括功能的多功能设备的驱动程序。*

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

设备和驱动程序安装、 卸载或重新安装不能在任何情况下。

除非系统需要重新启动驱动程序安装不得导致系统停止运行或重新启动而无需用户交互。

有单独的驱动程序启用不同的功能的多功能设备，为每个驱动程序必须能够安装和卸载单独使用没有启动顺序或隐藏的依赖项。 多功能设备是支持多种功能，一台设备。

用于操作的内置驱动程序的设备还必须满足这一要求。 此要求不适用于互联网小型计算机系统接口 (iSCSI) 设备。

*设计备注*

在多功能设备的情况下加载不同的驱动程序的各个函数的监督驱动程序不适与 Windows®。 特别是，驱动程序的支持很可能会丢失后的操作系统重新安装或升级，或通过 Windows Update 分发新的驱动程序。 因此，应避免使用此类监督的驱动程序。

使用"重新安装与 IO"测试，将测试这一要求。

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>此要求不适用于互联网小型计算机系统接口 (iSCSI) 设备。 PEP 和 HAL 扩展将考虑豁免这一要求。</p>
</tr>
</table>


### <a name="devicedevfundreliabilitydriveruninstallinstallotherdevicestability"></a>Device.DevFund.Reliability.DriverUninstallInstallOtherDeviceStability

*安装或卸载该驱动程序不得减少或消除的其他设备或系统上安装了同一设备的其他功能部件的功能。*

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

安装或卸载设备驱动程序不得减少或消除系统安装其他设备的功能。

该职能部门是否多功能设备上或作为一个整体的系统上，此要求也适用于职能部门的多功能设备。

*设计备注*

有关此要求的测试步骤详列其他设备稳定性测试设备安装检查︰ <http://msdn.microsoft.com/en-us/library/ff561407.aspx>。
 

### <a name="devicedevfundreliabilitynoreplacingsyscomponents"></a>Device.DevFund.Reliability.NoReplacingSysComponents

*供应商提供的驱动程序或软件必须更换系统组件。*

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

驱动程序或软件安装必须覆盖任何受保护的操作系统文件。 这包括不由 Microsoft，但它是操作系统的一部分的文件。

如果制造商的信息文件 (INF) 复制操作系统提供的任何文件，INF 必须从 Windows® 产品磁盘或预安装的源文件复制这些文件，除非组件是许可的可再发行组件。

不允许命名后的操作系统提供的驱动程序不由操作系统提供的驱动程序。

### <a name="devicedevfundreliabilitynormalopwithdep"></a>Device.DevFund.Reliability.NormalOpWithDEP

*所有的驱动程序必须正常运行，无错误地执行与数据执行保护 (DEP) 启用。*

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

有助于确保正确的设备和驱动程序的操作，提高抵御病毒和其他安全威胁的 Windows® 系统的安全性，启用数据执行保护 (DEP) 后的所有驱动程序必须正常工作。 DEP 可监视程序以确保程序安全地使用系统内存。 DEP 关闭尝试以不正确的方式从内存执行代码的任何程序保护系统。

为了满足这一要求，驱动程序必须不执行默认的堆页如数据页中的代码、 各种堆栈和内存池页。

DEP 是一套执行额外检查以帮助防止在系统上运行恶意代码的内存的硬件和软件技术。 DEP 的主要优点是有助于防止从数据页的代码执行。 通常情况下，不从默认堆和堆栈执行代码。 硬件强制 DEP 检测从这些位置运行的代码执行时，将引发异常。 软件实施 DEP 可帮助阻止恶意代码利用的异常处理机制在 Windows 中。

*设计备注*

DEP 有关的详细信息，包括如何启用 DEP，请访问下面的网站︰ <http://support.microsoft.com/kb/875352>。

用于 DEP 的测试目前系统测试类别中 Windows 硬件认证工具包 (WHCK) 的一部分。 此测试的设备版本将引入之前徽标对强制执行这一要求。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>DEP 可帮助增强运行 Windows 操作系统的系统的安全性。 DEP 还有助于防止恶意代码、 病毒和其他安全威胁。 使此要求必不可少的设备，将有助于确保保护所有签名的驱动程序通过硬件徽标计划，和驱动程序签名从防止恶意软件。</p>
</tr>
</table>


### <a name="devicedevfundreliabilitypnpids"></a>Device.DevFund.Reliability.PnPIDs

*嵌入到硬件设备，包括一个多功能设备，每个功能单元中插 Id 必须具有设备 Id 以支持即插。*

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

每个连接到扩展总线的设备必须能够提供其自己的设备 id。 每个函数或单独枚举多功能附加设备上的设备还必须提供设备 ID 的设备的功能使用总线。

以下是插设备 Id 的特定要求︰

-   必须单独列举每个单独的函数或系统主板上的设备。 因此，每个函数或设备必须提供设备 ID 的使用，总线当前插指标中技术指标的要求。

-   如果枚举扩展卡上的设备，该设备必须有一个唯一的 ID 和当前卡连接到总线的设备 ID 要求根据其自己的资源。 此要求完全包括单独列举的多功能卡或多功能的设备芯片。

-   特定于设备的即插规范中定义可以与具有相同的模型名称，其他设备共享插 ID。

-   每个逻辑设备的功能必须有一个不同即插即用 id。

-   安装 (INF) 部分必须关闭仅根据 Windows® 的驱动程序工具包中的插准则最特定 ID 的关键。

-   对于如串行、 并行和红外端口的旧式设备，旧式即插即用准则定义要求和设备自动配置、 资源分配和动态禁用功能的说明。

注意︰ 完全看不到操作系统，例如带外系统管理的设备的设备或智能输入/输出 (I2O) 隐藏设备，仍然必须使用高级配置和电源接口 (ACPI) 的方法来正确地保留资源并避免潜在的冲突。

多功能设备的单个设备 ID 要求的例外情况如下︰
 
-   同一个设备类，如多行的串行设备的多个设备不需要单独的设备 Id。

-   生成的加速器或辅助处理器和不具有独立的硬件 I/O 设备不需要单独的设备 Id。 该处理器必须具有一个 ID，然后 MF.sys 文件必须可用于枚举从属设备。

如果 OEM 使用专有机制来分配硬件资产或序列号，这些信息必须可通过 Windows 硬件检测技术的操作系统。

*设计备注*

查看 Windows 硬件检测实施准则 (WHIIG)，Version1.0，在下面的网站︰ <http://go.microsoft.com/fwlink/?LinkId=237095>*.*

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>唯一即插即用 ID 设备提供良好的用户体验。  因为唯一的设备安装设备驱动程序，这种要求将有助于防止 Windows Update 中出现的问题。 这一要求现在还包括相关的多功能设备，以便在设备与 Windows 一起使用时好即插即用体验的插的所有方面。 当 Windows 用于认证的设备，此要求增强了兼容性和可靠性。</p>
</tr>
</table>


### <a name="devicedevfundreliabilitypnpirps"></a>Device.DevFund.Reliability.PnPIRPs

*驱动程序必须支持所有即插即用 Irp*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

驱动程序必须支持根据要求所有插即用 I/O 请求数据包 (Irp) 以下网站︰

<http://msdn.microsoft.com/en-us/library/ff558807.aspx>下面的 Irp 通常是驱动程序问题的原因。 特别注意应给予它们的实现︰

- 删除

  - IRP\_明尼苏达州\_查询\_删除\_设备

  - IRP\_明尼苏达州\_取消\_删除\_设备

  - IRP\_明尼苏达州\_删除\_设备

- 重新平衡

  - IRP\_明尼苏达州\_查询\_停止\_设备

  - IRP\_明尼苏达州\_查询\_资源\_要求

  - IRP\_明尼苏达州\_筛选器\_资源\_要求

  - IRP\_明尼苏达州\_取消\_停止\_设备

  - IRP\_明尼苏达州\_停止\_设备

  - IRP\_明尼苏达州\_启动\_设备

  - IRP\_明尼苏达州\_中删除

- 意外删除

  - IRP\_明尼苏达州\_意外\_删除

 

### <a name="devicedevfundreliabilityproperinf"></a>Device.DevFund.Reliability.ProperINF

*设备驱动程序必须为其设备类 (DEVFUND-0001) 格式正确 INF。*

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

驱动程序安装和删除必须使用基于 Windows® 的方法。 因此，只有信息文件 (INF)-允许基于的安装例程。 设备驱动程序必须正确格式化的设备 INF，Windows 驱动程序工具包 (WDK)"创建一个 INF 文件"主题中所述。

*设计备注*

"针对单个 INF INFTest"测试 Windows 硬件认证工具包 (WHCK) 中验证了这一要求。 有关此测试的详细信息，请参阅帮助文档中的测试套件。

注︰ 如果设备不提供一个 INF 文件 （即，驱动程序和 INF 文件仅设备使用），这一要求不适用。

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>如果设备不提供一个 INF 文件 （即，驱动程序和 INF 文件仅设备使用），这一要求不适用。</p>
</tr>
</table>



### <a name="devicedevfundreliabilityremotedesktopservices"></a>Device.DevFund.Reliability.RemoteDesktopServices

*客户端和服务器设备必须正常工作之前、 期间和之后快速用户切换或 Microsoft 远程桌面服务会话 (DEVFUND-0009)。*

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

设备必须支持快速用户切换 (FUS) 和远程桌面服务，而不会丢失数据之前,、 期间或之后的会话。 设备的任何用户界面 (UI) 必须显示在用户界面应用到会话中。 设备使用率必须无限期地阻止其他用户会话中。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>FUS 和远程桌面服务是 Windows® 功能。 若要提供正确和一致的用户体验，每个设备需要正确地使用这些服务。</p>
</tr>
</table>


### <a name="devicedevfundreliabilitypcsupportslowpowerstates"></a>Device.DevFund.Reliability.PCSupportsLowPowerStates

*所有设备和驱动程序必须都支持 S4 和 S5**和 S0 低功耗空闲或 S3 休眠状态的系统集成在上或连接到它们。*

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

所有设备和驱动程序必须都满足以下要求的系统的输入 S4 （休眠） 和 S5 （软关机） 和任一 S0 低电源处于空闲状态或 S3 （睡眠）︰
 

-   所有设备和驱动程序必须正确都支持的系统，转到 S0、 S3、 S4，请求或 S5 状态。

-   设备和驱动程序不能阻止来自系统的请求。

-   设备必须支持的 S0、 S3、 S4 和 S5 状态。

-   所有的设备必须能够继续从 S0、 S3、 S4 和 S5 休眠状态和醒着的向上后会完全起作用。

-   设备和 （在多功能设备） 及其职能单位必须枚举适当设备恢复后。

-   所有设备和驱动程序必须正确地对事件作出都响应插，IOCtl 调用和 I/O 请求与睡眠状态转换同时颁发。

这一要求可以帮助确保设备用作系统的一部分或从外部连接到系统时，所有经认证和签名的设备将支持 S0、 S3、 S4 和 S5 休眠状态。 这种要求将有助于节省电源时系统未被使用的系统。 电源管理是良好的用户体验的一个重要方面。 系统应该能够控制哪些设备置于休眠状态时并不使用这些设备。 所有设备必须都符合系统进入睡眠状态并不能阻止该请求，从而使电源的另一个消耗的请求。

*设计备注*

这一要求将使用"睡眠与 IO 的压力"测试和"PnPDTest 与 DevPathExer 与并行的并发 IO"测试 Windows 硬件实验室工具包 (HLK) 中进行测试。

用于测试的系统必须支持 S0、 S3、 S4 和 S5。

注意支持连接待机状态的系统不支持 S3，并可能会或可能不支持 S4。 这种系统中的设备必须支持连接待机状态和 S4 请求，这一系统 （如果适用）。

### <a name="devicedevfundreliabilitysignable"></a>Device.DevFund.Reliability.Signable

*设备驱动程序必须能够由 Microsoft 签名。*

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

所有设备必须有都代码签名的驱动程序。 驱动程序的 Windows® 证书必须是代码签名和必须满足的 Windows 驱动程序工具包中定义的 Microsoft® 准则提交"WHQL 数字签名"的主题。 所有启动开始驱动程序必须都是使用证书有效的内核模块中嵌入签名。 设备必须通过自我签名设备提交给 Microsoft 认证前嵌入的签名。 所有驱动程序都通过自签名之前驱动程序被提交到 Microsoft，尽管这仅需的嵌入的签名的建议启动开始驱动程序。

*设计备注*

有关数字签名的要求，请参阅以下网站上的"驱动程序签名/文件保护"主题︰ <http://go.microsoft.com/fwlink/?LinkId=36678>。

INF2CAT signability 验证工具会自动安装在 Microsoft 网站创建提交第一次。 有关 INF2CAT 工具的详细信息，请访问下面的网站︰ <http://go.microsoft.com/fwlink/?LinkId=109929>。

**其他信息**

<table>
<tr>
<th>异常</th>
<td>
<p>此要求不适用于使用操作系统的内置驱动程序的设备。</p>
</td>
</tr>
</table>


### <a name="devicedevfundreliabilityswdeviceinstallsusepnpapis"></a>Device.DevFund.Reliability.SWDeviceInstallsUsePnPAPIs

*软件启动设备并安装必须使用插 Api 来安装设备驱动程序。*

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

设备安装程序直接操纵插资源导致系统不稳定。 因此，直接插资源的操作将阻止更高版本的 Windows® 上。 若要帮助确保与 Windows 版本兼容，必须使用标准即插即用的应用程序编程接口 (Api) 来安装设备驱动程序。

*设计备注*

In Windows Vista® 和更高版本的操作系统，如**SetupCopyOEMInf**调用的标准即插即用电话自动预登录系统中设备安装所有必需的文件。 预暂存的驱动程序包将促进过程系统升级到 Windows Vista 或更高版本的 Windows 操作系统中的驱动程序软件包迁移。 我们强烈鼓励以满足此徽标要求的驱动程序安装框架工具的使用。 DIFxAPI、 DIFxAPP 或 DPInst DIFx 工具的使用以满足这一要求。

<a name="device.devfund.reliability.3rdparty"></a>
## <a name="devicedevfundreliability3rdparty"></a>Device.DevFund.Reliability.3rdParty

*可靠性测试包含以前的 DEVFUND 测试的内容。*

### <a name="devicedevfundreliability3rdpartyformertests"></a>Device.DevFund.Reliability.3rdParty.FormerTests

*以前测试映射要求*

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

Device.DevFund.Reliability.3rdParty 的功能，这一要求是前者 DevFund 测试的其他需求中找不到映射的占位符。

**其他信息**

| 异常 | 此要求不适用于使用操作系统的内置驱动程序的设备。 |
|------------|------------------------------------------------------------------------------------------------|

<a name="device.devfund.reliability.interrupts"></a>
## <a name="devicedevfundreliabilityinterrupts"></a>Device.DevFund.Reliability.Interrupts

*可靠性对于设备中断*

### <a name="devicedevfundreliabilityinterruptsbasicreliabilityandperformance"></a>Device.DevFund.Reliability.Interrupts.BasicReliabilityAndPerformance

*驱动程序不能超过的最大的中断，数和所定义的操作系统必须支持资源仲裁到最低级别*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

驱动程序必须能够承受系统重新平衡中断资源有无故障，包括理论的最小值的行基于中断操作系统选择任何替代方案。

中断仲裁可能需要多个迭代。 驱动程序必须准备容忍在其初始中断请求将被拒绝的情况。 为了支持最佳及时中断仲裁，驱动程序应提供连续降低的中断计数在多个备选方案。 驱动程序应避免每个内核时可能多个中断请求。 任何请求大于 2048年中断每个设备函数都将被拒绝，每 PCIe 3.0 定义 MSI-X 表条目限制为 2048 每个设备。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>每个内核的多个中断请求可能会导致设置中的 IDT 耗尽其中许多设备都存在。 申请总数中断通常基于核心的数量，将导致内存分配问题。</p>
</tr>
</table>


<a name="device.devfund.reliabilitydisk"></a>
##Device.DevFund.ReliabilityDisk

*目标磁盘设备的可靠性测试*

### <a name="devicedevfundreliabilitydiskiocompletioncancellation"></a>Device.DevFund.ReliabilityDisk.IOCompletionCancellation

*设备驱动程序必须按照中 I/O 完成/取消准则 (DEVFUND 0013) 的设计细节。*

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

驱动程序的 I/O 完成和取消准则提供了规范性的要求，帮助确保设备驱动程序不会停止响应，并可以完全取消。 这些要求还建议可以按照驱动程序以提高性能的最佳做法。

根据该原则，所有的设备驱动程序必须满足以下要求︰

-   在五秒之内，不是资源有限的环境中，必须完成所有 I/O 请求数据包 (Irp)，将被取消。 即使取消请求可能在任何时刻，到达，即使之前驱动程序的调度例程查看 IRP，不取消应该被遗漏。

-   在 IRP 取消时，为了防止不利于取消高负载情况下的系统性能，必须释放已取消的 IRP 分配的所有资源。 IRP 的取消应关闭任何 I/O 密集型过程。

此外，我们强烈建议驱动程序执行的操作取决于期间取消其他资源的分配。

*设计备注*

Windows® I/O 管理器包括增强支持取消 MJ 的\_IRP\_创建过程。 Win32 应用程序编程接口 (Api) 包括支持取消的同步操作，如 CreateFile 的功能增强。 这些增强功能允许在多个环境中比在早期操作系统中 I/O 取消。 有关详细信息，请参阅"I/O 完成/取消准则"白皮书在下面的网站︰ <http://www.microsoft.com/whdc/driver/kernel/default.mspx>。

有关设计完成和取消逻辑的驱动程序的详细信息，请参阅 Windows 开发工具包 (WDK) 中的以下主题︰

正在完成 Irp 取消的 Irp 取消安全 IRP 队列使用系统的取消旋转锁定

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>这一要求的主要理由是为了防止驱动程序导致应用程序停止响应。 另外，用户不能终止或重新启动应用程序。 驱动程序会导致应用程序停止响应的客户不满的重要原因。  这一要求的次要理由是 I/O 取消点播用户，通过用户界面 (UI) 元素，如通用停止按钮或取消按钮，从而改善客户体验。 在 Windows Vista 引入了这一要求。 要求将要求添加到现有的驱动程序取消逻辑并添加驱动程序支持取消创建请求的要求。 停止响应的驱动程序可能会导致有时随机导致丢失的客户生产力、 丢失的客户数据，以及需要重新启动计算机的应用程序和操作系统的故障。 除了这些非常严重的问题，不存在或很差的 I/O 取消支持防止应用程序已成功停止操作，无需重新启动应用程序。</p>
</tr>
</table>


<a name="device.devfund.rollback"></a>
##Device.DevFund.Rollback

*驱动程序回滚*

### <a name="devicedevfundrollbackdriver"></a>Device.DevFund.Rollback.Driver

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

为了使最终用户能够将备份驱动程序 （即重新安装以前安装的驱动程序） 的设备驱动程序必须能够卸载和重新安装没有失败。

<a name="device.devfund.security"></a>
## <a name="devicedevfundsecurity"></a>Device.DevFund.Security

*其它的 TDI 筛选驱动程序和 LSP 与安全性相关的要求。*

### <a name="devicedevfundsecuritynotdifilterandlsp"></a>Device.DevFund.Security.NoTDIFilterAndLSP

*没有 TDI 筛选器或 Lsp 由驱动程序或关联的软件包安装期间安装或使用。*

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

可以无需使用的 TDI 筛选器或 Lsp 由内核模式软件或驱动程序，或者用户模式软件或驱动程序。

**其他信息**

<table>
<tr>
<th>业务理由</th>
<td>
<p>使用的 TDI 筛选和 Lsp 增加攻击面，并将因此不再能支持未来的操作系统版本。</p>
</tr>
</table>


<a name="device.devfund.server"></a>
##Device.DevFund.Server

### <a name="devicedevfundservercommandlineconfigurable"></a>Device.DevFund.Server.CommandLineConfigurable

*具有可配置的设置的 Windows 服务器的设备驱动程序提供命令行实用程序或功能的设备和驱动程序管理*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows® Server® 设备驱动程序是可配置的所需提供的 WMI 或基于 PowerShell 的、 远程的设备和驱动程序管理的功能。 下面的设备类别将包括︰

 - 网络，包括分组和无限带宽
 - 存储，包括多路径 I/O (MPIO)
 - 总线
 - 可能有可配置的设置的任何其它驱动程序

注意︰ 设备，如打印机、 扫描仪、 网络交换机和存储阵列，可以在网络上配置从任何系统 （其他服务器、 客户端系统等），无需满足这一要求。

具体要求如下所示︰

 - 实用程序或工具的功能可能会使用 PowerShell 或 Windows 管理规范 (WMI) 支持的 Windows 服务器核心安装选项的功能。

 - 实用程序或功能必须从命令行运行，或者是 WMI 对象并使用 Windows 管理工具命令行 (WMIC) 工具兼容的提供程序。

 - 该实用程序必须为该驱动程序包的一部分提供，默认情况下，驱动程序的系统上安装。

 - 该实用程序必须能够正确查询、 显示和更改任何值，可以更改的驱动程序。

 - 该实用程序必须未正确创建或设置不存在特定的设备或驱动程序的选项。 该实用程序必须能够更改任何设置，如果操作系统不提供从命令行更改该设置的能力。

 - 更改后的值或用户输入必须是自动的范围检查，以确保用户输入有效。

 - 该实用程序所做的更改必须不需要任何网络或存储堆栈重新启动或重新启动系统，除非启动、 系统或分页行为或位置已更改。

 - 在重新引导后，此实用程序所做的更改是永久性的。

 - 关于使用实用程序的帮助，是本地系统上可用的选项。 例如，必须提供该实用程序"/？" 命令行选项或产品的 WMI 选项必须公开通过标准 WMIC 命令。

 - 该实用程序不应安装信息文件 (INF)。

 - 默认情况下，应安装实用程序。 这可以通过使用共同安装程序。

此要求不适用于存储阵列、 存储结构、 交换机、 打印机或其他设备外部的服务器系统中并且可以由任何连接到以太网、 光纤通道或其他网络的系统管理的。

此要求不适用于任何设备都不具有可配置的设置。 例如，在系统中使用的图形用户界面，有没有"高级"、"电源管理"或其他附加的选项卡中的设备管理器界面中，也不是任何实用程序可从供应商，获得同样的效果。

此要求适用于任何物理设备或设备的 PCI id，都有一个驱动程序;对任何驱动程序所在的网络、 存储、 文件系统或其他叠;而且到任何设备或驱动程序，否则运行在服务器上的操作系统实例中的内核或用户模式。

设计备注︰

任何不符合这一要求的设备驱动程序将不能使用 Nano 服务器系统上

实施日期︰ 2 月 2016 2016年

### <a name="devicedevfundservermultipleprocessorgroups"></a>Device.DevFund.Server.MultipleProcessorGroups

*驱动程序必须在具有多个处理器组中配置的处理器服务器上正常运行*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows® Server 使用 KGROUPs 的概念扩展操作系统的单个实例可以支持多个 64 的处理器的数目。 同时 enlightened 和 unenlightened 的设备驱动程序必须在多个 KGROUP 配置中正常运行。

设计备注︰

有关详细信息，请参阅"支持系统，有超过 64 处理器:: 准则对于开发者，"为主题的白皮书，在下面的网站︰ http://www.microsoft.com/whdc/system/Sysinternals/MoreThan64proc.mspx

这要求所有服务器设备类别进行了都测试。 该测试使用 BCDEdit 功能更改操作系统，因此更改处理器组 （ **groupsize**设置） 的大小，以创建多个处理器组的引导配置数据库 (BCD)。 测试还使用 BCDEdit 功能添加到 BCD 的**groupaware**设置。 这将更改几个现在传统的应用程序编程接口 (Api) 的行为，以便测试发现更多的代码错误。

操作系统将不提供与其中的任何设置。 这些设置仅供测试并不在生产环境中受支持。 要重新配置为正常操作的系统，这些设置必须从删除 BCD，必须重新启动系统。 用于测试系统必须包含至少四个处理器核心。

供应商可以配置系统，使其与 Windows 徽标工具包 (WLK) 和设备测试管理器 (DTM) 系统类似。 供应商可以执行其自己的测试在多个处理器组配置中，按如下所述。

要添加的组设置并重新启动计算机的命令行如下所示︰

> bcdedit.exe/设置 groupsize 2
>
> bcdedit.exe/上设置 groupaware
>
> shutdown.exe-r-t 0-f

要删除组的设置，然后重新启动计算机的命令行如下所示︰

> bcdedit.exe /deletevalue groupsize
>
> bcdedit.exe /deletevalue groupaware
>
> shutdown.exe-r-t 0-f

### <a name="devicedevfundserveroperateinservercore"></a>Device.DevFund.Server.OperateInServerCore

*设备驱动程序必须安装，配置，提供服务，以及在 Windows 服务器核心工作。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

部署 Windows 服务器操作系统的硬件平台已在过去十年中大大发展。 随着这些图形较系统的设计成本和部署效率较高，客户希望完全安装、 部署、 配置和管理这些硬件平台上使用最少的命令行界面和 Windows Server Core 的自动化脚本。 Windows 服务器设备驱动程序必须发展以相似的方式，以使客户能够争取这些操作而没有影响。

设备驱动程序必须展示其能力来安装、 配置、 能提供服务，而无须依靠存在的 GUI 操作。

设计备注︰

任何不符合这一要求的设备驱动程序将不能使用 Windows 服务器核心系统

实施日期︰ 2 月 2016 2016年

### <a name="devicedevfundserverserverpowermanagement"></a>Device.DevFund.Server.ServerPowerManagement

*Windows 服务器的设备驱动程序必须支持查询电源并将电源管理请求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

在转换期间到休眠 (S4) 系统休眠状态，设备驱动程序从操作系统接收电源请求。 设备驱动程序必须遵守，必须正确处理查询电源和电源设置电源管理请求。 设备驱动程序永远不应该拒绝查询电源要求。 设备驱动程序接收 S4 设置电源电源管理请求时，驱动程序必须置于 D3 设备电源状态转换及其设备，并停止所有 I/O 操作。 这包括任何当前正在进行的直接内存访问 (DMA) 传输。 当驱动程序的设备处于低功耗状态，禁用中断，并暂停正在进行的所有 I/O 操作。

D3 状态可能是 D3"热"，以支持必须响应外部激励或 D3 的设备"冷"。

设备驱动程序未绑定到系统硬件，例如特定处理器的唯一地识别实例本身。

*设计备注*

有关详细信息，请参阅"驱动程序兼容性的动态硬件分区"白皮书在下面的网站︰ http://www.microsoft.com/whdc/system/platform/server/dhp.mspx

<a name="device.devfund.server.nano"></a>
## <a name="devicedevfundservernano"></a>Device.DevFund.Server.Nano

*Windows 服务器 Nano 的基本要求*

### <a name="devicedevfundservernanodeployment"></a>Device.DevFund.Server.Nano.Deployment

*适用于 Windows 服务器 Nano 的所有驱动程序都必须满足以下要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

用于 Windows 服务器 Nano 的所有驱动程序必须满足下列部署要求︰

- 驱动程序必须不能打包为 MSI。 必须提供一套可以复制到使用部署映像服务和管理 (DISM) 文件夹中的文件 （如.inf 和.sys 文件） 的所有驱动程序文件。
- 驱动程序必须安装使用 DISM 脱机。

所有的工具、 实用程序或代理 Nano 服务器上安装必须是可用作 Windows 服务器应用程序 (WSA) 安装程序包。

### <a name="devicedevfundservernanodiagnostics"></a>Device.DevFund.Server.Nano.Diagnostics

*适用于 Windows 服务器 Nano 的所有诊断实用程序必须满足以下要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

所有诊断工具和实用程序用于在 Microsoft Azure 堆栈解决方案必须都支持管理，通过下列方法之一︰

- 远程使用 Windows PowerShell 或 Windows 管理规范 (WMI)。
- 使用命令行工具，管理员可以通过连接到远程 Windows PowerShell 会话或 SSH 通过纳米服务器实例 Nano 服务器上运行。

如果工具或实用程序在 Nano 服务器上本地运行，它必须是可用作 Windows 服务器应用程序 (WSA) 安装程序包。

除上述系统运行 Windows 服务器 Nano 必须支持 Nano 服务器故障恢复控制台功能通过验证的所有相应的功能纳米服务器中使用的驱动程序正常工作。

### <a name="devicedevfundservernanofirmwareupdate"></a>Device.DevFund.Server.Nano.FirmwareUpdate

*服务器 Nano 的固件更新要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

所有固件更新工具和实用程序，用于 Windows 服务器 Nano 的必须都支持通过下列方法之一进行安装︰

- 使用 Windows PowerShell 或 WMI 远程安装
- 使用命令行工具，管理员可以通过连接到远程 Windows PowerShell 会话或 SSH 通过纳米服务器实例运行 Nano 服务器上本地安装

如果工具或实用程序在 Nano 服务器上本地运行，它必须是可用作 Windows 服务器应用程序 (WSA) 安装程序包。

### <a name="devicedevfundservernanomonitoringandtelemetry"></a>Device.DevFund.Server.Nano.MonitoringAndTelemetry

*对于 Windows 服务器 Nano 的监视要求。*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

所有监视工具、 实用程序和代理必须支持通过下列方法之一进行安装︰

- 使用 Windows PowerShell 或 WMI 远程安装
- 使用命令行工具，管理员可以通过连接到远程 Windows PowerShell 会话或 SSH 通过纳米服务器实例运行 Nano 服务器上本地安装

如果工具、 实用工具或代理 Nano 服务器在本地运行，它必须是可用作 Windows 服务器应用程序 (WSA) 安装程序包。

特别是，Microsoft Azure 堆栈，所有监视必须是无代理，和代理将不允许在主机上。 请参阅如果实施' System.Server.Manageability.Redfish Redfish 需求

### <a name="devicedevfundservernanooperateinservernano"></a>Device.DevFund.Server.Nano.OperateInServerNano

*设备驱动程序必须安装，配置，提供服务，以及在 Windows 服务器 Nano 中运行。*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

部署 Windows 服务器操作系统的硬件平台已在过去十年中大大发展。 随着这些图形较系统的设计成本和部署效率较高，客户希望完全安装、 部署、 配置和管理这些硬件平台上使用最少的命令行界面和 Windows 服务器 Nano 的自动化脚本。 Windows 服务器设备驱动程序必须发展以相似的方式，以使客户能够争取这些操作而没有影响。

设备驱动程序必须展示其能力来安装、 配置、 能提供服务，而无须依靠存在的 GUI 操作。

设计备注︰

任何不符合这一要求的设备驱动程序将不能使用 Windows 服务器纳米系统上

### <a name="devicedevfundservernanopatchandupdate"></a>Device.DevFund.Server.Nano.PatchAndUpdate

*修补程序对 Windows 服务器 Nano 的要求。*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

所有修补程序和更新程序必须能够安装脱机或联机映像创建的一部分。


<a name="device.devfund.server.pci"></a>
## <a name="devicedevfundserverpci"></a>Device.DevFund.Server.PCI

*PCI*

### <a name="devicedevfundserverpcipciaer"></a>Device.DevFund.Server.PCI.PCIAER

*支持高级错误报告所需的 Windows 服务器的 PCI Express 设备\[AER\] PCI Express 基规范 2.1 版中定义。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

请参阅表 6-2，6-3、 6-4 和 6-5 PCI 规范如何在硬件中检测到错误，该错误，并由代理程序检测到错误报告和记录有关错误的执行预期的操作的默认严重性上。

这三种方法的错误报告;完成状态、 错误消息、 错误转发\\数据中毒。

完成状态使请求者可以与特定请求的错误。

错误消息指示问题是否纠正，并严重与否

错误转发\\数据中毒可帮助您确定特定交换机的路径是否中毒 TLP

下表列出了部分 6.2 中的错误所需报告︰

| 错误的类型                      | 必需？ | 操作                                                         |
|-------------------------------------|-----------|----------------------------------------------------------------|
| 错误\_COR （纠正）              | 否        | 没有操作，不会记录在事件查看器系统不执行任何操作。 |
| 错误\_致命错误 （致命的非可修正） | 是       | Whea 通过句柄，并记录在事件查看器                       |
| 错误\_非致命错误                       | 是       | 无                                                           |

<a name="device.devfund.statictools"></a>
## <a name="devicedevfundstatictools"></a>Device.DevFund.StaticTools

### <a name="devicedevfundstatictoolscaandsdv"></a>Device.DevFund.StaticTools.CAandSDV

*驱动程序开发包括静态分析来提高使用代码分析 (CA) 和静态驱动程序验证程序 (SDV) 的可靠性。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

网络和存储驱动程序提交必须包含日志文件的静态驱动程序验证程序 (SDV) 和代码分析驱动程序 (CA)。

**设计备注**

Microsoft 的静态分析工具，即驱动程序 (CA) 和静态驱动程序验证程序 (SDV) 代码分析发现了要能够有效地提高通过标识将否则很难找到的编码问题的驱动程序的可靠性。

-   **仅适用于服务器︰**驱动程序兼容性提交的代码中，必须纠正通过 CA 和 SDV 发现被确定为是"服务器:: 必须修复"的问题。 将静态工具日志中报告发现的其他任何问题，但没有任何要求，以解决这些问题。

-   **仅用于客户端︰**通过 CA 和 SDV 中发现的问题将在静态工具日志，但不需要修复这些问题报告。

将通过硬件实验室工具包包含在设备提交包捕获 DVL 文件输出结果的静态分析工具。

**如何创建**

-   [代码分析日志](http://go.microsoft.com/fwlink/p/?LinkId=723117)

-   [SDV 日志](http://go.microsoft.com/fwlink/p/?LinkId=723119)

-   [DVL 结果文件](http://go.microsoft.com/fwlink/p/?LinkId=723120)

**注意︰**虽然建议，有没有要求规定提交并随后分布式驱动程序二进制文件被编译使用 Microsoft Windows 设备工具包或任何其他 Microsoft 工具。

**注意︰**微软保留权利在将来要求释放静态分析工具添加的其它设备类别。

