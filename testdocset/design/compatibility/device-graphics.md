---
title: Device.Graphics
Description: "要求所有的图形设备所需的基本功能集。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 9f31989982c9634669e612ba321fd453952615b7
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicegraphics"></a>Device.Graphics

 - [Device.Graphics.AdapterBase](#device.graphics.adapterbase)
 - [Device.Graphics.AdapterRender.D3D101Core](#device.graphics.adapterrender.d3d101core)
 - [Device.Graphics.AdapterRender.D3D101WDDM11](#device.graphics.adapterrender.d3d101wddm11)
 - [Device.Graphics.AdapterRender.D3D101WDDM12](#device.graphics.adapterrender.d3d101wddm12)
 - [Device.Graphics.AdapterRender.D3D10ComputeShader](#device.graphics.adapterrender.d3d10computeshader)
 - [Device.Graphics.AdapterRender.D3D10Core](#device.graphics.adapterrender.d3d10core)
 - [Device.Graphics.AdapterRender.D3D10D3D11LogicOps](#device.graphics.adapterrender.d3d10d3d11logicops)
 - [Device.Graphics.AdapterRender.D3D10Multisampling4X](#device.graphics.adapterrender.d3d10multisampling4x)
 - [Device.Graphics.AdapterRender.D3D10Multisampling8X](#device.graphics.adapterrender.d3d10multisampling8x)
 - [Device.Graphics.AdapterRender.D3D10WDDM11](#device.graphics.adapterrender.d3d10wddm11)
 - [Device.Graphics.AdapterRender.D3D10WDDM12](#device.graphics.adapterrender.d3d10wddm12)
 - [Device.Graphics.AdapterRender.D3D111Core](#device.graphics.adapterrender.d3d111core)
 - [Device.Graphics.AdapterRender.D3D11ASTC](#device.graphics.adapterrender.d3d11astc)
 - [Device.Graphics.AdapterRender.D3D11ConservativeRasterization](#device.graphics.adapterrender.d3d11conservativerasterization)
 - [Device.Graphics.AdapterRender.D3D11Core](#device.graphics.adapterrender.d3d11core)
 - [Device.Graphics.AdapterRender.D3D11DoublePrecisionShader](#device.graphics.adapterrender.d3d11doubleprecisionshader)
 - [Device.Graphics.AdapterRender.D3D11DriverCommandLists](#device.graphics.adapterrender.d3d11drivercommandlists)
 - [Device.Graphics.AdapterRender.D3D11DriverConcurrentObjectCreation](#device.graphics.adapterrender.d3d11driverconcurrentobjectcreation)
 - [Device.Graphics.AdapterRender.D3D11Level9WDDM12](#device.graphics.adapterrender.d3d11level9wddm12)
 - [Device.Graphics.AdapterRender.D3D11Level9WDDM13](#device.graphics.adapterrender.d3d11level9wddm13)
 - [Device.Graphics.AdapterRender.D3D11PartialPrecision](#device.graphics.adapterrender.d3d11partialprecision)
 - [Device.Graphics.AdapterRender.D3D11RasterizerOrderedViews](#device.graphics.adapterrender.d3d11rasterizerorderedviews)
 - [Device.Graphics.AdapterRender.D3D11StencilReference](#device.graphics.adapterrender.d3d11stencilreference)
 - [Device.Graphics.AdapterRender.D3D11TypedUAVLoads](#device.graphics.adapterrender.d3d11typeduavloads)
 - [Device.Graphics.AdapterRender.D3D11WDDM12](#device.graphics.adapterrender.d3d11wddm12)
 - [Device.Graphics.AdapterRender.D3D11WDDM12DoublePrecisionShader](#device.graphics.adapterrender.d3d11wddm12doubleprecisionshader)
 - [Device.Graphics.AdapterRender.D3D11WDDM13](#device.graphics.adapterrender.d3d11wddm13)
 - [Device.Graphics.AdapterRender.D3D11WDDM20](#device.graphics.adapterrender.d3d11wddm20)
 - [Device.Graphics.AdapterRender.D3D11WDDM21](#device.graphics.adapterrender.d3d11wddm21)
 - [Device.Graphics.AdapterRender.D3D12ASTC](#device.graphics.adapterrender.d3d12astc)
 - [Device.Graphics.AdapterRender.D3D12ConservativeRasterization](#device.graphics.adapterrender.d3d12conservativerasterization)
 - [Device.Graphics.AdapterRender.D3D12Core](#device.graphics.adapterrender.d3d12core)
 - [Device.Graphics.AdapterRender.D3D12Multiadapter](#device.graphics.adapterrender.d3d12multiadapter)
 - [Device.Graphics.AdapterRender.D3D12RasterizerOrderedViews](#device.graphics.adapterrender.d3d12rasterizerorderedviews)
 - [Device.Graphics.AdapterRender.D3D12StencilReference](#device.graphics.adapterrender.d3d12stencilreference)
 - [Device.Graphics.AdapterRender.D3D12TypedUAVLoads](#device.graphics.adapterrender.d3d12typeduavloads)
 - [Device.Graphics.AdapterRender.D312VolumeTiledResources](#device.graphics.adapterrender.d312volumetiledresources)
 - [Device.Graphics.IndirectDisplay.Wired](#device.graphics.indirectdisplay.wired)
 - [Device.Graphics.WDDM](#device.graphics.wddm)
 - [Device.Graphics.WDDM.Display](#device.graphics.wddm.display)
 - [Device.Graphics.WDDM.DisplayRender](#device.graphics.wddm.displayrender)
 - [Device.Graphics.WDDM.Render](#device.graphics.wddm.render)
 - [Device.Graphics.WDDM11](#device.graphics.wddm11)
 - [Device.Graphics.WDDM11.Display](#device.graphics.wddm11.display)
 - [Device.Graphics.WDDM11.DisplayRender](#device.graphics.wddm11.displayrender)
 - [Device.Graphics.WDDM11.DisplayRender.D3D9Overlay](#device.graphics.wddm11.displayrender.d3d9overlay)
 - [Device.Graphics.WDDM11.Render](#device.graphics.wddm11.render)
 - [Device.Graphics.WDDM11.Render.DXVAHD](#device.graphics.wddm11.render.dxvahd)
 - [Device.Graphics.WDDM12](#device.graphics.wddm12)
 - [Device.Graphics.WDDM12.Display](#device.graphics.wddm12.display)
 - [Device.Graphics.WDDM12.DisplayOnly](#device.graphics.wddm12.displayonly)
 - [Device.Graphics.WDDM12.DisplayRender](#device.graphics.wddm12.displayrender)
 - [Device.Graphics.WDDM12.DisplayRender.ProcessingStereoscopicVideoContent](#device.graphics.wddm12.displayrender.processingstereoscopicvideocontent)
 - [Device.Graphics.WDDM12.DisplayRender.RuntimePowerMgmt](#device.graphics.wddm12.displayrender.runtimepowermgmt)
 - [Device.Graphics.WDDM12.Render](#device.graphics.wddm12.render)
 - [Device.Graphics.WDDM12.RenderOnly](#device.graphics.wddm12.renderonly)
 - [Device.Graphics.WDDM12.StandbyHibernateFlags](#device.graphics.wddm12.standbyhibernateflags)
 - [Device.Graphics.WDDM13](#device.graphics.wddm13)
 - [Device.Graphics.WDDM13.DisplayRender](#device.graphics.wddm13.displayrender)
 - [Device.Graphics.WDDM13.DisplayRender.CoolingInterface](#device.graphics.wddm13.displayrender.coolinginterface)
 - [Device.Graphics.WDDM13.DisplayRender.WirelessDisplay](#device.graphics.wddm13.displayrender.wirelessdisplay)
 - [Device.Graphics.WDDM13.EnhancedPowerManagement](#device.graphics.wddm13.enhancedpowermanagement)
 - [Device.Graphics.WDDM13.Render](#device.graphics.wddm13.render)
 - [Device.Graphics.WDDM20](#device.graphics.wddm20)
 - [Device.Graphics.WDDM20.Core](#device.graphics.wddm20.core)
 - [Device.Graphics.WDDM20.DisplayRender](#device.graphics.wddm20.displayrender)
 - [Device.Graphics.WDDM20.Display.VirtualModeSupport](#device.graphics.wddm20.display.virtualmodesupport)
 - [Device.Graphics.WDDM21](#device.graphics.wddm21)

<a name="device.graphics.adapterbase"></a>
## <a name="devicegraphicsadapterbase"></a>Device.Graphics.AdapterBase

*所有的图形设备所需的基本功能集。*

### <a name="devicegraphicsadapterbaseapplicationverifier"></a>Device.Graphics.AdapterBase.ApplicationVerifier

*图形驱动程序组件必须遵守应用程序验证工具测试条件。*

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

应用程序验证工具测试的测试条件都必须满足所有用户模式模块 （.dll 文件或.exe 文件） 的图形驱动程序的一部分。 在测试期间的驱动程序，应用程序验证工具必须打开进程的执行驱动模块的位置。 当检测到错误时，应用程序验证工具将导致休息。

为图形驱动程序 AppVerifier 都需要关键的可执行文件 (例如，DWM.exe 为例) 用来测试的稳定性或图形驱动程序的可靠性。
此外，必须上 IHV 的控件面板可执行文件作为这一要求的一部分启用应用程序验证工具。
这些应用程序验证工具测试必须开启过程的测试过程︰

-   com
-   异常
-   句柄
-   堆
-   输入输出
-   泄漏
-   锁定
-   内存
-   rpc
-   线程池
-   tls
-   挂起

### <a name="devicegraphicsadapterbasedriverversion"></a>Device.Graphics.AdapterBase.DriverVersion

*图形适配器或芯片组的驱动程序文件已正确格式化的文件版本。*

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

必须匹配的驱动程序信息文件 (.inf)，内核模式驱动程序 (.sys) 和用户模式驱动程序 (.dll) 文件版本信息。 此外，任何文件的版本信息标识在\[SignatureAttributes\]部分作为二进制文件必须匹配的 PETrust.inf。 inf。 建议该驱动程序软件包匹配项中附加二进制文件的文件版本信息。 inf。

为了保持一致与旧版操作系统的通行文件版本控制要求，文件版本格式必须遵循 AA。BB。CCCCC。DDDDD 模式的位置︰

-   AA 表示最有能力.inf 中列出的设备的驱动程序模型版本

-   BB （WDDM v1.2 驱动程序和更高版本）

    -   指示最有能力的设备.inf 中列出的最高可用 D3D 功能级别

-   BB （WDDM 1.1 版的驱动程序和更低）

    -   指示最有能力在.inf 中列出设备支持的最高可用 DDI 版本

-   CCCCC 是一个数字到 5 位从 0 到 65535 之间选择供应商

-   DDDDD 是一个数字到 5 位从 0 到 65535 之间选择供应商

AA 字段的值︰

| 驱动程序模型 | AA 的值 |
|--------------|----------|
| WDDM v2.x    | 21       |
| WDDM v2.0    | 20       |
| WDDM v1.3    | 10       |
| WDDM v1.2    | 9        |
| WDDM v1.1    | 8        |
| WDDM v1.0    | 7        |
| XDDM         | 6        |

BB 字段的值 (WDDM v1.2 及更高版本):

| DirectX 功能级别 | BB 值 |
|-----------------------|----------|
| 12\_x                 | 21       |
| 12\_1                 | 20       |
| 12\_0                 | 19       |
| 11\_1                 | 18       |
| 11\_0                 | 17       |
| 10\_1                 | 16       |
| 10\_0                 | 15       |
| 9\_3                  | 14       |
| 9\_2                  | 14       |
| 9\_1                  | 14       |

BB 字段的值 (WDDMv1.1 以及更早版本):

| DDI 版本                      | BB 值 |
|----------------------------------|----------|
| D3D11-DDI 在特征级 11\_0 | 17       |
| D3D11-DDI 在特征级 10    | 16       |
| D3D10 DDI                        | 15       |
| D3D9 DDI                         | 14       |

**例如**︰

注意︰ 没有任何要求，即填充前导零的数字，不需要对 CCCCC 或 DDDDD 字段 00123 表示 123。 在以前版本的 Windows 操作系统的最后两个字段是 4 个数字，即 CCCC。DDDD。 因此在 Windows 10 和 WDDM 2.0 版以前的驱动程序版本的示例只有 4 位。

-   Windows Vista WDDM 1.0 版︰

    -   D3D9 DDI 驱动程序可以使用 7.14.0000.0000 至 7.14.9999.9999

    -   D3D10 DDI 驱动程序可以使用 7.15.0000.0000 至 7.15.9999.9999

-   Windows 7 WDDM 1.1 版︰

    -   D3D9 DDI 驱动程序可以使用 8.14.0000.0000 至 8.14.9999.9999

    -   D3D10 DDI 驱动程序可以使用 8.15.0000.0000 至 8.15.9999.9999

    -   与佛罗里达州的 D3D11 DDI\_10\_0 的驱动程序可以使用 8.16.0000.0000 至 8.16.9999.9999

    -   与佛罗里达州的 D3D11 DDI\_11\_0 的驱动程序可以使用 8.17.0000.0000 至 8.17.9999.9999

-   Windows 8 WDDM v1.2 驱动程序︰

    -   佛罗里达州\_10\_0 硬件可以使用 9.15.0000.0000 至 9.15.9999.9999

    -   佛罗里达州\_10\_1 硬件可以使用 9.16.0000.0000 至 9.16.9999.9999

    -   佛罗里达州\_11\_0 硬件可以使用 9.17.0000.0000 至 9.17.9999.9999

    -   佛罗里达州\_11\_1 硬件可以使用 9.18.0000.0000 至 9.18.9999.9999

-   Windows 8.1 WDDM v1.3 驱动程序︰

    -   佛罗里达州\_10\_0 硬件可以使用 10.15.0000.0000 至 10.15.9999.9999

    -   佛罗里达州\_10\_1 硬件可以使用 10.16.0000.0000 至 10.16.9999.9999

    -   佛罗里达州\_11\_0 硬件可以使用 10.17.0000.0000 至 10.17.9999.9999

    -   佛罗里达州\_11\_1 硬件可以使用 10.18.0000.0000 至 10.18.9999.9999

-   Windows 10 WDDM 2.0 版驱动程序︰

    -   佛罗里达州\_11\_1 硬件可以使用 20.18.0000.0000 为 20.18。 65535.65535

    -   佛罗里达州\_12\_0 硬件可以使用 20.19.0000.0000 为 20.19。 65535.65535

    -   佛罗里达州\_12\_1 硬件可以使用 20.20.0000.0000 到 20.20。 65535.65535

**强制执行︰**

高于 10586 将强制执行上述规则生成 Windows 10 HLK 认证播放列表中的强制性检验。 测试将用于较旧的操作系统版本可选。 对于 Windows 10 生成后 10586 WDDM 版本已更新为 2.1。 另一种方法来查看此是强制要求，只适用于天生 WDDM 2.1 或更高版本的驱动程序。

### <a name="devicegraphicsadapterbasepowermanagementcompliance"></a>Device.Graphics.AdapterBase.PowerManagementCompliance

*图形适配器必须符合 VESA 和 ACPI 电源管理规范，并使系统休眠。*

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

若要确保正确实现操作系统控制电源管理，图形适配器和驱动程序必须响应︰

-   WDK 中突出显示部分所需的设备 （D0 和 D3） 电源状态

-   操作系统的 ACPI 电源状态的电源管理

-   \*VESA BIOS 电源管理函数，这些函数定义扩展到 VGA ROM BIOS 电源管理服务。 (\*此行不适用于基于 UEFI GOP 平台。)

### <a name="devicegraphicsadapterbaseregistryentries"></a>Device.Graphics.AdapterBase.RegistryEntries

*安装图形设备的设备驱动程序的应用程序必须创建必需的注册表项。*

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

视频驱动程序安装过程中，必须创建以下注册表项︰
 

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\InstalledDisplayDrivers︰ 此项应包含用户模式驱动程序的名称。

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\HardwareInformation.MemorySize

下面的硬件信息值写入 WDDM 驱动程序︰

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\HardwareInformation.ChipType

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\HardwareInformation.DACType

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\HardwareInformation.AdapterString

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\HardwareInformation.BiosString

-   REG\_二进制︰ HKEY\_本地\_机\\系统\\开目前控制设置\\控件\\视频\\部件\_GUID\\ID\\HardwareInformation.MemorySize

在 INF 中必须包含下面的 INF 指令︰

-   功能评分-这是所有 WDDM 驱动程序必须都支持的常规安装设置。

-   支持即插即用停止指令的副本标志

-   驱动程序\\服务启动类型指令

-   若要禁用 OpenGL 的功能覆盖设置

-   \[版本\]部分指令

-   \[SourceDiskNames\]部分指令

-   常规 x 64 指令

-   常规\[安装\]部分指令

规定要求 Device.Graphics.AdapterBase.DriverVersion 驱动程序 DLL 必须有一个格式正确的文件版本。

### <a name="devicegraphicsadapterbaserunfromdriverstore"></a>Device.Graphics.AdapterBase.RunFromDriverStore

*从驱动程序存储区加载图形适配器或芯片组的驱动程序文件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>


**说明**

必须编写驱动程序，以便直接从驱动程序存储区运行及其组件 （用户模式驱动程序、 内核模式驱动程序等）。 他们不能有任何依赖项在系统路径，如 Windows\\System32。 这包括在驱动程序信息文件 (.inf) 选择*从驱动程序存储区运行*的选项。

请注意，一旦进行此更改后，唯一的名称或绝对路径必须使用要加载的依赖项。 对于选择来实现其他的可选并排比较功能的驱动程序，服务名称必须唯一每类硬件或驱动程序版本。

**业务理由︰**

有从驱动程序存储区中运行的驱动程序将提高升级体验。 它还使供应商能够支持更多的"并排比较"功能，如果它们这样选择--例如，这使得在运行不同的驱动程序版本的同一台计算机中有两个或多个不同系列的 Gpu 的方案。

另一个好处是它减少占用的磁盘空间，因为仍在驱动程序存储区中存在驱动程序，必须在 Windows 中有附加副本和\\System32 导致重复。

**实施**︰

HLK 测试将验证驱动程序信息文件 (.inf) 中的设置为高于 10586 建立 Windows 10。

### <a name="devicegraphicsadapterbasesubsystemresettable"></a>Device.Graphics.AdapterBase.SubsystemResettable

*图形子系统必须是 resettable 到正常操作状态。*

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

如果 GPU 挂起出于任何原因，独立的时候，正在处理什么硬件必须是 resettable 到正常操作状态。 这基本上意味着任何 GPU 必须支持 TDR。

混合系统应该能够处理 TDR 一样非混合系统和重置 （或两者） 的机制 GPU 使系统回到正常状态当操作系统检测到挂起。

*设计备注*

重置 GPU 的能力是独立于系统的当前工作状态。

### <a name="devicegraphicsadapterbasesymbols"></a>Device.Graphics.AdapterBase.Symbols

*符号必须提交和认证的驱动程序*

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

图形驱动程序提交的证书，当匹配符号文件必须提交在同一时间通过 WHKL"添加符号"工作流。 Microsoft 内部使用的故障分析匹配的符号。 而这些符号，不太可能 Microsoft 将能够分析故障并帮助合作伙伴在诊断驱动程序问题。 必须包含以下文件的符号︰

-   .sys 文件

-   中列出的.dll 文件\[SignatureAttributes\]的驱动程序.inf 为"PETrust"的二进制文件的节

"公用"或"专用" [MSDN 指南](https://msdn.microsoft.com/en-us/library/windows/hardware/ff550665.aspx)每可能符号。

<a name="devicegraphicsadapterrender"></a>Device.Graphics.AdapterRender
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*图形设备的呈现功能。*

### <a name="devicegraphicsadapterrenderminimumdirectxlevel"></a>Device.Graphics.AdapterRender.MinimumDirectXLevel

*图形适配器必须实现的最低硬件加速功能。*

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

实现的 DirectX 9 硬件规格所需的显示子系统和驱动程序需要通过 D3D9 UMD DDI 公开功能的 Direct3D 10 功能级别 9\_3 此处所述在 MSDN 中︰

-   <http://msdn.microsoft.com/en-us/library/ff476876.aspx>

-   <http://msdn.microsoft.com/EN-US/library/ff476150.aspx>

-   <http://msdn.microsoft.com/EN-US/library/ff476149.aspx>

-   <http://msdn.microsoft.com/en-us/library/ff471324.aspx>

注意︰ Windows 服务器的图形驱动程序是可选的。 所以他们不具有最低的 DirectX 要求不呈现显示唯一的图形驱动程序。 如果在服务器上加载完整的图形驱动程序时，它必须遵循的最小的 DirectX 功能级别。

### <a name="devicegraphicsadapterrenderrgbframebuffer"></a>Device.Graphics.AdapterRender.RGBFrameBuffer

*指定的组件的顺序和 8 bpp 或大于整数 RGB 帧缓冲区格式的字节序表示，必须实现显示芯片组。*

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

对于每个组件 N 位 RGB 帧缓冲区格式，最低的 N 位必须包含的蓝色成分下, 一步的 N 位必须包含绿色成分下, 一个 N 位必须包含的红色分量和其余 32-(3 x N) 位可能包含字母。 必须将生成的 32 位值存储在内存中小端字节序格式。

### <a name="devicegraphicsadapterrenderyuvsupport"></a>Device.Graphics.AdapterRender.YUVSupport

*支持 YUV 纹理的显示驱动程序必须正确处理纹理和函数。*

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

如果硬件支持 YUV 纹理表面和报告功能，驱动程序必须能够处理而无需任何中间转换这些曲面并正常运行。

<a name="device.graphics.adapterrender.d3d101core"></a>
## <a name="devicegraphicsadapterrenderd3d101core"></a>Device.Graphics.AdapterRender.D3D101Core

*D3D 10.1 核心功能*

### <a name="devicegraphicsadapterrenderd3d101cored3d101coreprimary"></a>Device.Graphics.AdapterRender.D3D101Core.D3D101CorePrimary

*如果图形设备支持 Direct3D 10.1，它必须遵守的 Direct3D 10.1 和 DXGI 规范。*

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

如果图形设备实现 Direct3D 10.1，它必须满足在*Direct3D 10.1 规范*中定义的所有要求，并必须提供足够的 Direct3D 10.1 功能的性能。 

由于 Direct3D 10.1 Direct3D 10 的超集，Direct3D 10.1 的实现还需要 Direct3D 10 功能集的支持。  

设备驱动程序包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 

<a name="device.graphics.adapterrender.d3d101wddm11"></a>
## <a name="devicegraphicsadapterrenderd3d101wddm11"></a>Device.Graphics.AdapterRender.D3D101WDDM11

*D3D 10.1 核心 WDDM 1.1 版新增功能*

### <a name="devicegraphicsadapterrenderd3d101wddm11d3d101v11primary"></a>Device.Graphics.AdapterRender.D3D101WDDM11.D3D101v11Primary

*如果 WDDM 1.1 图形设备支持 Direct3D 10.1，它必须遵守的 Direct3D 10.1 和 DXGI 规范，并支持 BGRA。*

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

如果图形硬件实现 Direct3D 10.1，它必须满足在*Direct3D 10.1 规范*中定义的所有要求，并必须提供足够的 Direct3D 10.1 功能的性能。 

由于 Direct3D 10.1 Direct3D 10 的超集，Direct3D 10.1 的实现还需要支持 Direct3D 10 功能集。  此外，最初在 D3D9 硬件规范中定义的以下功能现在都需要︰

-   BGRA

设备驱动程序包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 

<a name="device.graphics.adapterrender.d3d101wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d101wddm12"></a>Device.Graphics.AdapterRender.D3D101WDDM12

*D3D 10.1 WDDM 1.2 补充核心功能*

### <a name="devicegraphicsadapterrenderd3d101wddm12d3d101v12primary"></a>Device.Graphics.AdapterRender.D3D101WDDM12.D3D101v12Primary

*如果 WDDM 1.2 图形设备支持 Direct3D 10.1，它必须遵守 Direct3D 11.1 功能规范的 Direct3D 10.1、 DXGI 和 D3D10 部分。*

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

如果图形硬件实现 Direct3D 10.1，它必须满足所有要求， *Direct3D 10.1 规范*中定义，并且必须提供足够的 Direct3D 10.1 功能的性能。 

由于 Direct3D 10.1 Direct3D 10 的超集，Direct3D 10.1 的实现还需要支持 Direct3D 10 功能集。  此外，最初在 D3D9 硬件规范中定义的以下功能现在都需要︰

-   BGRA
-   半精度像素格式 (5551，565，4444)
-   同一面 Blts

请*Direct3D 11.1 功能规范*，用于公开与 D3D10 + 硬件的 WDDM 1.2 驱动程序所需的所有新功能的完整信息，参阅。

设备驱动程序，包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 

 

<a name="device.graphics.adapterrender.d3d10computeshader"></a>
## <a name="devicegraphicsadapterrenderd3d10computeshader"></a>Device.Graphics.AdapterRender.D3D10ComputeShader

*Direct3D 10 个着色器模型 4\_ \*计算着色器功能*

### <a name="devicegraphicsadapterrenderd3d10computeshaderd3d10corec"></a>Device.Graphics.AdapterRender.D3D10ComputeShader.D3D10CoreC

*如果图形硬件实现 Direct3D 10 着色器型号 4\_ \*计算着色器功能，它必须符合 D3D11 的硬件规格。*

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

D3D11 规范允许有选择地实施着色器型号 4\_ \*在 Direct3D 10 硬件上的计算着色器功能。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D11 硬件规范*中定义的规范。 

<a name="device.graphics.adapterrender.d3d10core"></a>
## <a name="devicegraphicsadapterrenderd3d10core"></a>Device.Graphics.AdapterRender.D3D10Core

*D3D 10 核心功能*

### <a name="devicegraphicsadapterrenderd3d10cored3d10coreprimary"></a>Device.Graphics.AdapterRender.D3D10Core.D3D10CorePrimary

*如果图形设备支持 Direct3D 10，它必须遵守的 Direct3D 10 和 DXGI 规范。*

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

如果图形硬件实现 Direct3D 10，它必须满足在*Direct3D 10 规范*中定义的所有要求，并必须提供足够的 Direct3D 10 功能的性能。 

设备驱动程序，包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 下面的列表包括一些 Direct3D 10 说明中提出的所需功能︰

-   几何着色器
-   输出流
-   整数指令集
-   新的压缩的格式
-   呈现到顶点缓冲区
-   呈现到多维数据集映射
-   呈现到卷

<a name="device.graphics.adapterrender.d3d10d3d11logicops"></a>
## <a name="devicegraphicsadapterrenderd3d10d3d11logicops"></a>Device.Graphics.AdapterRender.D3D10D3D11LogicOps

*D3D10 D3D11 逻辑操作*

### <a name="devicegraphicsadapterrenderd3d10d3d11logicopsd3d10cored"></a>Device.Graphics.AdapterRender.D3D10D3D11LogicOps.D3D10CoreD

*如果图形硬件实现逻辑操作的功能，它必须符合 D3D11 的硬件规格。*

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

D3D11.1 规范允许 （可选） 在 D3D10、 D3D10.1 和 D3D11 的硬件上实现逻辑操作的功能。   如果硬件支持，并公开对此功能的支持，它必须符合此功能的技术指标，在*D3D11.1 硬件规范*中定义。 

<a name="device.graphics.adapterrender.d3d10multisampling4x"></a>
## <a name="devicegraphicsadapterrenderd3d10multisampling4x"></a>Device.Graphics.AdapterRender.D3D10Multisampling4X

*D3D10 多级采样 (4 X)*

### <a name="devicegraphicsadapterrenderd3d10multisampling4xd3d10corea"></a>Device.Graphics.AdapterRender.D3D10Multisampling4X.D3D10CoreA

*如果图形硬件实现 D3D10 4 x 多级采样，它必须符合 D3D10 的硬件规格。*

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

D3D10 规范允许有选择地实施 4 X 多级采样。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D10 硬件规范*中定义的规范。 

<a name="device.graphics.adapterrender.d3d10multisampling8x"></a>
## <a name="devicegraphicsadapterrenderd3d10multisampling8x"></a>Device.Graphics.AdapterRender.D3D10Multisampling8X

* Direct3D 10 多级采样 (8 X)

### <a name="devicegraphicsadapterrenderd3d10multisampling8xd3d10coreb"></a>Device.Graphics.AdapterRender.D3D10Multisampling8X.D3D10CoreB

*如果图形硬件实现 Direct3D 10 8 X 多级采样，然后它必须符合的 Direct3D 10 硬件规格。*

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

D3D10 规范允许有选择地实施 8 X 多级采样。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D10 硬件规范*中定义的规范。 

<a name="device.graphics.adapterrender.d3d10wddm11"></a>
## <a name="devicegraphicsadapterrenderd3d10wddm11"></a>Device.Graphics.AdapterRender.D3D10WDDM11

*D3D 10 核心 WDDM 1.1 版新增功能*

### <a name="devicegraphicsadapterrenderd3d10wddm11d3d10v11primary"></a>Device.Graphics.AdapterRender.D3D10WDDM11.D3D10v11Primary

*如果图形硬件实现 Direct3D 10，该驱动程序是 WDDM1.1，它必须遵守的 Direct3D 10 和 DXGI 规范，并支持 BGRA。*

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

如果图形硬件实现 Direct3D 10，该驱动程序是 WDDM1.1，它必须满足在*Direct3D 10 规范*中定义的所有要求，并必须提供足够的 Direct3D 10 功能的性能。 此外，最初在 D3D9 硬件规范中定义的以下功能现在都需要︰

-   BGRA

设备驱动程序包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 下面的列表包括一些 Direct3D 10 说明中提出的所需功能︰

-   几何着色器
-   输出流
-   整数指令集
-   新的压缩的格式
-   呈现到顶点缓冲区
-   呈现到多维数据集映射
-   呈现到卷

<a name="device.graphics.adapterrender.d3d10wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d10wddm12"></a>Device.Graphics.AdapterRender.D3D10WDDM12

*D3D 10 WDDM 1.2 补充核心功能*

### <a name="devicegraphicsadapterrenderd3d10wddm12d3d10v12primary"></a>Device.Graphics.AdapterRender.D3D10WDDM12.D3D10v12Primary

*如果图形硬件实现 Direct3D 10，该驱动程序是 WDDM1.2，它必须遵守 Direct3D 10，DXGI 和在 Direct3D 11.1 功能规范中的 D3D10 附件。*

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

如果图形硬件实现 Direct3D 10，该驱动程序是 WDDM1.2，它必须满足在*Direct3D 10 规范*中定义的所有要求，并必须提供足够的 Direct3D 10 功能的性能。 此外，最初在 D3D9 硬件规范中定义的以下功能现在都需要︰

-   BGRA
-   半精度像素格式 (5551，565，4444)
-   同一面 Blts

 
请*Direct3D 11.1 功能规范*，用于公开与 D3D10 + 硬件的 WDDM 1.2 驱动程序所需的所有新功能的完整信息，参阅。

设备驱动程序包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 下面的列表包括一些 Direct3D 10 说明中提出的所需功能︰

-   几何着色器
-   输出流
-   整数指令集
-   新的压缩的格式
-   呈现到顶点缓冲区
-   呈现到多维数据集映射
-   呈现到卷

### <a name="devicegraphicsadapterrenderd3d10wddm12stereoscopic3darraysupport"></a>Device.Graphics.AdapterRender.D3D10WDDM12.Stereoscopic3DArraySupport

*WDDM1.2 驱动程序必须支持 Stereoscopic 3D 在 D3D 通过添加扩展的阵列的支持。*

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

通过 WDDM 1.2 所需支持
 

| DDI 或功能                                                                                                                                       | WDDM 1.1                    | WDDM 1.2                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|---------------------------------------------------|
| 创建 backbuffers （和原色），它使用 D3D10DDIARG\_CREATERESOURCE 和 D3D11DDIARG\_CREATERESOURCE                                              | 仅限于 ArraySize = 1 | 推广为 ArraySize = 2                      |
| DXGI UM 后缓冲 DDIs (DXGI\_DDI\_ARG\_BLT、 DXGI\_DDI\_ARG\_旋转\_资源\_标识、 DXGI\_DDI\_ARG\_存在、 DXGI\_DDI\_ARG\_SETDISPLAYMODE) | 仅限于 backbuffers   | 相同的但包括立体后台缓冲区           |
| 在常规 （内核和用户） 的演示文稿                                                                                                            | 仅限于 backbuffers   | 相同的但包括立体后台缓冲区           |
| 共享                                                                                                                                              | 仅限于 ArraySize = 1 | 通用于*任何*ArraySize (包括&gt;2) |
| GDI 互操作                                                                                                                                          | 仅限于 ArraySize = 1 | 通用于*任何*ArraySize (包括&gt;2) |
| HLSL 非数组取样器声明                                                                                                                | 仅限于 ArraySize = 1 | 通用于*任何*ArraySize (包括&gt;2) |

 
HLSL 非数组示例声明表示允许某些着色器中单-子资源的资源当前要从单个子资源-视图具有多个 subresources 的资源还取样，样本。
 
请注意，驱动程序必须支持扩展阵列的立体 3D 的 Api，但对于全屏幕独占立体 3D 应用程序来显示，驱动程序也应支持立体声 scanout 输出。  例如，在多适配器系统中有两个 WDDM 1.2 图形适配器，每个适配器可用于创建将立体声音频*窗口*swapchain，甚至如果只有其中一个适配器实际支持立体声输出。

 

<a name="device.graphics.adapterrender.d3d111core"></a>
## <a name="devicegraphicsadapterrenderd3d111core"></a>Device.Graphics.AdapterRender.D3D111Core

*D3D 11.1 核心功能*

### <a name="devicegraphicsadapterrenderd3d111cored3d111coreprimary"></a>Device.Graphics.AdapterRender.D3D111Core.D3D111CorePrimary

*如果图形设备支持 Direct3D 11.1，它必须遵守的 Direct3D 11.1 和 DXGI 规范。*

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

图形设备必须满足在*Direct3D 11.1 规范*中定义的所有要求，并且必须提供足够的 Direct3D 11.1 功能的性能。
 

Direct3D 11.1 是超集的 Direct3D 11 （它是的严格超集的 Direct3D 10.1 和 Direct3D 10）;因此，Direct3D 11.1 实现还需要分别定义 Direct3D 10 Direct3D 10.1，Direct3D 11 规范的功能的完全支持。

设备驱动程序，包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。 

<a name="device.graphics.adapterrender.d3d11astc"></a>
## <a name="devicegraphicsadapterrenderd3d11astc"></a>Device.Graphics.AdapterRender.D3D11ASTC

### <a name="devicegraphicsadapterrenderd3d11astccorerequirement"></a>Device.Graphics.AdapterRender.D3D11ASTC.CoreRequirement

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

实现 ASTC LDR 支持的 D3D11 驱动程序必须支持所有 2D ASTC 格式从采样。 ASTC 格式不是单独的可支持性，因此，必须所有 ASTC 被认为支持支持。 必须针对 ASTC LDR 支持才能有效支持的所有 ASTC 格式列表如下: (所有格式都有\_TYPELESS，和\_SRGB 等效)

-   DXGI\_格式\_4 X 4
-   DXGI\_格式\_5 X 4
-   DXGI\_格式\_5 X 5
-   DXGI\_格式\_6 X 5
-   DXGI\_格式\_6 X 6
-   DXGI\_格式\_8 X 5
-   DXGI\_格式\_8 X 6
-   DXGI\_格式\_8 X 8
-   DXGI\_格式\_10 X 5
-   DXGI\_格式\_10 X 6
-   DXGI\_格式\_10 X 8
-   DXGI\_格式\_10 X 10
-   DXGI\_格式\_12 X 10
-   DXGI\_格式\_12 X 12

<a name="device.graphics.adapterrender.d3d11conservativerasterization"></a>
## <a name="devicegraphicsadapterrenderd3d11conservativerasterization"></a>Device.Graphics.AdapterRender.D3D11ConservativeRasterization

### <a name="devicegraphicsadapterrenderd3d11conservativerasterizationcorerequirement"></a>Device.Graphics.AdapterRender.D3D11ConservativeRasterization.CoreRequirement

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

Direct3D 11 显示驱动程序应实现 DDIs 与保守光栅化，具有的功能层的补偿关系︰

 - 不是确定性范围︰
 - 内部的覆盖率
 - 后期对齐退化剔除
 - 其他管道的交互︰
   - TIR
   - MSAA
   - SampleMask 带有内部覆盖范围
   - 剪辑的距离
   - 查询
   - oMask
   - HelperPixel 覆盖范围
   - 内插特性 （推断）
   - 早期的 Z 深度外推带

有关其他详细信息，请参阅保守光栅化规范。

<a name="device.graphics.adapterrender.d3d11core"></a>
## <a name="devicegraphicsadapterrenderd3d11core"></a>Device.Graphics.AdapterRender.D3D11Core

*D3D 11 核心功能*

### <a name="devicegraphicsadapterrenderd3d11cored3d11coreprimary"></a>Device.Graphics.AdapterRender.D3D11Core.D3D11CorePrimary

*如果图形设备实现 Direct3D 11，它必须遵守的 Direct3D 11 和 DXGI 规范。*

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

如果图形设备实现 Direct3D 11，它必须满足在*Direct3D 11 规范*中定义的所有要求，并必须提供足够的 Direct3D 11 功能的性能。

由于 Direct3D 11 Direct3D 10 的超集，Direct 3D 11 的实现还需要支持 Direct3D 10.1 功能集，并通过扩展 Direct3D 10。 

设备驱动程序包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。

<a name="device.graphics.adapterrender.d3d11doubleprecisionshader"></a>
## <a name="devicegraphicsadapterrenderd3d11doubleprecisionshader"></a>Device.Graphics.AdapterRender.D3D11DoublePrecisionShader

*Direct3D 11 双精度着色器功能*

### <a name="devicegraphicsadapterrenderd3d11doubleprecisionshaderd3d11corec"></a>Device.Graphics.AdapterRender.D3D11DoublePrecisionShader.D3D11CoreC

*如果图形硬件实现 Direct3D 11 双精度，它必须符合功能规范，D3D11 硬件规范中所述。*

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

D3D11 规范允许选择在 Direct3D 11 硬件上实现双精度着色器的功能。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D11 硬件规范*中定义的规范。 

<a name="device.graphics.adapterrender.d3d11drivercommandlists"></a>
## <a name="devicegraphicsadapterrenderd3d11drivercommandlists"></a>Device.Graphics.AdapterRender.D3D11DriverCommandLists

*Direct3D 11 驱动程序命令列表*

### <a name="devicegraphicsadapterrenderd3d11drivercommandlistsd3d11coreb"></a>Device.Graphics.AdapterRender.D3D11DriverCommandLists.D3D11CoreB

*如果图形硬件实现 Direct3D 11 驱动程序命令列表，它必须符合 D3D11 的硬件规范中定义的功能规范。*

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

（可选） 在 Direct3D 11 硬件上实现 DriverCommandListfunctionality D3D11 规范允许。 如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在 D3D11 硬件规范中定义的规范。

<a name="device.graphics.adapterrender.d3d11driverconcurrentobjectcreation"></a>
## <a name="devicegraphicsadapterrenderd3d11driverconcurrentobjectcreation"></a>Device.Graphics.AdapterRender.D3D11DriverConcurrentObjectCreation

*创建 Direct3D 11 驱动程序并发对象*

### <a name="devicegraphicsadapterrenderd3d11driverconcurrentobjectcreationd3d11corea"></a>Device.Graphics.AdapterRender.D3D11DriverConcurrentObjectCreation.D3D11CoreA

*如果图形硬件实现 Direct3D 11 驱动程序并发对象创建，它必须符合 D3D11 的硬件规范中定义的功能规范。*

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

D3D11 规范允许选择在 Direct3D 11 硬件上实现驱动程序并发对象创建功能。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D11 硬件规范*中定义的规范。 

<a name="device.graphics.adapterrender.d3d11level9wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d11level9wddm12"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM12

*D3D9 UM DDI WDDM 1.2 更新*

### <a name="devicegraphicsadapterrenderd3d11level9wddm12d3d9umddiupdate"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM12.D3D9UMDDIUpdate

*如果图形硬件的驱动程序实现的 WDDM1.2 规范，它必须包含 D3D9 用户模式 DDI 添加 D3D11.1 API/DDI 规范的定义。*

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

WDDM 1.2 图形驱动程序，则需要实现 D3D9 适配器 DDI 和 D3D9 DDI 的添加项定义 D3D9 DDI，除了*D3D11.1 API 版 DDI 规范*中所定义的 DirectX 9 硬件和驱动程序的规范。
 

<a name="device.graphics.adapterrender.d3d11level9wddm13"></a>
## <a name="devicegraphicsadapterrenderd3d11level9wddm13"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13

对 D3D9 UM DDI 的 WDDM1.3 更新

### <a name="devicegraphicsadapterrenderd3d11level9wddm13largecapturetextures"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.LargeCaptureTextures

*Direct3D 大捕获纹理*

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

所有 9 UMDs，无论硬件，最大的功能级别现在必须正确验证传递给 CreateResource2 的纹理大小参数。

现在必须正常故障图形驱动程序 (通过返回 E\_INVALIDARG) 捕获纹理创建请求超出硬件的功能。

创建批准任何捕获纹理必须行为相同，以捕获定义它们的纹理。

### <a name="devicegraphicsadapterrenderd3d11level9wddm13level9instancing"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.Level9Instancing

*9 级实例化*

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

在 Windows 中，操作系统将做 D3D 实例化以减少 CPU/GPU 的使用量增加了的使用。 所有的 WDDM1.3 驱动程序必须支持实例存储功能级别 9 所述\_3。

### <a name="devicegraphicsadapterrenderd3d11level9wddm13nativestagingbuffers"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.NativeStagingBuffers

*Level9 本机临时缓冲区性能验证*

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

实现 WDDM1.3 的 Directx9 级别的图形硬件必须支持 D3D9 本机临时缓冲区 DDI。

### <a name="devicegraphicsadapterrenderd3d11level9wddm13nativeupdatesubresource"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.NativeUpdateSubresource

*Direct3D Level9 本机 UpdateSubresource*

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

对于 Windows，Direct3D9 DDI 规范将包括对 UpdateSubresource DDI 的本机支持。 当 D3D9 级部件实现此 DDI 时，速度不会低于 CPU 复制操作必须执行给定内存量为 UpdateSubresource API 调用。

### <a name="devicegraphicsadapterrenderd3d11level9wddm13timestampcountersupport"></a>Device.Graphics.AdapterRender.D3D11Level9WDDM13.TimestampCounterSupport

*Direct3D Level9 时间戳和计数器*

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

时间戳查询支持将进行强制所有 9 级 WDDM 1.3 的驱动程序，特别是这些查询类型︰

1.  D3DDDIQUERYTYPE\_时间戳
2.  D3DDDIQUERYTYPE\_TIMESTAMPDISJOINT
3.  D3DDDIQUERYTYPE\_TIMESTAMPFREQ

此外，还必须支持的 CheckDounter 和 CheckCounterInfo Direct3D11 计数器 DDIs。

<a name="device.graphics.adapterrender.d3d11partialprecision"></a>
## <a name="devicegraphicsadapterrenderd3d11partialprecision"></a>Device.Graphics.AdapterRender.D3D11PartialPrecision

*D3D11 部分精度着色器支持*

### <a name="devicegraphicsadapterrenderd3d11partialprecisiond3d11coree"></a>Device.Graphics.AdapterRender.D3D11PartialPrecision.D3D11CoreE

*如果图形硬件实现 D3D11.1 部分精度着色器功能，它必须符合功能规范，在 D3D11.1 硬件规范中定义。*

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

D3D11.1 规范 （可选） D3D9，D3D10 上实现部分精度着色器功能允许\*，和 Direct3D 11 WDDM 1.2 驱动程序的硬件。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D11.1 硬件规范*中定义的规范。  


<a name="device.graphics.adapterrender.d3d11rasterizerorderedviews"></a>
## <a name="devicegraphicsadapterrenderd3d11rasterizerorderedviews"></a>Device.Graphics.AdapterRender.D3D11RasterizerOrderedViews

### <a name="devicegraphicsadapterrenderd3d11rasterizerorderedviewscorerequirement"></a>Device.Graphics.AdapterRender.D3D11RasterizerOrderedViews.CoreRequirement 

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

**说明**︰

<a name="device.graphics.adapterrender.d3d11stencilreference"></a>
## <a name="devicegraphicsadapterrenderd3d11stencilreference"></a>Device.Graphics.AdapterRender.D3D11StencilReference

### <a name="devicegraphicsadapterrenderd3d11stencilreferencecorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D11StencilReference.CoreRequirement （如果实现）

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

Direct3D11 的显示驱动程序应实现 DDIs 与像素着色器模具参考相关︰

 - 将写入 SV\_STENCILREF 函数按预期的方式

有关其他信息，请参阅[PS-Specified 模具 Ref 规范](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/PS-Specified%20Stencil%20Reference%20Value%20-%20Unified%20Spec.docx?web=1)。

<a name="device.graphics.adapterrender.d3d11typeduavloads"></a>
## <a name="devicegraphicsadapterrenderd3d11typeduavloads"></a>Device.Graphics.AdapterRender.D3D11TypedUAVLoads

### <a name="devicegraphicsadapterrenderd3d11typeduavloadcorerequirement"></a>Device.Graphics.AdapterRender.D3D11TypedUAVLoad.CoreRequirement

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

Direct3D11 的显示驱动程序应实现对键入 UAV 负载相关的 DDIs:

-   如果设置类型化的 UAV 负载标志的所有所需的 UAV 格式支持类型化的负载

-   还可以声明类型的支持类型的负载

有关详细信息，请参阅[输入 UAV 负荷规范](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/UAV%20Typed%20Load%20Draft%20Specification.docx?web=1)

<a name="device.graphics.adapterrender.d3d11wddm12"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm12"></a>Device.Graphics.AdapterRender.D3D11WDDM12

*D3D 11 WDDM 1.2 补充核心功能*

### <a name="devicegraphicsadapterrenderd3d11wddm12d3d11v12primary"></a>Device.Graphics.AdapterRender.D3D11WDDM12.D3D11v12Primary

*如果 WDDM 1.2 图形设备实现 Direct3D 11，它必须遵守 Direct3D 11、 DXGI 和 D3D10 部分的 Direct3D 11.1 功能规范。*

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

如果图形设备实现 Direct3D 11，它必须满足在 Direct3D 11 规范中定义的所有要求，并必须提供足够的 Direct3D 11 功能的性能。

由于 Direct3D 11 Direct3D 10 的超集，Direct 3D 11 的实现还需要支持 Direct3D 10.1 功能集，并通过扩展 Direct3D 10。 

在 Windows 中，最初在 D3D9 硬件规范中定义的以下功能目前还需要︰

-   半精度像素格式 (5551，565，4444)
-   同一面 Blts

请*Direct3D 11.1 功能规范*，用于公开与 D3D10 + 硬件的 WDDM 1.2 驱动程序所需的所有新功能的完整信息，参阅。

设备驱动程序，包括为 DXGI DDI 标头定义这些功能必须公开该技术指标所需的所有功能。

<a name="device.graphics.adapterrender.d3d11wddm12doubleprecisionshader"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm12doubleprecisionshader"></a>Device.Graphics.AdapterRender.D3D11WDDM12DoublePrecisionShader

*Direct3D 11 双精度着色器的功能与其他操作数的代码引入 WDDM 1.2*

### <a name="devicegraphicsadapterrenderd3d11wddm12doubleprecisionshaderd3d11v12c"></a>Device.Graphics.AdapterRender.D3D11WDDM12DoublePrecisionShader.D3D11v12C

*如果图形硬件实现的 Direct3D 11 双精度着色器功能与 WDDM 1.2 驱动程序添加，它必须符合 D3D11 的硬件规范中定义的功能规范。*

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

D3D11 规范允许选择在 Direct3D 11 硬件上实现双精度着色器的功能。   如果硬件支持和驱动程序提供了此功能，它必须符合这项功能在*D3D11 硬件规范*中定义的规范。   对于 Windows，如果 WDDM 1.2 图形设备驱动程序支持双精度着色器的功能，它支持需要扩展双精度数学*着色器模型的改进规范*中所述。

<a name="device.graphics.adapterrender.d3d11wddm13"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm13"></a>Device.Graphics.AdapterRender.D3D11WDDM13

*D3D11.1 铺资源支持*

### <a name="devicegraphicsadapterrenderd3d11wddm13mapdefault"></a>Device.Graphics.AdapterRender.D3D11WDDM13.MapDefault

*将默认映射*

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

Direct3D 功能级别 11\_0 和较高部分的 WDDM1.3 驱动程序必须允许可映射的默认缓冲区创建。 应用程序将能够通过设置 CPU 请求这些可映射的资源\_CPU 读/\_WDDM1.3 规范中所述的写访问权限标志。 可映射的默认缓冲区应与作用的现有默认缓冲区今天从 API 的角度 （不是能够被映射）。 默认缓冲区可映射的映射/CPU 访问性能应等同于临时缓冲区。

<a name="device.graphics.adapterrender.d3d11wddm20"></a>
## <a name="devicegraphicsadapterrenderd3d11wddm20"></a>Device.Graphics.AdapterRender.D3D11WDDM20



### <a name="devicegraphicsadapterrenderd3d11wddm20corerequirement"></a>Device.Graphics.AdapterRender.D3D11WDDM20.CoreRequirement

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

<ol style="list-style-type: decimal">
<li><p><strong>高性能的计时数据︰</strong></p>
<p>注意︰ 此功能支持 D3D11 WDDM 2.0 驱动程序是强制性。</p>
<p>"高性能图形计时数据"提供图形工作负载轻的重量和高度详细的计时数据。 这些数据用于分析工具来识别性能或其他图形相关的 Windows 应用程序中的问题或图形堆栈。</p>
<p>WDDM2.0 驱动程序必须确保图形驱动，提供了以下功能︰</p>
<ul>
<li><p>高分辨率 GPU 计时器</p></li>
<li><p>12.5 MHz （80ns 分辨率） 或更高。</p></li>
<li><p>至少 32 位的时间戳分辨率</p></li>
<li><p>可以为所有引擎在 GPU 中取样 GPU 时间戳</p></li>
<li><p>GPU 时间戳可以取样 GPU 管线末端</p></li>
<li><p>GPU 时间戳频率可以进行抽样。</p></li>
<li><p>GPU 时间戳是不变并且不受 p-状态转换。</p></li>
</ul>
<p>有关此功能的其他更改，这将包括添加了两个新标志，与现有的 DdiControlEtwLogging 接口;当设置了这些标志，以使第一个标志是值为 1，第二个标志是值为 0，然后驱动程序必须确保︰</p>
<ul>
<li><p>所有引擎组件必须都确保它们永远不会制或电源关只要标志将保持启用状态，并且一般情况下必须避免输入任何空闲状态。 这些组件必须保持活动状态，以确保没有由于电源转换添加没有延迟。</p></li>
<li><p>所有引擎组件必须都确保在其操作值的最大稳定保持其处理频率和功能的总线带宽。 热量要求下的 P-状态转换的事件仍然发生以防止损坏的硬件，但应定义 P-状态，这样，这些都是不正常情况下看到很棒的实验室环境中的卓越事件。</p></li>
<li><p>可以使用以前颁发的图形命令相关样本的 GPU 时间戳</p></li>
<li><p>计时数据的生成默认情况下处于关闭状态，但可以打开和关闭任何时候。</p></li>
<li><p>收集性能数据的开销将比使用已在 D3D9 和 D3D10 + 中可用的时间戳查询技术不慢</p></li>
<li><p>可以直接命令列表和捆绑包中收集计时数据。 计时数据可启用/禁用在每个命令列表的基础上。</p></li>
<li><p>结果基于图块上的数据延迟呈现硬件出现如同它生成即时模式呈现的设备上。</p></li>
</ul>
</li>
</ol>


<a name="device.graphics.adapterrender.d3d11wddm21"></a>
##Device.Graphics.AdapterRender.D3D11WDDM21

WDDM 2.1 是生成大于 10586 引入 Windows 10 的可选版本级别。 如果一个驱动程序实现 WDDM 2.1 它必须实现所有 WDDM 2.1 要求。 WDDM 2.0 驱动程序将继续在更高版本的 Windows 上运行 10 个版本。

### <a name="devicegraphicsadapterrenderd3d11wddm21corerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D11WDDM21.CoreRequirement （如果实现）

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

<ol>
<li><p>**扩展 NV12 / 420 共享纹理支持**</p>

<p>注意︰ 此功能支持 D3D11 WDDM 2.1 驱动程序是强制性。</p>

<p>驱动程序必须支持共享几个纹理格式具有更多的属性，以启用服务器框架的方案。 目标是零拷贝之间捕获设备和视频引擎。</p></li>

<li><p>**eFSE/UWP 优化支持**</p>

<p>注意︰ 此功能是强制性 WDDM 2.1 驱动程序支持 D3D11 或 D3D9。</p>

<p>该驱动程序必须支持新的 pfnAcquireResource/pfnReleaseResource 方法用于启用驱动程序优化的 eFSE （模拟全屏幕独占） / UWP （通用 Windows 平台） 性能与 FSE 的奇偶校验。</p></li>
</ol>

<a name="device.graphics.adapterrender.d3d12astc"></a>
##Device.Graphics.AdapterRender.D3D12ASTC

### <a name="devicegraphicsadapterrenderd3d12astccorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12ASTC.CoreRequirement （如果实现）

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

Direct3D12 的显示驱动程序必须具有足够的性能在 Direct3D 12 规范中定义满足所有要求。

实现 ASTC LDR 支持的 D3D12 驱动程序必须支持所有 2D ASTC 格式从采样。 ASTC 格式不是单独的可支持性，因此，必须所有 ASTC 被认为支持支持。 必须针对 ASTC LDR 支持才能有效支持的所有 ASTC 格式列表如下: (所有格式都有\_TYPELESS，和\_SRGB equilovants。)

 - DXGI\_格式\_4 X 4
 - DXGI\_格式\_5 X 4
 - DXGI\_格式\_5 X 5
 - DXGI\_格式\_6 X 5
 - DXGI\_格式\_6 X 6
 - DXGI\_格式\_8 X 5
 - DXGI\_格式\_8 X 6
 - DXGI\_格式\_8 X 8
 - DXGI\_格式\_10 X 5
 - DXGI\_格式\_10 X 6
 - DXGI\_格式\_10 X 8
 - DXGI\_格式\_10 X 10
 - DXGI\_格式\_12 X 10
 - DXGI\_格式\_12 X 12

**业务理由︰**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。 这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。

<a name="device.graphics.adapterrender.d3d12conservativerasterization"></a>
## <a name="devicegraphicsadapterrenderd3d12conservativerasterization"></a>Device.Graphics.AdapterRender.D3D12ConservativeRasterization

### <a name="devicegraphicsadapterrenderd3d12conservativerasterizationcorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12ConservativeRasterization.CoreRequirement （如果实现）

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

Direct3D12 的显示驱动程序必须实现 DDIs 与保守光栅化，具有的功能层的补偿关系︰

 - 不是确定性范围︰
 - 内部的覆盖率
 - 后期对齐退化剔除
 - 其他管道的交互︰
 - TIR
 - MSAA
 - SampleMask 带有内部覆盖范围
 - 剪辑的距离
 - 查询
 - oMask
 - HelperPixel 覆盖范围
 - 内插特性 （推断）
 - 早期的 Z 深度外推带

有关其他详细信息，请参阅[保守光栅化规范](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/Conservative%20Rasterization%20-%20Unified%20Spec.docx?web=1)。

**业务理由︰**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。 这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。

<a name="device.graphics.adapterrender.d3d12core"></a>
## <a name="devicegraphicsadapterrenderd3d12core"></a>Device.Graphics.AdapterRender.D3D12Core

*D3D 12 核心功能*

### <a name="devicegraphicsadapterrenderd3d12corecorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12Core.CoreRequirement （如果实现）

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

说明︰

<p>显示驱动程序，Direct3D12 必须满足所有要求中定义的<strong><em>Direct3D 12 规范</em></strong>。</p>

<ol style="list-style-type: decimal">
<li><p><strong>用户堆</strong></p>
<p>GPU 必须读取和写入数据与内存页。 由 CPU 访问这些页面时，它们必须能够标记为回写或 cpu 的写组合。</p>
<p>驱动程序必须遵守写入合并请求与其他适配器和引擎系统高效地运行。 Gpu 都必须完全以正交方式支持其他网页属性。</p>
<p>GPU 必须能够读取和写入缓冲区的一维数据&amp;与 GPU 的所有操作的此类页面的多维纹理数据。 但是，限制和未定义的行为存在，在规范中说明。</p>
<p>它是适用于资源和堆要映射时主动读取或写入此类网页的 GPU。 请 DDI 规范的 GPU 读写操作的详细信息，参阅</p>

<blockquote>
<p>Gpu 支持的 I/O 一致性必须写回所需或选择驻留在物理系统内存中的页时使用它。</p>

<p>数据通常与缓冲区，并且需要对齐正常消耗的 gpu 间距线性纹理数据操作。 缓冲区和间距线性数据可能驻留旁彼此和甚至重叠。</p>
</blockquote>

<p>间距线性需求&amp;限制如下︰</p>

<ul>
<li><p>只有一个 3D 子资源，一次是必要的间距线性 / 行优先复制。</p></li>
<li><p>只有一个二维子资源，一次是必要的间距线性 / 行主要取样，呈现。</p></li>
<li><p>基址 / 间距线性纹理数据的偏移量都必须是 512 字节对齐，或更少。</p></li>
<li><p>宽度 stride 必须为 128 字节对齐的或较少，适用于所有纹理元素大小。 宽度步幅是 32 位并且可以比严格正确排列的特定纹理宽度的步幅大得多。</p></li>
<li><p>以正交方式支持任意高度，D3D 最。</p></li>
<li><p>对于体积纹理深度步幅是高度时间宽度步幅。</p></li>
<li><p>压缩的呈现目标必须能够解析要启用 CPU 读 / 写的纹理。</p></li>
</ul>
<p>通过 D3D11，不会更改缓冲区对齐限制︰</p>
<ul>
<li><p>常数数据读取必须从开始处堆 256 字节的倍数 (即只能从 256 字节对齐的地址)，或更少。</p></li>
<li><p>数据读取索引必须为索引数据类型大小的倍数 (即只能从自然对齐的数据的地址)，或更少。</p></li>
<li><p>绘制 * 间接数据必须为 4 的倍数的偏移量 (即只能从双字节对齐的地址)，或更少。</p></li>
</ul>

<ul>
  <li>
    <p>GPU 时 GPU 支持标准 swizzle，必须尽可能以正交方式为其他纹理，如纹理中，呈现为，将复制到支持所有多维操作&amp;从，re-swizzle 到&amp;，等等。</p>
    <ul>
        <li><p>块压缩格式和 ASTC 格式元素大小必须是相同的块大小。</p></li>
        <li><p>GPU 必须支持从所有引擎，包括扫描出标准 swizzle。</p></li>
        <li><p>压缩的呈现目标必须能够解析要启用 CPU 读 / 写的纹理。</p></li>
        <li><p>标准的 swizzle 数据必须为 4KB 和 64KB 页面边界对齐。</p></li>
    </ul>
  </li>
  <li>
    <p>GPU，应该不需要大于 64 KB，但 MSAA 资源与样本数大于 1 的纹理对齐。</p>
  </li>
  <li>
    <p>支持基于页面的虚拟地址的物理内存从在 GPU 上所有引擎。</p>
    <ul>
      <li>
        <p>如果 GPU 支持 GPU 虚拟寻址与适当的安全边界允许用户模式的修改，必须得到支持从所有引擎来实现其完整的好处。</p>
      </li>
    </ul>
  </li>
</ul>
</li>

<li><p><strong>资源绑定︰</strong></p>
<p>Direct3D 12 API 的显示驱动程序必须实现与相关对象描述符和描述符堆 （如下），DDIs 与补偿的功能层︰</p>
<ul>
<li><p>有关资源绑定层功能查询</p></li>
<li><p>描述符堆</p></li>
<li><p>设置说明符堆</p></li>
<li><p>创建描述符</p></li>
<li><p>复制描述符</p></li>
<li><p>创建根表布局</p></li>
<li><p>设置根表布局</p></li>
<li><p>在根表上设置描述符表</p></li>
<li><p>在根表上设置常数</p></li>
<li><p>在根表 （避开描述符的堆表） 上设置说明符</p></li>
<li><p>命令设置 IA/VB/SO/RT/DS 描述符列出 / 捆绑在一起</p></li>
<li><p>视图操作</p>
<p>请参阅"硬件支持级别"和"DDI"D3D12 资源绑定中的更多详细信息的功能规范的章节。</p></li>
</ul></li>

<li><p><strong>高性能的计时数据︰</strong></p>
<p>"高性能图形计时数据"提供图形工作负载轻的重量和高度详细的计时数据。 这些数据用于分析工具来识别性能或其他图形相关的 Windows 应用程序中的问题或图形堆栈。</p>

<ul>
<li><p>WDDM1.3 驱动程序必须确保图形驱动，提供了以下功能︰</p></li>
<li><p>高分辨率 GPU 计时器</p></li>
<li><p>12.5 MHz （80ns 分辨率） 或更高。</p></li>
<li><p>至少 32 位的时间戳分辨率</p></li>
<li><p>可以为所有引擎在 GPU 中取样 GPU 时间戳</p></li>
<li><p>GPU 时间戳可以取样 GPU 管线末端</p></li>
<li><p>GPU 时间戳频率可以进行抽样。</p></li>
<li><p>GPU 时间戳是不变并且不受 p-状态转换。</p></li>
<li><p>有关此功能的其他更改，这将包括添加了两个新标志，与现有的 DdiControlEtwLogging 接口;当设置了这些标志，以使第一个标志是值为 1，第二个标志是值为 0，然后驱动程序必须确保︰</p></li>
<li><p>所有引擎组件必须都确保它们永远不会制或电源关只要标志将保持启用状态，并且一般情况下必须避免输入任何空闲状态。 这些组件必须保持活动状态，以确保没有由于电源转换添加没有延迟。</p></li>
<li><p>所有引擎组件必须都确保在其操作值的最大稳定保持其处理频率和功能的总线带宽。 热量要求下的 P-状态转换的事件仍然发生以防止损坏的硬件，但应定义 P-状态，这样，这些都是不正常情况下看到很棒的实验室环境中的卓越事件。</p></li>
<li><p>可以使用以前颁发的图形命令相关样本的 GPU 时间戳</p></li>
<li><p>D3D12 驱动程序必须能够进行采样管道戳除了管道时间戳结束的开始。 管线的时间戳的开始时间必须在 GPU 开始执行使用执行命令其处理单元相关的图形命令时。</p></li>
<li><p>计时数据的生成默认情况下处于关闭状态，但可以打开和关闭任何时候。</p></li>
<li><p>收集性能数据的开销将比使用已在 D3D9 和 D3D10 + 中可用的时间戳查询技术不慢</p></li>
<li><p>可以直接命令列表和捆绑包中收集计时数据。 计时数据可启用/禁用在每个命令列表的基础上。</p></li>
<li><p>结果基于图块上的数据延迟呈现硬件出现如同它生成即时模式呈现的设备上。</p></li>
</ul>
</li>

<li><p><strong>时间戳的查询︰</strong></p>
<ul>
<li><p>D3D11 UAV 计数器、 流输出计数器和 D3D12 API 构造查询的简单映射必须产生通过相关的 D3D11 HLK 测试的结果。</p></li>
<li><p>D3D12 驱动程序必须正确地实现新的二进制遮蔽查询。</p></li>
<li><p>在着色器访问不存在的 UAV 计数器时，必须进行 GPU 页面错误。</p></li>
<li><p>动态索引的 UAV 计数器着色器必须能够正常工作</p></li>
<li><p>时间戳查询必须从事 3D 和计算命令队列。</p></li>
<li><p>Predication 必须适用于所有呈现操作 （包括那些包含在包中）</p></li>
<li><p>流输出、 UAV 计数器和 predication 缓冲区必须与所有的 D3D12 资源堆类型正常工作。</p></li>
</ul>
</li>

<li><p><strong>间接呈现︰</strong></p>
<ul>
<li><p>D3D12 驱动程序必须实现 GPU 的绘图调度，可间接 agument 缓冲区中。</p></li>
<li><p>具有任意间接参数缓冲区呈现应得到等价的一组 D3D12 命令列表 API 调用相同的结果。</p></li>
<li><p>必须在所有 D3D12 堆类型支持间接参数缓冲区。</p></li>
<li><p>必须支持任意字节的进步 （它们是 4 的倍数） 每个绘图结构之间。</p></li>
<li><p>单个命令列表生成间接参数缓冲区并使用该实例都必须能够正常工作 （驱动程序必须正确同步）。</p></li>
<li><p>D3D12 驱动程序必须 GPU 计算传递到驱动程序，MaxDrawCount 的最小值和 DrawCount 传递间接参数缓冲区中。</p></li>
</ul>
</li>

<li><p><strong>管道状态缓存︰</strong></p>

<ul>
<li><p>D3D12 驱动程序必须实现检索管道状态对象，着色器硬件本机代码的 DDIs 和 DDIs 用于重新构造此管道状态缓存着色器代码。</p></li>
<li><p>在 API 可用于构造任何管道状态必须是可缓存，包括计算管线。</p></li>
<li><p>使用来自缓存的着色器代码构造的管道状态必须产生比作一个从 HLSL 编译的字节码生成的相同的呈现结果。</p></li>
</ul>
</li>

</ol>


业务理由︰

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。  这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。


<a name="device.graphics.adapterrender.d3d12multiadapter"></a>
## <a name="devicegraphicsadapterrenderd3d12multiadapter"></a>Device.Graphics.AdapterRender.D3D12Multiadapter

### <a name="devicegraphicsadapterrenderd3d12multiadaptercorerequirement"></a>Device.Graphics.AdapterRender.D3D12Multiadapter.CoreRequirement

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

**说明︰**

显示驱动程序的 Direct3D12 必须具有足够的性能，在定义满足所有要求 

**Direct3D 12 规范**。

D3D12 显示驱动程序必须支持跨适配器共享的曲面，Direct3D 12 规范中所述。

如果在链接的显示适配器上运行的驱动程序，然后 Direct3D 12 链接适配器的功能是必需的。

注意︰ 此功能是强制自称 D3D12 兼容驱动程序的驱动程序。

**业务理由︰**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。 这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。

<a name="device.graphics.adapterrender.d3d12rasterizerorderedviews"></a>
## <a name="devicegraphicsadapterrenderd3d12rasterizerorderedviews"></a>Device.Graphics.AdapterRender.D3D12RasterizerOrderedViews

### <a name="devicegraphicsadapterrenderd3d12rasterizerorderedviewscorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12RasterizerOrderedViews.CoreRequirement （如果实现）

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

Direct3D12 的显示驱动程序必须实现 DDIs 与光栅订单视图︰

 - 正确排序操作对所有的 RasterizerOrdered\*类型

有关其他详细信息，请参阅[ROV 规范](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/ROVs%20-%20Unified%20Spec.docx?web=1)。

**业务理由︰**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。 这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。

<a name="device.graphics.adapterrender.d3d12stencilreference"></a>
## <a name="devicegraphicsadapterrenderd3d12stencilreference"></a>Device.Graphics.AdapterRender.D3D12StencilReference

### <a name="devicegraphicsadapterrenderd3d12stencilreferencecorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12StencilReference.CoreRequirement （如果实现）

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

**说明**︰

Direct3D12 的显示驱动程序必须实现 DDIs 与像素着色器模具参考相关︰

 - 将写入 SV\_STENCILREF 函数按预期的方式

有关其他信息，请参阅[PS-Specified 模具 Ref 规范](http://windowsteams/devx/GRFX/d3d/D3D%20Next%20Design/MQ%20Planning%20Documents/PS-Specified%20Stencil%20Reference%20Value%20-%20Unified%20Spec.docx?web=1)。

**业务理由︰**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。 这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。

<a name="device.graphics.adapterrender.d3d12typeduavloads"></a>
## <a name="devicegraphicsadapterrenderd3d12typeduavloads"></a>Device.Graphics.AdapterRender.D3D12TypedUAVLoads

### <a name="devicegraphicsadapterrenderd3d12typeduavloadcorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12TypedUAVLoad.CoreRequirement （如果实现）

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

Direct3D12 的显示驱动程序必须实现 DDIs 与键入的 UAV 加载︰

 - 如果设置类型化的 UAV 负载标志的所有所需的 UAV 格式支持类型化的负载
 - 还可以声明类型的支持类型的负载

有关详细信息，请参阅<a href="http://windowsteams/devx/GRFX/d3d/D3D Next Design/MQ Planning Documents/UAV Typed Load Draft Specification.docx?web=1">键入 UAV 负载</a>规范。


**业务理由**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。  这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。


<a name="device.graphics.adapterrender.d312volumetiledresources"></a>
## <a name="devicegraphicsadapterrenderd312volumetiledresources"></a>Device.Graphics.AdapterRender.D312VolumeTiledResources

### <a name="devicegraphicsadapterrenderd3d12volumetiledresourcescorerequirement-if-implemented"></a>Device.Graphics.AdapterRender.D3D12VolumeTiledResources.CoreRequirement （如果实现）

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

**说明**︰

报告对卷铺资源的支持 （通过公开铺资源第 3 层） 的驱动程序必须符合此 D3D IHV 规范中所述的功能的技术指标。 举例说明卷铺资源有趣指标详细信息是不同的图面格式卷铺资源中使用时所需的平铺形状。 此功能的所有其他行为属于铺资源的常规规格一般情况下，以及体积纹理一般情况下 – 因为此功能是两者的交集。

**业务理由︰**

用于实现 D3D12 DDI 所有显示驱动程序必须以一致的方式这样都做。 这使 D3D12 API 具有一致的行为，跨多个平台，这为 Isv 开发 PC/触/电话/XBOX 平台上的 3D 应用程序降低成本。

<a name="device.graphics.indirectdisplay.wired"></a>
## <a name="devicegraphicsindirectdisplaywired"></a>Device.Graphics.IndirectDisplay.Wired

*显示有线间接显示的功能要求。*

### <a name="devicegraphicsindirectdisplaywiredbase"></a>Device.Graphics.IndirectDisplay.Wired.Base

*有线的间接显示的要求。*

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

以间接方式显示是显示设备 （例如，监视） 连接到远程间接显示设备从符合 Microsoft 的间接显示发件人系统框架的用户模式驱动程序接收图像、 执行一些处理，然后在显示器上显示图像。

发件人的系统上显示图像需要以处理并传输到间接显示设备的 CPU 交互。 这种 CPU 交互可能直接操作只需编程的硬件来处理图像的图像。

一些示例包括但不是限于，通用坞站、 USB 显示连接器和显示器与 USB 显示功能。 

**常见的间接显示 DDIs**

间接显示必须实现所有必需的 DDI 列出 WDK 中间接显示驱动程序。

**要求︰**

**UMDF 和 DevFund 的要求︰**间接的显示驱动程序必须是 UMDF 驱动程序，并且必须遵守所有的 pertanent 设备 Fundemental 要求。 必须满足，但不是限于以下的 DevFund 驱动程序框架 UMDF 要求。

-   Device.DevFund.DriverFramework.UMDF

    -   Device.DevFund.DriverFramework.UMDF.Reliability

    -   Device.DevFund.DriverFramework.UMDF.WDFProperINF

**图形要求︰**间接的显示驱动程序必须遵守以下图形要求。

-   Device.Graphics.AdapterBase.PowerManagementCompliance-这应该来自于 USB 必需

-   Device.Graphics.AdapterBase.Symbols

-   Device.Graphics.WDDM.Display.GammaCorrection-（可选要求）

-   Device.Graphics.WDDM.Display.I2CSupport-（可选要求）

-   Device.Graphics.WDDM.Display.Multimon

-   Device.Graphics.WDDM12.Display.ContainerIDSupport

-   Device.Graphics.WDDM12.Display.ModeEnumeration

-   Device.Graphics.WDDM.DisplayRender.OutputProtection

HDCP 支持是可选的但该设备必须实现 OPM 并具有适当的 OPM 证书。

<a name="device.graphics.wddm"></a>
## <a name="devicegraphicswddm"></a>Device.Graphics.WDDM

*通过支持所有版本的 WDDM 驱动程序实现的基本功能集。*

### <a name="devicegraphicswddmbase"></a>Device.Graphics.WDDM.Base

*图形驱动程序必须实现每 WDDM 1.0 规范。*

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

作为 WDDM 1.0 规范所暗示的显示驱动程序必须至少支持 D3D9 和像素着色器 2.0。

WDDM 1.0 引入了以下关键要求︰

-   用户模式的显示驱动程序
-   视频内存管理器
  - (p1)线性的内存管理器
  - (p1)矩形的内存管理器
-   GPU 计划程序
-   体系结构清理模式切换
-   合并的微型端口和 DLL
-   从硬件挂起中恢复
-   简化的内核模式下的对象
-   传统的 DDI 整合
-   显示卡、 热插接，和对"克隆视图"支持热插拔

**MSDN 文档更新基于 WDDM 1.0 规范。请验证 WDDM 1.0 要求的 MSDN 文档。**

### <a name="devicegraphicswddmchecklist"></a>Device.Graphics.WDDM.Checklist

*所有图形设备必须都符合基本要求核对清单的图形卡，芯片组和驱动程序。*

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

所有的图形卡必须遵守下面的项目清单︰**内存分配和访问**（适用于所有的外形）

-   GPU 一定不能访问后提交到 GPU 引用分配，则报告为已完成的最后一次 DMA 缓冲区分配。

-   GPU 一定不能访问与正在执行的 DMA 缓冲区分配列表中未指定任何分配。

**卡/芯片组要求**（不适用于服务器的设备）

-   对于多向的显示适配器，建议所有的显示适配器公开显示通过单个函数，而不是多功能设备的资源。 如果声音控制器或调谐器设备的一部分，该设备可以然后公开为多功能设备。

<!-- -->

-   如果第二个显示类函数时暴露的旧版本兼容，适配器必须齐全而无需使用第二个头部。 第二个 （或更多） 职能领导必须︰

<!-- -->

-   有子类 80 （其他） 为了避免通用驱动程序正在使用。

-   不能扩展 rom。

-   大于 1 MB 的总内存空间资源的描述。

-   复制帧缓冲区资源。

-   描述任何中断资源。

-   描述任何 I/O 空间资源。

-   在同一设备上，例如多媒体设备类型、 子类视频设备或子类音频设备，非显示基类函数将不遵守这些限制。

**WDDM 驱动程序清单**（不适用于非 WDDM 驱动程序）

-   WDDM 驱动程序必须报告提交时限为直到真正完成相关联的提交操作已完成。 这是计划中的模型 WDDM 所必需的。 这样，Windows 的稳定性遭到破坏，WDDM 不得使用 DDI。

-   WDDM 驱动程序必须插入请求每个围栏围墙/中断对和必须不拖延报告该时限完成。 一旦关联所需的中断生成的 GPU，必须报告围墙。 例如，它必须等待直到计时器中断或直到下一个垂直同步。 这是计划中 DDM 模型所必需的。

-   不，WDDM 驱动程序必须等待或阻止 DdiSubmitCommand，在其中您只需在 WDDM 视频调度程序的角度来看。 驱动程序必须不等待或阻止在 DdiBuildPagingBuffer 调用的过程。

-   WDDM 驱动程序必须将每个物理引擎的多个节点不公开。 驱动程序和 GPU 无法安排一个物理引擎之间的多个节点。

-   WDDM 驱动程序必须将虚拟地址映射到直接向应用程序公开的视频内存。 这是视频内存管理支持 WDDM 驱动程序中的实现的基础。 不，WDDM 驱动程序必须隐藏或公开视频内存的视频内存管理器不了解的方式。
    专门针对 GPU （调试器、 探查器...） 的开发人员工具的实现允许到此异常。  此类异常必须仅适用于的方案的 GPU 开发人员工具，为了执行，需要将视频内存映射到虚拟地址空间，为会话的持续时间和仅应用程序正在对其进行操作的过程。

-   WDDM 驱动程序必须公开报告额外的视频内存，比其相应的使用实际上存在的目的使用任何内存段。 正确的视频内存量必须通过 Windows 的各种应用程序使用报告。 WDDM 驱动程序可以使用最多的系统内存的 5%用于内部如光标位图、 环形缓冲区等;不，上面的任何数额必须用于隐藏或公开方式的视频内存，以致不知道视频内存管理器。

-   WDDM 驱动程序必须使用 ACPI 系统 BIOS 与所有交互操作。 SMI 目前允许的但强烈建议不要通过 Microsoft。 WinHEC 2005 的演示文稿，请参阅*TWAR05007。*

*设计备注*

有关的详细信息部分中的项的详细信息，请参阅 Windows 驱动程序工具包和搜索的相关关键字。

### <a name="devicegraphicswddmgpufencecommands"></a>Device.Graphics.WDDM.GPUFenceCommands

*它占用的围墙命令时，能够处理命令队列中的围墙命令 GPU 必须触发给 CPU 中断。*

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

当硬件消耗围墙命令时，它必须通过触发与 CPU，围墙 id 传递给 ISR 中断通知操作系统

*设计备注*

请参阅 Windows 驱动程序工具包

<a name="device.graphics.wddm.display"></a>
## <a name="devicegraphicswddmdisplay"></a>Device.Graphics.WDDM.Display

*由驱动程序支持的所有版本的 WDDM 显示 DDIs 实现基本功能集。*

### <a name="devicegraphicswddmdisplaybase"></a>Device.Graphics.WDDM.Display.Base

*图形驱动程序必须实现 WDDM 1.0 规范。*

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

请参阅要求**Device.Graphics.WDDM.Base**
 

### <a name="devicegraphicswddmdisplaygammacorrection"></a>Device.Graphics.WDDM.Display.GammaCorrection

*图形适配器必须支持灰度校正硬件而无需使用任何其他图形内存带宽。*

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

执行附加的监视器伽玛矫正，并允许游戏应用程序切换调色板，ICM 使用能力。 此功能还支持在应用程序中的过渡效果。 支持 ICM、 显示适配器或芯片组必须以编程方式调整灰度系数。

若要在硬件中执行伽玛矫正，必须包含可下载 RAM DAC 项目 (LUT)。

LUT 必须实现每 8 位颜色通道的成分的分量视频输入至少 256 项。 硬件可实现更大的组件分辨率 LUT 如果使用至少 128 个采样点，通过插值。

这种能力必须支持无需图形内存带宽的使用。 这种能力必须支持 RGBA8888 和 RGBA1010102 的像素格式。
 

### <a name="devicegraphicswddmdisplayhotplugdetection"></a>Device.Graphics.WDDM.Display.HotPlugDetection

*图形适配器必须可靠地检测到连接和断开连接的显示设备的事件。*

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

Windows 支持显示检测的可中断和轮询可以两个的级别。

-   可中断被指能够自动检测中显示连接的更改并将其报告给 Windows 图形适配器的情况。 硬件的自动生成显示连接更改中断的能力被称为热插拔检测 (HPD)。 HPD 不得导致任何显示已连接到系统上任何视觉损坏。

-   轮询可以被定义为 Windows 不得不显式查询中显示连接的图形适配器对查询的更改的位置的情况。 在某些情况下，视觉损坏可能显示在非常短暂的时间。

  
所有标准数字接头 (DisplayPort，HDMI，DVI) 支持 HPD 和图形适配器必须报告作为中断这些连接器。 一旦硬件生成中断，图形适配器必须通知 Windows 通过 DxgkCbIndicateChildStatus 在此处找到的 DDI: <http://msdn.microsoft.com/en-us/library/ff559522.aspx>。

模拟接口 （HD-15、 S-视频、 组件、 复合） 不需要支持可中断显示检测。 但是，有可能，可以在硬件中实现 HPD （例如，加载感应，I2C） 这种连接器。 在这种情况下，图形适配器必须报告与上面一样中断此连接器。 不能使用软件轮询来实现模拟接头的 HPD 功能。

对于那些模拟连接器，其中 HPD 未实现的硬件中，图形适配器必须报告连接器，为轮询。 在这种情况下，图形适配器必须只执行检测 Windows D3DKMTPollDisplayChildren DDI，此处找到通过显式请求时连接器上︰ <http://msdn.microsoft.com/en-us/library/ff547077.aspx>。

*设计备注*

请参阅 Windows 驱动程序工具包︰ <http://msdn.microsoft.com/en-us/library/ff559522.aspx>为"DxgkCbIndicateChildStatus"。

以下的 HPD 方法是 VESA 标准︰ DVI HPD 享有在 VESA 插即用 (PnP) 标准/图形显示子系统、 发行 A.DisplayPort HPD 涵盖 DisplayPort 标准的所有版本中。

### <a name="devicegraphicswddmdisplayi2csupport"></a>Device.Graphics.WDDM.Display.I2CSupport

*图形设备驱动程序必须具有 WDDM I2C 支持。*

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

下面是每个 WDDM 驱动程序是必需为 I2C 支持实现的接口集︰

 - DxgkDdiI2CReceiveDataFromDisplay
 - DxgkDdiI2CTransmitDataToDisplay

这些接口都记录在 WDK 并可以在以下位置找到︰ <http://msdn.microsoft.com/en-us/library/ff567386.aspx>。


### <a name="devicegraphicswddmdisplaymultimon"></a>Device.Graphics.WDDM.Display.Multimon

*如果图形适配器可以支持多个源和一个目标，它必须在 Windows 支持多监视器的所有配置。*

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

源和目标，根据其能力，可以枚举的图形驱动程序。 Windows 通过调用 DxgkDdiEnumVidPnCofuncModality DDI，这里找到<http://msdn.microsoft.com/en-us/library/ff559649.aspx>查询的源和目标数的驱动程序。 Windows 支持以下监视器配置︰

-   单个监视器配置-只有一个物理显示器处于活动状态，并且整个桌面显示在其上。

-   扩展的监视器配置的多台监视器中处于活动状态并在其上显示桌面的不同部分。 这样等最大化 Windows 功能、 毛玻璃管理单元等工作按照规范都必须进行 GDI 意识的显示器的边界。

-   复制监视器配置的多个监视器显示的内容完全相同的桌面。

目标数必须大于或等于源的个数。

如果驱动程序枚举恰好有一个源和一个目标，要支持没有多显示器配置。

如果驱动程序枚举恰好有一个源和多个目标，然后驱动程序必须支持单个监视器和重复监视程序的配置。

如果多个源和多个目标，将枚举驱动程序，驱动程序必须支持所有受支持的配置。 另外︰

-   当启用 itsself，相对于分辨率，Direct 3D，受保护的内容播放，通过每个源的功能应该是相同的。 目标的能力的差异取决于目标的类型。

-   尽管该驱动程序可以限制哪些目标可以驱动组合，操作系统必须能够推动来自任何来源、 任何目标。

多监视器支持是 Windows 内置的;因此，图形驱动程序必须不包括任何特殊的代码来提供已在操作系统中可用的支持。

它必须能够为用户设置支持使用 Windows 控制面板显示所有配置并按下 Win + P 组合键。

<a name="device.graphics.wddm.displayrender"></a>
## <a name="devicegraphicswddmdisplayrender"></a>Device.Graphics.WDDM.DisplayRender

*通过显示和呈现 DDIs 支持的所有版本的 WDDM 驱动程序实现的基本功能集。*

### <a name="devicegraphicswddmdisplayrenderbase"></a>Device.Graphics.WDDM.DisplayRender.Base

*图形驱动程序必须实现 WDDM 1.0 规范。*

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

请参阅要求**Device.Graphics.WDDM.Base**

### <a name="devicegraphicswddmdisplayrenderdriversetupcompatible"></a>Device.Graphics.WDDM.DisplayRender.DriverSetupCompatible

*图形驱动程序必须实现 WDDM 1.0 规范。*

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

提交以供过帐到 Windows 更新目标 Windows 客户端 Sku 在注入到 Windows 操作系统映像的驱动程序必须正确安装的所有 WDDM 图形驱动程序将都存储在操作系统安装过程中。

### <a name="devicegraphicswddmdisplayrenderoutputprotection"></a>Device.Graphics.WDDM.DisplayRender.OutputProtection

*显示适配器必须支持输出接口内容保护功能，并提供通过保护介质路径输出保护管理器 (PVP OPM) 和认证输出保护协议 (COPP) 的控件。*

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

若要启用高级视频内容的播放，数字视频输出接口必须支持数字显示器链路的保护机制，如 HDCP 获取 Windows 8 客户端徽标。 这一要求是适用于所有的完整图形设备。

OPM API 和媒体基础 PMP 需要显示驱动程序正确实施 OPM DDIs 处理高级内容。 显示驱动程序不包含 PVP OPM 证书，高年级高级内容将不会传递到显示驱动程序。 支持 OPM DDIs 的驱动程序必须使用驱动程序的证书能够证实均已满足法规遵从性规则、 稳定性规则和 PVP OPM 的合法协议中的条款。
显示驱动程序必须支持这两种 COPP\*和 PVP OPM 驱动程序接口，用于控制和信号传输的视频输出的保护状态。

由 PVP OPM 的法规遵从性规则指定输出保护行为。  该文档可供图形通过向 wmla@microsoft.com 发送请求的供应商。

WDDM 驱动程序必须实现所需的显示模式管理 DDIs，并在 Windows 驱动程序工具包以及 WDDM 文档启用播放电视节目和内容保护模拟 (ACP) 中所述的结构支持 Media Center\*。

D3DKMDT\_VIDPN\_存在\_路径\_内容︰ Media center 将使用此信息来更改电视模式 (电视\_播放与 WIN\_图形)

D3DKMDT\_VIDPN\_存在\_路径\_COPYPROTECTION\_类型和 D3DKMDT\_VIDPN\_存在\_路径\_COPYPROTECTION\_支持︰ 这些结构是否有必要提供 ACP 通过 LDDM 驱动程序的支持。

S-video 和复合视频输出接口必须支持︰

 - CGMS A 行 20 上按照 IEC 61880
 - CGMS-A 线 21 由 EIA-608-B

分量 (YPbPr) 输出必须支持︰

 - 重新分发控件所指定的 EIA 805 的 CGMS A

当启用 tv-out 接口时，显示驱动程序必须公开 720 x 480 60 Hz 显示模式和/或 720 x 576 50 赫兹显示模式。 这些显示模式必须公开的视频微型端口并添加到 Windows 应用程序连接到标准清晰度电视时设置默认排练时间列表。

支持 SDTV 模式︰<br/>
WDDM 微型端口驱动程序必须将此参数设置为 TRUE，以公开与 NTSC 和 PAL 和 SECAM SDTV 模式的视频输出。

用 CableCARD 支持数字视频输出 （例如 HDMI 或 DP） 与有线电视就绪系统必须支持 HDCP 如 CableLabs 批准数字显示器链路保护机制。

 
*设计备注*

-   S-video 和复合视频输出接口可以通过相同的连接器来实现。 如果使用专有接口，则适配器必须可供既包含系统或可在零售点购买。 系统或使用 S-视频 7 针接头的设备不需要提供的适配器，只要前四个 7 针接头针脚是电与标准 4 针 S 视频接口兼容。 Microsoft 建议包括 SCART 输出时适用于该地区的销售。

-   \*COPP，ACP，CGMS A、 模拟 TV 输出和 SDTV 支持 x86 和 x64 体系结构和操作系统的系统要求。

### <a name="devicegraphicswddmdisplayrenderstability"></a>Device.Graphics.WDDM.DisplayRender.Stability

*所有 WDDM 图形驱动程序必须生成任何挂起或在长时间的压力情况下的故障。*

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

图形驱动程序必须正常运行，并不会生成任何挂起或整个工期压力测试的"4 小时 WDDM 配置"中指定的错误。

以"压力"的图形驱动程序，软件和硬件 （崩溃） 的比较可靠性分析器启动，并终止其他测试应用程序来模拟实际的方案。

<a name="device.graphics.wddm.render"></a>
## <a name="devicegraphicswddmrender"></a>Device.Graphics.WDDM.Render

*由驱动程序支持的所有版本的 WDDM 呈现 DDIs 实现基本功能集。*

### <a name="devicegraphicswddmrenderbase"></a>Device.Graphics.WDDM.Render.Base

*图形驱动程序必须实现 WDDM 1.0 规范。*

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

请参阅要求**Device.Graphics.WDDM.Base**

### <a name="devicegraphicswddmrendervideodecoding"></a>Device.Graphics.WDDM.Render.VideoDecoding

*显示驱动程序必须支持 DirectX VA 2.0 视频解码器 DDI。*

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

显示 WDDM 驱动程序必须支持以下 DXVA 2.0 视频解码器 DDI。

WDDM 驱动程序必须支持 DXVA 以下模式︰

-   DXVA\_ModeH264\_VLD

-   DXVA2\_ModeVC1\_D 或 DXVADDI\_ModeVC1\_D2010

如果硬件支持的 MPEG2 加速，WDDM 驱动程序支持以下 MPEG2 Guid 集至少︰

-   DXVA2\_ModeMPEG2\_VLD 和 DXVA2\_ModeMPEG2\_iDCT

-   DXVA2\_ModeMPEG2\_VLD 和 DXVA2\_ModeMPEG2\_MoComp

-   DXVA2\_ModeMPEG2\_iDCT

-   DXVA2\_ModeMPEG2and1\_VLD

如果硬件支持 H.265 加速，它必须支持 HEVC/H.265 模式︰

-   D3D11\_解码器\_配置文件\_HEVC\_VLD\_主

-   D3D11\_解码器\_配置文件\_HEVC\_VLD\_MAIN10 （可选如果硬件不支持 Main10 配置文件）

强烈建议对于驱动程序支持 D3D11\_解码器\_配置文件\_HEVC\_VLD\_MAIN10，作为主 10 是很常见的高级 HEVC 内容格式。

如果硬件支持 VPx 加速，它必须支持 VPx 模式︰

-   D3D11\_解码器\_配置文件\_VP8\_VLD

-   D3D11\_解码器\_配置文件\_VP9\_VLD\_PROFILE0

-   D3D11\_解码器\_配置文件\_VP9\_VLD\_PROFILE2 （如果硬件不支持配置文件 2 可选）

WDDM 驱动程序必须支持 DXGI\_格式\_420\_透明，DXGI\_格式\_NV12 解码器作为输出格式。 NV12 适用于需要着色器互操作方案。 HEVC 主 10，驱动程序必须支持 DXGI\_格式\_P010 解码器作为输出格式。

如果显示适配器支持硬件加速解码 H.264 的它必须支持任一 DXVA\_ModeH264\_MoComp GUID 或 DXVA\_ModeH264\_VLD GUID。

如果显示适配器支持硬件加速的 HEVC 解码，则它必须支持 DXVA\_ModeHEVC\_VLD\_主 GUID。

最后，WDDM 驱动程序必须支持标准化的 AES 128 H.264\* \* \*和 MPEG2，如果支持 MPEGE2 加速。

*设计备注*

\*\*\*标准化的 AES 128 支持 x86 和 x64 体系结构和操作系统的系统要求。

### <a name="devicegraphicswddmrendervideoprocessing-if-implemented"></a>Device.Graphics.WDDM.Render.VideoProcessing （如果实现）

*显示 WDDM 驱动程序必须支持 DirectX VA 2.0 视频处理器 DDI。*

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

如果实现，显示 WDDM 驱动程序必须支持 DXVA 2.0 视频处理器 DDI 和下面的视频处理器设备 Guid 的支持︰

-   DXVADDI\_VideoProcProgressiveDevice
-   DXVADDI\_VideoProcBobDevice

必须为每个视频处理器设备 Guid 支持下面的 DXVA2 视频处理器大写︰

-   DXVADDI\_VIDEOPROCESS\_YUV2RGB
-   DXVADDI\_VIDEOPROCESS\_YUV2RGBEXTENDED
-   DXVADDI\_VIDEOPROCESS\_STRETCHX
-   DXVADDI\_VIDEOPROCESS\_STRETCHY
-   DXVADDI\_VIDEOPROCESS\_SUBRECTS
-   DXVADDI\_VIDEOPROCESS\_SUBSTREAMS
-   DXVA2\_VideoProcess\_SubStreamsExtended
-   DXVA2\_VideoProcess\_Constriction

另外，为支持 DXVADDI\_VIDEOPROCESS\_YUV2RGBEXTENDED 帽下面的颜色参数必须是支持时颜色空间从 YUV 曲面转换为 RGB 曲面︰

-   D3DDDIARG\_VIDEOPROCESSBLT。DestFormat.NominalRange

    -   DXVADDI\_NominalRange\_未知 (应解释为 0\_255 如果不实现复杂的算法)
    
    -   DXVADDI\_NominalRange\_0\_255
    
    -   DXVADDI\_NominalRange\_16\_235

-   D3DDDIARG\_VIDEOPROCESSBLT.pSrcSurfaces\[\]。SampleFormat.VideoTransferMatrix

    -   DXVADDI\_VideoTransferMatrix\_（应解释为 BT601 除非源图面大于 576 的高度，在这种情况下应解释为 BT709） 的未知

    -   DXVADDI\_VideoTransferMatrix\_BT709

    -   DXVADDI\_VideoTransferMatrix\_BT601

必须以视频流的形式支持以下 YUV 格式︰

-   YUY2-8 位压缩 4:2:2
-   NV12-8 位平面 4:2:0

如果视频处理器支持 10 位 YUV 次像素采样，必须支持以下相应的格式︰

-   Y210-10 位压缩 4:2:2
-   Y410-10 位压缩 4:4:4
-   P210-10 位平面 4:2:2
-   P010-10 位平面 4:2:0

如果视频处理器支持 16 位 YUV 格式，必须支持以下格式︰

-   Y216-16 位压缩 4:2:2
-   Y416-16 位压缩 4:4:4
-   P216-16 位平面 4:2:2
-   P016-16 位平面 4:2:0

作为视频子流必须支持 YUV 格式如下︰

-   AYUV-8 位压缩 4:4:4

对于这些格式，颜色转换 YUV 到 RGB blits VideoProcessBlt 函数通过运行至少必须能够使用 BT. 601 和 BT. 709 转换矩阵。 此过程使图形以不同的颜色格式，以确保正确处理源自不同的标准颜色空间，例如 ITU-R 建议 BT.中所定义的视频 YUV 到 RGB 矩阵变换之间切换 601 和 BT.709，是必需的。

容差阈值︰ 50dB 的参考模式和 DXVAHD 模式之间的质量差异

-   颜色转换支持播放、 编码转换和捕获方案如下︰

    -   NV12-&gt;ARGB32
    -   YUY2-&gt;ARGB32
    -   ARGB32-&gt;NV12 （全摆和 studio 摆动）
    -   420O-&gt;NV12
    -   420O-&gt;ARGB32
    -   AYUV-&gt;NV12

-   重新缩放对于上述转换的支持

-   旋转支持

-   扩展的范围 （全摆） 支持编码转换和捕获方案

在连接在所述支持更新存在 DX9 和 DX10 + 用户模式 DDIs: <https://connect.microsoft.com/site1304/Downloads/DownloadDetails.aspx?DownloadID=47236>。

<a name="device.graphics.wddm11"></a>
## <a name="devicegraphicswddm11"></a>Device.Graphics.WDDM11

*通过支持 WDDM 1.1 驱动程序实现的基本功能集。*

### <a name="devicegraphicswddm11base"></a>Device.Graphics.WDDM11.Base

*面向离散图形适配器或集成的图形适配器设备的图形驱动程序必须满足 WDDM 1.1 规范中定义的所有要求。*

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

WDDM 1.1 介绍通过 WDDM 1.0 以下关键要求︰

-   选择 GDI 功能的硬件加速。

-   连接和配置显示 DMM DDIs 的实现

-   对 GDI 兼容 32 位 BGRA 像素格式的支持。 （通过 DirectX10 和更高版本的 DDIs。）

-   提供其他信息以帮助进行调试的垂直同步 TDRs。

-   必须编译内核模式驱动程序与框架指针优化 (FPO) 被禁用。

-   可选的功能，根据规范和 WDK 的文档，包括标准化 AES128、 DXVA HD、 叠加和 Direct3D11 必须合并如果实现。

**MSDN 文档更新基于 WDDM 1.1 规范。请对于 WDDM 1.1 要求，参考 MSDN 文档。**

<a name="device.graphics.wddm11.display"></a>
## <a name="devicegraphicswddm11display"></a>Device.Graphics.WDDM11.Display

*由驱动程序支持的所有版本的 WDDM 显示 DDIs 实现基本功能集。*

### <a name="devicegraphicswddm11displaybase"></a>Device.Graphics.WDDM11.Display.Base

*为离散图形适配器或集成的图形适配器设备编写图形驱动程序必须满足 WDDM 1.1 规范中定义的所有要求。*

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

请参阅要求**Device.Graphics.WDDM11.Base**

<a name="device.graphics.wddm11.displayrender"></a>
## <a name="devicegraphicswddm11displayrender"></a>Device.Graphics.WDDM11.DisplayRender

*通过显示和呈现 DDIs 支持的所有版本的 WDDM 驱动程序实现的基本功能集。*

### <a name="devicegraphicswddm11displayrenderbase"></a>Device.Graphics.WDDM11.DisplayRender.Base

*面向离散图形适配器或集成的图形适配器设备的图形驱动程序必须满足 WDDM 1.1 规范中定义的所有要求。*

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

请参阅要求**Device.Graphics.WDDM11.Base**

<a name="device.graphics.wddm11.displayrender.d3d9overlay"></a>
## <a name="devicegraphicswddm11displayrenderd3d9overlay"></a>Device.Graphics.WDDM11.DisplayRender.D3D9Overlay

*由 WDDM 1.1 驱动程序，并更好地允许曲面在硬件覆盖中呈现的可选功能。*

### <a name="devicegraphicswddm11displayrenderd3d9overlayd3d9overlay"></a>Device.Graphics.WDDM11.DisplayRender.D3D9Overlay.D3D9Overlay

*WDDM1.1 驱动程序必须支持 Direct3D 9 叠加。*

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

如果 WDDM1.1 驱动程序支持 Direct3D 9 贴，视频覆盖图演示文稿要求如下所示︰

-   WDDM 1.1 版驱动程序必须设置 D3DCAPS\_D3DCaps9.Caps 字段中的重叠位。

-   WDDM 1.1 版驱动程序必须支持的查询类型 D3DDDICAPS\_CHECKOVERLAYSUPPORT pfnGetCaps DDI 调用的用户模式。

-   WDDM 1.1 版驱动程序必须支持叠加中至少一个有效的配置 （Displaymode、 OverlayFormat、 宽度和高度） 时调用此函数以 DDICHECKOVERLAYSUPPORTDATA 为支持覆盖的最大宽度和高度支持覆盖必须大于零。

<a name="device.graphics.wddm11.render"></a>
## <a name="devicegraphicswddm11render"></a>Device.Graphics.WDDM11.Render

*由驱动程序支持的所有版本的 WDDM 呈现 DDIs 实现基本功能集。*

### <a name="devicegraphicswddm11renderbase"></a>Device.Graphics.WDDM11.Render.Base

*面向离散图形适配器或集成的图形适配器设备的图形驱动程序必须满足 WDDM 1.1 规范中定义的所有要求。*

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

请参阅要求**Device.Graphics.WDDM11.Base**

<a name="device.graphics.wddm11.render.dxvahd"></a>
## <a name="devicegraphicswddm11renderdxvahd"></a>Device.Graphics.WDDM11.Render.DXVAHD

*可选功能，通过支持新的基于状态的视频处理 DDIs WDDM 1.1 驱动程序实现的。*

### <a name="devicegraphicswddm11renderdxvahddxvahd"></a>Device.Graphics.WDDM11.Render.DXVAHD.DXVAHD

*WDDM1.1 驱动程序支持 DXVA 高清*

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

如果 WDDM1.1 驱动程序支持 DXVA HD，以下输入格式 (D3DDDICAPS\_DXVAHD\_GETVPINPUTFORMATS) 必须支持︰

-   YUY2
-   AYUV
-   NV12
-   X8R8G8B8
-   A8R8G8B8

该驱动程序还必须支持下列输出格式 (D3DDDICAPS\_DXVAHD\_GETVPOUTPUTFORMATS):

-   X8R8G8B8
-   A8R8G8B8



<a name="device.graphics.wddm12"></a>
## <a name="devicegraphicswddm12"></a>Device.Graphics.WDDM12

*通过支持 WDDM 1.2 驱动程序实现的基本功能集。*

### <a name="devicegraphicswddm12base"></a>Device.Graphics.WDDM12.Base

*图形驱动程序必须按照 WDDM 1.2 规范来实现。*

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

<html>
    <p>
WDDM v1.2 是 WDDM 1.1 和 WDDM 1.0 的超集。  <br />
这些 WDDM 版本，以下是摘要︰    </p>
    <table>
        <thead>
            <tr class="header">
                <th>操作系统</th>
                <th>受支持的驱动程序模型</th>
                <th>D3D 版本支持</th>
                <th>启用的功能</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Windows Vista</td>
                <td>
WDDM 1.0<br />
在服务器和有限的 UMPC XDDM                </td>
                <td>D3D9 D3D10</td>
                <td>调度、 内存管理、 容错、 D3D9 &amp; 10</td>
            </tr>
            <tr class="even">
                <td>Windows Vista SP1 / Windows 7 客户端包</td>
                <td>
WDDM 1.05<br />
XDDM Server 2008 上                </td>
                <td>D3D9，D3D10 D3D10.1</td>
                <td>+ 在 D3D10，D3D 10.1 BGRA 支持</td>
            </tr>
            <tr class="odd">
                <td>Windows 7</td>
                <td>
WDDM 1.1<br />
在 Server 2008 R2 上的 XDDM                </td>
                <td>D3D9，D3D11 D3D10，D3D10.1，</td>
                <td>
GDI 的硬件加速<br />
连接和配置显示，DXVA HD D3D11                </td>
            </tr>
            <tr class="even">
                <td>Windows 8</td>
                <td>WDDM 1.2</td>
                <td>D3D9、 D3D10、 D3D10.1、 D3D11、 D3D11.1</td>
                <td>
平滑旋转，<br />
三维立体声，<br />
D3D11 视频<br />
GPU 抢占<br />
TDR 的改进<br />
诊断的改进，<br />
性能和内存使用情况的优化，<br />
电源管理<br />
等。
                </td>
            </tr>
        </tbody>
    </table>

    <p>WDDM v1.2 also introduces new types of graphics drivers, targeting specific scenarios and is described below:</p>
    <ul>
        <li><p>WDDM Full Graphics Driver: This is the full version of the WDDM graphics driver that supports hardware accelerated 2D &amp; 3D operations. This driver is fully capable of handling all the render, display, and video functions. WDDM 1.0 and WDDM 1.1 are full graphics drivers. All Windows 8 client systems must have a full graphics WDDM 1.2 device as the primary boot device.</p></li>
        <li><p>WDDM Display Only Driver: This driver is only supported as a WDDM 1.2 driver and enables IHVs to write a WDDM based kernel mode driver that is capable of driving display only devices. The OS handles the 2D or 3D rendering using a software simulated GPU.</p></li>
        <li><p>WDDM Render Only Driver: This driver is only supported as a WDDM 1.2 driver and enables IHVs to write a WDDM driver that supports only rendering functionality. Render only devices are not allowed as the primary graphics device on client systems.</p></li>
    </ul>
    <p>Table below explains the scenario usage for the new driver types:</p>
    <table>
        <thead>
            <tr class="header">
                <th> </th>
                <th>Client</th>
                <th>Server</th>
                <th>Client running in a Virtual Environment</th>
                <th>Server Virtual</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Full Graphics</td>
                <td>Required as boot device</td>
                <td>Optional</td>
                <td>Optional</td>
                <td>Optional</td>
            </tr>
            <tr class="even">
                <td>Display Only</td>
                <td>Not allowed</td>
                <td>Optional</td>
                <td>Optional</td>
                <td>Optional</td>
            </tr>
            <tr class="odd">
                <td>Render Only</td>
                <td>Optional as non primary adapter</td>
                <td>Optional</td>
                <td>Optional</td>
                <td>Optional</td>
            </tr>
            <tr class="even">
                <td>Headless</td>
                <td>Not allowed</td>
                <td>Optional</td>
                <td>N/A</td>
                <td>N/A</td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>WDDM v1.2 Feature caps</strong>
    </p>
    <p>The table below lists the requirements for a WDDM v1.2 driver to specify to Windows the WDDM Driver Type, version, and the feature caps (visible to dxgkrnl) that WDDM v1.2 drivers are required to set. If a driver has wrongfully claimed itself as &quot;WDDM v1.2&quot; or has implemented partial features (only some of the mandatory features), then it will fail to create an adapter and the system will fall back to the Microsoft Basic Display Driver.</p>
    <p><strong>WDDM Driver Requirements</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th>WDDM driver type</th>
                <th>DDI requirements</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>Full Graphics</td>
                <td>Implement all the Render-specific and the Display-specific required DDIs</td>
            </tr>
            <tr class="even">
                <td>Display-Only</td>
                <td>Implement all the Display-specific DDIs and return a null pointer for all the Render-specific DDIs</td>
            </tr>
            <tr class="odd">
                <td>Render-Only</td>
                <td>
                    Implement all the Render-specific DDIs and return a null pointer for all the Display-specific DDIs<br />
                    <strong>OR</strong><br />
                    Implement all the DDIs for a full WDDM driver but report DISPLAY_ADAPTER_INFO::NumVidPnSources = 0 and DISPLAY_ADAPTER_INFO::NumVidPnTargets = 0
                </td>
            </tr>
        </tbody>
    </table>
    <p>
        <br />
        <strong>WDDM v1.2 Feature Caps</strong>
    </p>
    <table>
        <thead>
            <tr class="header">
                <th>Feature</th>
                <th>WDDM Driver Type</th>
                <th>Feature Caps</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td> </td>
                <td> <strong>Full Graphics</strong></td>
                <td><strong>Render Only</strong></td>
            </tr>
            <tr class="even">
                <td>WDDM version</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="odd">
                <td>Bugcheck and PnP Stop support for Non VGA</td>
                <td><strong>M</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="even">
                <td>Optimized screen rotation Support</td>
                <td><strong>M</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="odd">
                <td>GPU Preemption</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="even">
                <td>FlipOnVSyncMmIo</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="odd">
                <td>TDR Improvements</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="even">
                <td>Optimizing the graphics stack to improve performance on sleep &amp; resume</td>
                <td><strong>O</strong></td>
                <td><strong>O</strong></td>
            </tr>
            <tr class="odd">
                <td>Stereoscopic 3D: New infrastructure to process and present stereoscopic content</td>
                <td><strong>O</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="even">
                <td>DirectFlip</td>
                <td><strong>M</strong></td>
                <td><strong>NA</strong></td>
            </tr>
            <tr class="odd">
                <td>GDI Hardware acceleration (This is a required WDDM v1.1 feature)</td>
                <td><strong>M</strong></td>
                <td><strong>M</strong></td>
            </tr>
            <tr class="even">
                <td>GPU power management of idle and active power</td>
                <td><strong>O</strong></td>
                <td><strong>O</strong></td>
            </tr>
        </tbody>
    </table>
</html>

<a name="device.graphics.wddm12.display"></a>
## <a name="devicegraphicswddm12display"></a>Device.Graphics.WDDM12.Display

*显示所有显示的 WDDM12 驱动程序的功能要求特定的 DDIs*

### <a name="devicegraphicswddm12displaybase"></a>Device.Graphics.WDDM12.Display.Base

*要求以支持 WDDM 图形适配器显示功能*

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

WDDM 已得到扩展，以支持 WDDM 驱动程序，它只负责扫描显示出能力。 这些驱动程序不可以支持任何呈现功能。

如果它实现下面的 DDIs，一个驱动程序被视为仅 WDDM 显示驱动程序。
 

**公共 WDDM DDIs**

这些 DDIs 是针对常见的设备功能，例如支持即插即用和电源支持。 这些功能所需的所有 WDDM 驱动程序，并且如果未实现，不会被驱动程序启动 windows。 这些 DDIs 都已[记录在 WDK](http://msdn.microsoft.com/en-us/library/ff554066.aspx)。

**必填：**

 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**可选︰**

 - DxgkDdiInterruptRoutine\*
 - DxgkDdiDpcRoutine
 - DxgkDdiNotifyAcpiEvent
 - DxgkDdiQueryInterface
 - DxgkDdiControlEtwLogging
 - DxgkDdiEscape
 - DxgkDdiCollectDbgInfo

\***DxgkDdiInterruptRoutine**函数是必需的如果当前的硬件设备报告硬件中断。 在这种情况下，如果驱动程序未提供此 DDI 函数，操作系统就会失败初始化。 如果当前的硬件没有硬件中断驱动程序提供此 DDI 函数，操作系统仍将允许将加载此驱动程序，则不会调用 DxgkDdiInterruptRoutine。

\***DdiNotifyAcpiEvent**DDI 函数用于通知在某些 ACPI 事件的图形驱动程序。 它是可选的呈现的设备。 在普通 WDDM 图形设备上，此 DDI 函数将返回一个标志来指示 dxgkrnl.sys 采取一些进一步的动作，如重置显示模式或轮询连接的监视器。 用于呈现唯一的设备，这些标志未使用，必须设置为零。
 

**显示仅 DDIs**

下面的 DDI 函数需要通过仅显示驱动程序来实现。 如果驱动程序不提供所有这些 DDIs，Windows 将无法初始化该驱动程序。

 - DxgkDdiQueryChildRelations
 - DxgkDdiQueryChildStatus
 - DxgkDdiQueryDeviceDescriptor
 - DxgkDdiResetDevice
 - DxgkDdiQueryAdapterInfo
 - DxgkDdiSetPalette\*
 - DxgkDdiSetPointerPosition\*\*
 - DxgkDdiSetPointerShape\*\*
 - DxgkDdiIsSupportedVidPn
 - DxgkDdiRecommendFunctionalVidPn\*\*\*
 - DxgkDdiEnumVidPnCofuncModality
 - DxgkDdiSetVidPnSourceVisibility
 - DxgkDdiCommitVidPn
 - DxgkDdiUpdateActiveVidPnPresentPath
 - DxgkDdiRecommendMonitorModes
 - DxgkDdiGetScanLine
 - DxgkDdiQueryVidPnHWCapability
 - DxgkDdiPresentDisplayOnly
 - DxgkDdiReleasePostDisplayOwnership
 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite
 - DxgkDdiI2CReceiveDataFromDisplay
 - DxgkDdiI2CTransmitDataFromDisplay

\***DxgkDdiSetPalette**是必需的 DDI。 如果驱动程序不支持任何组件面板模式，它仍应提供此 DDI。

\*\***DxgkDdiSetPointerPosition**和**DxgkDdiSetPointerShape**是必需的 DDIs。 如果驱动程序不支持任何硬件光标，它仍应提供这些两个 DDIs。

\*\*\***DxgkDdiRecommendFunctionalVidPn**是必需的 DDI。 如果驱动程序不支持 ACPI 的任何事件，它仍应提供此 DDI。

### <a name="devicegraphicswddm12displaycontaineridsupport"></a>Device.Graphics.WDDM12.Display.ContainerIDSupport

*图形适配器必须支持 DDI 容器 id。*

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

图形适配器必须实现**DxgkDdiGetDeviceContainer** DDI。 Windows 会使用此 DDI 来驱动程序寻找容器 id。 驱动程序必须尝试并从显示硬件获取容器 ID。

如果显示设备不提供容器 ID，Windows 将自动制造用于显示一个容器的 ID。 通过使用制造 ID、 产品 ID 和序列号显示来自 EDID 的实现容器 ID 的唯一性。 使用此信息，另一个设备的驱动程序可以使用 RtlGenerateClass5Guid 函数 wdm.h 中包含生成与显示设备相同的容器 ID。

### <a name="devicegraphicswddm12displaydisplayoutputcontrol"></a>Device.Graphics.WDDM12.Display.DisplayOutputControl

*支持 WDDM WDDM 驱动程序正在运行时将控件的显示输出*

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

没有需要从显示控件窗口和 WDDM 图形驱动程序之间更加无缝的手。 这意味着，在某些情况下，Windows 需要显示扫描出的控制权而无为即插即用停止 WDDM 驱动程序。

一个此类方案时，Windows 需要错误检查系统，并显示蓝屏。 这套 DDIs 关闭使该清洗手。

下面的 DDIs 被要求完全和仅显示 WDDM 1.2 驱动程序实现。

 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite

这些 DDIs 是[WDK 上这里记载](http://msdn.microsoft.com/en-us/library/ff554066.aspx)︰ <http://msdn.microsoft.com/en-us/library/ff554066.aspx>。

以下是实现这些 DDIs 同时 WDDM 驱动程序的要求︰

-   当 Windows 调用 DxgkDdiSystemDisplayEnable 时，驱动程序必须取消所有 GPU 操作或将 GPU 重置为空闲状态。

-   Windows 将提供一个目标 ID 作为 DDI 调用的一部分。 驱动程序必须继续推动显示与目标 id。

    -   驱动程序必须检查连接情况的显示提供目标 id。 如果指定目标没有显示器已连接，驱动程序应失败状态此调用\_不\_支持。

    -   驱动程序必须禁用所有其他显示器连接至目标 ID 除适配器提供的信号。

        -   如果这是不可能的应该尝试驱动程序并将其置于所有其他显示一个空白图像。

        -   如果这是不可能的驱动程序必须将最后的图像保留在屏幕上保持不变。

-   为所选的目标 ID，驱动程序必须保留的当前显示模式并作为 DDI 调用的一部分回 Windows 提供这种模式。

    -   如果驱动程序不能维护的当前模式或目标 ID 不活动拓扑的一部分，驱动程序应尝试并设置显示器的本机分辨率或高分辨率模式。 最起码，驱动程序必须重设为大于或等于 640 x 480 24 位颜色格式保存在指定的目标模式。

    -   它不是必需的驱动程序应该使用线性帧缓冲区模式。 但该驱动程序应支持写操作从 D3DDDIFMT\_A8R8G8B8 源到此帧缓存器。

-   高 IRQL 级别或系统进行错误检查后，可能会调用此函数。 驱动程序应将此功能设置非分页的代码部分中，只能使用的非分页内存。

    -   调用此函数时，Windows 内核模式功能可能不可用。

-   一旦驱动程序已交给在显示控件窗口，Windows 将使用 DxgkDdiSystemDisplayWrite DDI 更新屏幕图像。 Windows 将使用 DDI 的图像块从指定的源映像写入屏幕，通过 DxgkDdiSystemDisplayEnable 函数将被重置。 此函数将传递给驱动程序源映像以及步幅、 宽度和高度的起始地址。 源图像的颜色格式始终是 D3DDDIFMT\_X8R8G8B8。 Windows 保证源图像中的非分页内存。 驱动程序必须将此源映像写入当前屏幕 (PostionX，PositionY)。

-   高 IRQL 级别或系统进行错误检查后，可能会调用此函数。 驱动程序应将此功能设置非分页的代码部分中，只能使用的非分页内存。

    -   调用此函数时，Windows 内核模式功能可能不可用。

-   建议用 CPU 来写入图像从源到帧缓冲区因为检测的错误可能由重复的 TDR 和 GPU 可能处于未知状态。

### <a name="devicegraphicswddm12displaymodeenumeration"></a>Device.Graphics.WDDM12.Display.ModeEnumeration

*枚举模式的要求*

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

**目标模式**

-   图形适配器必须能够扫描出任何分辨率大于或等于 1024 x 768 32 bpp 在渐进式和计时，最多是向上到 148.5 Mhz 的像素时钟 VESA 行业标准和准则每个计算机显示监视器计时 (DMT) 11 月 2007 年更新或 CEA-861-E 的规格。 图形驱动程序可能支持模式，大于或小于这些约束，但该驱动程序不需要执行此操作。

-   Drier 的图形不是必需的以支持任何交错的排练时间，但可能会选择这样做。

-   DxgkDdiEnumVidPnCofuncModality DDI 调用期间支持的目标模式必须是大于或等于固定的源模式只能模拟电视连接器类型和目标如果不能支持任何计时，分辨率为 1024x768 或更高版本。 这意味着，对于所有其他情况下，驱动程序只允许扩大规模。 如果用户请求它专为电视电视机之间薪酬，驱动程序将可以支持缩屏。

**源模式**

-   图形适配器必须支持集成面板中的本机分辨率。

-   如果图形适配器具有足够的带宽，它必须支持任何连接显示器的原始的分辨率。

-   图形驱动程序必须枚举每个可实现的详细计时显示器的 EDID 中的至少一个源的模式。

-   如果小于或等于为 640 x 480 显示设备支持的唯一模式，驱动程序可以在这种情况下缩小。 但是，源模式必须至少为 800 x 600。

-   图形驱动程序必须只列举的 32 位或更高版本的源模式。

**复制 （克隆） 模式**

-   如果存在重复的模式中，配置的 2 显示，图形适配器必须支持以下配置设置︰

    -   如果有任何常见的详细的计时之间小于或等于 1920 x 1080 处 32 bpp 渐进式 2 显示，图形适配器必须支持促进在此时间设置以重复模式显示。


-   至少，必须以重复模式支持 1024 x 768。

-   对于重复的模式中，配置的 2 个以上显示的图形适配器可以支持以适当模式。

-   最少，而不考虑重复模式下，显示数图形适配器必须能够支持源模式为 1024 x 768 32 bpp 在渐进中重复的模式。

**为扩展模式**

-   如果在扩展模式下配置 2 显示，图形适配器必须支持设置配置如下︰

    -   具有集成显示系统上︰ 集成的显示器和非集成显示 32 bpp 在同时达 1920 x 1080 渐进式的原始分辨率

    -   在每个非集成显示器上 32 bpp 达 1920 x 1080 渐进式

-   对于 2 个以上显示在扩展模式下配置的图形适配器可能会选择一套合适的模式，以支持根据可用带宽。

### <a name="devicegraphicswddm12displaypnpstopstartsupport"></a>Device.Graphics.WDDM12.Display.PnpStopStartSupport

*支持即插即用中 WDDM 停止*

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

由于 WDDM 介绍，每个驱动程序都需要支持即插即用的开始和停止。 这一要求增强支持的即插即用的开始和停止 WDDM 中。

一旦停止 WDDM 驱动程序，Windows 需要接管显示控制和驱动程序启动时，Windows 需要交付后显示控件与该驱动程序。

WDDM 1.2 引入了新的 DDI 以添加对基于 UEFI 系统支持以及改善用户体验，在这种情况下。

下面的 DDIs 被要求完全和仅显示 WDDM 1.2 驱动程序实现。

 - DxgkDdiReleasePostDisplayOwnership

以下是实现此 DDI 的驱动程序的要求。

-   Windows 将提供一个目标 ID 作为 DDI 调用的一部分。 驱动程序必须继续推动显示与目标 id。

    -   驱动程序必须检查连接情况的显示提供目标 id。 如果指定目标没有显示器已连接，驱动程序应失败状态此调用\_不\_支持。

    -   驱动程序必须禁用所有其他显示器连接至目标 ID 除适配器提供的信号。

        -   如果这是不可能的应该尝试驱动程序并将其置于所有其他显示一个空白图像。

        -   如果这是不可能的驱动程序必须将最后的图像保留在屏幕上保持不变。

-   如果 ACPI ID 与目标 ID，则它必须返回到 Windows 提供，作为 PDXGK 的返回数据结构的一部分\_显示\_的信息。

-   为所选的目标 ID，驱动程序必须保留的当前显示模式并作为 DDI 调用的一部分回 Windows 提供这种模式。

    -   如果驱动程序不能维护的当前模式或目标 ID 不活动拓扑的一部分，驱动程序应选择替代的活动目标并尝试维护目标的当前分辨率。 这是不可能的如果该驱动程序应尝试并设置显示器的本机分辨率或高分辨率模式。 最起码，驱动程序必须为大于或等于 800 x 600 24bpp 模式重置 (D3DDDIFMT\_R8G8B8) 或 32bpp (D3DDDIFMT\_X8R8G8B8)。

    -   如果没有目标处于活动状态，然后该驱动程序应尝试启用目标。 最好是内部面板 （如果可用）。

-   驱动程序必须清除当前帧缓存器、 禁用硬件光标、 禁用所有贴，并设置默认伽玛斜向进刀。

-   驱动程序必须将当前帧缓存器线性 （或者通过使用 swizzle 范围或禁用 swizzle 模式）。

-   驱动程序应由 CPU 访问当前帧缓存器。

-   驱动程序必须确保，可见性设置为"启用"，指定目标上。

### <a name="devicegraphicswddm12displayprovidelinearframebuffer"></a>Device.Graphics.WDDM12.Display.ProvideLinearFrameBuffer

*图形设备可以提供 Windows 可用线性帧缓冲。*

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

有许多方案在 Windows 操作系统中的组件需要能够更新显示时的 IHV 驱动程序未加载。 这些方案中的一些是︰ 引导、 错误检测时，安全模式和驱动程序升级等。要确保与这些 Windows 方案兼容图形设备，它必须︰

1.  确保必须出而无需添加 OEM IHV/扫描帧缓存器的更新。

2.  软件/驱动程序。 提供的线性框架缓冲区，则 CPU 可以按需从 IHV 驱动程序访问。

3.  在 UEFI 系统在引导时使用 UEFI 2.3 GOP。

4.  BIOS 使用 VBE 3.0 标准系统。

<a name="device.graphics.wddm12.displayonly"></a>
## <a name="devicegraphicswddm12displayonly"></a>Device.Graphics.WDDM12.DisplayOnly

*可选功能集由 WDDM 1.2 驱动程序支持仅显示特定的 DDIs。*

### <a name="devicegraphicswddm12displayonlybase"></a>Device.Graphics.WDDM12.DisplayOnly.Base

*要求以支持 WDDM 图形适配器显示功能*

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

WDDM 已得到扩展，以支持 WDDM 驱动程序，它只负责扫描显示出能力。 这些驱动程序不可以支持任何呈现功能。

如果只实现下面的 DDIs，并没有实现任何呈现 DDIs 驱动程序被视为仅 WDDM 显示驱动程序。
 

**公共 WDDM DDIs**

这些 DDIs 是针对常见的设备功能，例如支持即插即用和电源支持。 这些功能所需的所有 WDDM 驱动程序，并且如果未实现，不会被驱动程序启动 windows。 这些 DDIs 已[在 WDK 中记载](http://msdn.microsoft.com/en-us/library/ff554066.aspx)︰ <http://msdn.microsoft.com/en-us/library/ff554066.aspx>。

**必填：**
 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**可选︰**
 - DxgkDdiInterruptRoutine\*
 - DxgkDdiDpcRoutine
 - DxgkDdiNotifyAcpiEvent
 - DxgkDdiQueryInterface
 - DxgkDdiControlEtwLogging
 - DxgkDdiEscape
 - DxgkDdiCollectDbgInfo

\***DxgkDdiInterruptRoutine**函数是必需的如果当前的硬件设备报告硬件中断。 在这种情况下，如果驱动程序未提供此 DDI 函数，操作系统就会失败初始化。 如果当前的硬件并没有中断，该驱动程序提供此 DDI 函数，操作系统仍将允许将加载此驱动程序，则不会调用**DxgkDdiInterruptRoutine** 。

\***DdiNotifyAcpiEvent**DDI 函数用于通知在某些 ACPI 事件的图形驱动程序。 它是可选的呈现设备。 在普通 WDDM 图形设备上，此 DDI 函数将返回一个标志来指示 dxgkrnl.sys 采取一些进一步的动作，如重置显示模式或轮询连接的监视器。 用于呈现唯一的设备，这些标志未使用，必须设置为零。
 

**显示仅 DDIs**

以下 DDI 函数都是需要由仅显示驱动程序实现。 如果驱动程序不提供所有这些 DDIs，Windows 将无法初始化该驱动程序。

 - DxgkDdiQueryChildRelations
 - DxgkDdiQueryChildStatus
 - DxgkDdiQueryDeviceDescriptor
 - DxgkDdiResetDevice
 - DxgkDdiQueryAdapterInfo
 - DxgkDdiSetPalette\*
 - DxgkDdiSetPointerPosition\*\*
 - DxgkDdiSetPointerShape\*\*
 - DxgkDdiIsSupportedVidPn
 - DxgkDdiRecommendFunctionalVidPn\*\*\*
 - DxgkDdiEnumVidPnCofuncModality
 - DxgkDdiSetVidPnSourceVisibility
 - DxgkDdiCommitVidPn
 - DxgkDdiUpdateActiveVidPnPresentPath
 - DxgkDdiRecommendMonitorModes
 - DxgkDdiGetScanLine
 - DxgkDdiQueryVidPnHWCapability
 - DxgkDdiPresentDisplayOnly
 - DxgkDdiReleasePostDisplayOwnership
 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite

\***DxgkDdiSetPalette**是必需的 DDI。 如果驱动程序不支持任何组件面板模式，它仍应提供此 DDI。

\*\***DxgkDdiSetPointerPosition**和**DxgkDdiSetPointerShape**是必需的 DDIs。 如果驱动程序不支持任何硬件光标，它仍应提供这些两个 DDIs。

\*\*\***DxgkDdiRecommendFunctionalVidPn**是必需的 DDI。 如果驱动程序不支持 ACPI 的任何事件，它仍应提供此 DDI。

*设计注︰*唯一的颜色格式支持显示只有驱动程序是 D3DDDIFMT\_A8R8G8B8;因此，这些驱动程序应只列举这种格式的源模式。

<a name="device.graphics.wddm12.displayrender"></a>
## <a name="devicegraphicswddm12displayrender"></a>Device.Graphics.WDDM12.DisplayRender

*由 WDDM 1.2 驱动程序同时支持的可选功能集显示并呈现 DDIs。*

### <a name="devicegraphicswddm12displayrenderbase"></a>Device.Graphics.WDDM12.DisplayRender.Base

*要求实现渲染和显示 DDIs WDDM 图形适配器*

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

WDDM 已得到扩展，以支持 WDDM 驱动程序，它只负责扫描显示出能力。 这些驱动程序不可以支持任何呈现功能。

WDDM 也得到扩展，以支持 WDDM 驱动程序，它只负责呈现和计算 DDIs。 这些驱动程序不可以支持任何显示扫描出功能。

驱动程序的实现的 DDI 的 （显示和渲染） 两组被视为完整的图形适配器。
 

**公共 WDDM DDIs**

这些 DDIs 是针对常见的设备功能，例如支持即插即用和电源支持。 这些功能所需的所有 WDDM 驱动程序，并且如果未实现，不会被驱动程序启动 windows。 这些 DDIs 已[在 WDK 中记载](http://msdn.microsoft.com/en-us/library/ff554066.aspx)︰ <http://msdn.microsoft.com/en-us/library/ff554066.aspx>。

**必填：**
 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**可选︰**
 - DxgkDdiInterruptRoutine\*
 - DxgkDdiDpcRoutine
 - DxgkDdiNotifyAcpiEvent
 - DxgkDdiQueryInterface
 - DxgkDdiControlEtwLogging
 - DxgkDdiEscape
 - DxgkDdiCollectDbgInfo

\*DxgkDdiInterruptRoutine 函数是必需的如果当前的硬件设备报告硬件中断。 在这种情况下，如果驱动程序未提供此 DDI 函数，操作系统就会失败初始化。 如果当前的硬件并没有中断，该驱动程序提供此 DDI 函数，操作系统仍将允许将加载此驱动程序，则不会调用 DxgkDdiInterruptRoutine。
 

**显示仅 DDIs**

以下 DDI 函数都是需要由仅显示驱动程序实现。 如果驱动程序不提供所有这些 DDIs，Windows 将无法初始化该驱动程序。
 - DxgkDdiQueryChildRelations
 - DxgkDdiQueryChildStatus
 - DxgkDdiQueryDeviceDescriptor
 - DxgkDdiResetDevice
 - DxgkDdiQueryAdapterInfo
 - DxgkDdiSetPalette\*
 - DxgkDdiSetPointerPosition\*\*
 - DxgkDdiSetPointerShape\*\*
 - DxgkDdiIsSupportedVidPn
 - DxgkDdiRecommendFunctionalVidPn\*\*\*
 - DxgkDdiEnumVidPnCofuncModality
 - DxgkDdiSetVidPnSourceVisibility
 - DxgkDdiCommitVidPn
 - DxgkDdiUpdateActiveVidPnPresentPath
 - DxgkDdiRecommendMonitorModes
 - DxgkDdiGetScanLine
 - DxgkDdiQueryVidPnHWCapability
 - DxgkDdiPresentDisplayOnly
 - DxgkDdiReleasePostDisplayOwnership
 - DxgkDdiSystemDisplayEnable
 - DxgkDdiSystemDisplayWrite

\***DxgkDdiSetPalette**是必需的 DDI。 如果驱动程序不支持任何组件面板模式，它仍应提供此 DDI。

\*\***DxgkDdiSetPointerPosition**和**DxgkDdiSetPointerShape**是必需的 DDIs。 如果驱动程序不支持任何硬件光标，它仍应提供这些两个 DDIs。

\*\*\***DxgkDdiRecommendFunctionalVidPn**是必需的 DDI。 如果驱动程序不支持 ACPI 的任何事件，它仍应提供此 DDI。

\***DdiNotifyAcpiEvent**DDI 函数用于通知在某些 ACPI 事件的图形驱动程序。 它是可选的呈现设备。 在普通 WDDM 图形设备上，此 DDI 函数将返回一个标志来指示 dxgkrnl.sys 采取一些进一步措施如重置显示模式或轮询连接的监视器。 用于呈现唯一的设备，这些标志未使用，必须设置为零。
 

**呈现仅 DDIs**

这些 DDI 函数是用于呈现功能。

**必填：**

 - DxgkDdiInterruptRoutine
 - DxgkDdiDpcRoutine
 - DxgkDdiResetDevice
 - DxgkDdiCreateDevice
 - DxgkDdiDestroyAllocation
 - DxgkDdiDescribeAllocation
 - DxgkDdiOpenAllocation
 - DxgkDdiCloseAllocation
 - DxgkDdiGetStandardAllocationDriverData
 - DxgkDdiSubmitCommand
 - DxgkDdiPreemptCommand
 - DxgkDdiBuildPagingBuffer
 - DxgkDdiResetFromTimeout
 - DxgkDdiRestartFromTimeout
 - DxgkDdiQueryCurrentFence
 - DxgkDdiControlInterrupt
 - DxgkDdiDestroyDevice
 - DxgkDdiPresent
 - DxgkDdiCreateAllocation
 - DxgkDdiPatch
 - DxgkDdiRender
 - DxgkDdiRenderKm

**可选︰**

如果呈现硬件支持 swizzling 兵兵，驱动程序还应提供以下两个功能︰

 - DxgkDdiAcquireSwizzlingRange
 - DxgkDdiReleaseSwizzlingRange
 

<a name="device.graphics.wddm12.displayrender.processingstereoscopicvideocontent"></a>
## <a name="devicegraphicswddm12displayrenderprocessingstereoscopicvideocontent"></a>Device.Graphics.WDDM12.DisplayRender.ProcessingStereoscopicVideoContent

*可选的功能集由实现 WDDM 1.2 驱动程序支持 stereoscopic 视频处理。*

### <a name="devicegraphicswddm12displayrenderprocessingstereoscopicvideocontentprocessingstereoscopicvideocontent"></a>Device.Graphics.WDDM12.DisplayRender.ProcessingStereoscopicVideoContent.ProcessingStereoscopicVideoContent

*如果显示适配器支持演示文稿和 stereoscopic 的视频内容的处理，它必须符合立体 3D 的 DXGI 规范。*

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

WDDM 1.2 驱动程序可能会有选择地处理为立体声编码的视频数据。 如果驱动程序发布，它可以支持立体声输入，它必须支持处理中的内容的水平和垂直方向排列的左、 右眼视图左、 右眼视图，以及单独的流。
此外，如果该驱动程序发布，它可以支持立体声音频，它可以选择还处理下面的立体内容版式︰

-   隔行扫描的行  
-   交错的列  
-   棋盘  
-   翻转后的配置

最后，驱动程序也可能支持新立体声处理功能︰

-   单声道的偏移量
-   立体眼睛调整

对于所有可选内容版式和处理功能，驱动程序必须发布相应的上限，以指示它是否支持该功能。

<a name="device.graphics.wddm12.displayrender.runtimepowermgmt"></a>
## <a name="devicegraphicswddm12displayrenderruntimepowermgmt"></a>Device.Graphics.WDDM12.DisplayRender.RuntimePowerMgmt

*可选功能集由 WDDM 1.2 驱动程序支持的运行时电源管理 DDIs。*

### <a name="devicegraphicswddm12displayrenderruntimepowermgmtruntimepowermgmt"></a>Device.Graphics.WDDM12.DisplayRender.RuntimePowerMgmt.RuntimePowerMgmt

*如果实现-WDDM 1.2 驱动程序必须使用新 WDDM 1.2 GPU 电源管理 DDI F 状态和 p-状态电源管理。*

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

WDDM 1.2 驱动程序可以选择支持 F 状态和 p-状态电源管理。
SoC GPU 电源管理 WDDM v1.2 DDI 使用的详细信息，请参阅 Windows WDK 文档。

<a name="device.graphics.wddm12.render"></a>
## <a name="devicegraphicswddm12render"></a>Device.Graphics.WDDM12.Render

*由 WDDM 1.2 驱动程序支持其呈现的基本特征集特定的 DDIs。*

### <a name="devicegraphicswddm12renderbase"></a>Device.Graphics.WDDM12.Render.Base

*WDDM 图形适配器可以支持的需求呈现功能*

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

WDDM 已得到扩展，以支持 WDDM 驱动程序，它只负责呈现和计算 DDIs。 这些驱动程序不可以支持任何显示扫描出功能。

驱动程序被视为仅呈现 WDDM 驱动程序，如果满足以下两个条件之一︰

-   驱动程序实现完整的 WDDM 驱动程序，所需的所有 DDIs，但报告 0 源和 0 个目标。

-   驱动程序实现所有呈现特定 DDIs，并返回所有显示特定 DDIs 空指针。 为此需要 DDIs 称为下面。

**公共 WDDM DDIs**

这些 DDI 函数是针对常见的设备功能，例如支持即插即用和电源支持。 这些功能所需的所有 WDDM 驱动程序，并且如果未实现，不会被驱动程序启动 windows。 WDK 中已经说明这些 DDIs: <http://msdn.microsoft.com/en-us/library/ff554066.aspx>。

**必填：**
 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**可选︰**

 - DdiNotifyAcpiEvent\*

\*使用 DdiNotifyAcpiEvent DDI 函数提示上某些 ACPI 事件的图形驱动程序。 它是可选的呈现设备。 在普通 WDDM 图形设备上，此 DDI 函数将返回一个标志来指示 dxgkrnl.sys 采取一些进一步的动作，如重置显示模式或轮询连接的监视器。  用于呈现唯一的设备，这些标志未使用，必须设置为零。
 

**呈现仅 DDIs**

这些 DDI 函数是用于呈现功能。

**必填：**
 - DxgkDdiInterruptRoutine
 - DxgkDdiDpcRoutine
 - DxgkDdiResetDevice
 - DxgkDdiCreateDevice
 - DxgkDdiDestroyAllocation
 - DxgkDdiDescribeAllocation
 - DxgkDdiOpenAllocation
 - DxgkDdiCloseAllocation
 - DxgkDdiGetStandardAllocationDriverData
 - DxgkDdiSubmitCommand
 - DxgkDdiPreemptCommand
 - DxgkDdiBuildPagingBuffer
 - DxgkDdiResetFromTimeout
 - DxgkDdiRestartFromTimeout
 - DxgkDdiQueryCurrentFence
 - DxgkDdiControlInterrupt
 - DxgkDdiDestroyDevice
 - DxgkDdiPresent
 - DxgkDdiCreateAllocation
 - DxgkDdiPatch
 - DxgkDdiRender
 - DxgkDdiRenderKm

**可选︰**如果呈现硬件支持 swizzling 兵兵，驱动程序还应提供以下两个功能︰
 - DxgkDdiAcquireSwizzlingRange
 - DxgkDdiReleaseSwizzlingRange
 

### <a name="devicegraphicswddm12renderd3d11videodecoding"></a>Device.Graphics.WDDM12.Render.D3D11VideoDecoding

*显示驱动程序必须支持 DirectX 11 视频解码器 DDI。*

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

显示 WDDM 1.2 驱动程序支持 DirectX 11 视频解码器 DDI。

WDDM 驱动程序必须支持至少一种 H.264 Guid 的下面的设置︰

-   D3D11\_解码器\_配置文件\_H264\_VLD\_NOFGT
-   D3D11\_解码器\_配置文件\_H264\_VLD\_FGT
-   D3D11\_解码器\_配置文件\_H264\_VLD\_WITHFMOASO\_NOFGT

WDDM 驱动程序支持至少一个下列 VC1 模式︰

-   D3D11\_解码器\_配置文件\_VC1\_VLD
-   D3D11\_解码器\_配置文件\_VC1\_D2010

如果实现︰ WDDM 驱动程序支持至少以下 MPEG2 模式之一︰

-   D3D11\_解码器\_配置文件\_MPEG2\_VLD 和 D3D11\_解码器\_配置文件\_MPEG2\_IDCT
-   D3D11\_解码器\_配置文件\_MPEG2\_VLD 和 D3D11\_解码器\_配置文件\_MPEG2\_MOCOMP
-   D3D11\_解码器\_配置文件\_MPEG2\_IDCT
-   D3D11\_解码器\_配置文件\_MPEG2AND1\_VLD

如果实现的︰ HEVC/H.265 模式

-   D3D11\_解码器\_配置文件\_HEVC\_VLD\_主
-   D3D11\_解码器\_配置文件\_HEVC\_VLD\_MAIN10

强烈建议对于驱动程序支持 D3D11\_解码器\_配置文件\_HEVC\_VLD\_MAIN10 作为主 10 是很常见的高级 HEVC 内容格式。

如果实现的︰ VPx 模式︰

-   D3D11\_解码器\_配置文件\_VP8\_VLD
-   D3D11\_解码器\_配置文件\_VP9\_VLD\_PROFILE0
-   D3D11\_解码器\_配置文件\_VP9\_VLD\_PROFILE2 （如果硬件不支持配置文件 2 可选）

最后，WDDM 驱动程序必须支持 DXGI\_格式\_420\_透明，DXGI\_格式\_NV12 解码器作为输出格式。 HEVC 主 10，驱动程序必须支持 DXGI\_格式\_P010 解码器作为输出格式。

WDDM 驱动程序必须支持 H.264 标准 AES 128 （WDDM 1.1 版规范中所定义）\* \* \*和 MPEG2，如果支持 MPEGE2 加速。

设计备注

\*\*\*标准化的 AES 128 支持 x86 和 x64 体系结构和操作系统的系统要求。

### <a name="devicegraphicswddm12renderd3d11videoprocessing"></a>Device.Graphics.WDDM12.Render.D3D11VideoProcessing

*显示驱动程序必须支持相应的 DDIs DirectX 11 视频处理。*

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

必须支持以下视频处理器设备功能 DDIs:

-   BOB 逐行扫描

    -   DXVAHDDDI\_处理器\_CAP\_逐行扫描\_小明
    -   D3D11\_1DDI\_视频\_处理器\_处理器\_CAP\_逐行扫描\_小明 

-   Constriction

    -   DXVAHDDDI\_功能\_CAP\_CONSTRICTION
    -   D3D11\_1DDI\_视频\_处理器\_功能\_CAP\_CONSTRICTION

-   旋转

    -   DXVAHDDDI\_功能\_CAP\_旋转
    -   D3D11\_1DDI\_视频\_处理器\_功能\_CAP\_旋转

-   任意拉伸/收缩

-   必须对输入和输出支持完全和名义 RGB 范围 YCbCr 数据，特别是︰

    -   0 到 255

        -   DXVAHDDDI\_流\_状态\_输入\_颜色\_空间\_数据

RGB\_范围字段设置为 0:

-   DXVAHDDDI\_BLT\_状态\_输出\_颜色\_空间\_数据 RGB\_范围字段设置为 0

    -   D3D11\_1DDI\_视频\_处理器\_颜色\_空间 RGB\_范围字段设置为 0

-   16 到 235

    -   DXVAHDDDI\_流\_状态\_输入\_颜色\_空间\_数据

RGB\_范围字段设置为 1:

-   DXVAHDDDI\_BLT\_状态\_输出\_颜色\_空间\_数据 RGB\_范围字段设置为 1

    -   D3D11\_1DDI\_视频\_处理器\_颜色\_空间 RGB\_范围字段设置为 1

-   BT. 601 和 BT. 必须对输入和输出支持 709 转换矩阵 YCbCr 数据，特别是︰

-   DXVAHDDDI\_流\_状态\_输入\_颜色\_空间\_数据。YCbCr\_矩阵

    -   必须支持这两个字段设置为 0 （表示 BT.601） 和 1 （表示 BT.709）。

-   DXVAHDDDI\_BLT\_状态\_输出\_颜色\_空间\_数据。YCbCr\_矩阵

    -   必须支持这两个字段设置为 0 （表示 BT.601） 和 1 （表示 BT.709）。

-   D3D11\_1DDI\_视频\_处理器\_颜色\_空间。YCbCr\_矩阵

    -   必须支持这两个字段设置为 0 （表示 BT.601） 和 1 （表示 BT.709）。

-   任意的背景色

-   每个流源矩形

-   每个流目标矩形

-   总体目标矩形

-   至少一个流

必须输入支持以下格式︰

-   D3DFMT\_420\_不透明
-   D3DFMT\_NV12
-   D3DFMT\_YUY2
-   作为输出从 DXVA 2.0 支持的任何格式解码或 DirectX 11 视频解码

根据功能级别所提供的驱动程序的 Direct3D (如 9.1-9.3 的 Direct3D 9 DDIs，10.0 的 Direct3D 10 DDIs，等等)，必须为输出支持以下格式︰

-   9.1 9.3 功能级别

    -   D3DFMT\_A8R8G8B8
    -   D3DFMT\_NV12

-   10.0 10.1 功能级别

    -   DXGI\_格式\_R16G16B16A16\_浮动
    -   DXGI\_格式\_R8G8B8A8\_UNORM
    -   DXGI\_格式\_R10G10B10A2\_UNORM
    -   DXGI\_格式\_R8G8B8A8\_UNORM\_SRGB
    -   DXGI\_格式\_NV12

    -   如果驱动程序所支持的 swapchain 格式为下列格式也是必需的︰

        -   DXGI\_格式\_B8G8R8A8\_UNORM
        -   DXGI\_格式\_B8G8R8A8\_UNORM\_SRGB
        -   DXGI\_格式\_R10G10B10\_XR\_偏置\_A2\_UNORM

-   11.0 功能级别及未来

    -   DXGI\_格式\_R16G16B16A16\_浮动
    -   DXGI\_格式\_R8G8B8A8\_UNORM
    -   DXGI\_格式\_R10G10B10A2\_UNORM
    -   DXGI\_格式\_R8G8B8A8\_UNORM\_SRGB
    -   DXGI\_格式\_NV12，DXGI\_格式\_B8G8R8A8\_UNORM
    -   DXGI\_格式\_B8G8R8A8\_UNORM\_SRGB
    -   DXGI\_格式\_R10G10B10\_XR\_偏置\_A2\_UNORM

**设计备注**

MPEG-2 支持 x86 和 x64 体系结构和操作系统的系统要求。

### <a name="devicegraphicswddm12renderdirectflip"></a>Device.Graphics.WDDM12.Render.DirectFlip

*驱动程序必须支持 DirectFlip DDI。*

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

驱动程序必须发布的 SupportDirectFlip 字段为 true，则在 DXGK\_DRIVERCAPS 结构。
Direct3D 11 DDI WDDM 1.2 驱动程序必须实现 D3D11\_1DDI\_CHECKDIRECTFLIPSUPPORT DDI 和 DDI 被调用时使用至少以下参数中的返回 TRUE:

-   应用程序资源匹配 DWM 资源格式和像素尺寸。

-   D3DDDI\_CHECKDIRECTFLIP\_未设置直接标志。

Direct3D 9 DDI WDDM 1.2 驱动程序必须实现 D3DDDIARG\_CHECKDIRECTFLIPSUPPORT DDI 和 DDI 被调用时使用至少以下参数中的返回 TRUE:

-   应用程序资源匹配 DWM 资源格式和像素尺寸。

-   D3DDDI\_CHECKDIRECTFLIP\_未设置直接标志。

驱动程序必须支持创建的共享主 swapchains，明确标识为资源创建的︰

-   pPrimaryDesc 为非空。

-   D3D10\_DDI\_资源\_杂项\_在 MiscFlags 中设置共享。

-   D3D10\_DDI\_绑定\_着色器\_资源、 D3D10\_DDI\_绑定\_和 D3D10\_DDI\_绑定\_呈现\_目标在 BindFlags 中的所有设置。

当 SharedPrimaryTransition 位设置中进行 DXGK\_SETVIDVIDPNSOURCEADDRESS DDI，驱动程序必须︰

-   验证硬件可以无缝地切换两个分配。

-   执行无缝切换到新的主由 DDI。

### <a name="devicegraphicswddm12renderfliponvsyncmmio"></a>Device.Graphics.WDDM12.Render.FlipOnVSyncMmIo

*WDDM1.2 驱动程序必须支持在下一步的垂直同步生效内存映射 I/O MMIO 基于翻转。*

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

所有 WDDM1.2 驱动程序必须为 true，则在 DXGK 中都发布的 FlipOnVSyncMmIo 字段\_FLIPCAPS 结构和实施行为此处概述 FlipOnVSyncMmIo: <http://msdn.microsoft.com/en-us/library/ff561069.aspx>。
 

### <a name="devicegraphicswddm12renderofferreclaim"></a>Device.Graphics.WDDM12.Render.OfferReclaim

*WDDM 1.2 驱动程序必须使用优惠和回收 DDI 减少内存占用空间。*

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

WDDM 1.2 驱动程序必须使用新 UMD 提供和回收 DDI 来减少内存资源在本地视频和系统内存中创建临时的曲面的开销。  一个示例是使用临时缓冲区到 GPU 的本地内存中加快上载数据的过程。  通过提供这些资源，操作系统可以重用内存而冒破坏并重新创建频率高的费用。
WDDM 驱动程序还经常保持，以便该应用程序创建具有相同属性的另一种分配，则可能给出回旧应用程序不再使用的分配。  这就减少了对性能的影响迅速销毁并重新创建分配、 常见的不良行为，对于应用程序，但它也可以有非常高的内存成本。  通过提供这些分配，WDDM 1.2 驱动程序可以使大部分其性能，不会浪费内存。
下面是详细的子要求︰

-   WDDM 1.2 驱动程序必须始终"提供"内部临时缓冲区后使用它们。 这些临时缓冲区通常不保存数据被移动或从源复制到目标。 在 Windows 7 和以前的操作系统，这些临时曲面即使它们不再被使用在内存中保留。

-   WDDM 1.2 驱动程序必须始终"提供"回收的曲面的延迟的删除。 如果一个驱动程序决定推迟销毁的曲面，它至少必须提供它到视频内存管理器。

-   时的各个资源分配中包含所有已提供 ed，WDDM 1.2 驱动程序应该只提供打包的分配。 已经回收了任何单个资源时，应回收作为一个整体分配。

-   WDDM 1.2 驱动程序必须始终提供放弃分配，如果它实现自己的重命名机制。

-   WDDM 1.2 驱动程序永远不应包与其他分配，保证为应用程序提供能为他们带来预期的收益大小超过 64 KB 的分配。

优惠和回收 WDDM v1.2 DDI 使用的详细信息，请参阅 Windows WDK 文档。

### <a name="devicegraphicswddm12renderpreemptiongranularity"></a>Device.Graphics.WDDM12.Render.PreemptionGranularity

*WDDM 1.2 驱动程序必须报告 GPU 抢占的粒度级别。*

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

WDDM 1.2 驱动程序必须报告运行图形和计算方案的 GPU 抢占粒度。
WDDM 1.2 必须执行以下操作︰

-   WDDM 1.2 驱动程序必须首先设置"PreemptionAware"标志和"MultiEngineAware"标志，在\_DXGK\_VIDSCHCAPS DxgkDdiQueryAdapterInfo DDI 结构。

-   WDDM 1.2 驱动程序，必须设置相应的 GPU 抢占粒度，通过"D3DKMDT\_抢占\_CAP PreemptionCaps"。

实际的图形或计算的抢占级别上没有强制性要求。 例如，如果 GPU 不支持任何级别的如年年 DMA 缓冲区图形抢占三角形边界或其他人，然后它可以报告此上限为 D3DKMDT\_图形\_抢占\_DMA\_缓冲区\_边界。 同样，如果它不支持计算任意级别的精细抢占更细致，然后它必须报告 D3DKMDT 作为 cap\_计算\_抢占\_DMA\_缓冲区\_边界。

但是，如果中期 DMA 缓冲区或数据包抢占支持 GPU，然后 WDDM 1.2 驱动程序必须选择适当的上限要充分利用福利提供更细致的精细 GPU 抢占通过图形和/或计算。

使用 GPU 抢占 WDDM v1.2 DDI 的详细信息，请参阅 Windows WDK 文档。

### <a name="devicegraphicswddm12renderpremiumcontentplayback"></a>Device.Graphics.WDDM12.Render.PremiumContentPlayback

*WDDM1.2 驱动程序的受保护的环境签名要求*

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

任何 WDDM 1.2 用户模式图形驱动程序二进制文件所需的增值内容播放必须正确签名通过 Windows 保护环境 (PE) 许可程序，根据需要。 PVP OPM 许可协议中的部分 3.1 已要求与 PE 许可证程序的法规遵从性。 具体而言，所需的组中每个二进制文件到 Windows 操作系统代码完整性被识别为 PE，批准根必须经过签名，并且具有一个或两个以下签名特征︰

1.  目录与 PE 可信的整体特性的签名，使用哈希条目为每个特定文件设置字段和值的 PETrusted = 1。

2.  嵌入的页面每个哈希值签名。

此外，确定每个模块需要何种签名的正在标准化的过程。 现在每个 INF 文件必须包含唯一地标识哪种类型的签名适用于相关的驱动程序二进制文件的 SignatureAttributes 节。 向现有 inf 文件添加该节是一个非常简单的过程。

下面是一个示例︰

```
[SignatureAttributes]
NameOfFile.dll = SignatureAttributes.PETrust
[SignatureAttributes.PETrust]
PETrust=true
```

### <a name="devicegraphicswddm12rendertdrresiliency"></a>Device.Graphics.WDDM12.Render.TDRResiliency

*Gpu 都支持每个引擎重置为 WDDM 1.2 驱动程序必须将 Windows DDI 实现 TDR 的自我恢复能力。*

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

GPU 支持重置每个引擎的 WDDM 1.2 驱动程序必须实现 TDR DDI 的更高的可靠性和可恢复性。
WDDM 1.2 驱动程序必须执行以下操作︰

-   WDDM 1.2 驱动程序必须满足 WDDM 1.2 GPU 抢占要求。

-   WDDM 1.2 驱动程序必须实现以下的 GPU 引擎 DDIs:

<!-- -->

-   QueryDependentEngineGroup

-   QueryEngineStatus

-   ResetEngine

<!-- -->

-   WDDM 1.2 驱动程序必须支持的适配器范围内重置和重新启动 windows 以前版本 8 TDR 行为继续进行。 这些现有的 DDIs 的语义保留以前 Windows 8 一样。

使用 GPU 抢占和 TDR 改进 WDDM v1.2 DDI 的详细信息，请参阅 Windows WDK 文档。

### <a name="devicegraphicswddm12renderumdlogging"></a>Device.Graphics.WDDM12.Render.UMDLogging

*WDDM 1.2 驱动程序必须实现 WDDM 用户模式驱动程序或 UMD 日志记录以帮助诊断能力。*

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

WDDM 1.2 驱动程序必须通过实现日志记录 ETW 接口 UMD 公开 Direct3D 资源和视频内存分配之间的关系。 下面是驱动程序的特定要求︰

-   即使分配的内存的大小大于 UMD 必须报告在 CreateResource 调用中，指定将分配大小。

-   UMD 必须其内部分配的每个记录的 MapAllocation 事件并指定该分配的目的。

-   UMD 必须记录每个更名为表面的 MapAllocation 事件。

-   UMD 必须登录包插入现有的曲面，它的每个表面的 MapAllocation。

-   UMD 必须记录在简要介绍当前存在的每个表面的 MapAllocation。

-   UMD 必须登录 MapAllocation 响应 CreateResource 调用，即使没有新的内存分配。

-   UMD 必须销毁其内部分配每次登录 UnmapAllocation。

-   UMD 必须登录，UnmapAllocation 每次应用程序销毁分配，即使实际的内存分配不会被破坏。

-   UMD 必须关闭一个更名为分配每次登录 UnmapAllocation。

-   UMD 必须登录将被打包到一个更大的分配每个曲面 UnmapAllocation。

除了记录的 MapAllocation 和 UnmapAllocation 的事件发生时，该图形驱动程序必须能够及时报告现有资源和分配在任何点之间的所有映射。

UMD 记录 WDDM v1.2 DDI 使用的详细信息，请参阅 Windows WDK 文档。

### <a name="devicegraphicswddm12renderxpsrasterizationconformance"></a>Device.Graphics.WDDM12.Render.XPSRasterizationConformance

*WDDM 1.2 驱动程序必须支持 XPS 光栅化。*

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

为了确保品质的打印体验在 Windows 上，WDDM1.2 图形驱动程序必须支持 XPS 光栅化。

<a name="device.graphics.wddm12.renderonly"></a>
## <a name="devicegraphicswddm12renderonly"></a>Device.Graphics.WDDM12.RenderOnly

*可选功能集由 WDDM 1.2 驱动程序支持仅呈现特定的 DDIs。*

### <a name="devicegraphicswddm12renderonlybase"></a>Device.Graphics.WDDM12.RenderOnly.Base

*WDDM 图形适配器可以支持的需求呈现功能*

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

WDDM 已得到扩展，以支持 WDDM 驱动程序，它只负责呈现和计算 DDIs。 这些驱动程序不可以支持任何显示扫描出功能。

驱动程序被视为仅呈现 WDDM 驱动程序，如果满足以下两个条件之一︰

-   驱动程序实现完整的 WDDM 驱动程序，所需的所有 DDIs，但报告 0 源和 0 个目标。

-   驱动程序实现所有呈现特定 DDIs，并返回所有显示特定 DDIs 空指针。 为此需要 DDIs 称为下面。

**公共 WDDM DDIs**

这些 DDI 函数是针对常见的设备功能，例如支持即插即用和电源支持。 这些功能所需的所有 WDDM 驱动程序，并且如果未实现，不会被驱动程序启动 windows。 这些 DDIs 都已记录在 WDK， <http://msdn.microsoft.com/en-us/library/ff554066.aspx>。

**必填：**

 - DxgkDdiAddDevice
 - DxgkDdiStartDevice
 - DxgkDdiStopDevice
 - DxgkDdiRemoveDevice
 - DxgkDdiDispatchIoRequest
 - DxgkDdiSetPowerState
 - DxgkDdiUnload

**可选︰**

 - DdiNotifyAcpiEvent\*

\*使用 DdiNotifyAcpiEvent DDI 函数提示上某些 ACPI 事件的图形驱动程序。 它是可选的呈现设备。 在普通 WDDM 图形设备上，此 DDI 函数将返回一个标志来指示 dxgkrnl.sys 采取一些进一步的动作，如重置显示模式或轮询连接的监视器。  用于呈现唯一的设备，这些标志未使用，必须设置为零。
 

**呈现仅 DDIs**

这些 DDI 函数是用于呈现功能。

**必填：**

 - DxgkDdiInterruptRoutine
 - DxgkDdiDpcRoutine
 - DxgkDdiResetDevice
 - DxgkDdiCreateDevice
 - DxgkDdiDestroyAllocation
 - DxgkDdiDescribeAllocation
 - DxgkDdiOpenAllocation
 - DxgkDdiCloseAllocation
 - DxgkDdiGetStandardAllocationDriverData
 - DxgkDdiSubmitCommand
 - DxgkDdiPreemptCommand
 - DxgkDdiBuildPagingBuffer
 - DxgkDdiResetFromTimeout
 - DxgkDdiRestartFromTimeout
 - DxgkDdiQueryCurrentFence
 - DxgkDdiControlInterrupt
 - DxgkDdiDestroyDevice
 - DxgkDdiPresent
 - DxgkDdiCreateAllocation
 - DxgkDdiPatch
 - DxgkDdiRender
 - DxgkDdiRenderKm

**可选︰**如果呈现硬件支持 swizzling 兵兵，驱动程序还应提供以下两个功能︰

 - DxgkDdiAcquireSwizzlingRange
 - DxgkDdiReleaseSwizzlingRange
 

<a name="device.graphics.wddm12.standbyhibernateflags"></a>
## <a name="devicegraphicswddm12standbyhibernateflags"></a>Device.Graphics.WDDM12.StandbyHibernateFlags

*可选的功能，实现由 WDDM 1.2 驱动程序支持的休眠状态标志新的支架。*

### <a name="devicegraphicswddm12standbyhibernateflagsstandbyhibernateflags"></a>Device.Graphics.WDDM12.StandbyHibernateFlags.StandbyHibernateFlags

*如果他们支持 Windows 优化待机或休眠状态的标志，可以选择指定 WDDM v1.2 图形驱动程序。*

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

若要改善睡眠的性能和继续用于待机和休眠，WDDM 1.2 驱动程序可以利用新的 StandbyHibernateFlags （PreservedDuringStandby、 PreservedDuringHibernate 和 PartiallyPreservedDuringHibernate）。 要利用此功能，驱动程序必须将一个或多个 StandbyHibernateFlags 枚举段功能时。 此操作表示电源状态转换为相应的细分期间应跳过逐出。 验证内存保留的电源转换期间设置 StandbyHibernateFlag 的所有 WDDM 1.2 驱动程序进行都验证。

<a name="device.graphics.wddm13"></a>
## <a name="devicegraphicswddm13"></a>Device.Graphics.WDDM13

*通过支持 WDDM1.3 的驱动程序实现的基本功能集。*

### <a name="devicegraphicswddm13base"></a>Device.Graphics.WDDM13.Base

*图形驱动程序必须实现 WDDM1.3。*

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

WDDM 1.3 是必需的所有新系统都附带 Windows 10。

<html>
    <table>
        <thead>
            <tr class="header">
                <th>功能名称</th>
                <th>适用 DX H/W 类</th>
                <th>完整的图形驱动程序 x86/x64</th>
                <th>呈现只驱动程序 x86/x64</th>
                <th>ARM/RT 的完整图形驱动程序</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>混合图形 （GPU 内核）</td>
                <td>DX11 +</td>
                <td>如果实现</td>
                <td>NA</td>
                <td>NA</td>
            </tr>
            <tr class="even">
                <td>Multiplane 贴 （GPU 内核）</td>
                <td>所有</td>
                <td>如果实现</td>
                <td>NA</td>
                <td>必填字段</td>
            </tr>
            <tr class="odd">
                <td>无线显示支持</td>
                <td>所有</td>
                <td>如果实现</td>
                <td>NA</td>
                <td>如果实现</td>
            </tr>
            <tr class="even">
                <td>48 Hz 的视频播放</td>
                <td>所有</td>
                <td>必填字段</td>
                <td>NA</td>
                <td>必填字段</td>
            </tr>
            <tr class="odd">
                <td>共享表面支持多格式</td>
                <td>所有</td>
                <td>必填字段</td>
                <td>必填字段</td>
                <td>必填字段</td>
            </tr>
            <tr class="even">
                <td>现开销的优化</td>
                <td>所有</td>
                <td>必填字段</td>
                <td>必填字段</td>
                <td>必填字段</td>
            </tr>
            <tr class="odd">
                <td>内核的性能︰ GPU 引擎枚举</td>
                <td>所有</td>
                <td>必填字段</td>
                <td>必填字段</td>
                <td>必填字段</td>
            </tr>
            <tr class="even">
                <td>电源管理功能增强︰ GPU p-状态支持</td>
                <td>所有</td>
                <td>如果实现</td>
                <td>如果实现</td>
                <td>必填字段</td>
            </tr>
            <tr class="odd">
                <td>电源管理增强功能︰ 稳定 P-状态</td>
                <td>所有</td>
                <td>必填字段</td>
                <td>必填字段</td>
                <td>必填字段</td>
            </tr>
            <tr class="even">
                <td>电源管理功能增强︰ GPU f 状态滞后</td>
                <td>所有</td>
                <td>如果实现*</td>
                <td>如果实现</td>
                <td>强制</td>
            </tr>
            <tr class="odd">
                <td>电源管理增强功能︰ 雄心勃勃的 V 同步</td>
                <td>所有</td>
                <td>如果实现</td>
                <td>NA</td>
                <td>强制</td>
            </tr>
            <tr class="even">
                <td>热量接口访问</td>
                <td>所有</td>
                <td>如果实现</td>
                <td>如果实现</td>
                <td>如果实现</td>
            </tr>
            <tr class="odd">
                <td>呈现性能改进︰ D3D9 临时缓冲区</td>
                 <td>所有</td>
                <td>
                    <p>DX9.x 硬件强制</p>
                    <p>对于 DX10 + 可选</p>
                </td>
                <td>NA</td>
                <td>强制</td>
            </tr>
            <tr class="even">
                <td>呈现性能改进︰ D3D9 本机 UpdateSubResource</td>
                <td>所有</td>
                <td>
                    <p>DX9.x 硬件的强制</p>
                    <p>为 DX10 + 可选</p>
                </td>
                <td>NA</td>
                <td>强制</td>
            </tr>
            <tr class="odd">
                <td>呈现性能改进︰ D3D9 时间戳和计数器</td>
                <td>所有</td>
                <td>
                    <p>DX9.x 硬件强制</p>
                    <p>为 DX10 + 可选</p>
                </td>
                <td>NA</td>
                <td>强制</td>
            </tr>
            <tr class="even">
                <td>呈现性能改进︰ D3D 资源修剪</td>
                <td>所有</td>
                <td>强制</td>
                <td>强制</td>
                <td>强制</td>
            </tr>
            <tr class="odd">
                <td>呈现性能改进︰ 9 级实例存储功能</td>
                <td>所有</td>
                 <td>DX9.x 硬件强制</td>
                <td>NA</td>
                <td>强制</td>
            </tr>
            <tr class="even">
                <td>呈现性能改进︰ D3D9 大捕获纹理</td>
                <td>所有</td>
                <td>强制</td>
                <td>NA</td>
                <td>强制</td>
            </tr>
            <tr class="odd">
                <td>呈现性能改进︰ 将默认映射</td>
                <td>DX11 +</td>
                <td>强制</td>
                <td>NA</td>
                <td>NA</td> 
            </tr>
            <tr class="even">
                <td>Tiled Resources</td>
                <td>DX11.1</td>
                <td>If implemented</td>
                <td>If Implemented</td>
                <td>If implemented</td>
            </tr>
            <tr class="odd">
                <td>Independent Flip</td>
                <td>All</td>
                <td>Mandatory</td>
                <td>NA</td>
                <td>Mandatory</td>
            </tr>
            <tr class="even">
                <td>D3D Modification for Tools: High Performance Timing Data</td>
                <td>All</td>
                <td>Mandatory</td>
                <td>Mandatory</td>
                <td>Mandatory</td>
            </tr>
            <tr class="odd">
                <td>Full Range YUV Support</td>
                <td>DX10+</td>
                <td>Mandatory</td>
                <td>Mandatory</td>
                <td>Mandatory</td>
            </tr>
        </tbody>
    </table>
    <p></strong>Mandatory if implementing Connected Standby</p>
    <p>没有其他的要求显示唯一的驱动程序;因此，它不调用表中。</p>
    <p><strong>D3D 要求︰</strong></p>
    <table>
        <thead>
            <tr class="header">
                <th>DirectX 硬件</th>
                <th>KMD 要求</th>
                <th>UMD 要求</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>D3D9</td>
                <td>要求︰ WDDM v1.3</td>
                <td>要求︰ D3D9-UMD DDI</td>
            </tr>
            <tr class="even">
                <td>D3D10</td>
                <td>要求︰ WDDM v1.3</td>
                <td>
                    <p>要求︰ D3D9-UMD DDI</p>
                    <p>要求︰ D3D10-UMD DDI</p>
                    <p>要求︰ D3D11.1-UMD DDI</p>
                </td>
            </tr>
            <tr class="odd">
                <td>D3D10.1</td>
                <td>要求︰ WDDM v1.3</td>
                <td>
                    <p>要求︰ D3D9-UMD DDI</p>
                    <p>要求︰ D3D10-UMD DDI</p>
                    <p>要求︰ D3D10.1 的 UMD DDI</p>
                    <p>要求︰ D3D11.1-UMD DDI</p>
                </td>
            </tr>
            <tr class="even">
                <td>D3D11</td>
                <td>要求︰ WDDM v1.3</td>
                <td>
                    <p>要求︰ D3D9-UMD DDI</p>
                    <p>要求︰ D3D10-UMD DDI</p>
                    <p>要求︰ D3D10.1 的 UMD DDI</p>
                    <p>要求︰ D3D11-UMD DDI</p>
                    <p>要求︰ D3D11.1-UMD DDI</p>
                </td>
            </tr>
            <tr class="odd">
                <td>D3D11.1</td>
                <td>要求︰ WDDM v1.3</td>
                <td>
                    <p>要求︰ D3D9-UMD DDI</p>
                    <p>要求︰ D3D10-UMD DDI</p>
                    <p>要求︰ D3D10.1 的 UMD DDI</p>
                    <p>要求︰ D3D11-UMD DDI</p>
                    <p>要求︰ D3D11.1-UMD DDI</p>
                </td>
            </tr>
        </tbody>
    </table>
</html>

<a name="device.graphics.wddm13.displayrender"></a>
## <a name="devicegraphicswddm13displayrender"></a>Device.Graphics.WDDM13.DisplayRender

*父功能节点的显示的影响，并呈现 GPU 的要求。*

### <a name="devicegraphicswddm13displayrender48hzvideoplayback"></a>Device.Graphics.WDDM13.DisplayRender.48HzVideoPlayback

*WDDM1.3 驱动程序必须支持 48 Hz 的视频播放。*

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

实现 WDDM1.3 的图形驱动程序必须实现 DDIs 的︰

1.  报告是否集体系统可以无缝地切换到 48 Hz （交点的 SOC 和显示面板功能）。

2.  如果是这样，允许 （例如 48 Hz) 刷新率以指定的每个特定的存在 DDI。

HCK 测试将验证与请求的值，再假定图形驱动程序的 0.5%的公差范围内的刷新率报告支持的特定的刷新率。 这将验证设备*该报告支持 48 Hz 或通过功能 DDI 的 50hz* HCK 测试，其中 48 Hz IHV 规范中详细介绍了。

### <a name="devicegraphicswddm13displayrenderindependentflip"></a>Device.Graphics.WDDM13.DisplayRender.IndependentFlip

*IndependentFlip 支持*

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

所有 WDDM 1.3 驱动程序必须都支持 independentFlip。 在这种情况下，所有 WDDM 1.3 驱动器必须 UINT FlipIndependent 成员中都设置为 1 更新 DXGK\_FLIPCAPS 结构。 请参阅 IndependentFlip DDI 文档的更多详细信息更新 DXGK\_FLIPCAPS 结构。

<a name="device.graphics.wddm13.displayrender.coolinginterface"></a>
## <a name="devicegraphicswddm13displayrendercoolinginterface"></a>Device.Graphics.WDDM13.DisplayRender.CoolingInterface

*过热的提示功能*

### <a name="devicegraphicswddm13displayrendercoolinginterfacethermalhints"></a>Device.Graphics.WDDM13.DisplayRender.CoolingInterface.ThermalHints

*可选的热量提示 WDDM1.3 驱动程序的支持*

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

新 DeviceUid 字段添加到查询中 WDDM 图形 1.3 或更高版本驱动程序必须检查\_界面结构操作系统通过 DxgkDdiQueryInterface 函数，并将有效的接口函数返回在指定操作系统的设备上。

如果 ACPI 固件将当前图形设备添加到 ACPI ThermalZone，然后 IHV 微型端口必须支持上 GUID 的 DxgkDdiQueryInterface\_热\_冷却\_为当前图形设备接口。

**验证︰**

ACPI.sys 只查询热冷却界面，如果当前的设备处于过热区域。 Dxgkrnl.sys 可以验证 IHV 微型端口驱动程序支持 GUID\_热\_冷却\_接口 ACPI 查询此接口时。 在这种情况下，WHCK 可以接收错误日志的微型端口驱动程序失败的 GUID 的 DxgkDdiQueryInterface 调用\_热量\_冷却\_接口和 WHCK 测试。

<a name="device.graphics.wddm13.displayrender.wirelessdisplay"></a>
## <a name="devicegraphicswddm13displayrenderwirelessdisplay"></a>Device.Graphics.WDDM13.DisplayRender.WirelessDisplay

*可选功能集由 WDDM 1.3 驱动程序支持 Miracast 的功能实现。*

### <a name="devicegraphicswddm13displayrenderwirelessdisplaybasicwirelessdisplay"></a>Device.Graphics.WDDM13.DisplayRender.WirelessDisplay.BasicWirelessDisplay

*可选无线显示支持 WDDM1.3 驱动程序*

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

注意︰ 在 Windows 10 无线显示框架已显著使操作系统完成大部分的工作。 WDDM 2.0 驱动程序不适用于此节中的要求。 但是，现有 WDDM 1.3 驱动程序可以继续使用这种机制。

-   这是一项可选功能为 WDDM 1.3 驱动程序。

-   WDDM Miracast 用户模式驱动程序必须为单独的 DLL。

-   如果一个驱动程序支持 Miracast 显示，它必须列举一个 Miracast 目标以及其他受支持的目标。

-   驱动程序必须准确地报告到 Windows 的目标类型。 每当 Windows 连接到 Miracast 设备时，驱动程序必须使用新的目标类型，而不考虑 Miracast 结束点和显示设备之间的连接。

-   一旦建立 Miracast 会话，获得设备功能、 HDCP 协商已经发生，而且用户模式驱动程序已准备就绪，流到设备的显示驱动程序必须只在表明显示器的到达。

-   驱动程序必须使用新的 DDIs UMD KMD 之间的任何专用通信。 驱动程序必须为数据包状态轮询。

-   驱动程序必须使用新的 DDIs UMD KMD 之间的任何专用通信。 驱动程序必须为数据包状态轮询。

-   必须通过 DirectX Api 分配所有 gpu 的内存访问。 驱动程序不得划分或隐藏实现使用的内存。

-   为实现所使用的所有硬件必须都公开到 Windows，以便准确的电源管理。

-   无线显示驱动程序必须报告 v 同步。

-   驱动程序必须使用已发布的 Windows 用户模式从网络 Api 和 NW 驱动程序不能使用任何专用接口。

-   每次接收方请求了一个 i 帧，驱动程序必须登录它与使用新 DDI 的窗口。

-   如果 Miracast 设备支持音频，驱动程序必须枚举窗口类似于如何为 HDMI/显示端口枚举一个音频终结点。 音频设备的容器 ID 必须匹配相应 Miracast 的显示设备。

-   当 Windows 将 MC 显示设置为"显示器空闲"时，驱动程序必须设置"电源节能模式"进行了定义在标准 MC。 当用户提供输入继续从显示器空闲时，MC 显示必须取回到全功率和用户必须能够使用它，而无需重新连接。

-   用户模式的 Miracast 驱动程序必须完成新的 DDI 无法停止 Miracast 会话，在 3 秒内。

-   驱动程序必须符合相同的分辨率枚举要求与其他在 WHCK 中指定的目标类型。

-   中，物理上没有任何显示连接到 Miracast 接收器，然后驱动程序仍必须允许连接成功，但必须到 Windows 报告显示。 一旦显示物理连接，则驱动程序必须报告它到 windows。

-   用户实际将显示从 Miracast 接收器设备断开连接，驱动程序必须报告显示删除，Windows 将从会话断开连接。

-   WDDM 驱动程序必须能够通过 Miracast 支持 HDCP。

-   如果接收器设备不支持 HDCP，驱动程序必须仍会允许连接成功。

-   在驱动程序 TDR 的情况下，驱动程序应正确终止的会话。

<a name="device.graphics.wddm13.enhancedpowermanagement"></a>
## <a name="devicegraphicswddm13enhancedpowermanagement"></a>Device.Graphics.WDDM13.EnhancedPowerManagement

*图形核心电源管理增强功能*

### <a name="devicegraphicswddm13enhancedpowermanagementfstate"></a>Device.Graphics.WDDM13.EnhancedPowerManagement.FState

*F-状态滞后*

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

WDDM 1.3 引入一些电源管理增强功能。 如果再实施︰

延迟时间验证

从低功耗 F 状态过渡到一个更高，预计，完成转换所花费的时间将不会转换延迟时间对 10%以上报告驱动程序。

### <a name="devicegraphicswddm13enhancedpowermanagementvsync"></a>Device.Graphics.WDDM13.EnhancedPowerManagement.VSYNC

*雄心勃勃的垂直同步*

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

WDDM 1.3 引入一些电源管理增强功能︰

在阶段的垂直同步

启用垂直同步之后，98%的 Vsyncs 必须在 500 我们没有 Vsyncs 超过 1.5 毫秒以上的方差与所需的值。

<a name="device.graphics.wddm13.render"></a>
## <a name="devicegraphicswddm13render"></a>Device.Graphics.WDDM13.Render

*由 WDDM 1.3 驱动程序支持其呈现的基本特征集特定的 DDIs。*

### <a name="devicegraphicswddm13rendercheckddiboundaries"></a>Device.Graphics.WDDM13.Render.CheckDDIBoundaries

*混合图形*

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

**图形驱动程序不应回避 DDI 边界。**

-   允许系统级别或运行时级 API detouring – 不允许驱动程序截取 OS 系统或运行时调用，或修改 OS 系统或运行时 Api，通过传递参数或包装从 API 入口点返回的对象。

-   不允许访问和使用的内部数据结构。

-   允许没有驱动程序分层-允许一个用户模式/内核模式驱动程序被加载并运行库和内核二进制文件与通信。

### <a name="devicegraphicswddm13renderdirtyrect"></a>Device.Graphics.WDDM13.Render.DirtyRect

*可选的 DirtyRect WDDM1.3 驱动程序的支持*

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

WDDM1.3 引入了支持 DirtyRect 的能力。 如果实现了 DirtyRect，它必须遵循规范。

### <a name="devicegraphicswddm13rendergpunode"></a>Device.Graphics.WDDM13.Render.GPUNode

*图形核心性能*

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

如果实现了 WDDM1.3，则驱动程序必须︰

-   驱动程序必须指定一个有效的枚举值，为每个物理适配器的每个引擎。

-   驱动程序必须指定其中一个引擎类型 DXGK 的\_引擎\_类型\_3D 每个物理适配器。

-   为每个引擎，给定的枚举值必须满足的要求，DDI 的引擎定义表中所述。

### <a name="devicegraphicswddm13renderhighperformancetimingdata"></a>Device.Graphics.WDDM13.Render.HighPerformanceTimingData

*高性能图形计时数据*

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

"高性能图形计时数据"为图形的工作负载提供轻量和高详细计时数据。 这些数据用于分析工具来识别性能或其他图形相关的 Windows 应用程序中的问题或图形堆栈。

WDDM1.3 驱动程序必须确保图形驱动，提供了以下功能︰

-   高分辨率 GPU 计时器

    -   12.5 MHz （80ns 分辨率） 或更高。

    -   时间戳分辨率至少 32 位。

    -   在 GPU 中的所有引擎，可以抽样 GPU 时间戳。

    -   GPU 时间戳可以末尾的 GPU 管线进行抽样。

    -   GPU 时间戳频率可以进行抽样。

    -   GPU 时间戳是不变并且不受 p-状态转换。

<!-- -->

-   有关此功能的其他更改，这将包括添加了两个新标志，与现有的 DdiControlEtwLogging 接口;当设置了这些标志，以使第一个标志是值为 1，第二个标志是值为 0，然后驱动程序必须确保︰

    -   所有引擎组件必须都确保它们永远不会制或电源关只要标志将保持启用状态，并且一般情况下必须避免输入任何空闲状态。 这些组件必须保持活动状态，以确保没有由于电源转换添加没有延迟。

    -   所有引擎组件必须都确保在其操作值的最大稳定保持其处理频率和功能的总线带宽。 热量要求下的 P-状态转换的事件仍然发生以防止损坏的硬件，但应定义 P-状态，这样，这些都是不正常情况下看到很棒的实验室环境中的卓越事件。

<!-- -->

-   样本的 GPU 时间戳可以将与以前发出的图形命令关联起来。

-   计时数据的生成默认情况下处于关闭状态，但可以打开和关闭任何时候。

-   收集性能数据的开销比不使用已在 D3D9 和 D3D10 + 中可用的时间戳查询技术。

-   可以通过在第 9 级硬件功能上，D3D9 驱动程序和硬件功能级别 10 + 的 D3D10 驱动程序收集计时数据。

-   结果基于图块上的数据延迟呈现硬件出现如同它生成即时模式呈现的设备上。

### <a name="devicegraphicswddm13renderpresentoverheadoptimization"></a>Device.Graphics.WDDM13.Render.PresentOverheadOptimization

*现开销的优化*

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

WDDM1.3 驱动程序必须支持新的 DDI，Present1，以及通过 D3D11 DDI 功能 10 + 硬件上通过 D3D9 DDI，9 功能级硬件。 功能级别 10 + 硬件上的 WDDM1.3 驱动程序可以选择支持此功能通过 D3D9 DDI;但是，这种支持应符合对所有其他可选性能支持的功能 （例如，共享面） 的支持。

若要在使用 Present1 时，请确保所需的性能特性，以下是必需的︰

-   重新构造新呈现 DDI 必须与通过传统多呈现相同单存在 DDI 调用。

-   驱动程序必须只调用存在回调 DDI 调用每次 （并不是一次每个资源）。

### <a name="devicegraphicswddm13rendersharedsurfacesupport"></a>Device.Graphics.WDDM13.Render.SharedSurfaceSupport

*共享的表面支持*

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

WDDM1.3 驱动程序必须支持这些新的格式和功能共享的曲面︰

-   9 级硬件的驱动程序支持新格式

    -   A8\_UNORM

    -   R8\_UNORM

    -   R8G8\_UNORM

-   驱动程序在新格式中支持共享的曲面 (A8\_UNORM，R8G8\_UNORM、 R8\_UNORM、 BC1\_\*，BC2\_\*，和 BC3\_\*) 通过以下能力以及通过 D3D11 DDI 功能 10 + 硬件上通过 D3D9 DDI，9 功能级硬件。 功能级别 10 + 硬件上的 WDDM1.3 驱动程序可以选择支持此功能通过 D3D9 DDI;但是，这种支持应符合对所有其他可选性能支持的功能 （例如，存在开销） 的支持。

    -   资源共享;

    -   可以使用资源，如呈现器目标;

    -   可以混合的资源;

    -   资源可以进行筛选;

    -   可以访问的资源。

### <a name="devicegraphicswddm13displayrendermultiplaneoverlaysupport"></a>Device.Graphics.WDDM13.DisplayRender.MultiplaneOverlaySupport

*多平面覆盖支持*

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

所有 WDDM 1.3 显示驱动程序必须都报告多平面叠加使用 DDI 多平面叠加支持 DDI 规范定义的硬件功能。 WDDM 1.3 驱动程序声称支持多平面贴必须满足所有下列硬件条件︰

1.  硬件必须支持非重叠的平面。

    -   而另一平面可以涵盖不同，相互排斥，大部分屏幕一个平面可覆盖屏幕的一部分。

    -   如果没有未涵盖的平面屏幕中的任何部分，硬件必须扫描出该区域为黑色。 硬件可以假定是一个虚拟的平面处用黑色填充的最底部的 Z 顺序。

2.  硬件必须支持重叠的平面。 必须支持混合使用预先相乘得到的 alpha 的平面之间。 硬件必须能够启用/禁用 alpha 混合在每个平面的基础上。

3.  只有一个输出活动时，活动的输出必须支持多平面叠加。 对于多个输出在哪里同时处于活动状态的复制模式，硬件不应该报告它支持多平面叠加，除非所有活动的输出支持多平面叠加。

4.  DWM 的 swapchain （平面 0） 必须能够与其他覆盖平面交互。

5.  所有平面都必须能够启用和禁用，包括平面 0 (DWM 的 swapchain)。

6.  源和目标剪辑，包括平面 0 (DWM 的 swapchain)，则必须支持所有平面。

7.  收缩和拉伸，独立于其他可能启用的平面必须支持至少一个平面。

8.  支持缩放的平面必须支持这两个双线性过滤，且比双线性过滤质量。

9.  必须支持至少一个平面︰

    -   601 和 709 YUV 转换 RGB 矩阵的 YUV 格式。

    -   正常范围 YUV 明亮度 (16-235) 和全范围 YUV 明亮度 (0-255)。

10. 必须处理以下寄存器闭锁方案︰

  -   所有-平面特性 （缓冲区地址，剪切、 缩放、 等） 必须以原子方式张贴上垂直回描周期中。 当更新块中的寄存器，它们必须全部过帐以原子方式 （例如，如果编写 10 20 寄存器属于覆盖平面的其中任何一个可以开机自检直到下一个垂直同步因为他们不能全部张贴在当前垂直同步发生垂直同步）。

  -   可以从其他平面单独更新每个平面。 例如，如果已在垂直同步之前更新平面 0 寄存器和我们更新平面 1 注册垂直同步发生时，平面 1 更新可以等到下一个垂直同步，但在时间发生更新的平面 0。

  -   期间有一次更新多个平面后，应以原子方式进行更新。 例如，如果调用单个存在正在更新 0 并使平面平面 1，0 寄存器在垂直同步不应进行发布，除非平面 1 还注册相同的垂直同步开机的平面。

11.  转换时，缩放和混合应该发生如下 （按指定的顺序）︰

  -   根据指定的源矩形剪辑源分配。 保证源矩形之间的内源分配大小。

  -   如果请求，应用水平图像翻转，然后垂直图像翻转。

  -   应用比例根据目标矩形、 将剪辑的剪辑矩形，根据应用和应用适当的筛选，在缩放时。

  -   混合使用在其它图层分配。 混合应从上到下 （或直到命中不透明层） 在 Z-顺序中。 如果 alpha 混合请求，硬件必须遵守每个像素的字母和颜色值预乘以 alpha。 伪代码指示下，反复从上到下，这对目标执行"源"操作 (((层\[0\]通过层\[1\]) 通过层\[2\]) 对... 图层\[n\])。 外部的目标矩形中，每一层都必须视为透明 (0,0,0,0)。

> 颜色颜色 =\[0\];0 层是最顶层元素。
>
> Alpha 颜色 =\[0\]。字母;
>
> 为 (i = 1;字母&lt;1 & & i &lt; LayersToBlend;i + +）
>
> {
>
> 颜色 + = ((1-Alpha)\*颜色\[i\]);
>
> Alpha + = ((1-Alpha)\*颜色\[i\]。Alpha);
>
> }
>
> 输出颜色;

如果硬件融合从下到上，只要是相同的输出结果，是确定。 在这种情况下，应使用下面的混合算法︰

> 颜色颜色 =\[LayersToBlend 1\];最下面的大多数层
>
> Alpha 颜色 =\[LayersToBlend 1\]。字母;
>
> 如果 (LayersToBlend &gt; 1)
>
> {
>
> 为 (i = LayersToBlend-2;字母&lt;1 & & i &gt;= 0;i)
>
> {
>
> 颜色 = 颜色\[i\] + (1 – 颜色\[i\]。Alpha)\*颜色;
>
> Alpha 颜色 =\[i\]。Alpha + (1 – 颜色\[i\]。Alpha)\*字母;
>
> }
>
> }
>
> 输出颜色;

-   必须在区域显示黑色在不受任何图层中的目标矩形中的任何位置。 硬件可以假定没有概念的虚拟黑色底大多数是屏幕的大小的图层。


### <a name="devicegraphicswddm13rendertrimsupport"></a>Device.Graphics.WDDM13.Render.TrimSupport

*Direct3D 修剪*

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

修剪 API 是 D3D9 UM DDI WDDM1.3 更新新手。 图形设备必须支持此 API 和驱动程序必须执行以下操作︰

-   设备调用修剪后，图形驱动程序的内存使用量必须返回到其用法的 5%内初始设备创建后。

-   调用修剪后呈现操作的图形驱动程序的响应速度必须首次 Direct3D 设备创建后的驱动程序相媲美。

-   调用修剪不得更改的 Direct3D 设备状态 – 所有呈现操作应都继续正常计算。

<a name="device.graphics.wddm20"></a>
## <a name="devicegraphicswddm20"></a>Device.Graphics.WDDM20

### <a name="devicegraphicswddm20corerequirement-if-implemented"></a>Device.Graphics.WDDM20.CoreRequirement （如果实现）  

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

<ol style="list-style-type: decimal">
<li><p>Core.MemoryResidencyModel</p>

<p>WDDM 2.0 驱动程序必须满足所有要求 WDDM 2.0 规范中定义。</p>
<p>驱动程序必须支持 WDDM 2.0 管理常驻内存，内存分配模型规范中定义的新模型。</p>
<p>对于每个 D3D 设备驱动程序必须显式创建一个或多个分页队列。 必须完成同步操作的页面队列使用监控范围。 修剪的异步回调可能发生 UMD 必须处理通过退出资源直到内存使用量低于指定的限额为止。</p>
<p>必须为每个 D3D 设备通过 UMD 维护派驻在内存中的资源的列表。 UMD 必须使用修剪/刷新/等待应用程序超过其分配的内存使用的情况下取得了进展。</p>
<p>对于 D3D11 和早期版本的兼容性，UMD 必须管理派驻服务基于绑定和解除绑定操作。</p>
<p>UMD 必须处理优惠并回收以不同的方式请求以正确保持派驻服务列表。</p>

<table>
<thead>
<tr class="header">
<th>功能名称</th>
<th>适用 DX H/W 类</th>
<th>完整的图形驱动程序</th>
<th>呈现只有驱动程序</th>
<th>唯一的显示驱动程序</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>MakeResident 和退出</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>Lock2 支持</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>被监视的围墙支持</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>GPU 同步点</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>修剪回叫支持</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>提供/回收支持</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>MakeResident 和退出</td>
<td>所有</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
</tbody>
</table>
</li>

<li><p>虚拟内存︰</p>

<p>WDDM 2.0 驱动程序必须满足 WDDM 2.0 规范中定义的所有要求。</p>
<p>驱动程序必须支持新的模型 WDDM 2.0 管理内存分配。</p>
<p>实现 GPU 虚拟寻址的所有引擎必须都支持 GPU 虚拟内存 DDI 规范包括相关功能位设置中定义的功能。</p>
<p>对所有资源的引用都必须通过其虚拟地址和虚拟地址资源的生存期内必须保持恒定。</p>
<p>它是必需的以支持每个 GPU 每个进程的逻辑适配器的单 GPU 地址空间。</p>
<p>支持虚拟地址必须支持 GPUMMU 引擎模型虚拟寻址，并不能有任何依赖物理寻址。 对虚拟寻址的 iommu 取消模型的支持是可选的。</p>
<p>驱动程序必须支持多层级的页表，并且必须支持 4KB 和 64KB 页表的混合。</p>
<p>必须通过孔径段可寻址显示和集成 Gpu 的捕获曲面。</p>
<p>显示曲面离散 Gpu 中的必须从内存段连续分配。</p>

<table>
<thead>
<tr class="header">
<th>功能名称</th>
<th>适用 DX H/W 类</th>
<th>完整的图形驱动程序</th>
<th>呈现只有驱动程序</th>
<th>仅显示</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>虚拟分页支持</td>
<td>所有</td>
<td>如果实现了 VA</td>
<td>如果实现了 VA</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>多层级的页表支持</td>
<td>所有</td>
<td>如果实现了 VA</td>
<td>如果实现了 VA</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>通过并行 4k/64 K 页表</td>
<td>所有</td>
<td>如果实现了 VA</td>
<td>如果实现了 VA</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>基于页面的内存段管理</td>
<td>所有</td>
<td>如果实现了 VA</td>
<td>如果实现了 VA</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>平铺的资源</td>
<td>DX11.1 +</td>
<td>必填字段</td>
<td>必填字段</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>可编程的 CPU 主机口径支持</td>
<td>所有</td>
<td>如果适用</td>
<td>如果适用</td>
<td>N/A</td>
</tr>
<tr class="odd">
<td>LDA 的支持</td>
<td>所有</td>
<td>如果适用</td>
<td>如果适用</td>
<td></td>
</tr>
</tbody>
</table>
</li>

<li><p><strong>将默认映射</strong></p>

<p>显示驱动程序的 D3D11/D3D12 必须满足所有要求在<strong><em>D3D 11/D3D12 规格</em></strong>。</p>
<p>由 CPU 访问这些页面时，它们必须能够标记为回写或 cpu 的写组合。   默认情况下，使用的内存如果启用 CPU 读取 CPU 访问纹理必须标记为回写。  如果启用 CPU 写内存必须标记为写的组合，除高速缓存相干性 UMA 设计上。</p>
<p>间距线性需求&amp;限制如下︰</p>

<ul>
<li><p>基本地址 / 偏移量的映射的资源必须至少 16 字节对齐。</p></li>
<li><p>压缩的呈现目标必须能够解析要启用 CPU 读 / 写的纹理。</p></li>
</ul>

<p>内存要求&amp;限制如下︰</p>

<ul>
<li><p>基本地址 / 偏移量的映射的资源必须至少 16 字节对齐。</p></li>
<li><p>压缩的呈现目标必须能够解析要启用 CPU 读 / 写的纹理。</p></li>
<li><p>纹理必须驻留在系统内存中</p></li>
<li><p>不得重命名或卷影复制的结果映射纹理</p></li>
<li><p>纹理映射时不能使用 swizzle 范围</p></li>
</ul>
<ul>
<li><p>GPU 时 GPU 支持标准 swizzle，必须尽可能以正交方式为其他纹理，如纹理中，呈现为，将复制到支持所有多维操作&amp;从，re-swizzle 到&amp;，等等。</p>
<ul>
<li><p>块压缩格式和 ASTC 格式元素大小必须是相同的块大小。</p></li>
<li><p>GPU 必须支持从所有引擎，包括扫描出标准 swizzle。</p></li>
<li><p>压缩的呈现目标必须能够解析要启用 CPU 读 / 写的纹理。</p></li>
</ul></li>
</ul>
<p>标准的 swizzle 数据必须为 4KB 和 64KB 页面边界对齐。</p>
</li>
</ol>

业务理由︰

WDDM 2.0 引入了全新的功能和 DDI 变化方式最适合下一版本的 Windows。


<a name="device.graphics.wddm20.core"></a>
## <a name="devicegraphicswddm20core"></a>Device.Graphics.WDDM20.Core

*通过支持 WDDM2.0 的驱动程序实现的基本功能集。*

### <a name="devicegraphicswddm20corebase-if-implemented"></a>Device.Graphics.WDDM20.Core.Base （如果实现）

WDDM2.0

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

如果它们不支持 D3D12，图形驱动程序 （可选） 可以实现 WDDM 2.0。 但是，D3D12 支持，需要使用 WDDM 2.0。

Windows 10 引入一组新的功能和将被称为 WDDM2.0 的 DDI 变化。 WDDM2.0 的实现是可选的但这是必须实现支持 D3D12 的驱动程序。 如果实现，就必须遵循 WDDM2.0 规范。

**D3D 要求︰**

<table>
<thead>
<tr class="header">
<th>DirectX 硬件</th>
<th>KMD 要求</th>
<th>UMD 要求</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D3D9</td>
<td>要求︰ WDDM 2.0</td>
<td>要求︰ D3D9-UMD DDI</td>
</tr>
<tr class="even">
<td>D3D10</td>
<td>要求︰ WDDM 2.0</td>
<td>要求︰ D3D9-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D10-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D11.1-UMD DDI</td>
</tr>
<tr class="odd">
<td>D3D10.1</td>
<td>要求︰ WDDM 2.0</td>
<td>要求︰ D3D9-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D10-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D10.1 的 UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D11.1-UMD DDI</td>
</tr>
<tr class="odd">
<td>D3D11</td>
<td>要求︰ WDDM 2.0</td>
<td>要求︰ D3D9-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D10-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D10.1 的 UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D11-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D11.1-UMD DDI</td>
</tr>
<tr class="even">
<td>D3D11.1</td>
<td>要求︰ WDDM 2.0</td>
<td>要求︰ D3D9-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D10-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D10.1 的 UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D11-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D11.1-UMD DDI</td>
</tr>
<tr class="odd">
<td>D3D12</td>
<td>要求︰ WDDM 2.0</td>
<td>要求︰ D3D9-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D10-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D10.1 的 UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D11-UMD DDI</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td>要求︰ D3D11.1-UMD DDI</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td>要求︰ D3D12-UMD DDI</td>
</tr>
</tbody>
</table>

<a name="device.graphics.wddm20.displayrender"></a>
##Device.Graphics.WDDM20.DisplayRender

*父功能节点的显示的影响，并呈现 GPU 的要求。*

### <a name="devicegraphicswddm20displayrenderhardwarecontentprotection"></a>Device.Graphics.WDDM20.DisplayRender.HardwareContentProtection

*GPU 必须支持基于硬件的内容保护。*

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

下一版本的 Windows 的 GPU 驱动程序必须遵守的图形-D3D11 内容保护 DDI 规范。 

GPU 的驱动程序和硬件必须通过 Microsoft 硬件内容保护测试。 

需要网络连接和 PlayReady 内容保护访问测试服务器。

<a name="device.graphics.wddm20.display.virtualmodesupport"></a>
## <a name="devicegraphicswddm20displayvirtualmodesupport"></a>Device.Graphics.WDDM20.Display.VirtualModeSupport

### <a name="devicegraphicswddm20displayvirtualmodesupportcorerequirement-if-implemented"></a>Device.Graphics.WDDM20.Display.VirtualModeSupport.CoreRequirement （如果实现）

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

**说明**︰

WDDM2.0 驱动程序必须报告支持通过新的 VirtualModeSupport 成员在 DXGK 虚拟分辨率更改和 DWMClone，\_显示\_DRIVERCAPS\_扩展，通过将 VirtualModeSupport 设置为 1，当操作系统调用 DXGKQAITYPE DxgkDdiQueryAdapterInfo\_显示\_DRIVERCAPS\_扩展名。 

<a name="device.graphics.wddm21"></a>
## <a name="devicegraphicswddm21"></a>Device.Graphics.WDDM21

WDDM 2.1 是生成大于 10586 引入 Windows 10 的可选版本级别。 如果一个驱动程序实现 WDDM 2.1 它必须实现所有 WDDM 2.1 要求。 WDDM 2.0 驱动程序将继续在更高版本的 Windows 上运行 10 个版本。

### <a name="devicegraphicswddm21corerequirement-if-implemented"></a>Device.Graphics.WDDM21.CoreRequirement （如果实现）

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

**说明**︰

WDDM 2.1 驱动程序必须满足 WDDM 2.1 规范中定义的所有要求。 特别是，驱动程序应实现以下 （取决于硬件功能）︰

1.  产品/回收

    WDDM 2.1 驱动程序必须支持对提议的更改 / 回收功能。

2.  视频的受保护区域

    硬件实现单范围 VPR （视频受保护地区） 必须支持新移动寻呼 DDIs 这样 VPR 可以进行碎片整理。

3.  大页面 PTE 编码

    如果硬件支持较大的页面 Pte，如 64 KB，这些受 WDDM 2.1 和应该实现。

4.  前/后存在优化

    对于涉及前/后存在优化方案使新回调 WDDM 2.1 (UpdateAllocationProperties) 中。 这是可选的。

### <a name="devicegraphicswddm21flipqueuelatency-if-implemented"></a>Device.Graphics.WDDM21.FlipQueueLatency （如果实现）

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

**说明**︰

WDDM2.1 驱动程序必须支持 64 位 PresentID 成员 DXGK\_MULTIPLANE\_覆盖\_垂直同步\_INFO2 分配给每个特定 MPO 平面翻转的请求。 此值将在翻转请求的时间传递到驱动程序，驱动程序必须报告回垂直同步 ISR 回调中的当前已确认的 PresentId 值。

多个相同的 MPO 平面上的垂直翻转上同步请求进行排队的能力必须受中 DXGK 的 MaxQueuedMultiPlaneOverlayFlipVSync 成员\_DRIVERCAPS。

对于不能支持多个飞行垂直翻转上同步请求中的硬件，则驱动程序必须 MaxQueuedMultiPlaneOverlayFlipVSync 设置为 1。

如果操作系统通过非负 MaxImmediateFlipLine (成员 DXGK\_MULTIPLANE\_覆盖\_PLANE3) 到驱动程序和驱动程序检测到的硬件尚未开始扫描从水平线&gt;= MaxImmediateFlipLine，驱动程序必须为新曲面执行立即翻转。

转换后的立即翻转将覆盖以前挂起的垂直翻转上同步的情况下，驱动程序必须报告立即翻转转换成功。

驱动程序必须在垂直同步 ISR 回调将 GPU 时钟和频率值传递 (DXGKARGCB\_通知\_中断\_数据)。

