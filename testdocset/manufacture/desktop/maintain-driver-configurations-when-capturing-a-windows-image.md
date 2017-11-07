---
author: Justinha
Description: "在捕获 Windows 映像时维护驱动程序配置"
ms.assetid: 4712b33a-c6ab-4715-ba55-041c0c6fa2b1
MSHAttr: PreferredLib:/library/windows/hardware
title: "在捕获 Windows 映像时维护驱动程序配置"
ms.openlocfilehash: 10c8b4058cb7056104944ec4d68fd679bf865533
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="maintain-driver-configurations-when-capturing-a-windows-image"></a>在捕获 Windows 映像时维护驱动程序配置


常见部署方案是捕获一个从参考计算机 Windows 映像，然后将映像应用到一组具有相同硬件配置的目标计算机。

若要保存在安装过程并提高最终用户的全新体验 (OOBE) 的速度，您可以指示 Windows 安装程序维护从参考计算机的驱动程序配置为 Windows 映像的一部分。 仅在参考计算机上的硬件和目标计算机上的硬件完全相同时，才应执行此操作。 执行此操作时，Windows 安装程序在图像捕获和部署维护驱动程序配置。

本主题︰

-   [指示 Windows 安装程序维护驱动程序配置](#bkmk-1)
-   [概述](#bkmk-2)
-   [驱动程序版本和驱动程序分级的最佳做法](#bkmk-3)
-   [故障诊断硬件配置差异](#bkmk-4)
-   [解决驱动程序冲突](#bkmk-5)

## <a name="span-idbkmk1spanspan-idbkmk1spaninstructing-windows-setup-to-maintain-driver-configurations"></a><span id="bkmk_1"></span><span id="BKMK_1"></span>指示 Windows 安装程序维护驱动程序配置


捕获映像之前，通用化计算机通过使用应答文件指示 Windows 安装程序维护驱动程序配置。

**若要通过使用应答文件维护驱动程序配置**

1.  技术人员计算机上打开 Windows 系统映像管理器 （Windows sim 卡）。 单击**开始**，键入**Windows 系统映像管理器**，然后选择**Windows 系统映像管理器**。
2.  创建新的应答文件，或更新现有的应答文件。 有关详细信息，请参阅[创建或打开答案文件](https://msdn.microsoft.com/library/windows/hardware/dn915085)和[创作答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)。
3.  添加 Microsoft Windows PnpSysprep /**PersistAllDeviceInstalls**设置。 有关详细信息，请参阅本主题中的[概述](#bkmk-2)部分。
4.  如果计算机无法检测的硬件，包括 Microsoft Windows PnpSysprep /**DoNotCleanUpNonPresentDevices**设置。 有关详细信息，请参阅本主题[无法检测的硬件](#undetectablehardware)部分。
5.  对计算机进行一般化使用答案文件。 例如︰

    ``` syntax
    Sysprep /generalize /unattend:C:\unattend.xml
    ```

## <a name="span-idbkmk2spanspan-idbkmk2spanoverview"></a><span id="bkmk_2"></span><span id="BKMK_2"></span>概述


Windows 中内置驱动程序程序包包括支持各种流行的硬件的设备驱动程序。 如果您的特定硬件需要附加的设备驱动程序来启动，可以预附加的设备驱动程序安装在 Windows 映像上。 通常，独立硬件供应商 (Ihv) 提供其设备硬件以及这些附加的设备驱动程序。 有关如何添加设备驱动程序的详细信息，请参阅[添加驱动程序在线在审核模式下](add-a-driver-online-in-audit-mode.md)。

准备 Windows 映像部署到多台计算机，您必须使用系统准备 (Sysprep) 工具一般化 Windows 映像。 泛化 Windows 映像中删除特定于计算机的信息，并准备为第一个引导设备驱动程序。 这些准备工作包括下列步骤︰

-   删除硬件设备的状态。

-   引导关键驱动程序设置重置为其默认值。

-   设备日志文件被删除。

当您对计算机进行一般化时，使用答案文件包含 Microsoft Windows PnpSysPrep\\**PersistAllDeviceInstalls**设置以节省时间。 此设置会阻止 Windows 安装程序从中移除并重新配置相同的硬件的设备状态。 首次启动，检测到的设备驱动程序都已预配置，可能会允许更快的第一次启动体验。

**重要**  
避免使用的**PersistAllDeviceInstalls**设置时的硬件和与参考计算机上的硬件配置不是与目标计算机的相同。 即使表面上硬件或硬件配置中的细微差别可能会导致严重或很容易被忽视的问题。 有关详细信息，请参阅本主题[解决硬件配置差异](#bkmk-4)部分。

 

它是一个好的习惯，不能使用**PersistAllDeviceInstalls**设置主要参考图像上。 相反，针对具有不同硬件配置的计算机的每个组，第一次加载到有计划的硬件配置的新引用计算机上您主要参考映像。 接下来，捕获此安装程序的新图像，并使用**PersistAllDeviceInstalls**设置。

有关如何进行一般化 Windows 映像的详细信息，请参阅[Sysprep （通用化） 的 Windows 安装](sysprep--generalize--a-windows-installation.md)。

## <a name="span-idbkmk3spanspan-idbkmk3spanbest-practices-for-driver-revisions-and-driver-ranking"></a><span id="bkmk_3"></span><span id="BKMK_3"></span>驱动程序版本和驱动程序分级的最佳做法


没有维护多个版本或修订版本中相同的图像相同的驱动程序包。 使用脱机或联机服务的工具来更新驱动程序。

通常情况下，Windows 安装程序可以启动一台计算机，该计算机上有多个版本的驱动程序包安装程序确定要使用驱动程序分级安装的驱动程序。 但正常的驱动程序分级流程时使用的**PersistAllDeviceInstalls**设置，不会发生。 因此，使用过期的驱动程序的设备可能会保留其安装。 关于排名的驱动程序的详细信息，请参阅 MSDN 上的[如何 Windows 通道驱动程序](http://go.microsoft.com/fwlink/?LinkId=91227)。

如果您必须使用的**PersistAllDeviceInstalls**设置的图像添加设备驱动程序，您可以使用下列方法之一更新您的设备驱动程序︰

-   使用脱机服务工具，如部署映像服务和管理 (DISM) 工具或无人参与的答案文件。 有关详细信息，请参阅[添加和删除脱机 Windows 映像的驱动程序](add-and-remove-drivers-to-an-offline-windows-image.md)。

-   使用在线服务方法或工具，如无人参与的答案文件。 有关详细信息，请参阅[添加驱动程序在线在审核模式下](add-a-driver-online-in-audit-mode.md)。

## <a name="span-idbkmk4spanspan-idbkmk4spantroubleshooting-hardware-configuration-differences"></a><span id="bkmk_4"></span><span id="BKMK_4"></span>故障诊断硬件配置差异


正常的**PersistAllDeviceInstalls**设置，必须完全相同，在参考计算机和目标计算机上的硬件配置。 硬件配置包括以下组件︰

-   **硬件制造商和型号。**

-   **固件。** 更新、 修订版本和配置差异可能导致报告不同标准对某些设备匹配的设备驱动程序，或使用不同的资源。 例如︰

    -   外围组件互连 PCI 基于设备中其报告硬件 Id 嵌入不同的子系统修订号。

    -   BIOS 版本可以更改的高级配置和电源接口 (ACPI) 命名空间。 这会导致 Windows 安装程序报告现有设备各不相同，或引入新设备与现有设备。

    -   BIOS 系统配置的差异可以导致系统设备，并声称不同内存、 I/O、 直接内存访问 (DMA) 或中断请求 (IRQ) 资源。

-   **物理位置。** 硬件配置必须使用同一插槽、 端口或插槽号来连接到外部设备。 例如︰

    -   在相同的插槽号，必须插入 PCI 扩展卡。

    -   USB 设备必须连接或连接到同一个 USB 主机控制器上相同的端口号和集成集线器。

    -   存储设备必须连接到同一个存储控制器和通道。

### <a name="span-idtypesofhardwarelikelytocauseproblemsspanspan-idtypesofhardwarelikelytocauseproblemsspanspan-idtypesofhardwarelikelytocauseproblemsspanlow-risk-medium-risk-and-high-risk-differences-in-hardware-configuration"></a><span id="TypesOfHardwareLikelyToCauseProblems"></span><span id="typesofhardwarelikelytocauseproblems"></span><span id="TYPESOFHARDWARELIKELYTOCAUSEPROBLEMS"></span>在硬件配置中的低风险、 中等风险和高风险差异

当您使用**PersistAllDeviceInstalls**设置时，任何硬件差别可能导致问题。 但是一些差异更有可能会造成比其他的问题。

### <a name="span-idlow-riskdifferencesspanspan-idlow-riskdifferencesspanspan-idlow-riskdifferencesspanlow-risk-differences"></a><span id="Low-risk_differences"></span><span id="low-risk_differences"></span><span id="LOW-RISK_DIFFERENCES"></span>低风险的差异

为下列类型的硬件差异，您可能能够解决潜在驱动程序冲突，而且仍使用**PersistAllDeviceInstalls**设置︰

-   CPU 时钟速度

-   内存量

-   硬盘容量

-   外部输入的设备，如键盘和鼠标设备

-   显示器

### <a name="span-idmedium-riskdifferencesspanspan-idmedium-riskdifferencesspanspan-idmedium-riskdifferencesspanmedium-risk-differences"></a><span id="Medium-risk_differences"></span><span id="medium-risk_differences"></span><span id="MEDIUM-RISK_DIFFERENCES"></span>中等风险差异

对于以下类型的硬件差异，建议您不要使用**PersistAllDeviceInstalls**设置︰

-   视频卡

-   存储驱动器和介质读者，如光盘驱动器和读卡器

-   内部或集成总线设备，例如 USB 或 1394年设备

当这些类型硬件差异的存在时，使用此设置可能不减少安装时间，即使解决潜在驱动程序冲突。

### <a name="span-idhigh-riskdifferencesspanspan-idhigh-riskdifferencesspanspan-idhigh-riskdifferencesspanhigh-risk-differences"></a><span id="High-risk_differences"></span><span id="high-risk_differences"></span><span id="HIGH-RISK_DIFFERENCES"></span>高风险的差异

为主要的硬件差异，不要使用**PersistAllDeviceInstalls**设置。 这些差异包括︰

-   主板芯片组或 CPU 的品牌

-   存储控制器

-   机身的差异，如更改从桌面到便携式计算机或便携式计算机桌面的

-   键盘布局的差异，像从标准的 101 键键盘更改为日语的 106 个键键盘

-   在枚举窗口的路径的任何其它设备启动卷

### <a name="span-idwhattypesofproblemscanoccurspanspan-idwhattypesofproblemscanoccurspanspan-idwhattypesofproblemscanoccurspantypes-of-problems-that-can-occur-with-a-hardware-configuration-change"></a><span id="WhatTypesOfProblemsCanOccur"></span><span id="whattypesofproblemscanoccur"></span><span id="WHATTYPESOFPROBLEMSCANOCCUR"></span>类型的硬件配置更改时可能出现的问题

即使表面上硬件或硬件配置中的细微差别可能会导致严重或很容易被忽视，类似这样的问题︰

-   系统不稳定

-   不能使用某些设备的基本或扩展功能

-   扩展的启动时间和扩展的安装时间

-   名不符实的设备在设备和打印机文件夹、 设备管理器和其他设备相关的用户界面

-   严重的系统问题，导致计算机处于非启动状态

### <a name="span-idbootcriticaldriverpackagesspanspan-idbootcriticaldriverpackagesspanspan-idbootcriticaldriverpackagesspanhardware-configuration-differences-that-can-cause-system-boot-failures"></a><span id="BootCriticalDriverPackages"></span><span id="bootcriticaldriverpackages"></span><span id="BOOTCRITICALDRIVERPACKAGES"></span>可能会导致系统启动故障的硬件配置差异

引导所必需的硬件不完全相同，在参考计算机和目标计算机上，使用**PersistAllDeviceInstalls**设置可能导致严重的系统问题，会使计算机处于非启动状态。

引导关键驱动程序软件包可以属于任何以下 Windows 设备安装程序类，ClassGUID 中的指令来标识*&lt;版本&gt;*部分中其驱动程序包的.inf 文件。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">系统提供的设备安装程序类</th>
<th align="left">ClassGUID</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>System</p></td>
<td align="left"><p>{4D36E97D-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>计算机</p></td>
<td align="left"><p>{4D36E966-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Processor</p></td>
<td align="left"><p>{50127DC3-0F36-415E-A6CC-4CB3BE910B65}</p></td>
</tr>
<tr class="even">
<td align="left"><p>PCMCIA</p></td>
<td align="left"><p>{4D36E977-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>HDC</p></td>
<td align="left"><p>{4D36E96A-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>SCSIAdapter</p></td>
<td align="left"><p>{4D36E97B-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>磁盘驱动器</p></td>
<td align="left"><p>{4D36E967-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>光驱</p></td>
<td align="left"><p>{4D36E965-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>FDC</p></td>
<td align="left"><p>{4D36E969-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>软盘上</p></td>
<td align="left"><p>{4D36E980-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>音量</p></td>
<td align="left"><p>{71A27CDD-812A-11D0-BEC7-08002BE2092F}</p></td>
</tr>
<tr class="even">
<td align="left"><p>USB</p></td>
<td align="left"><p>{36FC9E60-C465-11CF-8056-444553540000}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>SBP2</p></td>
<td align="left"><p>{D48179BE-EC20-11D1-B6B8-00C04FA372A7}</p></td>
</tr>
<tr class="even">
<td align="left"><p>1394</p></td>
<td align="left"><p>{6BDD1FC1-810F-11D0-BEC7-08002BE2092F}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Enum1394</p></td>
<td align="left"><p>{C459DF55-DB08-11D1-B009-00A0C9081FF6}</p></td>
</tr>
<tr class="even">
<td align="left"><p>Keyboard</p></td>
<td align="left"><p>{4D36E96B-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>鼠标</p></td>
<td align="left"><p>{4D36E96F-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
<tr class="even">
<td align="left"><p>HIDClass</p></td>
<td align="left"><p>{745A17A0-74D3-11D0-B6FE-00A0C90F57DA}</p></td>
</tr>
<tr class="odd">
<td align="left"><p>端口</p></td>
<td align="left"><p>{4D36E978-E325-11CE-BFC1-08002BE10318}</p></td>
</tr>
</tbody>
</table>

 

有关下列设备安装程序类的详细信息，请参阅 MSDN 上的[System-Supplied 设备安装程序类](http://go.microsoft.com/fwlink/?LinkId=237677)。

### <a name="span-idundetectablehardwarespanspan-idundetectablehardwarespanspan-idundetectablehardwarespanundetectable-hardware"></a><span id="UndetectableHardware"></span><span id="undetectablehardware"></span><span id="UNDETECTABLEHARDWARE"></span>无法检测硬件

向最终用户部署一台新计算机时，某些硬件，如可移动设备或开/关切换的设备可能不存在或检测到首次启动期间。 默认情况下，在第一次启动时，Windows 安装程序将删除未检测到硬件的预配置的设备状态。

部署可能不存在或在首次启动，检测到的硬件添加到参考映像的任何适用的设备驱动程序、 连接或开启相应的设备，以便 Windows 可以安装它们，并使用 Microsoft Windows PnpSysprep /**DoNotCleanUpNonPresentDevices**设置时您捕获图像。

**重要**  
使用**DoNotCleanUpNonPresentDevices**设置可以导致不必要的多余设备状态存储，并有利于较慢的启动时间。

 

## <a name="span-idbkmk5spanspan-idbkmk5spantroubleshooting-driver-conflicts"></a><span id="bkmk_5"></span><span id="BKMK_5"></span>解决驱动程序冲突


若要避免独立启动关键驱动程序软件包之间的驱动程序冲突，IHV 必须确保每个设备驱动程序使用不同的服务名称、 注册表键值和二进制文件的名称。

### <a name="span-idexampleofapotentialdriverconflictspanspan-idexampleofapotentialdriverconflictspanspan-idexampleofapotentialdriverconflictspanexample-of-a-potential-driver-conflict"></a><span id="Example_of_a_potential_driver_conflict"></span><span id="example_of_a_potential_driver_conflict"></span><span id="EXAMPLE_OF_A_POTENTIAL_DRIVER_CONFLICT"></span>潜在的驱动程序冲突的示例

在以下示例中，名为 Fabrikam 虚构 IHV 将产生两种类型的存储控制器︰ StandardController 和 ExtremeController。 Fabrikam 假定只有一种类型的存储控制器安装在特定计算机上的一次。

该驱动程序包定义要使用同一驱动程序服务名称，storctrl 的 StandardController 和 ExtremeController 配置。 Storctrl 驱动程序服务使用不同的服务更改的设置，具体取决于已安装的硬件 （StandardController 或 ExtremeController）。 StandardController 和 ExtremeController 使用相同的服务，因为他们不能共存。

此示例演示包文件 Storctrl.inf 的驱动程序中的内容︰

``` syntax
[Version]
Signature = "$WINDOWS NT$"
Class = SCSIAdapter
ClassGuid = {4D36E97B-E325-11CE-BFC1-08002BE10318}
...
[Manufacturer]
%Fabrikam% = Fabrikam,NTx86

[Fabrikam.NTx86]
%StandardController% = StandardController_DDInstall,PCI\VEN_ABCD&DEV_0001
%ExtremeController%  = ExtremeController_DDInstall, PCI\VEN_ABCD&DEV_0002

...

[StandardController_DDInstall.Services]
AddService = storctrl,0x00000002,StandardController_ServiceInstall

[StandardController_ServiceInstall]
ServiceType  = 1 ; SERVICE_KERNEL_DRIVER
StartType    = 0 ; SERVICE_BOOT_START
ErrorControl = 1 ; SERVICE_ERROR_NORMAL
ImagePath    = %12%\storctrl.sys
AddReg       = StandardController_ServiceSettings

[StandardController_ServiceSettings]
HKR,Settings,LowPowerMode,0x00010001,1
HKR,Settings,ErrorCorrection,0x00010001,1

...

[ExtremeController_DDInstall.Services]
AddService = storctrl,0x00000002,ExtremeController_ServiceInstall

[ExtremeController_ServiceInstall]
ServiceType  = 1 ; SERVICE_KERNEL_DRIVER
StartType    = 0 ; SERVICE_BOOT_START
ErrorControl = 1 ; SERVICE_ERROR_NORMAL
ImagePath    = %12%\storctrl.sys
AddReg       = ExtremeController_ServiceSettings

[ExtremeController_ServiceSettings]
HKR,Settings,LowPowerMode,0x00010001,0
HKR,Settings,ErrorCorrection,0x00010001,4
...
```

如果 StandardController 是在参考计算机上的设置都保存在映像捕获过程，是预先配置的 storctrl 驱动程序服务。 如果 ExtremeController 是在目标计算机上，Windows 可以使用的预配置的设置和文件的适用于 StandardController。 这可能导致意外的结果。

IHV 可以帮助您通过使用以下选项之一来解决冲突︰

-   创建具有每一种配置，单独的.inf 文件的单独的驱动程序包并在部署期间将只有必需的驱动程序程序包导入 Windows 映像。 例如，分成 Storctrl.inf 两个单独的.inf 文件，一个版本的 StandardController 和一个版本的 ExtremeController，并且将只有必需的驱动程序程序包导入到 Windows 映像。

<!-- -->

-   为每个配置驱动程序包中创建另一个服务。 为每个服务指定一个不同的名称 （例如，storctrl 和 storctrlx），并且指向不同的二进制图像文件 （例如，Storctrl.sys 和 Storctrlx.sys）。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)

 

 






