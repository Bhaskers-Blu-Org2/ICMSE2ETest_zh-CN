---
title: Device.BusController.UsbController
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 5fbf26151b20bd2cf29fcae04f6ec2748bde235d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.BusController.UsbController

 - [Device.BusController.UsbController](#device.buscontroller.usbcontroller)
-->

<a name="device.buscontroller.usbcontroller"></a>
##Device.BusController.UsbController

### <a name="devicebuscontrollerusbcontrollerimplementatleastonexhcispcstructforusb2"></a>Device.BusController.UsbController.ImplementAtLeastOneXhciSpcStructForUSB2

*xHCI 控制器必须为 USB 2.0 实现至少一个 xHCI 支持协议功能结构。*

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

XHCI 规范的 7.2 节中所述扩展主机控制器接口 (xHCI) 控制器必须实现 USB 2.0 至少一个支持的 xHCI 协议功能结构。

这会影响与 USB 2.0 的向后兼容性。

### <a name="devicebuscontrollerusbcontrollermaintaindevicestateonresumes1ands3"></a>Device.BusController.UsbController.MaintainDeviceStateOnResumeS1andS3

*USB 主机控制器必须维护设备恢复从 S1 或 S3 状态。*

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

维护设备状态的主机控制器，USB 主机控制器必须不发出重置系统休眠状态转换从 S3 到 S0 或 S1 到 S0 上的 USB 总线。

USB 主控制器集成或嵌入到南桥芯片组必须分离开来 USB 总线重置从 PCI 总线重置以减少恢复时间。 从 S1 或 S3 的恢复操作必须生成 USB 总线重置。 USB 总线重置是经由 USB 设备连接到 USB 主机控制器的 USB 总线重置信号。 

允许连接的 USB 键盘的系统执行从 S3 的系统恢复时使用密码解锁系统的 USB 总线重置。

为安全起见中移动系统, 的 BIOS 可以发出了 USB 总线复位如果系统连接到插接站的硬盘驱动器 (HDD)，是第一个恢复密码锁定。

无论停靠移动系统允许的硬盘驱动器密码重置。 允许使用下列方案︰
 

-   一个密码启用硬盘的接驳的系统

-   使用一个密码启用硬盘固定的系统

-   添加或删除硬盘

如果坞站没有本机硬盘或坞站没有密码，则 BIOS 必须不发出 USB 总线重置。

那么就可以允许系统使用电池电源时丢失在 S3 中的电源控制器。

*设计备注*  

请参见通用串行总线，修订版 1.0，附录 A 的增强的主控制器接口规范

此要求不适用于支持连接的备用系统。
 

### <a name="devicebuscontrollerusbcontrollermustresumewithoutforcedreset"></a>Device.BusController.UsbController.MustResumeWithoutForcedReset

*所有 USB 主控制器必须时从休眠，休眠状态，恢复正常工作，或重新启动而无需强制重置。*

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

所有 USB 主控制器时从休眠，休眠状态，恢复正常工作或不强制重置 USB 主机控制器的情况下重新启动。

*设计备注*

在重置后的整个 USB 主机控制器结果显著增加时所需的所有 USB 设备后系统恢复，因为有可能只有一个设备 0 一次变得可用，此枚举具有要序列化的总线上的所有 USB 设备。 我们也知道，重置主机控制器可能会导致非法 SE1 信号状态某些主机控制器，这反过来又会导致挂起或总线放置一些 USB 设备上。 此外，设备都无法保持任何私有状态在睡眠恢复为该状态将重置在丢失。

### <a name="devicebuscontrollerusbcontrollerpreservedevicestateafterdisableenable"></a>Device.BusController.UsbController.PreserveDeviceStateAfterDisableEnable

*USB 控制器必须保留后禁用设备状态并重新启用。*

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

如果 USB 控制器被禁用并重新启用，禁用 USB 控制器前连接到该控制器的所有设备都所需有 USB 控制器后重新启用。

### <a name="devicebuscontrollerusbcontrollerusbifcertification"></a>Device.BusController.UsbController.UsbifCertification

*USB 主控制器是 USB 如果认证。*

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

USB 主控制器必须通过 USB 实现论坛 （如果） 测试。 有关详细信息，请参阅以下链接︰

-   <https://msdn.microsoft.com/en-us/library/windows/hardware/dn434058.aspx>

USB 类型 C PD 硅 （如，PD 控制器） 必须实现版本 1.1 版或更高的 USB 类型 C 规范和修订版 2.0 1.1 版或更高的 PD 规范并必须认证根据 USB-如果的 USB C 产品测试矩阵。

注︰ 由于 USB-如果当前不验证控制器的 Windows ARM 系统上，ARM 控制器上的 Windows 不受无需获取完整的 USB-如果证书。 相反，预期工单协议控制器通过所有的 Windows 硬件认证测试包括事件、 回环和寄存器运行的测试，获得作为一部分的 USB-如果证书。

### <a name="devicebuscontrollerusbcontrollerusbtypecaltmodecertification"></a>Device.BusController.UsbController.UsbTypeCAltModeCertification

*USB 类型 C 替换模式子系统与他们各自组织认证。*

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

硅如果 USB 类型 C PD 硅 （如，PD 控制器） 支持备用模式标准和行业组拥有标准具有相应的证书，必须获取该证书，以及 USB-如果证书。

例如，如果 USB 类型 C PD 硅支持 USB 和 PD DisplayPort 备用模式，然后该硅必须由 VESA DisplayPort 功能，此外到 USB-如果由于 USB 和 PD 的功能。

证书的特定于供应商的备选模式不是必需的。

### <a name="devicebuscontrollerusbcontrollerusbtypecucm"></a>Device.BusController.UsbController.UsbTypeCUCM

*USB 类型 C 子系统支持 UCM*

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

以 10 为 Windows 系统上运行并不实现 UCSI 的 USB 类型 C PD 硅 （如，PD 控制器） 必须附带 3<sup>rd</sup>-方 UCMCx 客户端驱动程序。 3<sup>rd</sup>-方 UCMCx 客户机驱动程序必须实现按照下面的 MSDN 文档︰

-   <https://msdn.microsoft.com/en-us/library/windows/hardware/mt188011.aspx>。

UCMCx 客户机驱动程序，我们需要实现以下 Api:

 - UcmInitializeDevice

 - UcmConnectorCreate

 - UcmConnectorTypeCAttach

 - UcmConnectorTypeCDetach

 - UcmConnectorTypeCCurrentAdChanged

 - UcmConnectorChargingStateChanged

如果系统或控制器支持功率传输，适用于以下附加要求︰

 - UcmConnectorPowerDirectionChanged

 - UcmConnectorPdSourceCaps

 - UcmConnectorPdPartnerSourceCaps

 - UcmConnectorPdConnectionStateChanged

如果系统或控制器公开双重角色端口，将应用以下附加要求︰

 - UcmConnectorDataDirectionChanged

### <a name="devicebuscontrollerusbcontrollerusbtypecucsi"></a>Device.BusController.UsbController.UsbTypeCUCSI

*USB 类型 C 子支持系统 UCSI 正确实现*

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

运行在 Windows 10 和嵌入式控制器中实现其 PD/USB 类型 C 状态机的 USB 类型 C PD 硅 （如，PD 控制器） 必须实现 UCSI 1.0 版 （或更高版本）。 此外，它必须实现 UCSI 规范中的以下可选功能。

*命令*

-   获得\_替代\_模式

-   获得\_CAM\_支持

-   获得\_PDOS

-   设置\_通知\_启用

    -   系统或控制器必须支持在此命令中的下列通知︰

        -   受支持的提供程序功能更改

        -   协商的电源级别更改

-   获得\_连接器\_状态

    -   系统或控制器必须支持以下连接器状态更改此命令中︰

        -   受支持的提供程序功能更改

        -   协商的电源级别更改

<!-- -->

-   系统或控制器必须支持下面的字段中获取\_连接器\_状态结构

    -   提供程序功能受限的原因

### <a name="devicebuscontrollerusbcontrollertestedusingmicrosoftusbstack"></a>Device.BusController.UsbController.TestedUsingMicrosoftUsbStack

*xHCI 控制器必须经微软 xHCI 安装堆栈。*

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

可扩展的主机控制器接口 (xHCI) 控制器必须经微软的 Windows 系统上安装并启用的 xHCI 堆栈。 将检查所有 USB 传输类型 （同步、 中断以及大容量） 的支持，以确保基本的兼容性。

### <a name="devicebuscontrollerusbcontrollerxhciac64bit"></a>Device.BusController.UsbController.XhciAc64Bit

*xHCI 控制器必须将 AC64 位设置为 1 HCCPARAMS 寄存器中。*

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

xHCI 控制器必须为 1 节 5.3.6 的 xHCI 规范中所描述的 HCCPARAMS 寄存器设置 AC64 位。
因此，控制器必须支持︰

-   64 位寻址，所述节 5.3.6

-   64 位寄存器的访问、 5.1 节中所述

*设计备注*︰ 检查 AC64 要设置非常简单，在法规遵从性驱动程序注册检查。
若要测试 64 位寻址，我们将需要要求 WLK 用户的客户端系统有至少 6 GB 的 RAM。  测试将使用 MmAllocateContiguousMemorySpecifyCache 来获取物理内存超过 4 GB。  它将验证控制器可以访问该内存区域的某些方面。
测试会尝试写入一或多个寄存器使用 64 位注册访问并读取使用 64 位回注册权确认寄存器被正确更新。  合理的寄存器来测试的一个示例是:"**事件环段表基本地址注册 (ERSTBA)**"（第 5.5.2.3.2 节）。

如果未设置 AC64，没有可供测试。

### <a name="devicebuscontrollerusbcontrollerxhciaddincardsmapportsconsistently"></a>Device.BusController.UsbController.XhciAddInCardsMapPortsConsistently

*xHCI 外接卡必须以一致的方式映射 USB 3.0 和 USB 2.0 端口。*

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

一致的 USB 2.0 和 USB 3.0 端口映射需要帮助系统能够有效地管理端口。 

注意︰ 此要求仅适用于外接卡因为集成的 xHCI 控制器的端口映射应执行通过高级配置和电源接口 (ACPI)。 有关详细信息，请参阅 SYSFUND 226 要求。

可扩展的主机控制器接口 (xHCI) 外接卡 （在"外卡"指未集成在主板上的卡），这一要求的复杂程度极大地取决于外接卡中是否包含任何内部 （集成或嵌入） 集线器。

如果没有内部的集线器，然后端口编号必须对照 xHCI 1.x 版规范中给出。 也就是说，第一个 USB 3.0 端口必须连接到相同的连接器作为首先 2.0 端口，第二个与第二个，依此类推。 例如，如果 USB 2.0 端口将编号 1 和 2，而 USB 3.0 端口编号 3 和 4，端口 1 和 3 必须映射到相同的连接器，而端口 2 和 4 必须映射到相同的连接器。 有关详细信息，请参阅 xHCI 1.x 版规范，4.24.2.1 和 4.24.2.2 部分。 如果主机没有任何内部集线器，可以忽略此要求的其余文本。

但是，如果有内部集线器 （集成或嵌入），然后要求是更为复杂。 请注意，严格地说，XHCI 规范不允许附加卡的这种集线器因为不能与 ACPI 通过软件通信端口映射信息。 但是，通过这种要求，我们已使这种集线器并定义所需的端口映射。 但是，这种机制有一些限制，它不允许集成控制器时所描述的 ACPI 允许的任意配置。

添加卡，xHCI 主机控制器可以实现"集成的集线器"和/或"嵌入的集线器"4.24.2.1 和 4.24.2.2 的 xHCI 规范部分中定义。  不需要限制为在系统主板上嵌入的集线器。  但是，以下限制适用︰

-   附加卡的嵌入式的中心必须是 （这种限制是唯一的这种要求的情形，不属于 xHCI 规范） 的 USB 3.0 集线器。

-   外接卡可能有至多 1 集成的中心。

-   如果外接卡有一个集成的集线器，它必须具有根集线器上的只有 1 个 USB2 协议端口。  此端口为连接到集成集线器的端口。

-   实现一个集成的集线器外接 xHCI 卡必须设置集成中心实现 (IHI) 根集线器端口连接到集成集线器中 USB 2.0 xHCI 支持协议功能结构与"1"位 （请参阅部分的 xHCI 规范的 7.2.2.1.3.2）。

-   所有集成或嵌入集线器必须标记为不可移动其父端口中。

集成集线器的实现确定控制器的外部端口。  外部端口是节 4.24.2 顺序端口的 xHCI 规范中定义的一个概念，因此可以将它们映射到连接器。  在所有情况下，让有*n* USB2 协议外部端口编号 1 至*n*，并且*m* USB3 协议外部端口编号为*n*+ 1 到*n*+*m*。

 
外部端口号分配给符合以下属性 （不在 xHCI 规范中定义）。  请注意，集成的集线器必须 USB 2.0 集线器。

-   如果 xHCI 实现了一个集成的集线器， *n*的 USB2 协议外部端口数将等于集成集线器上下游对开的端口数。

-   否则， *n*等于根集线器上下游对开的 USB2 协议端口数。

-   *m*，USB3 协议外部端口数等于根集线器上下游对开 USB3 协议端口数。

-   分配的外部端口号，外部端口 1 到*n*是 USB2 协议端口和外部端口*n*+ 1 到*n*+*m* USB3 协议外部端口，并且保留每个协议内订购的端口。

 
**如果没有嵌入的 hub(s):**USB2 协议外部端口和 USB3 协议外部端口必须映射到连接器使用节所述 4.24.2.2 xHCI 规范的标题下的"未实现嵌入式中心"时的"默认值"映射。

**是否存在嵌入的 hub(s):**嵌入的集线器必须为 USB 3.0 集线器。  首先，确定连接器映射，好像没有任何嵌入的集线器，xHCI 规范的 4.24.2.2 部分中使用"默认"映射。  对于每个嵌入的中心，两个上游端口必须连接到相同的连接器。  嵌入的集线器的下游端口映射到新的连接器中非嵌入式 USB 3.0 集线器的端口相同的方式。

**非公开连接器︰**嵌入到主控制器的设备必须标记为不可移动其父端口中。  如果按照上面的连接器映射，与第二个端口共享非可移动外围设备连接器，第二个端口不能连接或可连接到任何设备。  另一方面，其端口全部标记为可拆卸任何连接器被认为是公开的接口，即它必须是物理连接。

请注意是否没有 ACPI 信息，根集线器无法具有嵌入式的 USB2 设备和集成的 USB2 中心;相反，嵌入的设备必须连接到集成集线器。

### <a name="devicebuscontrollerusbcontrollerxhciaddincardsreportinternaldevices"></a>Device.BusController.UsbController.XhciAddInCardsReportInternalDevices

*xHCI 卡外接程序的控制器必须正确报告内部连接的设备。*

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

可扩展的主机控制器接口 (xHCI) 控制器必须为 1 具有内部连接的设备的每个端口的 PORTSC 寄存器中设置设备的可移动 (DR) 位指示内部连接的设备。 这适用于不具有 ACPI 信息的控制器。 有关详细信息，请参阅 xHCI 规范的 5.4.8 部分。
 

-   这一要求将会阻止操作系统标记为可移动的固定设备。

-   外接程序中卡被定义为未集成在主板上的主控制器。

*设计备注*

注意︰ 此要求仅适用于外接卡因为集成的 xHCI 控制器的端口映射应执行通过高级配置和电源接口 (ACPI)。

### <a name="devicebuscontrollerusbcontrollerxhcisupportdebuggingonallexposedports"></a>Device.BusController.UsbController.XhciSupportDebuggingOnAllExposedPorts

*xHCI 控制器必须支持 USB 调试公开的所有端口。*

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

可扩展的主机控制器接口 (xHCI) 主控制器在所有端口上都能够调试。 报告调试功能不需要具有嵌入非可移动设备连接的端口。
 

-   USB 调试部分 7.6 xHCI 规范中定义。  

-   此要求不适用于外接卡主机控制器。 

### <a name="devicebuscontrollerusbcontrollerxhcisupportmsimsixinterrupts"></a>Device.BusController.UsbController.XhciSupportMsiMsixInterrupts

*xHCI 控制器必须支持 MSI 和/或 MSI-X 中断。*

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

可扩展的主机控制器接口 (xHCI) 控制器支持 PCI 局部总线技术指标修订版 3.0，部分 5.2.6 xHCI 规范的第 6.8 节中定义的消息信号中断 (MSI) 和 MSI-X 中断。

### <a name="devicebuscontrollerusbcontrollerxhcisupportsminimum31streams"></a>Device.BusController.UsbController.XhciSupportsMinimum31Streams

*xHCI 控制器必须支持至少 31 主要流，每个终结点。*

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

请参阅可扩展的主机控制器接口规范 4.12.2 部分。

这一要求是在 HCCPARAMS 设置为至少 4 能够最好的数据传输速率 UAS 设备 MaxPSASize。

基于对 USB 连接 SCSI 协议 (UASP) 的存储设备将利用流以实现更快的数据传输速率。  若要启用这些设备的最佳体验，xHCI 中的每个控制器都需要支持至少 31 主数据流。

### <a name="devicebuscontrollerusbcontrollerxhcisupportsruntimepowermanagement"></a>Device.BusController.UsbController.XhciSupportsRuntimePowerManagement

*如果实现，运行时唤醒 USB 主机控制器 xHCI 必须支持运行时电源管理包括。*

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

所有 USB xHCI 主机控制器必须都支持运行时电源管理，根据需要通过可扩展的主机控制器接口规范版本 1.0，部分 4.15。

运行时被定义为系统工作状态 (S0)，包括连接待机状态 S0 子状态，如果控制器支持连接待机状态的系统上进行测试。

主机控制器的电源管理，以及 （可选） 包含软件启动空闲关闭电源 （控制器低功耗状态如 D3），软件启动电源硬件启动唤醒信号。

如果 xHCI 控制器报告以支持运行时唤醒信号，它必须能够唤醒自身成功在以下任一事件时︰ 信号 B） 任何端口 A） 任何端口检测设备唤醒检测连接，断开，或过电流，当相应的 PORTSC 唤醒 Xxx 位设置为 '1'。
有关更多详细信息，请参阅一节 4.15 xHCI 规范。

若要报告控制器是否支持运行时唤醒信号︰
- 对于外接程序控制器，该控制器的 PCI 配置空间必须准确报告控制器是否能通过 PME 唤醒。  注意︰ 报告控制器支持通过 PME 唤醒意味着控制器可以成功地执行在运行时，PCI 唤醒并成功唤醒系统低功耗状态，根据适当的 PCI 规范的系统。
- 对于集成控制器，ACPI \_S0W 对象必须报告控制器是否能运行时唤醒信号。

### <a name="devicebuscontrollerusbcontrollerxhciversioncompliant"></a>Device.BusController.UsbController.XhciVersionCompliant

*USB 3.0 控制器是 XHCI 版本兼容。*

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

USB 3.0 控制器必须遵守可扩展的主机控制器接口 (xHCI) 规范版本 1.0 和任何 USB-如果勘误表发布通过 USB-如果。 在 2019 Microsoft 将转换为此要求作为文本"USB 3.1 控制器必须遵守可扩展的主机控制器接口 (xHCI) 1.1 版规范和任何 USB-如果勘误表发布通过 USB-如果。 “. Microsoft 强烈建议过渡到 2019年日期之前所遵循的规范版本 1.1。

