---
title: Device.Storage
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 76a99600aaae5125d53387386062ecb471aa3483
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicestorage"></a>Device.Storage

 - [Device.Storage.Controller](#device.storage.controller)
 - [Device.Storage.Controller.Ata](#device.storage.controller.ata)
 - [Device.Storage.Controller.AzureStack](#device.storage.controller.azurestack)
 - [Device.Storage.Controller.Boot](#device.storage.controller.boot)
 - [Device.Storage.Controller.Fc](#device.storage.controller.fc)
 - [Device.Storage.Controller.Fc.NPIV](#device.storage.controller.fc.npiv)
 - [Device.Storage.Controller.Fcoe](#device.storage.controller.fcoe)
 - [Device.Storage.Controller.Flush](#device.storage.controller.flush)
 - [Device.Storage.Controller.Iscsi](#device.storage.controller.iscsi)
 - [Device.Storage.Controller.Iscsi.iSCSIBootComponent](#device.storage.controller.iscsi.iscsibootcomponent)
 - [Device.Storage.Controller.Optical](#device.storage.controller.optical)
 - [Device.Storage.Controller.PassThroughSupport](#device.storage.controller.passthroughsupport)
 - [Device.Storage.Controller.Raid](#device.storage.controller.raid)
 - [Device.Storage.Controller.Raid.ContinuousAvailability](#device.storage.controller.raid.continuousavailability)
 - [Device.Storage.Controller.Sas](#device.storage.controller.sas)
 - [Device.Storage.Controller.Sata](#device.storage.controller.sata)
 - [Device.Storage.Controller.SD](#device.storage.controller.sd)
 - [Device.Storage.ControllerDrive.NVMe](#device.storage.controllerdrive.nvme)
 - [Device.Storage.Enclosure](#device.storage.enclosure)
 - [Device.Storage.Enclosure.AzureStack](#device.storage.enclosure.azurestack)
 - [Device.Storage.Hd](#device.storage.hd)
 - [Device.Storage.Hd.1394](#device.storage.hd.1394)
 - [Device.Storage.Hd.Alua](#device.storage.hd.alua)
 - [Device.Storage.Hd.Ata](#device.storage.hd.ata)
 - [Device.Storage.Hd.AtaProtocol](#device.storage.hd.ataprotocol)
 - [Device.Storage.Hd.AzureStack](#device.storage.hd.azurestack)
 - [Device.Storage.Hd.DataVerification](#device.storage.hd.dataverification)
 - [Device.Storage.Hd.Ehdd](#device.storage.hd.ehdd)
 - [Device.Storage.Hd.EMMC](#device.storage.hd.emmc)
 - [Device.Storage.Hd.EnhancedStorage](#device.storage.hd.enhancedstorage)
 - [Device.Storage.Hd.FibreChannel](#device.storage.hd.fibrechannel)
 - [Device.Storage.Hd.Flush](#device.storage.hd.flush)
 - [Device.Storage.Hd.Iscsi](#device.storage.hd.iscsi)
 - [Device.Storage.Hd.Mpio](#device.storage.hd.mpio)
 - [Device.Storage.Hd.MultipleAccess](#device.storage.hd.multipleaccess)
 - [Device.Storage.Hd.MultipleAccess.PersistentReservation](#device.storage.hd.multipleaccess.persistentreservation)
 - [Device.Storage.Hd.OffloadedDataTransfer](#device.storage.hd.offloadeddatatransfer)
 - [Device.Storage.Hd.PersistentReservation](#device.storage.hd.persistentreservation)
 - [Device.Storage.Hd.PortAssociation](#device.storage.hd.portassociation)
 - [Device.Storage.Hd.RaidArray](#device.storage.hd.raidarray)
 - [Device.Storage.Hd.ReadZeroOnTrimUnmap](#device.storage.hd.readzeroontrimunmap)
 - [Device.Storage.Hd.RemovableMedia](#device.storage.hd.removablemedia)
 - [Device.Storage.Hd.Sas](#device.storage.hd.sas)
 - [Device.Storage.Hd.Sata](#device.storage.hd.sata)
 - [Device.Storage.Hd.Sata.HybridInformation](#device.storage.hd.sata.hybridinformation)
 - [Device.Storage.Hd.Scsi](#device.storage.hd.scsi)
 - [Device.Storage.Hd.Scsi.ReliabilityCounters](#device.storage.hd.scsi.reliabilitycounters)
 - [Device.Storage.Hd.ScsiProtocol](#device.storage.hd.scsiprotocol)
 - [Device.Storage.Hd.SMR](#device.storage.hd.smr)
 - [Device.Storage.Hd.ThinProvisioning](#device.storage.hd.thinprovisioning)
 - [Device.Storage.Hd.Trim](#device.storage.hd.trim)
 - [Device.Storage.Hd.Uas](#device.storage.hd.uas)
 - [Device.Storage.Hd.UasOnEHCI](#device.storage.hd.uasonehci)
 - [Device.Storage.Hd.Usb](#device.storage.hd.usb)
 - [Device.Storage.Hd.Usb3](#device.storage.hd.usb3)
 - [Device.Storage.Hd.WindowsToGoCapableUSBDrive](#device.storage.hd.windowstogocapableusbdrive)
 - [Device.Storage.Optical](#device.storage.optical)
 - [Device.Storage.Optical.BluRayReader](#device.storage.optical.blurayreader)
 - [Device.Storage.Optical.BluRayWriter](#device.storage.optical.bluraywriter)
 - [Device.Storage.Optical.Sata](#device.storage.optical.sata)

<a name="device.storage.controller"></a>
## <a name="devicestoragecontroller"></a>Device.Storage.Controller

*适用于所有存储控制器的常规功能*

### <a name="devicestoragecontrollerbasicfunction"></a>Device.Storage.Controller.BasicFunction

*存储控制器的基本功能*

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

控制器的基本功能

基于 PCI 的主控制器和适配器必须支持 PCI 总线主控的默认设置，并直接访问虚拟内存 (DMA) 服务必须支持在主机适配器选项 rom。

不能执行其他注册表的修改，而不会自动执行设备类共同安装程序，而其功能的设备没有认证资格。

除非控制器的 RAID 适配器，则必须将所有命令都传递到基础物理设备。

如果设备返回较少比请求的数据，它必须正确地指出不足条件和适配器必须处理这根据 WDK （调整 DataTransferLength）。

非 RAID 控制器

RAID 驱动程序之外的微型端口驱动程序可能不会创建要用作目标适配器的管理命令的存在没有实际 Lun 时的伪设备。 相反，SCSI 微型 INF 必须指定 CreateInitiatorLu 参数在参数项的服务并将该 DWORD 值设置为 1。 这可能不为了使用共同安装程序。 因为可能始终使用了适配器，即使没有设备存在存储微型端口驱动程序不使用此参数。 WDK 中记录存储驱动程序的值。

以下存储控制器驱动程序徽标是要求在当前的 Windows 硬件认证计划中没有匹配的提交类别的存储控制器驱动程序。 任何具有匹配的提交类别的存储控制器应提交其匹配类别下。

-   存储控制器驱动程序必须 STORPORT 微型端口驱动程序。

-   注册表项 STORPORT 微型端口驱动程序-存储\_总线\_类型必须设置为 BusTypeUnknown (0x00)。

-   对于存储控制器，控制器本身必须正确命令翻译，即使控制器实现如 SATA、 NVMe 或 PQI 不同的接口类型上的其他命令协议响应相应的 SCSI 规范，根据。 不能识别的任何命令必须导致 SCSI 检查条件与有效的检测数据。

### <a name="devicestoragecontrollerclasscode"></a>Device.Storage.Controller.ClassCode

*总线连接控制器必须实现正确的类子类代码 PCI 代码和 ID 分配规范 (修订版 1.6) 中定义。*

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

控制器类代码

存储主机控制器和适配器必须符合所使用的设备协议的要求和相关设备存储总线的任何要求。
总线连接控制器必须实现正确的类子类代码所指定的 PCI 2.3，附录 d。这适用于所有总线类型包括但不是限于 IDE、 光纤通道、 SCSI 以及基于 SATA 设备。 任何设备在硬件中实现 RAID 功能无论是否完成的 RAID 实现固件或驱动程序的代码中，必须实现 PCI RAID 类 (01/04) 的代码和不使用互连类代码 （例如，SATA RAID 控制器必须实现 01/04 类代码而不是 AHCI 类代码 01/06/01）。

非 PCI 附加的存储主机控制器不需要报告 PCI 类代码。 但是，它必须报告等效 ACPI 兼容 id。
 

### <a name="devicestoragecontrollerinffile"></a>Device.Storage.Controller.InfFile

*所有主机适配器必须安装使用插的机制，需要使用的 INF 文件。*

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

控制器的 INF 文件所有主机适配器必须安装使用插的机制，需要使用的 INF。 安装程序必须使用的 INF 文件，必须通过最新的 Chkinf 工具，可以显式修改注册表值，只能通过 INF 文件构造符合 Windows 认证计划的要求。 仅在以下项进行更改︰

-   在类驱动程序的 TimeoutValues 服务键 （磁盘和磁带）。

-   而实现的仅为 SpecialTargetList。

-   设备的服务密钥 (必须是 HKLM\\系统\\开目前控制设置\\服务\\和参数\\下，设备子项)。

-   在任何链接转换或热插拔事件的检测信号 BusChangeDetected。 之前这发出的信号，但它必须是可通过注册表参数设置，允许有限的安定。

-   BusType 注册表 dword 值，可以在 NTDDSTOR 中正确设置按照枚举接口类型的实现。H （请参阅 WDK）。 该服务的参数项下的微型端口的 INF 中必须设置此值。 没有通过编程方式进行设置，您可能不依赖共同安装程序按照它们在所有情况下不运行。
     

### <a name="devicestoragecontrollerminiportdrivermodel"></a>Device.Storage.Controller.MiniportDriverModel

*存储微型端口驱动程序模型*

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

微型端口驱动程序模型

用于存储控制器的驱动程序必须按照微型端口驱动程序模型。 WDK 中定义，存储微型必须遵守所有的微型端口接口定义。 光纤通道、 iSCSI、 SAS、 SAS RAID SATA、 SATA RAID、 SCSI 和 SCSI RAID 控制器驱动程序必须 STORPORT 微型端口发送。 一体式、 全端口驱动程序或其他类型的遵循微型端口模型的驱动程序没有认证资格。 必须实现物理硬件的所有驱动程序以支持插。 不再支持旧版的驱动程序。

任何依赖于物理磁盘驱动器功能的筛选器驱动程序的设备不合格认证。 筛选器驱动程序不能用于绕过存储堆栈的任何部分。 例如，筛选器驱动程序很多不是直接访问 （如使用 HAL 调用） 的任何硬件和筛选器驱动程序可能不用于将缓存管理器链接到的硬件实现。 筛选器驱动程序可能不用于违反认证计划中的任何条款。

多路径驱动程序可能不会与特定 Hba 除 PCI RAID 控制器，并且必须使用 MPIO 模型。

不可能会向系统公开瞬态或伪设备。 指定 NODRV 的驱动程序可用于"声称"管理设备报告为处理器、 控制器或 MSC 的设备类型。 服务项不涉及此类驱动程序没有资格认证，但他们可以对其进行签名。

<a name="device.storage.controller.ata"></a>
## <a name="devicestoragecontrollerata"></a>Device.Storage.Controller.Ata

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrolleratainterface"></a>Device.Storage.Controller.Ata.Interface

*PATA 控制器接口*

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

PATA 接口 PATA 控制器必须遵守的 ATA/ATAPI-7 规范。 总线主控 DMA 功能是必需的但小巧 flash 以及类似 flash 内存设备的所有 PATA 控制器。
以下要求也可应用到 ATA/ATAP 控制器。

-   数据包命令协议定义部分 11.8-2 ATA/ATAPI-7 卷必须不实现仅 ATA 控制器中。

-   在 ATA/ATAPI-7 卷 2，部分 11.8，PATA 控制器支持数据包命令协议必须完全实现。

-   确定设备的数据字段 (61:60) 和 (103:100) 必须不能用于确定 28 或 48 位 LBA 地址的支持。 相反，位 10 个单词 83 和 86 字的 10 位必须检查的 48 位 LBA 地址支持 ATA/ATAPI-7，第 1 卷，4.2.1 节中定义。



<a name="device.storage.controller.azurestack"></a>
## <a name="devicestoragecontrollerazurestack"></a>Device.Storage.Controller.AzureStack

*定义存储控制器支持基于 Microsoft Azure 堆栈私有云解决方案中必须满足的要求*

### <a name="devicestoragecontrollerazurestackbasicfunction"></a>Device.Storage.Controller.AzureStack.BasicFunction

*存储控制器的 Microsoft Azure 堆栈解决方案中使用的基本要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

通过下表来捕获存储控制器的 Microsoft Azure 堆栈要求。

<table>
    <tr><th>功能</th><th>要求</th></tr>
    <tr><td rowspan="4">Device.Storage.Controller</td><td>Device.Storage.Controller.BasicFunction</td></tr>
    <tr><td>Device.Storage.Controller.ClassCode</td></tr>
    <tr><td>Device.Storage.Controller.InfFile</td></tr>
    <tr><td>Device.Storage.Controller.MiniportDriverModel</td></tr>
    <tr><td>Device.Storage.Controller.Boot</td><td>如果实现 'Device.Storage.Controller.Boot.BasicFunction'，然后 'Device.Storage.Controller.Boot.BitLocker' 是必需的</td></tr>
    <tr><td>Device.Storage.Controller.Flush</td><td>Device.Storage.Controller.Flush.BasicFunction</td></tr>
    <tr><td>Device.Storage.Controller.PassThroughSupport</td><td>Device.Storage.Controller.PassThroughSupport.BasicFunction</td></tr>
    <tr><td>Device.Storage.Controller.Sas</td><td>如果实现 'Device.Storage.Controller.Sas.Interface'，然后 'Device.Storage.Controller.Sas.TranslationLayer' 是必需的</td></tr>
    <tr><td>Device.Storage.ControllerDrive.NVMe</td><td>Device.Storage.ControllerDrive.NVMe.BasicFunction</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

除此之外，必须满足以下要求︰

1.  SAS HBA 所需的 SAS 和 SATA 磁盘设备
2.  SE 功能所需的 SAS 和 SATA 设备与 SAS 扩展器

### <a name="devicestoragecontrollerazurestackcloudstress"></a>Device.Storage.Controller.AzureStack.CloudStress
*用于连接到群集存储私有云解决方案的存储控制器必须符合本规范* 

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

私有云解决方案构成了紧密集成的软件和硬件组件，以提供高性能的可恢复性。 中的任何组件 （软件、 硬件、 驱动程序、 固件等） 的问题会危害解决方案，并会破坏任何私有云的有关服务级别协议 (SLA) 所做的承诺。 

许多这些问题都只能在云高强度的专用模拟出来后。 私有云模拟器 (PC) 使您可以验证您的组件在云方案并确定此类问题。 它通过创建 VM 工作负载、 调度管理操作 （负载平衡、 软件/硬件维护），和在私有云上注入故障 （没有计划的硬件/软件故障） 来模拟实时数据中心/私有云。 

为遵守此规范，控制器必须通过电脑测试运行的存储控制器 – Azure 堆栈上的 4 节点群集配置的配置文件。

### <a name="devicestoragecontrollerazurestackfirmwareupdate"></a>Device.Storage.Controller.AzureStack.FirmwareUpdate
*用于连接到群集存储私有云解决方案的存储控制器必须符合本规范*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

Microsoft Azure 堆栈需要 SAS 和 NVMe 控制器是可更新的固件。 对于 NVMe 控制器，这必须是通过收件箱[固件更新机制](https://blogs.technet.microsoft.com/filecab/2016/01/25/updating-firmware-for-disk-drives-in-windows-server-2016-tp4/)引入 WS 2016 (更新 StorageFirmware) 中。 此外，SAS Hba 必须正确翻译固件下载和激活命令根据[SAT-4](http://www.t10.org/cgi-bin/ac.pl?t=f&f=sat4r04a.pdf)规范。


<a name="device.storage.controller.boot"></a>
## <a name="devicestoragecontrollerboot"></a>Device.Storage.Controller.Boot

*定义存储控制器支持引导如果必须满足的要求*

### <a name="devicestoragecontrollerbootbasicfunction"></a>Device.Storage.Controller.Boot.BasicFunction

*如果该控制器实现了引导支持，它必须支持 Int13h 函数。*

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

控制器启动支持

主控制器和接口的任何类型的适配器中的选项 Rom，包括提供启动支持必须完全支持的 RAID 控制器 BIOS 增强磁盘驱动器服务-3 中定义扩展 Int13h 函数 (函数 4xh) \[T13 D1572\]，3 或更高版本。 逻辑块寻址是受支持的唯一寻址机制。

控制器还支持启动使用可扩展固件接口 (EFI) 和按 EDD 3 中定义实现设备路径建议。 从 Windows 8，它是必需的控制器以支持启动使用可扩展固件接口 (EFI)。

SD/eMMC/NAND 闪存控制器没有选项 ROM，所以不适用这一要求的第一部分。 EFI 支持是必需的。

### <a name="devicestoragecontrollerbootbitlocker"></a>Device.Storage.Controller.Boot.BitLocker

*BitLocker 必须不会导致失败 SAN 引导通过存储控制器。*

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

必须正确启用 BitLocker 保护在 SAN 启动配置操作系统。

**业务理由**

（1） 当一台服务器放在没有足够的物理安全性的环境中，BitLocker 保护以防未经授权的访问服务器上的数据，如果一台服务器被盗;（2） 当宿主服务提供程序的用途或停止使用的存储阵列，BitLocker 磁盘加密可以防止数据泄露。

<a name="device.storage.controller.fc"></a>
## <a name="devicestoragecontrollerfc"></a>Device.Storage.Controller.Fc

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollerfcinterface"></a>Device.Storage.Controller.Fc.Interface

*光纤通道 HBA 接口*

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

光纤通道接口光纤通道主机总线适配器驱动程序必须支持的 WMI 类和使用 Microsoft HBAAPI 实现光纤通道 HBA 或 SM API 所需的方法。DLL 中。 供应商将不会替换 HBAAPI Microsoft 提供版本。DLL 文件。 Hbapiwmi.mof WMI 类和方法的一个子集所需的 Windows 兼容性。 其他 WMI 类都是可选的并分组到窗体的功能集。 如果一个驱动程序实现任何可选功能集的一部分，所有相关类，必须支持的功能集。 在某些情况下，某些功能划分子功能。 如果一个驱动程序实现此类 subfeature，驱动程序必须正确支持该特定的 subfeature。
 

<a name="device.storage.controller.fc.npiv"></a>
## <a name="devicestoragecontrollerfcnpiv"></a>Device.Storage.Controller.Fc.NPIV

*在 Hyper-V 中提供虚拟光纤通道功能用于 NPIV。*

### <a name="devicestoragecontrollerfcnpivbasicfunction"></a>Device.Storage.Controller.Fc.NPIV.BasicFunction

*Hyper-V 虚拟光纤通道 N\_IO 端口的虚拟化支持*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

N\_端口 IO 虚拟化 (NPIV) 是 Hyper-V 功能虚拟光纤通道中使用的基础技术。 这些测试允许供应商在开发周期中，并在提交的更新驱动程序对 Microsoft 证书颁发前自我测试驱动程序的兼容性在 API 级别的虚拟光纤通道。

下面的类是需要︰ MSFC\_VirtualFibrePortAttributes，MSFC\_FibrePortNPIVAttributes，MSFC\_FibrePortNPIVMethodsEx，MSFC\_FibrePortNPIVCapabilities，MSFC\_NPIVCapabilities，MSFC\_NPIVLUNMappingInformationEx。 （可选） MSFC\_DH\_Chap\_可以实现参数。

这些测试包括典型的有效和无效 API 调用，但不是包括涉及 VM 工作负载、 存储目标功能和数据的完整性、 性能或其他考虑事项的详细情形。

<a name="device.storage.controller.fcoe"></a>
## <a name="devicestoragecontrollerfcoe"></a>Device.Storage.Controller.Fcoe

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollerfcoeinterface"></a>Device.Storage.Controller.Fcoe.Interface

*通过以太网主机总线适配器的光纤通道*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

通过以太网主机总线适配器的光纤通道  
 

-   FCoE 适配器必须实现 FC-BB-5 FC BB\_E 规范。

-   FCoE 适配器微型端口必须作为 Storport 微型端口来实现。

-   FCoE 适配器微型端口必须定义 VER\_FILEDESCRIPTION\_STR 和包含子字符串"\[FCoE\]"。

-   对于 FCoE 适配器微型端口 INF 的\[服务安装部分\]:

    -   "显示名称"输入值是必需的并且必须包含子字符串"\[FCoE\]"。

    -   "说明"条目的值是可选的如果指定，则必须包含子字符串"\[FCoE\]"。

-   对于 FCoE 微型端口适配器 INF 的模型部分\[节的模型名称\] | \[节的模型名称。TargetOSVersion\]:

    -   "设备描述"输入的值必须包含子字符串"\[FCoE\]"。

-   FCoE 适配器微型端口必须声明为其存储区的 BusTypeFibre\_总线\_在 INF 文件中的类型。 存储\_总线\_类型枚举

-   公开 PCI 存储设备的 FCoE 适配器 / FCoE 帧处理 （出口或入口） 的函数必须报告 0x0c0400 （光纤通道） 作为其类代码 （基础类、 子类和接口的代码）。

### <a name="devicestoragecontrollerfcoeinteroperability"></a>Device.Storage.Controller.Fcoe.Interoperability

*通过以太网主机总线适配器的互操作性的光纤通道*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

互操作性
 

-   FCoE 适配器必须通过 FCF FC SAN 设备兼容。

-   FCoE 适配器必须使用本机 FCoE 设备进行互操作。

-   同时必须有能力对传输网络 (IP) 和存储 (FCoE) 流量 FCoE 适配器。

-   禁用/删除/FC （存储） 功能损失必须不影响网络 （以太网） 连接和功能。

-   FCoE 适配器必须能够访问并满足光纤通道和本机 FCoE 设备同时 （通过 FCF)。

 
发起人共存
 

-   FCoE 适配器必须不受干扰，在同一系统上的光纤通道适配器与共存。

-   FCoE 适配器必须与其他 FCoE 适配器不在同一系统受干扰共存。

<a name="device.storage.controller.flush"></a>
## <a name="devicestoragecontrollerflush"></a>Device.Storage.Controller.Flush

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollerflushbasicfunction"></a>Device.Storage.Controller.Flush.BasicFunction

*刷新已连接到设备*

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

行业标准规格要求︰

-   对于 ATA 设备，请刷新缓存 (E7h，非数据) 28 位命令是可选的 ATA 设备和 ATAPI 设备。 刷新缓存分机 (EAh，非数据) 48 位命令是强制实施的 48 位地址功能集的设备。

-   对于 SCSI 设备，应实现同步缓存 (10) 和/或同步缓存 (16) 命令。

Windows 设计规范要求的控制器︰

-   控制器和设备驱动程序的所有总线类型 （ATA、 SCSI 和 USB） 刷新缓存命令应发送到连接的设备，而无需任何遗漏。

<a name="device.storage.controller.iscsi"></a>
## <a name="devicestoragecontrolleriscsi"></a>Device.Storage.Controller.Iscsi

*定义的行业和 Microsoft 必须满足的标准*

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

### <a name="devicestoragecontrolleriscsiinterface"></a>Device.Storage.Controller.Iscsi.Interface

*iSCSI 接口*

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

iSCSI 接口 iSCSI 主机总线适配器必须与 iSCSI RFC3720 兼容，必须实现所有强制性的要求。 唯一的例外是 IPsec 不是必需的但，如果实现，将进行测试。 所有的可选组件，如果实施，必须遵守本规范。
 

-   可选的行为必须不削弱对 iSCSI 技术指标或 iSCSI 的 Windows 认证程序要求遵守。

-   设备和驱动程序还必须符合适用的 SCSI 控制器和设备的要求。

-   ISNS 客户端可能会实现，而且如果是这样，符合 RFC3723。

-   一个适配器必须能够接收 ping (ICMP) 和发送 ping (ICMP)。

-   设备登录必须符合 Microsoft iSCSI 发现服务。

-   必须在启动之后到服务报告任何通过其他方式配置的引导设备。

-   任何其他持久性目标分配和会话控制的 HBA 必须报告可用时使用 WMI iSCSI 启动器服务。

-   以下登录身份验证是必需的︰

    <!-- -->

    -   "验证启动器的 CHAP 目标身份"

    -   无

    <!-- -->

-   双方 CHAP，如果实现，必须符合规范和测试。

-   本文档中的所有可用 IPSec 要求必须遵循 IPSec 支持。

-   HBA 驱动程序必须实现所有所需的 WMI 接口 WDK 中记录。

-   启动器必须执行自动登录到作为永久目标分配给计算机的目标。 之前由 Windows，开头到 LUN 0 查询枚举目标，发起者将连接到所有永久的目标。 如果连接中断，它将继续尝试重新连接。 设备不能依赖此信息的搜索服务。

-   启动器必须︰

    <!-- -->

    -   维护注册表中或在 NVRAM 中的持久的登录信息。

    -   定义管理持久性登录时支持新的 WMI 类。

    -   保留 IP 的网络适配器和发现配置 （IP 配置信息，例如，静态 IP 地址、 静态默认网关 IP 地址、 静态子网掩码和 DNS 服务器） 或使用 DHCP 来获取此信息。

    -   对于发现配置，请记住哪些发现方法都使用过，而且，对于 iSNS （如果实现），维护 iSNS 服务器的地址。

    <!-- -->

-   更换器、 磁盘、 磁带和外部 RAID 设备都必须支持 iSCSI HBA。

<a name="device.storage.controller.iscsi.iscsibootcomponent"></a>
## <a name="devicestoragecontrolleriscsiiscsibootcomponent"></a>Device.Storage.Controller.Iscsi.iSCSIBootComponent

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrolleriscsiiscsibootcomponentfwtable"></a>Device.Storage.Controller.Iscsi.iSCSIBootComponent.FwTable

*iSCSI 启动功能*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

iSCSI 启动功能 iSCSI 启动组件必须︰

-   能兼容与作品到 iSCSI RFC3720 的 iSCSI 目标。

-   推迟到 Microsoft iSCSI 软件启动器后 Windows 引导序列开始 （一旦 ntoskrnl.exe 加载） 的所有 iSCSI 功能。

-   支持登录重定向。

-   支持单向 CHAP 和必须维护 CHAP 机密在非易失性内存中。

-   固件或选项 ROM 中的 iSCSI 启动固件表实现每 ACPI SIIG 可选的表中。

-   支持故障转储。

-   支持使用 IPV6 寻址。

-   支持为最小错误处理与 iSCSI 目标登录初始化序列期间出现错误时重新登录。

-   支持下面的 DHCP 选项编号︰ 1、 3、 17、 43、 51、 54、 57、 60、 61、 255、 201、 202、 203、 204、 205 和 206。

-   支持下列 DHCP 参数︰

-   DHCPDISCOVER 可获得分配 IP 地址。

-   DHCPREQUEST 以获取 iSCSI 协议参数。

-   DHCPINFORM，查询信息从 DHCP 服务器中的更新。

另外：

-   从 iSCSI 预启动组件 DHCP 客户端对 DHCP 服务器的所有请求必须都使用选项 60 来通知相应的供应商范围。

-   从 iSCSI 预启动组件 DHCP 客户端对 DHCP 服务器的所有请求必须都使用选项 61 信号此给定客户端的标识。 如果未定义客户端 Alt ID，则类型字段应设置为 0x01，和 EN MAC 地址必须用于定义客户端标识。 如果定义了客户端 Alt Id，然后类型字段应设置为 0x00 和 CAID 字段必须使用。

-   从 iSCSI 预启动组件 DHCP 客户端对 DHCP 服务器的所有请求必须都使用 CHADDR 字段包含 EN MAC 地址的 DHCP 客户端。

-   在 iSCSI 预启动组件中 CIADDR 的使用必须符合 CIADDR 的 DHCP 使用情况。

-   YIADDR iSCSI 预启动组件的使用必须符合 DHCP 使用 YIADDR;亦即，iSCSI 预启动组件 DHCP 客户机必须接受 YIADDR 在 DHCPREQUESTÃ³DHCPACK 或 DHCPINFORMÃ³DHCPACK 事务过程中由 DHCP 服务器提供。

-   SIADDR 在 iSCSI 预启动组件的使用必须符合 DHCP 使用 SIADDR;亦即，iSCSI 预启动组件 DHCP 客户机必须使用此地址 DHCPREQUESTÃ³DHCPACK 或 DHCPINFORMÃ³DHCPACK 事务处理期间访问 DHCP 服务器。

-   若要支持 DHCP 选项 1，从 iSCSI 预启动组件 DHCPOFFER 回复中提供的子网掩码必须提供子网掩码。

-   ISCSI 之间的所有交易记录预启动组件的 DHCP 客户机和 DHCP 服务器必须是单个框架事务。

-   为了避免冲突与其他服务，iSCSI 预启动组件必须不使用 DHCP 选项 52。

-   在 iSCSI 预启动组件中的多个选项响应的实现必须符合 RFC 3396。

<a name="device.storage.controller.optical"></a>
## <a name="devicestoragecontrolleroptical"></a>Device.Storage.Controller.Optical

*在满足一般适用于所有存储控制器，以确保光盘刻录要求的功能。*

### <a name="devicestoragecontrolleropticalbasicfunction"></a>Device.Storage.Controller.Optical.BasicFunction

*存储 HBA 驱动程序必须支持光驱。*

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

控制器的光纤支持

存储 HBA 驱动程序必须支持光学设备。 Cdb 发给光学设备和光学设备的响应，必须正确处理。
 

<a name="device.storage.controller.passthroughsupport"></a>
## <a name="devicestoragecontrollerpassthroughsupport"></a>Device.Storage.Controller.PassThroughSupport

*传递查询存储控制器的基本功能*

### <a name="devicestoragecontrollerpassthroughsupportbasicfunction"></a>Device.Storage.Controller.PassThroughSupport.BasicFunction

*传递查询存储控制器的基本功能*

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

总线适配器必须报告给已连接的驱动器使用的实际总线类型 （例如，驱动器均通过 SAS 总线连接; 报告驱动器，如通过"RAID"总线连接是无效的）。  所有的命令必须通过直接传递到底层的物理设备。  应不抽象的物理设备 （例如，形成逻辑的 RAID 磁盘） 和总线适配器必须响应代表的物理设备的命令。

注意︰ 这只适用于 SAS 和 SATA 控制器。

<a name="device.storage.controller.raid"></a>
## <a name="devicestoragecontrollerraid"></a>Device.Storage.Controller.Raid

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollerraidbasicfunction"></a>Device.Storage.Controller.Raid.BasicFunction

*RAID 控制器*

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

RAID 控制器

-   为 PCI RAID 适配器的微型端口驱动程序可能会创建 LU 如果此设备是始终可用的管理命令，具有一种设备类型以外的其他磁盘管理。 由于此设备将显示在设备管理器中，可以提交 NODRV INF 声称此设备并防止用户弹出窗口 （可能签署这个 INF）。

-   RAID 控制器，控制器本身必须正确解释这些命令和响应相应的 SCSI 规范，根据即使控制器实现对不同的接口类型，如 SATA RAID。 不能识别的任何命令必须导致 SCSI 检查条件与有效的检测数据。

-   （如果实现）如果 RAID 控制器支持磁盘直通模式 （也称为 HBA 模式），并且使用了 SATA 驱动器，它下面的 T10 SAT-4 规范 （修订版 03a） 翻译实现文件应至少︰

    -   下载的微码模式 0Eh （第 8.16.2.5 节）

    -   下载的微码模式 0Fh （第 8.16.2.6 节）

    注意︰ 通过连接到 HBA 模式中的 Raid 控制器的 SATA 驱动器，符合 Windows 10 固件更新要求，且运行 HLK 固件更新测试，符合这一要求应进行测试。

可以在 Device.Storage.SCSI 部分找到 SCSI 要求。

<a name="device.storage.controller.raid.continuousavailability"></a>
## <a name="devicestoragecontrollerraidcontinuousavailability"></a>Device.Storage.Controller.Raid.ContinuousAvailability

*验证连续可用性 (CA) 存储控制器和驱动程序符合所有适用的要求*

### <a name="devicestoragecontrollerraidcontinuousavailabilityactivemode"></a>Device.Storage.Controller.Raid.ContinuousAvailability.ActiveMode

*一种设备及其驱动程序必须支持活动 LUN 访问 Windows 故障转移群集系统配置中的每个节点上。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

当在 Windows 故障转移群集中的多个节点中配置的设备和驱动程序时，每个节点必须支持为最小的"双活"访问权限，至少一个 lun 都将故障转移到群集中的另一个节点的功能定义为完全的读写功能。 具体来说，设备不允许只支持被动操作位置的设备和驱动程序只能在运行备用模式直到群集故障转移的 LUN 从另一个节点。

设计备注︰

-   对于这种"双活"访问，Lun 不需要完整，提供与群集中所有节点的性能读/写功能。 只需要得到支持，以支持有效的 Windows 故障转移群集，必须从其他节点访问。

-   具体来说，它是理想的但不是必需支持 LUN 从群集中的多个节点同时共享访问。

### <a name="devicestoragecontrollerraidcontinuousavailabilityfailoverclustering"></a>Device.Storage.Controller.Raid.ContinuousAvailability.FailoverClustering

*设备和驱动程序必须满足要求在 Windows 故障转移群集中运行的最小集合。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

设备必须符合 SPC 3 节 6.11 永久保留在命令

-   设备必须符合 SPC 3 节 6.12 出永久保留命令

    -   设备必须支持持久保留类型，如 6.11.3.4 一节中定义表 107:

        <!-- -->

        -   5h 写独占 – 仅登记

        <!-- -->

-   设备必须遵守保留行为，SPC 3 5.6 节中的定义

-   具体来说，SCSI 符合性测试应特别注意，以验证以下各项︰

    -   验证 Reserving – 一次保留、 范围及现有的永久保留的类型不能更改

    -   遵守部分 5.6.1 – 表 32

    -   遵守部分 5.6.6 – 表 33，34，表 36 – 验证好状态条件

    -   要验证，请重新注册 I\_T 结点已经注册 (5.6.6) – 应返回正常状态

    -   验证，重新预留 I\_T 结点包含永久保留 (5.6.9) – 应返回正常状态

    -   如果 PRO 服务操作命令返回预留冲突 – 抢占或抢占和中止发送具有无效服务操作保留键 (5.6.10.4.4)

    -   每 6.11.3.2-验证其他长度字段应返回零，当持有没有永久保留

设计备注︰

-   建议除了标准 HCT 鉴定，所有解决方案都还都验证了使用"Microsoft 群集配置验证向导"(ClusPrep) 工具。

-   只有使用串行 SCSI 协议 (SSP) 传输的 SAS 设备将支持故障转移群集 （包括 SAS JBOD 或任何 SAS SSP RAID 系统）。

如果系统磁盘连接的总线类型不是有效的类型共享存储 （光纤通道、 iSCSI 或 SAS 不是），然后将系统磁盘和共享。

### <a name="devicestoragecontrollerraidcontinuousavailabilitylunaccess"></a>Device.Storage.Controller.Raid.ContinuousAvailability.LunAccess

*设备和驱动程序必须符合要求访问 Windows 故障转移群集配置中的 Lun。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

当 Windows 故障转移群集中的节点故障转移资源，计划内或计划外 （例如，从一个节点故障或节点电源故障结果），设备和驱动程序必须满足以下要求︰

-   在故障转移之前成功确认写操作的所有数据都必须保留并从存活节点可访问。 具体而言，对应的数据写操作后发送给设备和在故障节点上的驱动程序之前开始其 Lun 中的故障转移 （即幸存节点上的相应 RAID 控制器接收从故障节点对应于 Lun 的永久保留请求），有未经确认为已完成驱动程序从幸存节点的故障转移完成后必须可访问性。 此外，所有数据都可能被挂起故障转移的开始处未确认写操作不得更改随后从幸存节点向设备写入数据。

-   当 Lun 支持 RAID 控制器出现故障的节点上停止正在访问 （即停止确认和处理 I/O 请求），LUN 必须进行访问 （即承认和处理 I/O 请求） 被至少一个其他节点在群集中具有最大延迟为 5 秒。 此时间限制必须支持多达 100 个 Lun 或控制器所支持的 Lun 的最大数量，以二者中较小者为准。

在正常操作期间 (即不是在故障转移过程) 在 Windows 故障转移群集中，设备和驱动程序必须满足以下要求︰

-   对任何 RAID 控制器所支持的 LUN 的所有 I/O 请求必须在 25 秒内都完成。 此时间限制必须支持多达 100 个 Lun 或控制器所支持的 Lun 的最大数量，以二者中较小者为准。

### <a name="devicestoragecontrollerraidcontinuousavailabilityraid"></a>Device.Storage.Controller.Raid.ContinuousAvailability.RAID

*设备和驱动程序必须满足的 RAID 功能要求的最小集合。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

-   设备及其驱动程序必须支持从 SBC 2 （或更高版本） 的命令而不考虑该驱动器接口实现。

-   设备及其驱动程序必须支持，最少的一个︰ RAID1、 RAID 5、 与 RAID6 或 RAID 1/0，或者等效的功能支持完整 LUN 出现故障的单个数据驱动器的功能。

-   设备和驱动程序 RAID 实现的必须提供一个解决方案，以防止数据丢失，因为 RAID"写孔"故障机制。 （请参阅设计备注 RAID"写孔"故障机制的定义）。

**设计备注**

如果在活动的写操作期间系统或控制器故障，条带化 （如奇偶校验） 擦除代码信息可能会变得不一致的数据。 如果此擦除错误代码信息以后用于重建该带区中的丢失块，可能会导致数据丢失。 这个问题被称为 RAID"写洞"。

-   属于典型的 RAID 写入漏洞问题的解决方案是提供机制来检测和恢复被中断的更新的就地操作或避免就地更新语义。

### <a name="devicestoragecontrollerraidcontinuousavailabilityrecoveryprocessing"></a>Device.Storage.Controller.Raid.ContinuousAvailability.RecoveryProcessing

*设备和驱动程序必须自动完成所有通过 LUN 从 Windows 故障转移群集中的节点产生故障的恢复处理。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

当在 Windows 故障转移群集中配置的设备和驱动程序和故障修复后恢复 LUN 访问权限 （请参阅要求 CAHWStorage 0004），必须自动完成所有设备和驱动程序的故障转移操作恢复，并恢复正常操作所需的处理即无需任何手动干预。

<a name="device.storage.controller.sas"></a>
## <a name="devicestoragecontrollersas"></a>Device.Storage.Controller.Sas

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollersasinterface"></a>Device.Storage.Controller.Sas.Interface

*SAS 控制器接口*

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

SAS 接口

SAS 主机总线适配器微型端口驱动程序必须使用 Microsoft hbaapi DLL 以支持 Windows 管理规范 (WMI) 方法。 特定于所需的 WMI 类和方法分组并指定为必需或可选。 必须支持所有必需的类和方法。 如果一组标识为可选，微型端口驱动程序支持该组各个方法和该组内的类也归为实现组时，如果必需还是可选的如果在组中未实现。

**注意︰**SAS HBA API 目前在 T11.5 工作组在草拟阶段。 草稿文档已完成，这种支持将不要求。 WHQL 将发出公告，要求这种支持时。

### <a name="devicestoragecontrollersastranslationlayer"></a>Device.Storage.Controller.Sas.TranslationLayer

*定义从 SAS 为必须实现的 SATA 的特定翻译*

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

（如果实现）

SAS Hba 和/或其驱动程序应实现以下 SCSI / ATA 翻译，定义在 T10 SAT-4 规格 （修订 03a）︰

-   下载的微码模式 0Eh （第 8.16.2.5 节）
-   下载的微码模式 0Fh （第 8.16.2.6 节）

注意︰ 通过连接到 SAS HBA 的 SATA 驱动器，符合 Windows 10 固件更新要求，且运行 HLK 固件更新测试，符合这一要求应进行测试。 测试控制器的转换层应通过 SAS 扩展器的目标 （SATA 驱动器） 和控制器 (HBA) 之间。

<a name="device.storage.controller.sata"></a>
## <a name="devicestoragecontrollersata"></a>Device.Storage.Controller.Sata

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollersatainterface"></a>Device.Storage.Controller.Sata.Interface

*SATA 控制器接口*

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

SATA 接口
 

-   SATA 控制器必须遵守的 ATA/ATAPI-7 规范。

-   SATA 控制器必须支持热插拔。

-   在串行 ATA SATA 控制器应支持异步通知︰ 高速度序列化在附件、 2.6 或更高版本，AHCI 1.3 或更高版本。

-   如果实现，必须正确地支持 NCQ。

-   如果实现，必须正确地支持大扇区 512 字节以外。

-   AHCI SATA 控制器必须遵守 AHCI 1.0 规范或更高版本。

-   SATA 控制器应不会模拟 PATA。

-   AHCI SATA 控制器的接口实现接口以外 AHCI，Windows 的收件箱驱动程序必须支持必须证明提供的驱动程序集。 提供的驱动程序必须满足本文档中的驱动程序认证要求。

-   建议︰ SATA 控制器应实现接口的电源管理。

-   建议︰ SATA 控制器应实现本机命令队列 (NCQ) 的支持。

<a name="device.storage.controller.sd"></a>
## <a name="devicestoragecontrollersd"></a>Device.Storage.Controller.SD

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragecontrollersdbasicfunction"></a>Device.Storage.Controller.SD.BasicFunction

*SD 控制器的基本功能*

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

-   支持 SD 标准的主机接口 (按照 SD 3.0 标准)。

-   支持 CMD21 eMMC HS200 的优化。

-   除缓冲区读取已准备好执行 SD 3.0 设备 (CMD19) 或 eMMC 4.5 设备 (CMD21) 的调节过程时，应禁用所有中断。

-   调节过程必须使用调节块分别在 SD 和 eMMC 标准规范中定义的标准。

-   支持 1.8 v 和 3.3 v 信号电压。

-   支持 ADMA2 （没有系统 DMA）。

-   正确表达的标准功能寄存器中的主控制器所支持的所有功能。

-   支持字节 （8 位）、 （16 位），字和双字 （32 位） 寄存器访问基于寄存器大小标准主机控制器规范中给出。

-   支持写保护写保护的位置将由值为 0。

-   支持 1 位，4 位总线宽度。 8 位总线宽度也是必需的 eMMC 控制器。

-   支持所有 UHS-我模式 (SDR50，DDR50，SDR104)。 HS200 也是必需的 eMMC 控制器。

-   没有 retuning 应为所需的 SDR50 模式。

-   Retuning 不应要求软件计时器。

-   支持自动 CMD23 和自动 CMD12。

-   任何专用寄存器位没有切换应启用所有功能所需。

-   时钟频率应根据标准规范进行计算。

-   支持标准错误恢复过程。

<a name="device.storage.controllerdrive.nvme"></a>
## <a name="devicestoragecontrollerdrivenvme"></a>Device.Storage.ControllerDrive.NVMe

*NVMe 存储功能*

### <a name="devicestoragecontrollerdrivenvmebasicfunction"></a>Device.Storage.ControllerDrive.NVMe.BasicFunction

*NVMe 设备要求*

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

**说明**

必须由 NVMe 设备通常满足以下要求︰

-   该设备必须支持 PCIe Gen2 或更高版本。

该设备必须支持以下中断模式︰


-   运行使用的中断请求的数量 (即&gt;1 MSI 或 MSI-X 基于中断)

-   与只有一个 MSI 或 MSI-X 中断运行

-   与只有 1 行基于中断运行

    -   \[服务器\]MSI-X 是必需的

    -   \[客户端\]MSI 或 MSI X 是必需的

该设备必须使用以下类和子类代码标识，为进一步匹配的供应商和产品标识的驱动程序应使用︰

-   基本类︰ 01 h

-   Sub-h 类︰ 08

-   编程接口︰ 02 h

该设备必须有至少一个可升级固件插槽。

\[客户端\]（如果实现） 的设备应支持任何一个︰

-   最大列出的耗电量不超过 5mW 和退出的延迟小于 100 （隐含 L1.2），可操作状态为非操作 NVMe 电源状态或

-   从 D3cold 中恢复的能力 （关机） 内 500，同时不超过 1,000ms 的输入延迟。

注︰ 如果设备不提供这样的电源状态或功能，连接备用系统上的经验将会影响产生负面当电池消耗增加显著。

强烈建议，将被用于在客户端系统中具有有限的冷却功能的 NVMe 设备支持至少 100%除了以下打开和关闭状态︰

-   1 可操作电源状态 （降低性能） – 这样，可能会大量热量限制设备

-   1 非运营电源状态，恢复延迟至多 50 毫秒。

该设备必须满足以下要求是特定于版本 1.0 的官方的 NVMe 规范︰

-   3.1.1 控制器功能

    -   MPSMIN （内存页大小最小值） 必须设置为 0。 位︰ 51:48

-   5.2 异步事件请求

    -   错误事件，以及智能 / 健康状态事件必须得到支持，请参阅一节 5.12 下面。

-   5.3 创建 I/O 完成队列

-   5.4 创建 I/O 提交队列

-   5.5 删除 I/O 完成队列

-   5.6 删除 I/O 提交队列

-   5.3 通过 5.6 版必须支持至少 2 队列

    -   I/O 提交和完成队列的 1 套，1 套管理提交和完成队列是容许的。

    -   注意︰ 建议在客户端设备和 16 或更多服务器设备提供一套每个处理器的队列绑定到系统的能力上提供至少 4 个 I/O 队列。

-   5.7 固件提交

    -   不需要电源循环设备的情况下应该进行激活的固件映像。

    -   激活过程有望通过主机启动重置，能实现的规范版本大 1.2 a 8.1 节中所述。

-   5.8 固件图像下载

    -   该设备一定不能 I/O 失败的下载阶段，应继续为 I/O 提供服务。

-   5.9 得到功能 – 至少必须准确报告如下︰

-   5.12.1.5 错误恢复

-   5.12.1.6 易失写入高速缓存

    -   易失写入缓存不在设备上需要遵守这些要求。 此字段的准确报告。

-   5.12.1.8 中断合并

    -   \[服务器\]所需

    -   \[客户端\]不需要

-   5.12.1.11 异步事件配置

-   5.10 获取日志页

    -   设备必须实施和错误的信息 (01h) 智能至少填充日志页 / 固件插槽信息 (03h) 和健康信息 (02)，

-   5.11 标识

    -   MDTS （最大数据传输大小） 必须为 0 （无限制） 或至少 5 (128 KB)。 字节︰ 77

        -   注意︰ 增加这个值可能会在将来的修订下, 一代设备的设计应符合这一点。

    -   NN （的命名空间数） 必须至少为 1。 字节数︰ 519:516

    -   必须有 FLBAS （LBA 格式大小） 位设置为 0 的 4。 字节︰ 26

        -   如果支持元数据功能功能，保留这一要求，否则它可以忽略;亦即，iff MC 1 位设置为 1，上面的 FLBAS 要求绑定。 字节︰ 27

    -   LBADS （LBA 数据大小） 必须设置为 9 或 12，即 512B 或 4 KB。 比特︰ 23:16

        -   其他 LBA 数据大小是可以接受的，，只要支持 512B 或 4 KB。

    -   NGUID （Namespace 全局唯一标识符） / EUI64 必须实现。

        -   创建命名空间时，控制器应此字段或 EUI64 字段中指定命名空间的全局唯一标识符。

-   5.12 设置功能 – 至少必须实现以下︰

    -   错误恢复 (05h)

    -   易失写入缓存 (06h)

        -   如果设备中存在的易失写入高速缓存

    -   队列 (07h) 的数目

    -   中断合并 (08h)

    -   异步事件配置 (0Bh)

-   5.13 （如果实现） 格式 NVM

    -   该设备能够执行加密的擦除 （SE 值 \r 010b）

        -   如果不支持加密的擦除，则 Windows 将无法利用的 FormatNVM 命令。

    -   NVM 格式必须是可在单个名称空间，亦即，位 1 和 0 位在确定控制器的数据结构中，字节 524 (FNA)，必须设置为 0。

-   6.6 数据集管理--解除分配

    -   所有 I/O 和解除分配命令应在少于 500 毫秒内都完成。

    -   应以不超过 100 毫秒为单位完成 I/O 命令的 98.5%。

-   6.7 刷新

    -   如果设备中存在的易失性缓存

-   6.8 读

-   6.9 写

<a name="device.storage.enclosure"></a>
## <a name="devicestorageenclosure"></a>Device.Storage.Enclosure

*驱动器箱必须满足这些要求。*

### <a name="devicestorageenclosuredirectaccess"></a>Device.Storage.Enclosure.DirectAccess

*驱动器机箱必须提供直接访问它们存放的驱动器。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

存储模块不必须是抽象的他们存放的驱动器 （例如，形成逻辑的 RAID 磁盘）。  集成的交换机，如果存在，必须提供发现和访问存储模块中的所有驱动器而无需额外的物理主机连接。

### <a name="devicestorageenclosuredriveidentification"></a>Device.Storage.Enclosure.DriveIdentification

*驱动器机箱必须提供驱动器标识服务。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

存储箱必须满足以下要求才能支持存储空间配置。

-   必须支持下列命令︰

    -   查询

    -   发送诊断

    -   诊断结果

    -   请求检测

    -   准备好测试单元

-   必须设置一个标准的查询数据 (SPC4)，以指示该存储目标设备中的 ENCSERV 位包含通过该逻辑单元可查找嵌入盘柜服务组件。

-   盘柜服务设备都必须支持以下诊断页︰

    -   受支持诊断页诊断页 (00h)

    -   配置诊断页 (01h)

    -   盘柜控制诊断页 (02h)

    -   盘柜状态诊断页 (02h)

    -   其他元素状态诊断页 (0Ah)

-   以下类型的控件和状态元素使用在 Windows 存储空间功能;

| 元素类型代码 | 元素类型名称                        |
|-------------------|------------------------------------------|
| 01h               | 设备的插槽                              |
| 02h               | 电源设备                             |
| 03h               | 冷却                                  |
| 04h               | 温度传感器                       |
| 07 h               | 盘柜服务控制器电路 |
| 12 小时               | 电压传感器                           |
| 13 h               | 当前传感器                           |
| 17 h               | 阵列设备插槽                        |

-   设备的插槽 (01h) 或阵列设备插槽 (17 h) 元素类型必须支持存储盘柜。 所有其他元素类型 （电源、 冷却、 温度传感器、 盘柜服务控制器电路、 电压传感器和当前传感器） 是可选的。

<!-- -->

-   对于其他元素状态诊断页 (0Ah)，存储模块应提供其他元素状态描述符 EIP （元素索引存在） 位设置为 1:

    -   报告的驱动器托架的元素索引字段的升序顺序。

    -   协议标识符必须设置为 6 h (SAS)。

-   SES 设备必须报告驱动器报告设备标识 VPD 页 (83 h) 相同的地址应包括在其中的目标端口名称或标识符 （参见 SAM 5） 表示一个指定描述符。 指定描述符中，如果有的话，应有关联字段设置为 01b （即目标端口），并将标志类型字段设置为︰

    - 下半年 (即基于 EUI-64);

    - 3 h （亦即，naa） 制定;或

    - 8 h （例如，SCSI 名称字符串）。

<!-- -->

-   盘柜控制诊断页 (02h) 控制描述符将按升序排序的磁盘托架号枚举中。

-   必须遵守 T10 SES3 规范来实现存储模块控制诊断页和盘柜状态信息，1NON 紧急、 紧急和 UNRECOV 位诊断页。

-   在所有状态元素格式元素状态代码字段必须采用以下代码︰

| 代码     | 名称              | 条件                                                                                                                  |
|----------|-------------------|----------------------------------------------------------------------------------------------------------------------------|
| 0 h       | 不受支持       | 此元素未实现状态检测。                                                                      |
| 上半年       | 确定                | 安装元素，都已知的任何错误条件。                                                                    |
| 2 h       | 关键          | 临界条件被检测到。                                                                                            |
| 3 小时       | 非关键       | 非关键条件被检测到                                                                                          |
| 4 h       | 无法恢复     | 检测到无法恢复的情况。                                                                                       |
| 5 h       | 未安装     | 元素未安装在存储模块中。                                                                                     |
| 6 h       | 未知           | 传感器发生故障或元素状态不可用。                                                                      |
| 7 h       | 不可用     | 元素是安装，没有已知的错误，但该元素尚未开启或设置插入操作。                       |
| 8 h       | 不允许访问 | 启动器端口不从中接收接收诊断结果命令不具有访问此元素。 |
| 9h 对 fh 命令 | 保留          |  &nbsp;          |

备注︰ Windows 与关联字段设置为 1 关联到驱动器通过特定协议的信息，将驱动器的设备标识 VPD 页 (83 h) 盘柜服务。

<a name="device.storage.enclosure.azurestack"></a>
## <a name="devicestorageenclosureazurestack"></a>Device.Storage.Enclosure.AzureStack

*定义如果驱动器机箱支持 Microsoft Azure 堆栈基于私有云解决方案中必须满足的要求*

### <a name="devicestorageenclosureazurestackbasicfunction"></a>Device.Storage.Enclosure.AzureStack.BasicFunction

*在 Microsoft Azure 堆栈解决方案中使用的驱动器箱的基本要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

通过下表来捕获驱动器机箱的 Microsoft Azure 堆栈要求。

<table>
    <tr><th>功能</th><th>要求</th></tr>
    <tr><td rowspan="2">Device.Storage.Enclosure</td><td>Device.Storage.Enclosure.DirectAccess</td></tr>
    <tr><td>Device.Storage.Enclosure.DriveIdentification</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

除此之外，必须满足以下要求︰

- 存储箱必须有和报告的唯一 ID

### <a name="devicestorageenclosureazurestackcloudstress"></a>Device.Storage.Enclosure.AzureStack.CloudStress

*驱动器机箱提供私有云解决方案的群集存储，必须符合本规范* 

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

私有云解决方案构成了紧密集成的软件和硬件组件，以提供高性能的可恢复性。 中的任何组件 （软件、 硬件、 驱动程序、 固件等） 的问题会危害解决方案，并会破坏任何私有云的有关服务级别协议 (SLA) 所做的承诺。

许多这些问题都只能在云高强度的专用模拟出来后。 私有云模拟器 (PC) 使您可以验证您的组件在云方案并确定此类问题。 它通过创建 VM 工作负载、 调度管理操作 （负载平衡、 软件/硬件维护），和在私有云上注入故障 （没有计划的硬件/软件故障） 来模拟实时数据中心/私有云。

为遵守此规范，控制器必须通过 PC 上的测试运行的存储盘柜配置文件 4 节点群集配置中。

### <a name="devicestorageenclosureazurestackfirmwareupdate"></a>Device.Storage.Enclosure.AzureStack.FirmwareUpdate

*驱动器机箱提供私有云解决方案的群集存储，必须符合本规范* 

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

Microsoft Azure 堆栈需要存储模块是可更新的固件。



<a name="device.storage.hd"></a>
## <a name="devicestoragehd"></a>Device.Storage.Hd

### <a name="devicestoragehdbasicfunction"></a>Device.Storage.Hd.BasicFunction

*HD 基本功能*

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

该设备必须能够执行下列方案︰

-   顺序读
-   顺序写入
-   连续验证 （写跟读和比较）
-   随机读取
-   随机写入
-   随机验证

### <a name="devicestoragehdphysicalsectorsizereportsaccurately"></a>Device.Storage.Hd.PhysicalSectorSizeReportsAccurately

*报告物理扇区大小必须为单位的原子写。*

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

**以下适用于基于 ATA 硬磁盘驱动器中︰**

如果实现，支持大于 512 字节需要实现 ATA 8 规范中所述的逻辑扇区大小的存储设备。 请参阅 INCITS T13 规范存储库访问规范。

**以下适用于基于 SCSI 的硬磁盘驱动器中︰**

如果实现，支持大于 512 字节需要实现 SBC 3、 SPC-4 和 SAT-3 规范中所述的逻辑扇区大小的存储设备。 请参阅 INCITS T10 规范存储库访问相关的规范。
 
**业务理由**

某些硬盘驱动器错误地报告该磁盘的物理扇区大小。 例如，发布该驱动器而不报告它确实 4k 驱动器驱动器"4k"。 应用程序使用的报告物理扇区大小与原子性的概念和执行基于此的 i/o 操作。 最基本的示例为数据库样式应用程序只能存储一个提交记录内的原子写丢失为单位如果发生断电情况，或物理扇区将成为物理上损坏。 报告物理扇区大小不是原子性的单位，严重的可靠性问题会出现在方案中如丢失电源所在︰ 应用程序可能无法恢复，并且用户将需要从备份中还原。 应用程序可能无法恢复，但该应用程序将需要执行冗长的一致性检查。 元数据、 日志文件数据、 用户数据或从其他应用程序甚至数据已损坏。

### <a name="devicestoragehdrotationalrate"></a>Device.Storage.Hd.RotationalRate

*高清旋转速率徽标要求*

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

固态硬盘 (SSD) 设备应设置为非旋转的中等价值的名义介质旋转速率。 一种旋转或者混合的旋转和 SSD 设备应报告旋转介质的旋转速率。

**以下适用于基于 ATA 硬磁盘驱动器**︰

ATA 硬盘设备必须报告名义介质旋转速率的 ATA 8 规范中所述。 返回标识设备的 Word 217 命令不应 0000h。

**公称媒体旋转速率值描述**

| 值       | 说明                                                                         |
|-------------|-------------------------------------------------------------------------------------|
| 0000h。       | 未报告的速率                                                                   |
| 0001 h       | 非旋转介质 （例如，固态设备）                                       |
| 0002 h-0400 h | 保留                                                                            |
| 0401 h FFFEh | 在旋转，每分钟 (rpm) (例如︰ rpm = 1C20h 7 200) 名义介质旋转速率 |
| FFFFh       | 保留                                                                            |

**以下适用于基于 SCSI 硬盘的磁盘驱动器**︰

SCSI 硬盘设备必须报告名义介质旋转速率的 T10 SBC3 规范中所述。 使用查询命令返回的块设备特征 VPD 页面不应设置介质旋转速率 = 0000h。

**中型旋转速率字段**

| 代码        | 说明                                                                                              |
|-------------|----------------------------------------------------------------------------------------------------------|
| 0000h。       | 未报告介质旋转速率                                                                     |
| 0001 h       | 非旋转介质 （例如，固态）                                                                  |
| 0002 h-0400 h | 保留                                                                                                 |
| 0401 h FFFEh | 以 rpm （例如，7 200 rpm = 1C20h、 10000 rpm = 2710 h，和 15 000 rpm = 3A98h） 的名义中型旋转速率 |
| FFFFh       | 保留                                                                                                 |

<a name="device.storage.hd.1394"></a>
## <a name="devicestoragehd1394"></a>Device.Storage.Hd.1394

### <a name="devicestoragehd1394compliance"></a>Device.Storage.Hd.1394.Compliance

*IEEE 1394 硬盘驱动器上规范法规遵从性*

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

1394 法规遵从性

IEEE 1394 (Firewire) 的设备必须符合串行的总线协议 2 (sbp-2) 和 SCSI 主的命令-2 (SPC-2) 和磁盘设备必须符合与 SCSI 减少块命令 (RBC)。

参考规范标准...: sbp-2、 SPC 2、 Min:RBC
 

<a name="device.storage.hd.alua"></a>
## <a name="devicestoragehdalua"></a>Device.Storage.Hd.Alua

### <a name="devicestoragehdaluacompliance"></a>Device.Storage.Hd.Alua.Compliance

*非对称逻辑单元访问 (ALUA)*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

如果设备支持非对称逻辑单元访问 (ALUA)，设备必须符合 SPC3 r23 部分 6.4.2 作为标准查询数据中实现目标端口组支持 (TPGS) 的要求。

必须支持报告目标端口组中的命令，如果他们支持 ALUA 标准查询数据中报告的逻辑单元。 存储设备必须符合 SPC3-r23 部分 6.25 报告目标端口组根据其 TPGS 域代码中常用的查询数据的命令。
 

<a name="device.storage.hd.ata"></a>
## <a name="devicestoragehdata"></a>Device.Storage.Hd.Ata

### <a name="devicestoragehdatabasicfunction"></a>Device.Storage.Hd.Ata.BasicFunction

*ATA/ATAPI 接口*

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

PATA 设备 （传统）

（PATA 设备将不再被接受后 2013 年 6 月的 WHQL 提交。）

Microsoft 建议使用 SATA 的新设备。 但是，与基本的现有设备的兼容性的精神，在以下要求提供 PATA 设备。

共享的总线功能所需的 PATA 设备;设备应为设备 0 或 1 的设备配置。
 

### <a name="devicestoragehdatadma"></a>Device.Storage.Hd.Ata.Dma

*ATA/ATAPI DMA 模式。*

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

ATA/ATAPI DMA 模式

在 ATA/ATAPI-7 中定义的所有 PATA 控制器和 PATA 外围设备应都支持超高 DMA。

对齐︰

除了提高的传输速率，超高 DMA 还提供错误检查对以前 PATA 实施改进了可靠性。

<a name="device.storage.hd.ataprotocol"></a>
## <a name="devicestoragehdataprotocol"></a>Device.Storage.Hd.AtaProtocol

### <a name="devicestoragehdataprotocolperformance"></a>Device.Storage.Hd.AtaProtocol.Performance

*ATA 设备性能*

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

ATA 设备性能

数据块存储设备的 Windows 7 Windows 系统评估工具 (WinSAT) 磁盘正式测试必须通过以下性能要求的任何可见的存储空间利用率达 95%（的利用率的看到通过 Windows 文件系统"使用空间"%%）。

-   磁盘顺序 64k 字节读取&gt;25 MB/s

-   磁盘随机 16k 字节读取&gt;0.5 MB/s

-   磁盘顺序 64k 字节写入&gt;20 MB/s

-   平均读取时间顺序写入与&lt;25 毫秒

-   滞后时间︰ 95% &lt;120 毫秒

-   延迟︰ 最大&lt;700 毫秒

-   平均读取时间与随机写入&lt;40 毫秒

### <a name="devicestoragehdataprotocolprotocol"></a>Device.Storage.Hd.AtaProtocol.Protocol

*ATA/ATAPI 协议*

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

ATA/ATAPI 协议
 

-   ATA/ATAP 控制器和设备应符合以下标准

    -   INCITS 397-2005 (1532D): 在附件与数据包接口-7 或更高版本，也称为作为 ATA/ATAPI-7 本文档中。 在附件数据包接口-8 或更高版本将是必需的最终和发布此版本 8 时。

-   ATA/ATAP 控制器应支持 Windows 操作系统启动

-   ATA/ATAPI 设备不应依赖识别设备数据字段 (61:60) 和 (103:100) 来确定 28 或 48 位 LBA 寻址的支持。 ATA/ATAPI 应改为依靠的 word 83 位 10 和 word 86 弄寻址 （根据 ATA/ATAPI-7) 支持 48 位 LBA 的第 10 位。  

*设计备注*

建议︰

报告的标称媒体旋转速率

如果设备需要 Windows 碎片整理，关闭默认情况下，设备应为 0001 h 非旋转介质 （例如，固态设备） 根据 ATA8 ACS1 规范，部分 7.16.7.77 报告其标称的介质旋转速率。 

对齐︰

除 0001 h 非旋转介质设备报告的标称媒体旋转速率时，Windows 将默认执行碎片整理的数据块存储设备。
 

<a name="device.storage.hd.azurestack"></a>
## <a name="devicestoragehdazurestack"></a>Device.Storage.Hd.AzureStack

*定义磁盘支持基于 Microsoft Azure 堆栈私有云解决方案中必须满足的要求*

### <a name="devicestoragehdazurestackbasicfunction"></a>Device.Storage.Hd.AzureStack.BasicFunction

*对于 Microsoft Azure 堆栈解决方案中使用的磁盘的基本要求*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

通过下表来捕获 Microsoft Azure 堆栈要求磁盘。

<table>
    <tr><th>功能</th><th>要求</th></tr>
    <tr><td rowspan="3">Device.Storage.Hd</td><td>Device.Storage.Hd.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.PhysicalSectorSizeReportsAccurately</td></tr>
    <tr><td>Device.Storage.Hd.RotationalRate</td></tr>
    <tr><td>Device.Storage.Hd.DataVerification</td><td>Device.Storage.Hd.DataVerification.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.Flush</td><td>Device.Storage.Hd.Flush.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.PortAssociation</td><td>Device.Storage.Hd.PortAssociation.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.Sas</td><td>Device.Storage.Hd.Sas.ComplyWithIndustrySpec</td></tr>
    <tr><td>Device.Storage.Hd.Sata</td><td>Device.Storage.Hd.Sata.BasicFunction</td></tr>
    <tr><td>Device.Storage.Hd.Scsi.ReliabilityCounters</td><td>Device.Storage.Hd.Scsi.ReliabilityCounters.BasicFunction</td></tr>
    <tr><td rowspan="3">Device.Storage.Hd.ScsiProtocol</td><td>Device.Storage.Hd.ScsiProtocol.ReferenceSpec</td></tr>
    <tr><td>Device.Storage.Hd.ScsiProtocol.SamCompliance</td></tr>
    <tr><td>Device.Storage.Hd.ScsiProtocol.SpcCompliance</td></tr>
    <tr><td rowspan="6">Device.DevFund.Server.Nano</td><td>Device.DevFund.Server.OperateInServerNano</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Deployment</td></tr>
    <tr><td>Device.DevFund.Server.Nano.Diagnostics</td></tr>
    <tr><td>Device.DevFund.Server.Nano.PatchAndUpdate</td></tr>
    <tr><td>Device.DevFund.Server.Nano.MonitoringAndTelemetry</td></tr>
    <tr><td>Device.DevFund.Server.Nano.FirmwareUpdate</td></tr>
</table>

除此之外，必须满足以下要求︰

- 磁盘设备必须的并且报告为，SATA、 SAS 或 NVMe 总线类型
- 磁盘设备必须的并且报告为，SSD 或硬盘介质类型
- 磁盘设备必须有和报告的唯一 ID

### <a name="devicestoragehdazurestackcloudstress"></a>Device.Storage.Hd.AzureStack.CloudStress

*用作群集存储私有云解决方案的磁盘必须符合本规范*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

私有云解决方案构成了紧密集成的软件和硬件组件，以提供高性能的可恢复性。 中的任何组件 （软件、 硬件、 驱动程序、 固件等） 的问题会危害解决方案，并会破坏任何私有云的有关服务级别协议 (SLA) 所做的承诺。 

许多这些问题都只能在云高强度的专用模拟出来后。 私有云模拟器 (PC) 使您可以验证您的组件在云方案并确定此类问题。 它通过创建 VM 工作负载、 调度管理操作 （负载平衡、 软件/硬件维护），和在私有云上注入故障 （没有计划的硬件/软件故障） 来模拟实时数据中心/私有云。 

为遵守此规范，磁盘必须通过电脑测试运行使用存储磁盘 – AzureStack 上的 4 节点群集配置的配置文件。

### <a name="devicestoragehdazurestackfirmwareupdate"></a>Device.Storage.Hd.AzureStack.FirmwareUpdate

*用作群集存储私有云解决方案的磁盘必须符合本规范*

<table><tr><th>适用于</th><td><p>Windows 服务器 2016 x64</p></td></tr></table>

**说明**

Microsoft Azure 堆栈需要 SAS 和 SATA 驱动器将固件更新使用收件箱[固件更新机制](https://blogs.technet.microsoft.com/filecab/2016/01/25/updating-firmware-for-disk-drives-in-windows-server-2016-tp4/)，引入了在 Windows 服务器 2016 (更新-StorageFirmware)。


<a name="device.storage.hd.dataverification"></a>
## <a name="devicestoragehddataverification"></a>Device.Storage.Hd.DataVerification

*磁盘验证测试以确保没有数据丢失或损坏*

### <a name="devicestoragehddataverificationbasicfunction"></a>Device.Storage.Hd.DataVerification.BasicFunction

*所有存储设备必须在 Windows 中正常都工作。*

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

存储设备必须可靠地读取和写入数据而不会丢失数据或数据损坏。

<a name="device.storage.hd.ehdd"></a>
## <a name="devicestoragehdehdd"></a>Device.Storage.Hd.Ehdd

### <a name="devicestoragehdehddcompliance"></a>Device.Storage.Hd.Ehdd.Compliance

*加密的硬盘符合 Microsoft 和行业规范。*

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

加密的硬盘

eDrives 必须符合下列工业技术指标

-   IEEE 1667 版本 IEEE 1667-2009

    <!-- -->

    -   支持探测器思洛存储器
    -   支持 TCG 存储思洛存储器

    <!-- -->

-   TCG

    <!-- -->

    -   TCG 核心规范 2.0 版

    -   OPAL SSC 2.0

        <!-- -->

        -   以编程方式 TPer 重置修订版
        -   可修改的 CommonName 列
        -   SID 颁发机构禁用

        <!-- -->

    -   OPAL SSC 的功能集

        <!-- -->

        -   一组其他数据存储区 Rev 1.05 或更高版本
        -   单用户模式下 Rev 1.02 或更高版本

        <!-- -->

-   SCSI

    <!-- -->

    -   SPC4
    -   SAT2

    <!-- -->

-   ATA

    <!-- -->

    -   ACS2

eDrives 必须遵守这些 Windows 设计规范要求︰

-   至少支持 AES 128

-   支持一个或多个下面的密码模式

    <!-- -->

    -   CBC
    -   XTS

    <!-- -->

-   支持至少 8 带区

-   支持其他数据存储区表

-   支持范围跨越

-   支持的身份验证方法

-   支持密码保护信息

-   支持可修改的公用名称

-   支持 TCG 堆栈重置

-   支持以编程方式 TPer 重置

-   支持单用户模式

-   如果 SCSI devices(SPC4):-

    <!-- -->

    -   1667 版本描述符，0xFFC2 (IEEE 1667-2009年) 应报告在查询数据。 查询数据的额外长度字段必须是大于或等于 0x38。

    -   00，01，02，EE 支持安全协议列表有效负载中必须报告安全协议在输出

    <!-- -->

-   如果 ATA 设备 (ACS2):-

    <!-- -->

    -   TrustedComputer.FeatureSupported (word 48-0 位必须设置为"1") 必须在识别数据报告

    -   AdditionalSupported.IEEE1667IDENTIFY (字 69-7 位应设置为"1") 必须在识别数据报告

    -   受信任的接收输出应报告 00,01，02，以支持安全协议列表负载 EE

    <!-- -->

-   如果 SATA USB:-

    <!-- -->

    -   支持 SAT2

    <!-- -->

-   命令性能:-驱动器必须在指定的持续时间内完成以下操作

| 操作            | 最大完成时间 |
|-----------------------|---------------------|
| 发现/枚举 | 24 秒 （8 段）    |
| 激活              | 45 秒              |
| 还原                | 8 秒               |
| 创建带区           | 1.5 秒             |
| 删除带区           | 2 秒               |
| 删除带区            | 2 秒               |
| 设置元数据          | 20 秒              |
| 获取元数据          | 14 秒              |
| 带锁             | 1.5 秒             |
| 解除锁定带           | 1.5 秒             |

<a name="device.storage.hd.emmc"></a>
## <a name="devicestoragehdemmc"></a>Device.Storage.Hd.EMMC

*定义的行业和 Microsoft 必须满足的标准*

### <a name="devicestoragehdemmcbasicfunction"></a>Device.Storage.Hd.EMMC.BasicFunction

*Emmc 的基本功能*

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

必须支持行业标准。

eMMC 4.5.1 要求

-   支持放弃/净化两扇区大小和擦除块边界。

-   支持 HPI/BKOPS。

-   支持打包的命令。

-   支持 HS200 信令。

-   支持 DDR50 信令。

-   支持的大小和创建 Gpp 至少 128 KB RPMB。

-   支持睡眠 (CMD5)。

-   支持加密卸载操作 (CMD53/54)。

-   支持操作系统启动缓存刷新如果设备支持易失性缓存。

<a name="device.storage.hd.enhancedstorage"></a>
## <a name="devicestoragehdenhancedstorage"></a>Device.Storage.Hd.EnhancedStorage

### <a name="devicestoragehdenhancedstorage1667compliance"></a>Device.Storage.Hd.EnhancedStorage.1667Compliance

*增强的存储设备必须符合 IEEE 1667 定义标准。*

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

IEEE1667 类 （增强型存储） 启用存储设备必须符合行业标准。
增强的存储设备必须符合 IEEE 1667 定义标准。

-   必须增强的存储设备︰

    -   对主机进行身份验证的支持

    -   实现支持 IEEE 1667 （版本 1.1 版或更高版本） 定义探测器思洛存储器设备上。

    -   在设备上实现至少一个证书或密码思洛存储器。

-   必须增强实现证书思洛存储器的存储设备︰

    -   加载本机 windows 证书思洛存储器的驱动程序。

    -   对 IEEE 1667 1.1 版规范的所有命令做出响应。

    -   验证基于证书的身份验证用于允许和阻止访问卷。

-   必须增强实现密码思洛存储器的存储设备︰

    -   加载本地密码思洛存储器的驱动程序。

    -   对 IEEE 1667 密码思洛存储器规范中的所有命令作出响应。 

    -   验证基于密码的身份验证用于允许和阻止访问该卷。

*设计备注*

从以下位置的 IEEE 获取 IEEE 1667 规格︰<http://go.microsoft.com/fwlink/?LinkID=110100>

<a name="device.storage.hd.fibrechannel"></a>
## <a name="devicestoragehdfibrechannel"></a>Device.Storage.Hd.FibreChannel

### <a name="devicestoragehdfibrechannelcompliance"></a>Device.Storage.Hd.FibreChannel.Compliance

*光纤通道设备*

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

光纤通道设备必须符合 SCSI，第二个版本 (FCP 2) 光纤通道协议或更高版本。 若要确保电源和信号传输级别的互操作性，光纤通道设备必须符合第三代光纤通道物理和信号传输接口 (以前称为 ANSI X3。 303:1998)。
 

<a name="device.storage.hd.flush"></a>
## <a name="devicestoragehdflush"></a>Device.Storage.Hd.Flush

### <a name="devicestoragehdflushbasicfunction"></a>Device.Storage.Hd.Flush.BasicFunction

*刷新命令完成*

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

行业标准规格要求︰
 

-   对于 ATA 设备，刷新缓存 (E7h，非数据) 28 位命令是可选的 ATA 设备和 ATAPI 设备。 刷新缓存分机 (EAh，非数据) 48 位命令是强制实施的 48 位地址功能集的设备。

-   对于 SCSI 设备，应实现同步缓存 (10) 命令和/或同步缓存 (16) 命令。

Windows 设计规范要求的硬盘︰

-   正确的完成报告︰ 已经保持了高速缓存的内容时，仅当操作系统发出刷新缓存命令时，存储设备应同步报告命令的完成。

注︰ 此要求不适用于便携式计算机。

<a name="device.storage.hd.iscsi"></a>
## <a name="devicestoragehdiscsi"></a>Device.Storage.Hd.Iscsi

### <a name="devicestoragehdiscsibasicfunction"></a>Device.Storage.Hd.Iscsi.BasicFunction

*iSCSI 设备*

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

iSCSI 设备 iSCSI 设备必须符合 RFC3720，RFC3721 和 RFC3723。

-   设备必须使用 Microsoft iSCSI 发起程序来测试完成。

-   设备必须能够接收 ping (ICMP) 和发送 ping (ICMP)。

-   以下的 iSCSI 协议功能是必需的︰

-   发送的目标。

-   登录身份验证︰ CHAP 和无。 目标可能委托半径的 CHAP 身份验证。

-   查询会话登录键/值对︰ InitiatorName、 SessionType，以及身份验证方法。

-   普通会话登录键/值对︰ InitiatorName、 SessionType、 身份验证方法和 TargetName。

-   DataPDUInOrder。

-   DataSequenceInOrder。

-   DefaultTime2Wait。

-   DefaultTime2Retain

-   ErrorRecoveryLevel = 0。

-   允许不同的目标共享机密信息，以便不同的启动器名称。

以下的 iSCSI 协议功能必须通过测试，如果它们实现了︰

-   双方 CHAP。

-   HeaderDigest: CRC32 和无。

-   DataDigest: CRC32 和无。

-   InitialR2T。

-   IPsec;当使用 IPsec，则主模式必须可用。 此外，下列各项所需的 IPsec 实现时︰

    <!-- -->

    -   必须实现 IPsec 传输模式。

    -   Internet 密钥交换 (IKE) 实现必须支持主模式和预先共享的密钥。 目标端口具有相同的 IP 地址必须预料到相同的主模式 IKE 策略。

    -   目标方和发起方必须允许不同的标识符有效载荷的不同的预共享的密钥。

    -   目标方和发起方必须具有主模式的静态 IP 地址。

    -   其他标准查询数据版本描述符 (SPC-3) 是必需的

    -   至少一个 iSCSI 版本描述符是必需的 (值 = 0960 h)。

<a name="device.storage.hd.mpio"></a>
## <a name="devicestoragehdmpio"></a>Device.Storage.Hd.Mpio

### <a name="devicestoragehdmpiobasicfunction"></a>Device.Storage.Hd.Mpio.BasicFunction

*提供了多路径解决方案的 RAID 实现必须遵循与 Microsoft 多路径 I/O (MPIO)。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

提供了多路径解决方案的内部或外部 RAID 实现必须符合 Microsoft 多路径 I/O (MPIO)。 Windows 的多路径解决方案必须包含的设备特定模块 (DSM) 使用 Microsoft MPIO DDK 创建的必须遵守多路径 I/O 计划协议中规定的所有要求。
下面一些 WMI 类时，必须由第三方 DSM 来实现。

-     DSM\_QuerySupportedLBPolicies

-     DSM\_QueryUniqyeId

第三方 DSM 必须 DSM 的报告主要的次要版本号
 

<a name="device.storage.hd.multipleaccess"></a>
## <a name="devicestoragehdmultipleaccess"></a>Device.Storage.Hd.MultipleAccess

*支持多个访问的驱动器必须满足这些要求。*

### <a name="devicestoragehdmultipleaccessmultipleports"></a>Device.Storage.Hd.MultipleAccess.MultiplePorts

*多端口的驱动器必须提供对称的访问。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

多端口驱动器必须在所有端口上都支持一组相同的命令。  驱动器不能提供不同的行为，或根据哪一个端口用于命令送达的命令的性能降低。

当驱动器连接到主机通过多个路径时，驱动器必须使用 Windows 的多路径 IO (MPIO) 解决方案与 Microsoft 设备特定模块 (DSM)。

例如︰ 驱动器必须提供相同的性能数据访问命令和永久保留命令到达不同的端口为它们提供了在同一端口上收到的那些命令时相同的行为。

10%范围内，应该是任何两个端口之间的性能下降。

说明︰ 多端口的驱动器可能连接到一个或多个计算机主机，每个主机的一个或多个路径。  将驱动器连接到多个主机，Windows 可以使用的驱动器作为主机的故障转移群集的一部分。  将驱动器连接到一台主机的多个路径通过使 Windows 继续提供在电缆故障驱动器的访问。  Windows 支持独立和联合使用这些连接的拓扑。

<a name="device.storage.hd.multipleaccess.persistentreservation"></a>
## <a name="devicestoragehdmultipleaccesspersistentreservation"></a>Device.Storage.Hd.MultipleAccess.PersistentReservation

*支持永久保留的驱动器必须满足这些要求。*

### <a name="devicestoragehdmultipleaccesspersistentreservationbasicfunction"></a>Device.Storage.Hd.MultipleAccess.PersistentReservation.BasicFunction

*驱动器必须提供永久保留。*

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

驱动器必须实现持久保留根据 scsi-3 主命令 (SPC-3) 规范。  在正确的行为取决于 Windows 下永久保留功能。
 

-   读取密钥 (00h) 中永久保留
-   永久保留在读取保留 (01h)
-   永久保留，出准备金 (01h)
    -   范围︰ LU\_范围 (0 h)
    -   类型︰ 编写独占-只登记 (5h)
-   永久保留，出发行 (02h)
-   永久保留，出清除 (03h)
-   永久保留，出抢占 (04h)
-   永久保留出登记并忽略现有的密钥 (06h)
-   永久保留，出登记 (00h)

备注︰ Windows 可以使用的物理磁盘存储池。  从存储池中，Windows 可以定义称为存储空间的虚拟磁盘。  故障转移群集可以使物理磁盘、 定义它们，则存储空间和它们包含的数据池高度可用。  除了标准 HCT 资格认证，物理磁盘应该还能通过"Microsoft 群集配置验证向导"(ClusPrep) 工具。

<a name="device.storage.hd.offloadeddatatransfer"></a>
## <a name="devicestoragehdoffloadeddatatransfer"></a>Device.Storage.Hd.OffloadedDataTransfer

*Windows 的卸载的数据传输*

### <a name="devicestoragehdoffloadeddatatransfercopyoffload"></a>Device.Storage.Hd.OffloadedDataTransfer.CopyOffload

*如果支持卸载副本，则必须实现这些要求。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

**行业标准规格要求︰**

-   支持 Windows 副本卸载功能的目标必须实现 T10 XCOPY 精简规范 (11-059r8):

    <!-- -->

    -   支持 VPD 页 （必须包含 ECOP VPD 页面 (页面代码 8Fh) 在支持 VPD 页列表）

    -   ECOP VPD 页或 ECOP VPD 页面 (页面代码 8Fh) + 块设备杆限制 ECOP 描述符 (0000h。)

    -   阻止限制 VPD 页面 (页面代码 B0h)

    -   根据 T10 11 059r8 规范中，Windows 将采用 83 h 操作码 + 10 个服务操作代码填充标记和 83 h 操作码 + 11 服务操作代码编写使用标记命令。

    -   根据 T10 11 059r8 规范中，Windows 将采用 84 h 操作码 + 07 服务操作代码接收杆标记信息的命令。 响应服务操作字段，并命令参数应符合 T10 XCOPY 精简规范 (11-059r8)。

**Windows 设计规范要求︰**

-   在目标设备枚举时，Windows 将沿支持 VPD 页 VPD 页查询发送。 如果 8F 包含在支持 VPD 页列表，Windows 将询问 ECOP VPD 的页和阻止限制 VPD 页。

-   实施和错误处理与 ECOP VPD 页的参数

    <!-- -->

    -   最大值范围说明符中的标记填充或编写使用令牌命令的块设备范围说明符的数目超过了最大范围说明符，如果复制管理器将终止检查条件状态命令与探测关键字设置为非法请求和太多的段描述符设置的附加探测代码。

    -   最大非活动状态计时器 (最大 IAT)-如果标记填充命令的不活动超时时间超过最大非活动状态计时器，复制管理器将终止命令检查条件状态及与探测关键字设置为非法请求，并将设置为无效的字段在参数列表的附加探测代码。

    -   标记的最大传输大小的

        -   如果在编写使用令牌命令的所有块设备范围说明符中的逻辑块编号字段的总和大于最大令牌传输的大小，复制管理器将与探测关键字设置为非法请求，并将设置为无效的字段在参数列表的附加探测代码终止检查条件状态的命令。

        -   如果在填充令牌的所有块设备范围说明符中的逻辑块编号字段的总和大于最大令牌传输的大小，复制管理器将探测关键字设置为非法请求，并将设置为无效的字段在参数列表的附加探测代码与终止检查条件状态的命令。

    <!-- -->

-   实施和错误处理块限制 VPD 页的参数

-   最大传输长度字段指示复制管理器接受为一个块设备范围描述符的块中的最大传输长度。 如果复制管理器收到请求的逻辑块的数目超过此最大值，然后复制管理器将检查疾病状态的命令终止与探测关键字设置为非法请求和附加探测代码设置为无效的字段在参数列表。

-   存储阵列必须同时支持同步和异步填充标记和编写使用令牌根据 T10 11 059r8、 11-078r4 和 11 204r0 规范。

-   存储阵列必须完成在很短的时间 （4 秒） 同步标记填充和编写使用令牌的命令，而不会导致任何 SCSI 命令的超时值。

**用户体验需求︰**

-   回退到旧的副本-Windows 副本卸载操作应该能够回到传统复制操作时副本卸载错误或报告的限制。

-   拖放复制经验-必须是能够支持拖，副本卸载能够存储目标设备使用拖放复制。

<a name="device.storage.hd.persistentreservation"></a>
## <a name="devicestoragehdpersistentreservation"></a>Device.Storage.Hd.PersistentReservation

### <a name="devicestoragehdpersistentreservationclusterfailover"></a>Device.Storage.Hd.PersistentReservation.ClusterFailover

*对于 RAID 阵列系统的群集故障转移*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

**要求**︰ 所有 Microsoft MPIO 设备特定模块 (DSMs) 必须是 Windows 硬件认证合格并支持注册和注销跨所有路径的持久预留。

设计备注︰

-   所有主机总线适配器 (HBA) 使用故障转移群集节点上可都使用仅在基于 Storport 微型端口模型 Windows 硬件认证合格的微型端口驱动程序。

-   利用高可用性故障转移群集上的所有多路径 I/O 解决方案必须基于 Microsoft MPIO。

-   我们建议，除了标准 HCT 限定所有解决方案，还要都验证使用"Microsoft 群集配置验证向导"(ClusPrep) 工具。

-   光纤通道、 iSCSI 和特别是串行连接 SCSI (SAS) 故障切换群集解决方案不能基于 RAID Hba 位置缓存和/或 RAID 配置为特定计算机/节点。 RAID 设置信息以及硬件缓存必须位于单个共享点，居住在外部存储控制器。

-   SAS、 FC 和 iSCSI 具有 （即当前 8nodes） 它们所支持的节点数没有限制。

注意︰ 旧并行 SCSI 服务器群集被限制在 2 个节点的最大大小。

-   只有使用串行 SCSI 协议 (SSP) 传输的 SAS 设备将支持故障转移群集 （包括 SAS JBOD 或任何 SAS SSP RAID 系统）。 SATA 设备连接至 SAS 域必须是 RAID 系统的一部分。

-   直接的 SATA 连接并不支持 SATA JBOD;系统必须包含 RAID。

-   如果系统磁盘连接到总线类型，它不是有效类型为共享存储 （其他东西然后光纤通道、 iSCSI 或 SAS），则系统磁盘和共享的存储必须存放在单独的物理控制器/主机总线适配器。

<a name="device.storage.hd.portassociation"></a>
## <a name="devicestoragehdportassociation"></a>Device.Storage.Hd.PortAssociation

*驱动器必须提供端口关联。*

### <a name="devicestoragehdportassociationbasicfunction"></a>Device.Storage.Hd.PortAssociation.BasicFunction

*驱动器必须提供端口关联。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

驱动器必须报告其端口地址的设备标识 VPD 页 83 h 查询关联类型 1 （端口关联）。  这必须是相同的地址到 SCSI 盘柜服务 (SES) 设备和 SES 设备提供驱动器报告通过 SES 诊断页 0Ah 协议标识符设置为 6 h。

注意︰ Windows 取决于驱动器机箱提供 SCSI 盘柜服务 (SES) 的功能，如驱动器插槽标识和视觉的驱动器 （通常为驱动器指示灯实现） 的迹象。  Windows 匹配 SES 标识功能的存储模块中的驱动器通过驱动器的端口地址。  计算机主机可能是不同的驱动器箱或集成驱动器箱。

<a name="device.storage.hd.raidarray"></a>
## <a name="devicestoragehdraidarray"></a>Device.Storage.Hd.RaidArray

### <a name="devicestoragehdraidarraybasicfunction"></a>Device.Storage.Hd.RaidArray.BasicFunction

*RAID 阵列系统*

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

RAID 要求

RAID 系统和设备都必须支持从 SBC 2 （或更高版本） 的命令而不考虑该驱动器接口实现。

RAID 控制器和 RAID 系统必须支持，最少的一个︰ RAID1、 RAID 5、 与 RAID6 或 RAID 1/0。

外部 RAID 阵列必须允许是多余的不需要关闭或暂停系统手动替换出现故障的驱动器。 这一要求包括，但不是限于、 镜像集、"热备份"，取代物理驱动器和 RAID 级别 5 阵列中的第一个故障的驱动器中的驱动器。 RAID 子系统还必须允许数据丢失，重建不会影响系统操作。 预计 RAID 阵列吞吐量在重建期间，会受到影响。

### <a name="devicestoragehdraidarraybitlocker"></a>Device.Storage.Hd.RaidArray.BitLocker

*BitLocker 不得导致在存储阵列上的数据损坏。*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

必须正确启用 BitLocker 保护存储阵列上的数据量。

**业务理由**

（1） 当一台服务器放在没有足够的物理安全性的环境中时，BitLocker 保护以防未经授权的访问服务器上的数据，如果有人偷走了一台服务器。 （2） 当宿主服务提供程序的用途或停止使用的存储阵列，BitLocker 磁盘加密可以防止数据泄露。

<a name="device.storage.hd.readzeroontrimunmap"></a>
## <a name="devicestoragehdreadzeroontrimunmap"></a>Device.Storage.Hd.ReadZeroOnTrimUnmap

### <a name="devicestoragehdreadzeroontrimunmapbasicfunction"></a>Device.Storage.Hd.ReadZeroOnTrimUnmap.BasicFunction

*此要求适用于硬磁盘驱动器。*

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

如果资源调配读取的逻辑块零 (LBPRZ) 位设置为 1，则设备服务器应将所有位均为零的读操作上的映射 （释放或锚定） LBA Data-In 缓冲区中。

<a name="device.storage.hd.removablemedia"></a>
## <a name="devicestoragehdremovablemedia"></a>Device.Storage.Hd.RemovableMedia

*定义存储设备是否可移动的即必须满足的要求有 RMB 位设置为 1。*

### <a name="devicestoragehdremovablemediabasicfunction"></a>Device.Storage.Hd.RemovableMedia.BasicFunction

*真正的可移动存储介质的设备*

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

与真正的可移动存储介质的设备应报告为 True 的可移动媒体 (RMB = 1) 根据 SPC 4 修订 29 日部分 6.4.2。

<a name="device.storage.hd.sas"></a>
## <a name="devicestoragehdsas"></a>Device.Storage.Hd.Sas

### <a name="devicestoragehdsascomplywithindustryspec"></a>Device.Storage.Hd.Sas.ComplyWithIndustrySpec

*串行连接的 SCSI 设备必须遵守行业规范。*

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

规范标准的参考资料。 作为最小值，说明基线规范是必需的。 "拍摄:"表示规范的首选的版本。 如果不另外指定，否则列出的版本将是最低要求。 除非另有说明，必须实现由标准机构归为必填字段的引用规范的所有功能。

SAS-1、 SAM 3、 SPC-3，Min:SBC-2 日，拍摄︰ SBC 3

串行连接 SCSI 设备符合串行连接 SCSI (SAS) 规范 1 或更高版本。

-   应不超过 10 %io 性能下降时导致 MPIO 配置中使用 SAS 存储设备。

-   SAS 存储设备应建立排在以下事件的检测单位注意。

    <!-- -->

    -   打开电源
    -   硬重置
    -   逻辑单元复位
    -   我\_T 结点丢失
    -   预期的断电

    <!-- -->

-   SAS SSD 必须实现以下 T10 (SCSI) 命令规范︰

    -   读取容量 (16)
    -   阻止限制 VPD 页 (页面代码 B0h)
    -   块设备特征 VPD 页面 (页面代码 B1h)
    -   资源调配 VPD 页面 (页面代码 B2h) 的逻辑块
        -   SAS 设备必须支持 SAM 5 规范 (T10) 中所述的任务中止功能。

-   SAS SSD 必须满足以下要求︰

    -   SAS SSD 目标设备必须返回中旋转速率 = 0001 h （非旋转中）

    -   SAS SSD 目标设备必须返回读取容量 (16) 命令与 LBPME 位设置为 1，设置类型字段 = 0 (000b) 报告资源调配的类型或在逻辑块资源调配 VPD 页面 (页面代码 B2) 1 (001b) 资源 Provisioned。

    -   SAS SSD 设备必须实现块限制 VPD 页 (页面代码 B0h) 并支持以下参数。

        <!-- -->

        -   最大值取消映射 LBA 计数
        -   最大值取消映射描述符块计数
        -   最佳粒度取消映射
        -   取消映射粒度对齐方式
        -   UGAVALID 位

    -   SAS SSD 目标设备必须实现逻辑块资源调配 VPD 页 (页面代码 B2h) 并支持以下参数︰

        -   LBPU 位
        -   LBPRZ 位
        -   供应类型字段。

    -   SAS SSD 必须支持 UNMAP (10) 命令和 LBP VPD 页中的 LBPU 位应设置为 1。

        -   如果设备报告搜寻的惩罚 (SMR)，应用下面的阈值︰

            -   98.5%的所有 i/o 操作必须在 200 毫秒内完成
            -   在 1,000ms 内完成 100%的所有 i/o 操作必须

        -   否则为 (SSD):

            -   98.5%的所有 i/o 操作必须在 100 毫秒内完成
            -   100%的所有 i/o 操作必须在 500年内完成

<!-- -->

-   如果返回 ReadCapacity(16) 中的 LBPME 位设成 1，SAS SSD 设备必须支持逻辑块资源调配 VPD 页面 (页面代码 B2h)

-   如果返回 ReadCapacity(16) 中的 LBPRZ 位设成 1，SAS SSD 设备必须将 LBPRZ 位逻辑块资源调配 VPD 页设置为。

（如果实现）固件下载和激活

SAS 设备实现能够下载和激活固件，即命令写入缓冲区，应表现方式如下︰

-   0Eh 模式 (下载与偏移量的微代码保存，并推迟激活) 和 0Fh （激活延迟微码） 写入缓冲区的命令应由设备支持。

-   该设备必须通过固件下载/激活周期保留永久保留。

-   设备必须保留 VPD 0x83 翻阅下载和激活的固件映像。

-   下载操作必须能够使用 SCSI 缓冲区 ID 0 和传输大小为 64 KB。

-   写入缓冲区命令 (子 0Eh) 的执行不应防止执行的其他读取或写入 I/O 设备队列中。 下载操作 (子 0Eh) 过程中应无 I/O 故障

-   如果从其他发起方的 i/o 操作失败 (子 0Fh)--在激活期间能与探测微代码已更改的代码。

-   激活过程必须发生而不需要重启主机或总线重置，即，必须通过 SAS 驱动器的内部复位完成激活。

<a name="device.storage.hd.sata"></a>
## <a name="devicestoragehdsata"></a>Device.Storage.Hd.Sata

### <a name="devicestoragehdsatabasicfunction"></a>Device.Storage.Hd.Sata.BasicFunction

*ATA 设备性能*

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

SATA 设备︰ 

SATA 设备︰ 

-   要求︰ SATA 设备应满足的要求的串行 ATA︰ 高速度序列化在附件、 2.6 或更高版本。

-   建议︰ SATA 设备应实现电源管理接口

-   建议︰ SATA 设备应实现本机命令队列 (NCQ) 的支持

-   热插拔程序︰

    -   如果设备连接到端口标记为"外部"热插拔支持是必需的。 一个端口被视为"外部"如果以下寄存器设置 （根据 AHCI 行业规范） 的任何一个为真︰

        -   PxCMD.HPCP = 1;

        -   首字下沉。SXS = 1，PxCMD.ESP = 1;

        -   首字下沉。SMPS = 1，PxCMD.MPSP = 1

    -   如果设备连接到标记为"内部"端口需要热插拔事件生成无中断

（如果实现）固件下载和激活

SATA 驱动器实现能够下载和激活固件，即命令下载微码 DMA (识别设备字 69 位 8 = = 1) 或命令下载微码 (识别设备字 83 位 0 = = 1) 应表现在以下方面︰

-   设备必须保留以下标识设备数据通过下载和激活的固件映像︰ 供应商 ID、 模型 ID 的序列号。

-   激活过程必须发生而不需要重启主机或总线重置，即，必须通过内部复位的 SATA 设备完成激活。

-   \[DMA\]驱动器应支持识别设备数据日志页 03h。

    -   字段"DM 偏移推迟支持位"应设置为 1，表示支持子 0EH 和 0FH。

-   \[DMA\] 0Eh"下载，偏移量和保存以备将来使用的微代码"应支持下载微码 DMA 命令的子命令。

-   \[DMA\]下载微码 DMA 应支持的命令的子命令 0Fh"激活下载微码"。

注意︰ 这些命令的 DMA 实现是首选但不是要求

<a name="device.storage.hd.sata.hybridinformation"></a>
## <a name="devicestoragehdsatahybridinformation"></a>Device.Storage.Hd.Sata.HybridInformation

*此功能将支持混合信息功能的所有设备。*

### <a name="devicestoragehdsatahybridinformationbasicfunction"></a>Device.Storage.Hd.Sata.HybridInformation.BasicFunction

*SATAIO 混合驱动器的要求*

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

以下功能和要求必须支持的设备，通常是指混合设备。 在使用 Windows 内置驱动程序 (StorAHCI.sys) 的需要。

如果一个驱动器报告自身状态为混合驱动器，它必须包含一个旋转磁盘并在单个物理设备中的至少一个非易失性缓存 (NVC) 组件。

自锁定上启动

设备应实现自我针 1 和针引导文件，即在窗口成为活动的最高优先级级别的缓存到之前的任何机制。 具体来说，驱动器应自行收回以这种方式从电源上混合信息日志页读取之前。 驱动器应停止 160 MB 的数据具有固定后自我锁定为头等大事。 所有其他自我锁定驱动器执行多只应出现在优先级为 0。

高速缓存大小

混合缓存已向主机提供至少 5 GB （5 x 2<sup>30</sup>个字节） 的可用容量。

注意︰ 设备提供少于 12 GB 的可用高速缓存容量不会有资格受益于后，交换文件，或其他连续 I/O 缓存。

6 优先级 (0 到 5)

该设备必须支持至少 6 优先级级别。 由主机放置到缓存中没有数据应被逐出范围 1 到 5 的设备，除非 Windows 指定它通过调用以退出，demotebysize 或修剪，或问题进一步 I/o 优先级&gt;0 到完整的缓存 （即缓存翻涌着）。

优先级为 0

提示在优先级为 0 的任何 i/o 请求应直接由盘片上，而不考虑当前的状态 （即，如果盘片降速或接收一个优先级为 0 的 I/O，它应加速）。 I/O 优先级为 0 曾暗示应绕过非易失性缓存，并使任何驻留在缓存中的 LBAs，提示在优先级为 0 并立即显示在盘片上。

闪存的直接访问

时盘片降速，所有的提示的写命令 — 优先级为 0 写入-除应直接由非易失性缓存提供服务。 写 I/O 应不转移在盘片上第一次，以避免盘加速旋转。 如果写不能由非易失性缓存，由于资源限制 （没有干净的页面，等等） 磁碟可能加速 I/O 提供服务。

在待机电

该设备必须支持 SATA 规范 ATA ACS-3 中定义电源设置在待机功能 (PUIS)。

高速缓存页替换

驱动器应重新调整用途，较低的优先级，以满足在更高的优先级，优先级最低启动 i/o 操作的高速缓存页数。 例如，如果缓存已满在优先级为 0 的 25%，按优先级 2、 50%和 25 %3 的优先级和优先级 3 读/写发生不在缓存中，缓存页面应该改变用途以容纳优先级优先级 0 3 LBA 读取。 一旦所有优先级为 0 的高速缓存页数改变都用途，将分别改变都用途优先级别 1 和 2 页。 如果页面没有低优先级可用，应重新调整优先级 3 页面第一次类似于 LRU 算法选择的。

在 IO （读/写） 更新优先级

与缓存中的 LBAs 的优先级必须更新所有后续的读取或写入该 LBA，从任何有效的优先级为任何有效的优先级。 此外，如果读取或写入到当前未驻留在缓存 LBA 区域颁发，然后它应放置在指定的优先级在缓存 （缓存中没有空间，或有块可以被逐出的较低优先级的 — 缓存已满时提供）。

Trim

设备应支持在 Windows 8 硬件认证要求，在 Device.Storage.Hd.Trim.BasicFunction 中定义修剪。

非易失性缓存性能︰

随机读取︰ &gt;= 8 MB/s @ 4 KB (队列深度 = 1)

滞后时间︰

设置已更新高和脏的低阈值应在 50 毫秒内完成。

可以以异步方式完成此命令。

执行优先级信息的 I/O 不应显著低于无优先级信息的 I/O。 读取或写入具有指定的优先级必须不会大于大滞后造成轻微影响相同的 I/O 优先级信息或 0.5 毫秒 （最多 （10%，0.5 毫秒)） 的 10%。 与永远不会超过 100%的非优先级 I/O 的损失，对 95%的所有 I/o 实现这是可以接受的。

HybridDemoteBySize 必须返回内 500年 3/255<sup>个</sup>缓存大小的上调用时。

HybridChangePriorityByLBARange 必须在 32 MB 区域的数据调用时 150 毫秒内返回。

这些命令可能异步实现是可以接受的。

命令/协议要求

以下功能和要求必须支持的设备，并引用 SATA 修订 3.2 由 SATAIO 处理的︰

13.7.5.4.11 MaxPriority 行为

MaxPriority 行为位必须设置为 0。

13.3.15 启用/禁用混合信息

13.6.5.4.13 混合控制

启用/禁用缓存中

窗口必须具有能够启用和禁用混合缓存。 后禁用混合缓存，缓存中的所有脏数据必须与最终的存储介质进行同步。

脏的低阈值

脏页高阈值

脏数据应同步中的升序排列优先级，例如，优先级为 1 的脏数据同步前，应进行同步优先级为 0 的脏数据。 当在设备上的脏数据量超过脏高阈值标记时，该设备必须以脏数据的同步。 它可以理解，这需要以加速旋转的盘片。

13.6.5.4.7 混合降级的大小

混合的信息功能相关的日志

该设备必须启用 Windows 混合日志页中读取并返回合理的信息。 换句话说，一般用途记录是必需的应设置版本编号为 0001 的 h。 具体来说︰

13.7.9 一个单词 0x12 的"常规用途日志目录"应设置为"1"指示"NCQ 非-数据"日志支持。

13.7.10 0x13 字"常规用途日志目录"应设置为"1"指示"NCQ 发送和接收"日志支持。

13.7.12 字 0x14"常规用途日志目录"应设置为"1"指示"NCQ 混合信息"日志支持。 Windows 包含能够确定如下︰

缓存中运行状况

脏的低阈值

脏页高阈值

最大的混合优先级别

最大优先级行为

NVM 大小

最大逐出命令。

最大值移出数据块

针对每个优先级级别︰

已消耗的 NVM 大小分数

用映射资源部分

脏数据小部分消耗的 NVM 大小

脏数据分数的消耗映射资源

13.6.5.4.1 混合中退出

退出命令指定的 LBA 范围应针对主像常规写入介质。 主机将通过后续刷新命令确保一致性 – – 酌情。 这样数据只驻留在盘片上的退出命令完成后，退出的 LBA 区域应失效 NVC 中。

13.6.5.4.10 混合 LBA 区域更改

必须支持设备，包括命令的缓存行为位 LBA 区域通过混合更改。

<a name="device.storage.hd.scsi"></a>
## <a name="devicestoragehdscsi"></a>Device.Storage.Hd.Scsi

### <a name="devicestoragehdscsiconnectors"></a>Device.Storage.Hd.Scsi.Connectors

*SCSI 接头*

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

如果已实现的外部连接器的 SCSI 接头，必须符合在 SCSI 或更高版本的规范要求。 SCSI 接头不得作为系统上的任何其他非 SCSI 接口使用相同的连接器类型。 所有外部并行 SCSI 接口必须使用 ANSI 批准总线图标进行标记。 对于内部和外部配置 SCSI 总线电缆必须插入主机适配器和设备的牛角和键控接头。 这将确保电缆已正确放置，以便用户无法正确插入电缆。 对于内部配置，一边的带状电缆和键控 SCSI 外围设备连接器，则必须指定针脚 1 的方向。

### <a name="devicestoragehdscsiparallelinterface"></a>Device.Storage.Hd.Scsi.ParallelInterface

*并行 SCSI 接口*

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

并行 SCSI 接口
 

-   并行 SCSI 设备和适配器遵循与 SCSI 平行界面-4 (SPI-4) 或更高版本。

-   终止︰ 自动终止电路和 SCSI 终结器满足 SPI 4 标准或更高版本。 并行 SCSI 主机控制器和适配器必须使用允许用户添加外接设备而不删除服务器机箱的自动终止。 在 SCSI 主机适配器中使用终结器必须是受管制的终结器，也称为为活动、 SCSI SPI-4 或 Boulay 的终结器。 内部电缆上建立的 SCSI 终结还必须满足的 SPI 4 规范。

-   终结器电源必须提供到 SCSI 总线与过电流保护。 主机适配器必须使用 PCI 或另一个扩展总线到 SCSI 总线系统主板实现提供终止电源 (TERMPWR)。 必须从 SCSI 总线中的 TERMPWR 线供电外部 SCSI 总线上的所有终结器。 此外，提供 TERMPWR 的电路必须具有内置的过电流保护。

-   自动终止或访问板载终止开关，必须提供外部可移动磁盘、 硬盘和 CD/DVD 光驱。 至少，必须提供一种机械的方式设置终止和交换机必须能够访问用户而无需打开设备机箱。

-   支持热插拔的所有 SCSI 设备必须都遵守附录 D 的 SPI-4，哪些地址 SCSI 设备插入和删除操作，并没有任何命令的活动。

-   差异的设备必须支持 DIFFSENS 定义在 SPI 4 标准或更高版本。

<a name="device.storage.hd.scsi.reliabilitycounters"></a>
## <a name="devicestoragehdscsireliabilitycounters"></a>Device.Storage.Hd.Scsi.ReliabilityCounters

*为实现该 SCSI 命令的磁盘的基本可靠性计数器功能设置。*

### <a name="devicestoragehdscsireliabilitycountersbasicfunction"></a>Device.Storage.Hd.Scsi.ReliabilityCounters.BasicFunction

*为实现该 SCSI 命令的磁盘的基本可靠性计数器功能设置。*

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

所有 SCSI 驱动器必须都提供有效的数据日志检测页面 (日志检测 4Dh) 参数，按照 SCSI 主命令 4 (SPC-4) 和 SCSI 命令第 3 块 (SBC-3) 规范之下。

-   开始-停止循环计数器 (0Eh)

<!-- -->

-   生产日期 (0001 h)

<!-- -->

-   读取错误计数器 (03h)

    <!-- -->

    -   总计 (0002 h)

    -   总的错误更正 (0003 h)

    -   未更正的错误总数 (0006 h)

    <!-- -->

-   温度 (0Dh)

    <!-- -->

    -   温度 (0000h。)

    -   参考温度 (0001 h)

    <!-- -->

-   写入错误计数器 (02h)

    <!-- -->

    -   总计 (0002 h)

    -   总的错误更正 (0003 h)

    -   未更正的错误总数 (0006 h)

    <!-- -->

-   后台扫描 (15h)

    <!-- -->

    -   后台扫描状态 (0000h。)

驱动器的物理移动记录介质和/或读写设备，如硬盘驱动器，必须提供有效的数据低于日志按照 SCSI 主命令 4 (SPC 4) 规范的意义上页 (日志检测 4Dh) 参数。

-   开始-停止循环计数器 (0Eh)

    <!-- -->

    -   指定的周期计数转移设备生存期 (0003 h)

    -   累计的启动停止周期 (0004 h)

    -   指定的加载卸载计数转移设备生存期 (0005 h)

    -   累计的加载卸载循环 (0006 h)

固态驱动器必须提供有效的数据低于日志按照 SCSI 命令第 3 块 (SBC-3) 规范的意义上页 (日志检测 4Dh) 参数。

-   固态介质 (11 h)

    <!-- -->

    -   使用耐受指示器 (0001 h) 百分比

<a name="device.storage.hd.scsiprotocol"></a>
## <a name="devicestoragehdscsiprotocol"></a>Device.Storage.Hd.ScsiProtocol

### <a name="devicestoragehdscsiprotocolreferencespec"></a>Device.Storage.Hd.ScsiProtocol.ReferenceSpec

*对规范的引用*

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

作为最小值，说明基线规范是必需的。 Rec 指示首选的版本的规范。 如果不另外指定，否则列出的版本将是最低要求。 除非另有说明，必须实现由标准机构归为必填字段的引用规范的所有功能。

SPI 4、 SAM-3，Min:SPC-2 日，拍摄︰ SPC 3、 最小值︰ SBC、 拍摄︰ SBC 2
 

### <a name="devicestoragehdscsiprotocolsamcompliance"></a>Device.Storage.Hd.ScsiProtocol.SamCompliance

*体系结构模型 SAM scsi-3*

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

体系结构模型 SAM scsi-3

SCSI 设备必须符合与体系结构模型 SAM scsi-3 或更高版本 （如 1394年设备的所述 sbp-2 除外），包括下列要求︰

-   所有设备都必须都支持 LUN 重置。 特别是，如果两个 Lun L0 和 L1 在同一目标下的有未完成的命令，将重置为 L0 LUN 必须清除为 L0 任何发出的未决命令只。

-   按照重置，所有设备必须都返回相应单位注意条件到任何一台启动器当前有权访问逻辑单元。

-   所有光纤通道、 iSCSI、 SCSI 和 SAS 设备必须支持多个启动器。

-   模式选择命令更改参数必须导致单元强调条件引发 SAM 3 与一致的任何其他启动器。

-   必须实现所有目标的 LUN 0。 至少，LUN 0 必须响应查询和多个 LUN 的所有目标必须都支持报告 LUN 命令。

-   如果添加或删除任何 LUN，启动器访问，设备必须报告单位注意条件 (06/3F/0E) 报告 LUN 数据已更改模式选择。 命令更改参数必须导致单元强调条件将受更改影响的任何其他发起人为引发。

-   无法识别的任何 SCSI 命令或格式不正确的命令描述符块 (CDB) 必须导致报告给发起人立即检查条件。

### <a name="devicestoragehdscsiprotocolspccompliance"></a>Device.Storage.Hd.ScsiProtocol.SpcCompliance

*主要 SCSI 命令 （SPC 3、 SPC 4 和 SBC-3）*

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

主命令 scsi-3 (SPC-3)，SCSI 主的命令-4 (SPC-4) 和 SCSI 数据块命令-3 (SBC-3)

设备必须遵守主要的 SCSI 命令︰ 支持作为必需的 SCSI 主命令中列出的命令 （SPC 3 或更高版本）。 此外，每种设备类型必须实现设置该类型 (SBC-3 块设备等等) 的强制性命令。

**为 SCSI 查询和报表 LUN 命令**︰

所有设备都必须都支持的 SCSI 查询命令。

多 LUN 设备必须始终响应发送到 LUN 0 即使未实现 LUN 0 的查询命令。 这可以通过返回设备类型限定符的 3 所示。

-   所有多 LUN 设备必须都支持报告 LUN 命令定义在 SPC 2 或更高版本。

-   Windows 支持仅单级最大为 255; 逻辑单元号请参见 SAM 3。 使用任何其他格式将被错误地解释，和设备可能不可用或将发生数据损坏。

所有标准查询数据必须正确设置的设备功能。

-   版本字段必须是大于或等于 04。 SA，则此字段必须 05 或更高版本。

-   附加的媒体更换器的驱动器必须在标准查询数据设置 MChgnr 位。

-   多 LUN 设备必须为 LUN 0 返回报告 LUN 的有效数据。

-   如果 LUN 0 不是可访问的外围设备类型，则应作为 1 返回外围的限定符。 如果使用 3 的限定符，则 scsi 端口将枚举整个目标设备。 强烈建议将 LUN 0 不能类型 0，因为它必须面临的所有发起程序。 数组可以将不同的逻辑单元映射到的每个启动器的 LUN 0 的情况下，才允许类型 0。

-   如果一个设备具有多个端口，必须设置 MultiP 位和页 83 h 描述符必须正确反映的端口信息。

重要产品数据 (VPD) 页︰

-   页号 （支持页面 VPD 页） 是必需的。

-   页面 B1h （块设备特征 VPD 页） 是必需的。

-   页面 80h （装置序列号 VPD 页） 是必需的。

    页 83 h （设备标识 VPD 页） 是必需的。 VPD 页 83，至少一个类型 3 或其中一个必须为每个逻辑单元，返回类型 2 描述符的值必须使用代码设置 1 （二进制） 的值必须是唯一的该逻辑单元，它必须为相同的值，而不管对该请求的响应的端口的路径。 对于多端口设备的相应描述符所需除此之外必填字段描述符。 支持别名的设备还必须支持相应描述符类型。 特定于供应商的设备标识符 （如果存在） 必须使用类型 0，并且必须按照指定的格式，包括正确的页面长度。

-   供应商特定的标识符不是必需的 2/3 类型描述符的替代方案。 即使设备索赔符合以前版本的格式设置规则规定在 SPC 3 或更高版本，必须符合所有的设备标识符。

-   设备必须符合 SPC 3 节 7.6.3 设备标识 VPD 页 83 h。

至少一个标识说明符必须将标识符类型字段设置为︰

-   下半年 （EUI-64-基于） 在 7.6.3.5 中定义

-   3 h （naa） 制定;或在 7.6.3.6 中定义

-   在中定义的 7.6.3.11 8 h （SCSI 名称字符串）

**SCSI 模式识别命令和页面**

模式感知 (6) 的实施模式有意义 (10) 的 RBC 设备以外的所有设备。 DBD 位必须得到支持。

-   模式页面 3Fh （返回所有页面模式页） 是必需的。

-   在本文档的特定于设备的部分列出的设备特定类型的页面。

-   所有设备的附加命令如下所示︰

-   所有设备都必须都支持单元检测就绪并请求检测命令。

**块存储 （磁盘和 RAID） 设备**

块存储 （磁盘和 RAID） 设备必须符合以下要求︰

-   SCSI 块命令 (SBC) 或更高版本 (RBC 1394)。 这些要求适用于任何设备报告为设备类型 0，包括公开的 RAID 控制器或子系统的逻辑单元。

-   块设备必须支持的 SCSI 启动停止单位命令来降低功耗。

-   读取容量 (10) 的命令。 如果一个设备具有多个 2 ^32 1 扇区，必须为返回逻辑块地址字段返回值为 0xFFFFFFFF 的和必须支持读取容量 (16) 命令 （见下文）。

-   对产能的任何更改必须设置数据已更改容量单位注意的条件为具有访问权限的所有启动器为逻辑单元。

-   READ(10)。

-   WRITE(10)。 支持强制单元访问 (FUA) 是必填字段为单独的物理磁盘驱动器或 RAID 控制器，它包含不稳定 （非电池供电） 高速缓存并且必须使用此命令在命令完成之前要提交到物理介质导致发送的数据。

-   重新分配块 （仅适用于硬盘）。 处理坏块替换 RAID 控制器应成功执行此命令。

-   验证 (10)。

-   单元开始停止。 此命令必须执行任何其他操作，例如路径故障切换。

-   （使用任何可选字段） 同步缓存 (10)。 物理磁盘驱动器，此命令会在写缓存中，如果启用了写缓存，则提交到物理介质引起所有数据。 未能遵守这可能会导致数据损坏。

模式的页面︰

-   用下面的位模式页 08 h （缓存模式页） 必须包含有效信息︰ WCE （写入缓存启用）、 缓存段大小和数量的缓存段 （可选）。 RBC 的设备都支持页 6，而不是 8 页 （WCD、 WRITED、 FORMATD 和 LOCKD 位）。

    -   如果设备支持禁用写入缓存通过使用 WCE 位，这位还必须为可更改报告和支持的模式选择的操作，这可以修改它。 写缓存状态通过阅读模式下，第 8 页上必须是可见的。 供应商可以实现有限 SBC 在内外部缓存策略和禁用写缓存不需要为通过此模式页面。

-   模式页面 0Ah （控件模式页） 是必需的。

-   模式页面 1Ah （电源条件模式页） 是必需的

支持大于 2 TB 的逻辑单元 （包括 1394年磁盘） 的磁盘设备。 设备必须符合 SPC 3 和必须实现所有 SCSI 块命令-2 (SBC 2) 规范依照下列情况︰

-   读取容量 (16)

-   读 (16)

-   (16) 写 FUA （设备上存在易失性缓存时，必须支持位）

-   验证 (16)

-   重新分配块。 必须支持 LONGLBA 字段。

**可擦写的 SCSI 磁盘设备**

可擦写的 SCSI 磁盘设备还必须支持下面的命令或功能︰

-   擦除︰ 全端和选定块擦除。

-   使用格式命令报告格式要求。

-   模式感知 (6) 总备用块可用，写保护状态。

-   阻止允许移出介质选项并开始停止单位。

-   重新分配的块和读取缺陷数据 (10)。

    对于擦写前擦除，而只光盘。

<a name="device.storage.hd.smr"></a>
## <a name="devicestoragehdsmr"></a>Device.Storage.Hd.SMR

*定义的行业和 Microsoft 驱动器 SMR 作为自我识别，同时注意主机或主机托管 （也称为受限） 应满足的标准。驱动器管理 SMR （也称为 Autonomous） 没有其他 Microsoft 要求。*

### <a name="devicestoragehdsmrbasicfunction"></a>Device.Storage.Hd.SMR.BasicFunction

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>
 
**说明**

*SMR 主机的注意/主机管理设备基本功能，适用于 ZAC (ATA) 和 ZBC (SCSI/SA) 设备。*

**SMR 设备基本功能**

-   写指针区域应的长度为 256 MB。

-   传统的区域都是建议 （但不是要求） 的长度为 256 MB。

-   从开始 LBA 0 （第一个可寻址逻辑扇区），应有连续到驱动器的可寻址 LBA 空间至少 0.1%的总的常规区域。 *（例如，10 TB 设备应提供至少 10GB 的传统空间，建议将向上舍入到下一多为 256 MB）*

-   SMR 设备可能允许通过驱动器的 LBA 空间，包括最后一次区域的其他常规区域。

-   SMR 知道主机设备应至少为 128 的打开顺序写入首选区域提供支持。

-   SMR 主机托管设备应至少为 128 所需的打开顺序写入的区域提供支持。

### <a name="devicestoragehdsmrata"></a>Device.Storage.Hd.SMR.ATA

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>
 

**说明**

**SMR 主机的注意/主机管理设备应支持以下行业标准︰**

-   T13 分区设备 ATA 命令设置 (ZAC)，修订版本 04i 或更高版本

-   T13 ATA 命令集 – 4 (ACS-4) 修订版本 10 或更高版本 （适用于该分区的设备的部分）

-   设备应支持所有 ACS 4 功能定义为必需在 ZAC r04i SMR 设备类型，并不应都支持 ACS 4 功能定义为禁止 SMR 设备类型的 ZAC r04i 中。

-   设备应支持 NCQ 功能集，ACS 4 r10 中定义。

-   SMR 知道主机设备应报告的最佳首选的打开顺序写入区域数 ZAC r04i 中定义 6.2.2 分区设备信息页面。

-   SMR 主机托管设备应报告的最大数量的打开顺序写入首选区域 ZAC r04i 中定义 6.2.2 分区设备信息页面。 

 

### <a name="devicestoragehdsmrscsi"></a>Device.Storage.Hd.SMR.SCSI

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>
 

**说明**

**SMR 主机的注意/主机管理设备应特别支持行业标准︰**

-   T10 分区块的命令 (ZBC)，版本 4 或更高版本

-   （对于该分区的设备的某些部分） 的 T10 SCSI 块命令-4 (SBC-4) 修订版本 9 或更高版本

-   设备应支持所有 SBC 4 功能定义为必需在 ZBC r4 SMR 设备类型，并且应都支持 SBC 4 功能定义为在 ZBC r4 SMR 设备类型的禁止。

-   SMR 知道主机设备应报告最佳的打开顺序写入首选区域数在 ZBC r4 6.4.2 分区块设备特征 VPD 页。

-   SMR 主机托管设备应报告的最大数量的打开顺序写入首选区域，在 ZBC r4 6.4.2 分区块设备特征 VPD 页。

<a name="device.storage.hd.thinprovisioning"></a>
## <a name="devicestoragehdthinprovisioning"></a>Device.Storage.Hd.ThinProvisioning

### <a name="devicestoragehdthinprovisioningbasicfunction"></a>Device.Storage.Hd.ThinProvisioning.BasicFunction

*精简资源调配*

<table>
<tr>
<th>适用于</th>
<td>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

**行业标准规格要求︰**

-   支持精简资源调配功能必须实现以下 T10 SPC4 和 SBC3 规范的目标︰

-   支持的 VPD 页 VPD （页代码则为 00h）

-   阻止限制 VPD 页 (页面代码 B0h)

-   资源调配 VPD 页面 (页面代码 B2h) 的逻辑块

-   设置日志页面 (页面代码 0Ch) 的逻辑块

**Windows 设计规范要求︰**
 

-   精简资源调配功能与目标设备必须满足以下要求。

    <!-- -->

    -   必须为支持 VPD VPD 页与 B0h 和 B2h 返回查询命令。

    -   必须返回 LBPU 位集到一个和资源调配类型字段 = 3 (\r 010b) 的逻辑块资源调配 VPD 页面 (页面代码 B2)。 

    -   必须实现块限制 VPD 页 (页面代码 B0h) 并支持以下参数。

        <!-- -->

        -   最大值取消映射 LBA 计数
        -   最大值取消映射描述符块计数
        -   最佳粒度取消映射
        -   取消映射粒度对齐方式
        -   UGAVALID 位

        <!-- -->

    -   必须实现逻辑块资源调配 VPD 页 (页面代码 B2h) 并支持以下参数。

        <!-- -->

        -   阈值指数
        -   LBPU 位
        -   LBPRZ 位
        -   供应类型字段

        <!-- -->

    -   精简资源调配目标设备应支持日志检测命令来检索逻辑块设置日志页 (页面代码 0Ch)-添加阈值通知系统事件日志中的以下信息。

        <!-- -->

        -   使用精简资源调配的 LUN 的 LBA 映射资源。
        -   精简资源调配的 LUN 为可用的 LBA 映射资源。

        <!-- -->

    -   存储阵列必须支持 UNMAP (10) 命令、 LBP VPD 页中位 LBPU 应设置为 1。

    -   必须支持获取 LBA 状态 (16) 命令按照 T10 SBC3 规范。

    <!-- -->

-   如果返回 ReadCapacity(16) 中的 LBPME 位设置为 1 或 B2h 报告支持 VPD VPD 页中，存储阵列必须支持逻辑块资源调配 VPD 页面 (页面代码 B2h)。

-   如果返回 ReadCapacity(16) 中的 LBPRZ 位设成 1，则存储阵列必须设置为一个 LBPRZ 位逻辑块资源调配 VPD 页。

-   阈值通知 (TN)、 临时资源枯竭 (TRE) 和永久资源枯竭 (PRE) 通过以下意义上项、 附加探测代码和附加探测代码限定符返回为 SPC4 和 SBC3 规范，必须支持的存储阵列。

    <!-- -->

    -   TN 感应键/ASC/ASCQ (38/06/07)
    -   TRE 感应键/ASC/ASCQ (04/02/14)
    -   预检测键/ASC/ASCQ (07/27/07)

**用户体验需求︰**

-   必须能够设置阈值，通过供应商的存储管理实用程序和精简资源调配的软阈值达到监视系统事件日志中。

-   必须支持日志检测命令以检索报告可用 LBA 映射资源和用 LBA 将资源信息映射到精简资源调配的 LUN，如果实现了日志页面 (页面代码 OCh) LBP 日志页。

<a name="device.storage.hd.trim"></a>
## <a name="devicestoragehdtrim"></a>Device.Storage.Hd.Trim

### <a name="devicestoragehdtrimbasicfunction"></a>Device.Storage.Hd.Trim.BasicFunction

*ATA 修剪和 SCSI 取消映射功能*

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

如果该设备实现了 ATA 非-NCQ 修剪或 SCSI 取消映射的支持︰

-   修剪的实现会遵守 ATA ACS2 节 7.10 （数据集管理命令）。

-   取消映射的 SCSI 命令实现会遵守 T10 SBC3 节 5.28 （UNMAP 命令）。

-   如果该设备报告，指示旋转介质对查找产生负面影响︰

    -   所有 IO 和修剪/Unmap 命令应在少于 1000 毫秒内完成。

    -   98.5%的 IO 命令应在少于 200 毫秒内完成。

-   否则为 (SSD):

    -   所有 IO 和修剪/Unmap 命令应在少于 500 毫秒内完成。

    -   应以不超过 100 毫秒为单位完成的 IO 命令的 98.5%。

如果 SATA 设备上设置了 RZAT 位或在 SCSI 设备上设置了 LBPRZ 位，设备应读命令之前重新编写正确修剪的已返回所有 ' 0 的。

<a name="device.storage.hd.uas"></a>
## <a name="devicestoragehduas"></a>Device.Storage.Hd.Uas

### <a name="devicestoragehduascompliance"></a>Device.Storage.Hd.Uas.Compliance

*UAS USB 存储设备*

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

此外必须符合 USB UASP 1.0 版和 SPC4，SBC3 UASP USB 存储设备。
UASP USB 存储设备必须支持︰

-   模式的页面代码︰ 0x08 模式子页代码︰ 00

-   阻止限制页-0xB0 SPC3 6.5.3

-   支持至少 16 个数据流

-   支持任务管理命令

**           Note:**有关模式页面的详细信息，请参阅 SPC4: D.6 模式页面代码。

-   支持 SPC，SBC 版本描述符

-   支持/报表 R02。 R04 版本描述符

-   设备必须报告固定，如果它不是真正的可移动介质 (RMB = 0)

**注意︰**有关模式页面的详细信息，请参阅 SPC4: D.6 模式页面代码。
数据设备必须执行所述︰

-   最小的顺序写入速度︰ 100 MB/s

-   最小值顺序读取速度︰ 110 MB/s

其他要求︰ 如果设备支持 XHCI 上的 UASP，它必须支持 UASP 在 EHCI 上。

<a name="device.storage.hd.uasonehci"></a>
## <a name="devicestoragehduasonehci"></a>Device.Storage.Hd.UasOnEHCI

### <a name="devicestoragehduasonehcibasicfunction"></a>Device.Storage.Hd.UasOnEHCI.BasicFunction

*UAS USB 存储设备*

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

如果设备支持 UASP 在 XHCI 上，它必须在 EHCI 上支持 UASP。

<a name="device.storage.hd.usb"></a>
## <a name="devicestoragehdusb"></a>Device.Storage.Hd.Usb

### <a name="devicestoragehdusbcompatibility"></a>Device.Storage.Hd.Usb.Compatibility

*USB 兼容性*

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

USB 兼容性
 

-   所有 USB 存储设备必须都满足的要求的通用串行总线大容量存储类指标概述，V1.2 修订。 这包括所有 USB 大容量存储类文档，包括只批量、 控制/批量/中断、 Bootability，和 UFI 命令的规范。

-   BOT1.0，SPC 2、 SBC 2

-   USB 3.0 设备必须保留虽然以较低的速度，使用 USB 2.0 Pc 允许 Superspeed 设备使用，并允许其现有的缆线连接到 USB 3.0 Superspeed Type-A 连接器具有高速设备类型 A 接头向后兼容性。

-   USB 存储设备必须符合 USB 3.0-节 11 互操作性和功率传输规格。 下表列出了 USB 3.0 和 USB 2.0 兼容性矩阵。 识别主机端口支持 USB 3.0 硬件和软件支持 USB 3.0 的含意是到位;否则，端口只应视为一个 USB 2.0 端口。

<html>
    <table>
        <thead>
            <tr class="header">
                <th>USB 主机端口</th>
                <th>USB 设备的功能</th>
                <th>连接的模式</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <th rowspan="2">USB 2.0</th>
                <td>USB 2.0</td>
                <td>
USB 2.0 高速、 全速，或<br />
低速度                </td>
            </tr>
            <tr class="even">
                <td>USB 3.0</td>
                <td>
高速 USB 2.0<br />
                </td>
            </tr>
            <tr class="odd">
                <th rowspan="2">USB 3.0</th>
                <td>USB 2.0</td>
                <td>
USB 2.0 高速、 全速，或<br />
低速度                </td>
            </tr>
            <tr class="even">
                <td>USB 3.0</td>
                <td>
USB 3.0 SuperSpeed<br />
                </td>
            </tr>
        </tbody>
    </table>
</html>

-   USB 存储设备必须符合资质要求的 USB 设备，USB 存储设备

注意︰  
请参阅 USB3.0 规范部分 3.1.4 USB 3.0 体系结构摘要

-   USB3.0 超级速度-5 Gb/s
-   USB2.0 高速-480 Mb/s
-   全速-12 Mb/s
-   低速-1.5 Mb/s

<a name="device.storage.hd.usb3"></a>
## <a name="devicestoragehdusb3"></a>Device.Storage.Hd.Usb3

### <a name="devicestoragehdusb3compliance"></a>Device.Storage.Hd.Usb3.Compliance

*USB 3.0 存储设备*

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

USB 3.0 存储设备必须支持行业规范，如下所示︰
 

-   所有 USB 3.0 存储设备都必须符合 USB 3.0 版本 1.0 规范

-   提供每个存储终结点 （BOT，UASP） 通过独特的产品标识

    <!-- -->

    -   USB VID/PID

数据设备必须执行所述︰

-   最小的顺序写入速度︰ 60 MB/s

-   最小值顺序读取速度︰ 90 MB/s

<a name="device.storage.hd.windowstogocapableusbdrive"></a>
## <a name="devicestoragehdwindowstogocapableusbdrive"></a>Device.Storage.Hd.WindowsToGoCapableUSBDrive

*Windows 转支持 USB 驱动器功能*

### <a name="devicestoragehdwindowstogocapableusbdrivewindowstogocapableusbdrive"></a>Device.Storage.Hd.WindowsToGoCapableUSBDrive.WindowsToGoCapableUSBDrive

*Windows 转功能的 USB 驱动器*

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

引导的 USB 设备必须是 USB 3.0，并且符合下列工业技术指标︰

-   USB 3.0 版本 1.0 规范
-   USB BOT 规范
-   SCSI 块命令 3 (SBC-3) 规范


必须引导的 USB 设备︰

-   启动窗口

    -   SuperSpeed 连接到 USB 3.0 端口时的工作

    -   成功地输入，并继续从 (S3) 睡眠和休眠 (S4)

-   在 MS OS 描述符中包含扩展属性的值"WindowsBootCapable"DWORD 值 1

-   至少 32 gb 大小 (20 GB 可用容量)

-   提供唯一的、 统一的产品标识

    -   USB VID/PID
    -   查询序列号
    -   查询模型编号

-   报告固定 (RMB = 0)

-   实现块特征 VPD 设备页面

-   **未**实现 IEEE 1667

-   在启动过程中**不**公开多个 LUN

-   **不**支持 USB 连接 SCSI (UAS) 协议

-   如果 WTG 驱动器公开到操作系统的多个函数︰

    -   该设备必须设计成复合 USB 设备

    -   复合设备必须将 DeviceClass、 子类和协议设置为 0 的复合节点的设备描述符

    -   必须实现 WTG 存储和智能卡以外的其它任何函数

    -   存储函数必须是公开的第一个函数

-   支持以下模式页

    -   模式的页面代码︰ 0x08 模式子页代码︰ 00

-   满足以下性能︰

    -   随机写入 4 KB 的 IOPs &gt;= 200 （旋转驱动器免除）

    -   随机的 4 KB 读 IOPs &gt;= 2000 （旋转驱动器免除）

    -   读/写性能应成线性比例在混合工作负载的随机访问读/写

    -   顺序写入速度&gt;= 80 MB/s

    -   读取速度的连续&gt;= 80 MB/s

    -   最大 I/O 延迟&lt;500 毫秒

    -   最多 16 秒-总和的用户代表工作负荷，用户感觉 I/O 位置定义为至少 100 毫秒的延迟的任何 1 小时的时段内的用户感觉 I/O 等待时间

<a name="device.storage.optical"></a>
## <a name="devicestorageoptical"></a>Device.Storage.Optical

### <a name="devicestorageopticalcdrawrecording"></a>Device.Storage.Optical.CdRawRecording

*光盘驱动器必须支持原始 CD 录制。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

光盘驱动器必须支持 CD 原始模式录制的 CD-R 和 CD-RW 配置文件。

### <a name="devicestorageopticalcommandperformance"></a>Device.Storage.Optical.CommandPerformance

*光盘驱动器必须在允许的时间框架内完成性能命令。*

</table>
<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

 
光盘驱动器必须完成的最大允许时间按下表中的所有命令。

| 命令                                                                              | 基本认证要求 （毫秒） | 异常 (异常条件 / 毫秒)                                    |
|--------------------------------------------------------------------------------------|----------------------------------------|-------------------------------------------------------------------------|
| 获取配置                                                                    | 20                                     | &nbsp; |
| 获取事件状态通知                                                        | 20                                     | &nbsp; |
| 获得的性能                                                                      | 20                                     | &nbsp; |
| 查询                                                                              | 20                                     | &nbsp; |
| 机制的状态                                                                     | 20                                     | &nbsp; |
| 模式选择                                                                          | 20                                     | &nbsp; |
| 状态检测                                                                           | 20                                     | &nbsp; |
| 阻止允许移出介质                                                         | 20                                     | &nbsp; |
| 读取目录 PMA ATIP                                                                    | 20                                     | &nbsp; |
| 读取的缓冲区容量                                                                 | 20                                     | &nbsp; |
| 读取容量                                                                        | 20                                     | &nbsp; |
| 读取 CD<sup>1,2,4</sup>                                                              | 500                                    | &nbsp; |
| 读取的磁盘信息                                                                | 50                                     | &nbsp; |
| 读的格式容量                                                               | 20                                     | &nbsp; |
| 读取的跟踪信息                                                               | 20                                     | &nbsp; |
| 请求检测 （当没有按照命令失败，出现错误状态）                | 20                                     | &nbsp; |
| OPC 信息发送                                                                 | 60000                                  | 对于双面媒体，即 DVD + R DL、 DVD-R DL、 BD-RE DL / 70000        |
| 提前设置只读                                                                       | 20                                     | &nbsp; |
| 设置流                                                                        | 20                                     | &nbsp; |
| 单元开始停止 (Immed = 1b)                                                           | 20                                     | &nbsp; |
| 单元开始停止 (弹出，Immed = 0b)                                                    | 7000                                   | &nbsp; |
| 开始停止单位 (插入、 Immed = 0b，直到媒体已准备就绪)                             | 25000                                  | DVD-RAM / 40000<br/>对于双面媒体，即 DVD + R DL、 DVD-R DL、 BD-RE DL / 30000 |
| 同步缓存 (Immed = 1b)                                                         | 20                                     | &nbsp; |
| 同步缓存 (Immed = 0b)                                                         | 15000                                  | &nbsp; |
| 准备好测试单元                                                                      | 20                                     | &nbsp; |
| 空白 (Immed = 1b)                                                                     | 20                                     | &nbsp; |
| 空白 (Immed = 0b)                                                                     | N/A                                    | &nbsp; |
| 密切跟踪会话 (Immed = 1b)                                                       | 20                                     | &nbsp; |
| 关闭跟踪会话 (Immed = 0b 关闭逻辑磁道或会话、 不完成光盘刻录) | 65000                                  | DVD + R DL、 DVD-R DL / 300000<br/>定版 DVD-R SL、 DVD-RW / 180000 |
| 密切跟踪会话 (Immed = 0b，完成光盘刻录)                                        | 65000                                  | DVD + R DL 300000<br/>定版 DVD-R SL、 DVD-R DL DVD-RW / 900000 |
| 格式单元 （立即）                                                              | 20                                     | &nbsp; |
| 加载/卸载媒体                                                                   | N/A                                    | &nbsp; |
| READ10<sup>1,2,4</sup>                                                               | 500                                    | DVD-RAM / 800                                                           |
| READ12 （不流）<sup>1,2,4</sup>                                               | 500                                    | DVD-RAM / 800                                                           |
| READ12 （流）<sup>1,2,4</sup>                                                   | 100                                    | 1 X 在 CD / 500;            2 x 处的 CD / 350;             4 x 处的 CD / 200 |
| 只读的光盘结构<sup>6</sup>                                                      | 20                                     | &nbsp; |
| 读取媒体序列号<sup>2</sup>                                                 | 500                                    | &nbsp; |
| 报告参数                                                                           | 20                                     | &nbsp; |
| 保留曲目                                                                        | N/A                                    | &nbsp; |
| 发送提示工作表                                                                       | N/A                                    | &nbsp; |
| 发送光盘结构                                                                  | N/A                                    | &nbsp; |
| 发送键                                                                             | 20                                     | &nbsp; |
| 设置 CD 的速度                                                                         | 20                                     | &nbsp; |
| 写 10 (FUA = 0) <sup>1，3</sup>                                                      | 50                                     | &nbsp; |
| 写 12 (FUA = 0) <sup>1，3</sup>                                                      | 50                                     | &nbsp; |
| 写入缓冲区                                                                         | N/A                                    | &nbsp; |
| 擦除                                                                                | N/A                                    | &nbsp; |
| 读取缓冲区                                                                          | N/A                                    | &nbsp; |
| 只读的光盘 MSF<sup>1,2,4</sup>                                                          | 500                                    | &nbsp; |
| 修复的轨道                                                                         | N/A                                    | &nbsp; |
| SEEK10                                                                               | N/A                                    | &nbsp; |
| 验证 10                                                                            | N/A                                    | &nbsp; |
| 编写和验证 10                                                                  | N/A                                    | &nbsp; |

 
**"命令完成时间"指离开 Microsoft 端口的命令之间的时间 / 微型端口驱动程序和完成命令所返回到 Microsoft 端口 / 微型端口驱动程序。如果该命令失败，错误状态，这一次还包括使 Microsoft 端口随后要求 Sense 指令 / 微型端口驱动程序和请求检测命令完成后返回到 Microsoft 端口 / 微型端口驱动程序。**

所有命令执行时间性能测量都应符合相关委员会-即 DVD 论坛，BDA，DVD + RW 联盟从介质物理层标准规范的媒体上。 此外，它们应执行正常的温度和湿度运营条件下设备规范中声明。

**注意︰**只读的驱动器将从 Windows 认证计划在 2010 年 6 月 1 日终止。 因此，认证要求和测试将停止存在只读驱动器上 2010 年 6 月 1 日。 希望接收有只读驱动器的系统上的 Windows 认证的合作伙伴仍将可以到。 但是，在"未分类"类别的设备下属于只读驱动器。
 
<sup>1</sup>︰ 传输长度为读取和写入性能测试是向一个 ECC 块 （32 KB 或 64 KB 具体取决于当前的媒体类型，例如，CD 和 BD，dvd 32 KB 的 64 KB） 相等或更小。

<sup>2</sup>︰ 性能测试可以实施报告为支持的设备，包括 1 个媒体速度，如果因此报告为支持任何速度。

<sup>3</sup>︰ 驱动器***必须***使用写入缓冲区和通过任何形式的媒体访问中***不得***延迟命令完成。 如果写入缓冲区已满时，驱动器***必须***失败进行有意义的信息 (02h/04h/08h) 在长时间的写入具有写命令。
 
<sup>4</sup>︰ 第一个十万媒体到达后读取 I/O 命令或从待机电源状态或设置 Cd 速度恢复或设置流允许累计达 60 000 延迟毫秒才能完成允许额外的启动时间。 这些命令可能分别需要任意时间最多 7 000 毫秒，但累积时间完成所有 hundred 命令都不应该超过 60 000 个毫秒。 之间的时间的连续的读取命令两个的时间并不表示 （即，主机不测量的延迟） 时读取的命令发送到设备，并完成该读取的命令将考虑到设备。

<sup>6</sup>︰ 光盘结构代码的列表仅限于;物理格式信息 (格式 = 0x00，地址 = 0) 的 DVD-RAM 介质状态 (格式 = 0x09，地址 = 0)，DVD + RW 编写抑制 DCB (格式 = 0x30 地址 = 0x57444300)，写保护状态 (格式 = 0xC0 地址 = 0)<sup>7</sup>︰ 蓝光驱动器及 9.5 毫米高度以及 DVD 驱动器 7 毫米高度较小和较小的双层写入配置文件*将被要求在 2010 年 6 月 1* 。 这将结束这些外形为前一个异常。

### <a name="devicestorageopticaldrivedefinition"></a>Device.Storage.Optical.DriveDefinition

*如何为证书定义的光盘驱动器。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

将光盘驱动器，必须将设备定义为 CD （光盘） 设备、 DVD （数字多功能光盘或数字视频盘） 设备、 BD （蓝光光盘） 设备或外围设备类型 5 每个 INCITS 的 T10 命令设置 SCSI 主的命令，将自己标识任何设备 SPC （任何版本）。

### <a name="devicestorageopticalfeatures"></a>Device.Storage.Optical.Features

*所需的光驱功能*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

光盘驱动器必须支持以下列出的所需的功能︰

-   核心功能
-   配置文件列表功能
-   每个配置文件必需的功能
-   从保持联系的可移动媒体功能 富士 7
-   报告正确的送纸器的状态
-   电源管理功能
-   变形特征
-   驱动器序列号功能
-   DVD CSS 功能 (0106 h)

### <a name="devicestorageopticalmmcversion"></a>Device.Storage.Optical.MmcVersion

*光盘驱动器必须遵守 MMC。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

INCITS 的 T10 命令集和多媒体命令设置-6 (MMC-6) 发布时必须符合的光盘驱动器。 MMC-6 的发布被推迟，因为光盘驱动器必须在中期符合 INCITS 的 T10 命令集的组合多媒体命令设置-5 (MMC-5)，SFF 的保持联系 多媒体设备版本 7 (INF 8090i v7) 之前发布的 MMC-6 的富士命令。 如果 MMC-5 和 INF 8090i v7 彼此，和下列要求未显式指定所需的行为，法规遵从性到 MMC 5 所 （除了新 INF 8090i v7 中定义的功能）。

### <a name="devicestorageopticalprofiles"></a>Device.Storage.Optical.Profiles

*所需的光盘驱动器配置文件*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

光盘驱动器必须支持所需的模板，如下所示︰

-   光盘
-   DVD-ROM
-   可移动磁盘
-   CD-R
-   CD-RW
-   定版 DVD-R 连续录制
-   受限制的 DVD-RW 覆盖
-   定版 DVD-R 双面连续录制
-   DVD + RW
-   DVD + R
-   DVD + R DL

### <a name="devicestorageopticalrealtimestreaming"></a>Device.Storage.Optical.RealTimeStreaming

*光盘驱动器必须支持实时流。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

光盘驱动器必须支持实时流，根据需要按照配置文件要求。 对于所有可录制和重写配置文件，以下字段应相应地设置︰ 流写入 (SW) = 1b 和写入速度性能描述符 (WSPD) = 1b。

<a name="device.storage.optical.blurayreader"></a>
## <a name="devicestorageopticalblurayreader"></a>Device.Storage.Optical.BluRayReader

### <a name="devicestorageopticalblurayreaderprofiles"></a>Device.Storage.Optical.BluRayReader.Profiles

*蓝光读者所需的配置文件*

</table>
<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

蓝光读卡器的驱动器必须支持 BD ROM 的配置文件。

<a name="device.storage.optical.bluraywriter"></a>
## <a name="devicestorageopticalbluraywriter"></a>Device.Storage.Optical.BluRayWriter

### <a name="devicestorageopticalbluraywriterprofiles"></a>Device.Storage.Optical.BluRayWriter.Profiles

*蓝光编写器所需的配置文件*

</table>
<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

蓝光驱动器，可以写必须支持 BD ROM、 BD-R 连续录制和 BD-RE 配置文件。

<a name="device.storage.optical.sata"></a>
## <a name="devicestorageopticalsata"></a>Device.Storage.Optical.Sata

### <a name="devicestorageopticalsataasynchronousnotification"></a>Device.Storage.Optical.Sata.AsynchronousNotification

*异步通知是必需的所有连接的 SATA 驱动器。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

通过 SATA 总线连接的光盘驱动器必须支持异步通知。

