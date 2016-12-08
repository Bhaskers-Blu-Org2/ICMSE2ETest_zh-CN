---
title: Device.Imaging.Printer
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: c8f7a0e9c4f0eff60951f4f20000208cb5a72f65
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceimagingprinter"></a>Device.Imaging.Printer

 - [Device.Imaging.Printer.Base](#device.imaging.printer.base)
 - [Device.Imaging.Printer.Mobile](#device.imaging.printer.mobile)
 - [Device.Imaging.Printer.Mobile.WSD20](#device.imaging.printer.mobile.wsd20)
 - [Device.Imaging.Printer.OXPS](#device.imaging.printer.oxps)
 - [Device.Imaging.Printer.USB](#device.imaging.printer.usb)
 - [Device.Imaging.Printer.WSD](#device.imaging.printer.wsd)
 - [Device.Imaging.Printer.XPS](#device.imaging.printer.xps)

<a name="device.imaging.printer.base"></a>
## <a name="deviceimagingprinterbase"></a>Device.Imaging.Printer.Base

### <a name="deviceimagingprinterbaseapplicationverifier"></a>Device.Imaging.Printer.Base.applicationVerifier

*打印机驱动程序组件必须遵守应用程序验证工具测试条件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有用户模式模块 （.dll 文件或.exe 文件） 的打印机驱动程序的一部分必须都满足应用程序验证工具测试的条件。 驱动程序在测试期间，应用程序验证工具必须打开驱动模块在其中执行的进程。 应用程序验证工具检测到错误时，应用程序验证工具会引起的中断。
打印机驱动程序，必须在测试过程中打开的应用程序验证工具的常用应用程序如下所示︰

-   Splwow64.exe。

-   Spoolsv.exe。 该进程加载打印测试期间呈现和驱动程序的用户界面部分。

-   Printfilterpipelinesvc.exe。 该进程加载的 XPS 呈现的筛选器。

-   任何供应商提供的应用程序属于该驱动程序包，如自定义状态监视器。 被签名的驱动程序文件包的所有部分必须都是强健的。

-   加载驱动程序的模块，用于呈现或 UI 目的的任何测试。 这些测试通常加载 UI 和呈现模块。

下面的应用程序验证工具测试必须打开这些进程的测试过程︰

-   堆
-   锁定
-   处理
-   可
-   HighVersionLie
-   DFWChecksNonSetup
-   SecurityChecks
-   打印

*设计备注*

应用程序验证工具有关的信息，请参阅<http://go.microsoft.com/fwlink/?LinkId=58371>*.*

### <a name="deviceimagingprinterbaseconfigurationfiles"></a>Device.Imaging.Printer.Base.configurationFiles

*版本 4 打印驱动程序必须提供有效的配置文件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

版本 4 打印驱动程序必须提供有效的配置文件。

-   这些文件必须符合 WDK 的语法有效。

-   当硬件支持的配置文件必须支持下列功能︰

    -   方向
    -   双面打印
    -   Collate
    -   每多
    -   纸张大小
    -   纸张类型
    -   送纸器
    -   质量
    -   颜色
    -   装订
    -   孔冲孔
    -   绑定

-   GPD 或 PPD 文件应定义的大多数功能和约束中驱动程序的 PrintCapabilities 表示。 根据需要 JavaScript 实现应补充这些功能。

-   JavaScript 文件必须符合 WDK 的语法有效。

    -   它们必须包含在该驱动程序包，并且不能包中的子目录中。

    -   他们可能只包括在版本 4 打印驱动程序。

    -   他们应该安全地设计和验证任何不可靠的数据，将对其进行分析;这包括 PrintCapabilities、 PrintTicket、 XPS 文档和属性包。

### <a name="deviceimagingprinterbaseconnectionrecovery"></a>Device.Imaging.Printer.Base.connectionRecovery

*打印机必须继续正常工作，如果在打印作业过程中，计算机变得不可用。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

如果计算机不可用 （例如，如果计算机进入睡眠状态或网络故障或其他事件会中断计算机和打印机之间的连接） 在打印作业期间，打印机必须恢复，以便继续进行正常的打印操作而无需用户交互。

*设计备注*

特别是，打印机必须不失败状态的最终用户必须手动重新启动打印机或清除卡纸。
打印机没有完成或当计算机再次可用时继续失败的打印作业。 但是，当计算机与打印机通信恢复，新打印作业必须能够后台和正常完成。

### <a name="deviceimagingprinterbasedevicecapabilities"></a>Device.Imaging.Printer.Base.deviceCapabilities

*打印机必须正确支持 DeviceCapabilities 和 GetDeviceCaps 应用程序编程接口 (Api) 基于 Windows 驱动程序工具包中的准则。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求阐明了现有 WLK 测试使用。 打印驱动程序设备功能测试确定打印机驱动程序是否返回的**DeviceCapabilities**和**GetDeviceCaps** API 调用的正确信息。
有关详细信息，请参阅<http://msdn.microsoft.com/en-us/library/dd183552.aspx>和<http://msdn.microsoft.com/en-us/library/ff566075.aspx>*.*

### <a name="deviceimagingprinterbasedrivercategory"></a>Device.Imaging.Printer.Base.driverCategory

*版本 4 的打印机驱动程序必须声明有效的打印机类别。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

所有的 V4 打印机驱动程序必须声明其驱动程序清单中的有效 DriverCategory。 V3 打印机驱动程序不需要声明一个类别。  如果 V3 的打印机驱动程序 does 声明 DriverCategory，它必须是有效的值。

DriverCategory 必须是以下值之一︰

-   PrintFax.Printer
-   PrintFax.Fax
-   PrintFax.Printer.File
-   PrintFax.Printer.Virtual
-   PrintFax.Printer.Service


### <a name="deviceimagingprinterbasedriverpdc-if-implemented"></a>Device.Imaging.Printer.Base.DriverPDC （如果实现）

INF 文件必须具有正确的语法，当 PWG 光栅呈现筛选器是包含

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**︰

所有的 v4 打印驱动程序使您能够使用 PrintDeviceCapabilities 数据文件的类型都必须正确地实现他们的 PrintDeviceCapabilities 文件。 驱动程序使您能够使用 PWG 光栅标准呈现筛选器必须提供 PrintDeviceCapabilities 数据文件，这符合这一要求。

### <a name="deviceimagingprinterbasegdlfile"></a>Device.Imaging.Printer.Base.GDLFile

*GDL 文件必须在 Windows 驱动程序工具包中使用正确的语法根据的准则。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求阐明了现有 WLK 测试使用。 一般说明语言 (GDL) 正确性测试确定 GDL 文件是否使用 WDK 根据正确的语法。
有关详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff549787.aspx> *和* <http://msdn.microsoft.com/en-us/library/ff563355.aspx>*.*

### <a name="deviceimagingprinterbaseinffile"></a>Device.Imaging.Printer.Base.infFile

*INF 文件必须使用 Windows 驱动程序工具包中根据准则的正确语法。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求阐明了现有 WLK 测试使用。
INFGate 确定 INF 文件和 v4 清单使用 WDK 根据正确的语法。
打印驱动程序的版本 4 使用版本 4 Inf 和清单文件。
V4 驱动程序 INF 必须︰

-   定义每个驱动程序 PrinterDriverID 来指示为打印机共享兼容的驱动程序 INF 中。

   -   PrinterDriverID 必须是一个 GUID。

-   设置数据文件为 GPD 或 PPD 文件。

-   使用仅以下 DestinationDirs: DriverStore，66000;或颜色目录，66003。

-   指定命名筛选 xml 管道配置文件\*-应，或 v4 驱动程序清单中指定 RequiredClass。

V4 驱动程序清单文件必须︰

-   定义每个驱动程序 PrinterDriverID 来指示为打印机共享兼容的驱动程序的清单中。

   -   PrinterDriverID 必须是一个 GUID。

-   设置数据文件为 GPD 或 PPD 文件。

不可以 V4 驱动程序︰

-   利用以下的 INF 指令 ClassInstall32、 ClassInstall32.Services、 DDInstall.Services、 DDInstall.HW、 DDInstall.CoInstallers、 DDInstall.FactDef、 DDInstall.LogConfigOverride、 DDInstall.Interfaces、 InterfaceInstall32、 DefaultInstall、 DefaultInstall.Services、 AddReg、 DelReg、 DelFiles、 RenFiles、 AddService、 DelService、 AddInterface、 BitReg、 LogConfig、 UpdateInis、 UpdateIniFields 或 Ini2Reg。

版本 3 的 INF 文件必须使用 WDK 根据正确的语法。
V3 INF 文件的详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff560902.aspx> *和* <http://msdn.microsoft.com/en-us/library/ff563414.aspx>*.*



### <a name="deviceimagingprinterbaseprintprocessor"></a>Device.Imaging.Printer.Base.printProcessor

*打印处理器必须基于 Windows 驱动程序工具包中的指导原则来实现。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求阐明了现有 WLK 测试使用。 打印处理器 API 测试有助于确保基于 WDK 准则实现打印处理器。
所有的打印处理器必须支持下列终结点︰

-   OpenPrintProcessor
-   ClosePrintProcessor
-   ControlPrintProcessor
-   EnumPrintProcessorDatatypesW
-   PrintDocumentOnPrintProcessor
-   GetPrintProcessorCapabilities

有关详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff566084.aspx>*.*

### <a name="deviceimagingprinterbaseprintregions"></a>Device.Imaging.Printer.Base.printRegions

*打印机必须准确地支持可打印区域。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

打印机必须能够打印输出的可打印区域，用户可以选择 Windows 用户界面中显示的整个区域。

*设计备注*

请注意，是否打印机支持"无边框"打印功能，此限制可能会放宽允许对设备的可打印区域超出物理介质纸的尺寸。 在这些情况下，打印机必须能够打印输出的页面维度的范围内。

此测试将应用于实际，则打印机支持的所有纸张大小。 如果打印机支持自动缩放用户界面公开不能实际加载到打印机的用户的其他纸张大小，打印机必须在调整大小时保持正确的纵横比。 在此上下文中，"自动调整"是任何硬件或更改打印作业以适合可用的纸张大小，而无需用户交互或警告的驱动程序中的新功能。

如果打印机不支持在物理介质上打印最少 4 x 4 英寸大小，打印机是免于这种要求。

### <a name="deviceimagingprinterbaseprintticket"></a>Device.Imaging.Printer.Base.printTicket

*打印机驱动程序必须支持 PrintTicket/PrintCapabilities。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

打印设备必须完全支持的**PrintTicket**和**PrintCapabilities**对象。 这取决于您的打印驱动程序的实现，这可能会或可能不需要实施某些**PrintTicket**或**PrintCapabilities**接口。 有关详细信息，请参阅 WDK 文档。

打印机驱动程序必须支持公共的打印架构元素类型，每个关键字，如果打印设备的打印机驱动程序中包含指定的功能。 打印机驱动程序必须为每个关键字也支持公共的打印架构元素类型，是否存在，但不可配置相应的功能。 打印机驱动程序必须支持每个关键字的元素类型包括所有此类功能、 选项、 ParameterDef、 ParameterRef、 属性和公共的打印架构定义中包含的 ScoredProperty。 打印机驱动程序不需要支持公共打印架构关键字，如果打印设备的打印机驱动程序不包含指定的功能。

打印机驱动程序必须支持下列基本的打印架构元素类型︰

-   DocumentCollate
-   JobCopiesAllDocuments
-   JobDuplexAllDocumentsContiguously
-   PageColorManagement
-   PageImageableSize
-   PageMediaSize
-   PageMediaType
-   PageOrientation
-   PageOutputColor
-   PageResolution
-   PageICMRenderingIntent
-   下列情况之一︰ JobInputBin、 DocumentInputBin 或 PageInputBin

### <a name="deviceimagingprinterbaserendering"></a>Device.Imaging.Printer.Base.rendering

*打印机必须正确提交打印作业。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

这一要求阐明了使用以下现有 WLK 测试以确保打印机正确地呈现打印作业︰

-   Pgremlin/Pgremlin2

    此测试会生成大量输出的页面，包括形状、 渐变填充、 alpha 混合和一些复杂的字体。 该测试检查可以使驱动程序的设备驱动程序接口 (DDI) 电话。

-   WinFX 标记内容呈现测试

    WinFX 标记内容呈现测试加载八个 WinFX XAML 文件并生成指定的打印机上输出。

-   照片打印测试

    照片打印测试打印横向和纵向方向的照片，以试验打印机功能。

有关 Pgremlin 的详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff566081.aspx>*.*
有关 Pgremlin2 的详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff566079.aspx>*.*
WinFX 标记内容呈现测试有关的详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff569275.aspx>*.*
有关照片打印测试的详细信息，请参阅<http://msdn.microsoft.com/en-us/library/ff565234.aspx>*.*

### <a name="deviceimagingprinterbasetcpmon"></a>Device.Imaging.Printer.Base.TCPMon

*支持使用 Microsoft 标准端口监视器 (TCPMon) 端口 9100 打印的网络连接的打印机必须为设备提供丰富的状态。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

如果打印机使用的网络接口端口连接，并支持端口 9100 在使用 Microsoft 标准端口监视器 (TCPmon) 打印 （raw 打印），它还必须支持简单网络管理协议 (SNMP)、 主机资源管理信息基 (MIB)，和常见的打印机 MIB 和打印机端口监视器 MIB 1.0 （IEEE-ISTO5107.1-2005 年），以便操作系统可以为设备提供丰富的状态。

<a name="device.imaging.printer.mobile"></a>
## <a name="deviceimagingprintermobile"></a>Device.Imaging.Printer.Mobile

### <a name="deviceimagingprintermobilemobile-if-implemented"></a>Device.Imaging.Printer.Mobile.Mobile （如果实现）

打印机必须实现以下各项中的说明，以确保功能正常

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**︰

<html>
    <ol style="list-style-type: decimal">
        <li>
            <p>打印机必须实现&quot;MobilePrint&quot;在他们的 WS-发现邮件 PNP-X DeviceCategory 元素的类别定义。</p>

            <p>Devices which support Windows Mobile Printing must add the &quot;MobilePrinter&quot; category to their WS-Discovery ThisModel response.</p>
            <p>The following table provides additional information about the MobilePrinter category keyword.</p>

            <table>
                <thead>
                    <tr class="header">
                        <th>Constant/Value</th>
                        <th>Description</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="odd">
                        <td>
                            <p>PNPX_DEVICECATEGORY_PRINTER_MOBILE</p>
                            <p>L&quot;MobilePrinter&quot;</p>
                        </td>
                        <td>
                            <p>MobilePrinter category</p>
                            <p>Keywords: Printer</p>
                        </td>
                    </tr>
                </tbody>
            </table>
        </li>

        <li><p>V4 print drivers that use PrintDeviceCapabilities must ensure that it is correctly defined by including a PrintDeviceCapabilities DataFile.</p></li>

        <li><p>If a v4 print driver includes the PWG Raster standard rendering filter, then a PrintDeviceCapabilities DataFile must be included.</p></li>
    </ol>
</html>


### <a name="deviceimagingprintermobilepdl-if-implemented"></a>Device.Imaging.Printer.Mobile.PDL （如果实现） 

具有移动打印功能的打印机必须支持以下 PDLs 之一，符合它的相关要求。

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**PWG 光栅**

打印机支持 PWG 光栅必须符合 PWG 光栅行业标准，并实现以下要求。

<html>
    <ol style="list-style-type: decimal">
        <li><p>按照 PWG 5102.4 2012年中所述的所有规则。</p></li>
        <li><p>支持双面打印设备必须支持 InsertPage 指令。</p></li>
        <li><p>设备必须使用所有颜色的格式和分辨率的 PrintDeviceCapabilities 文件中公布。</p></li>
        <li><p>设备必须支持所有公布的 psk:PageMediaSizes 从 PrintDeviceCapabilities 文件时编码 PWG 光栅页标题，根据 PWG 5101.1 定义的自我描述的媒体名称。</p></li>
        <li>
        <p>设备必须支持下列颜色格式之一︰</p>
            <ul>
                <li><p>Srgb_8</p></li>
                <li><p>Cmyk_8</p></li>
                <li><p>Sgray_8</p></li>
            </ul>
        </li>
        <li><p>支持 WS 打印 v2.0 设备必须表明至少一个 psk:PageResolution 这是小于或等于 360 dpi 的支持。</p></li>
        <li><p>为了使移动的兼容模式下，设备必须支持 300 DPI 输出</p></li>
        <li><p>对于移动兼容模式，设备必须接受字母或 A4 格式。</p></li>
    </ol>
    <p><strong>PCLm</strong></p>
    <p>打印机支持 PCLm 必须符合行业标准，并实现以下要求。</p>
    <ol style="list-style-type: decimal">
        <li><p>设备必须支持 Wi-Fi 直接服务打印技术规格 1.0 版 4.2.9 节中定义的默认设置︰</p>
        <table>
            <thead>
                <tr class="header">
                    <th><strong>属性</strong></th>
                    <th><strong>默认设置</strong></th>
                </tr>
            </thead>
            <tbody>
                <tr class="odd">
                    <td>StripHeight</td>
                    <td>16</td>
                </tr>
                <tr class="even">
                    <td>媒体</td>
                    <td>字母</td>
                </tr>
                <tr class="odd">
                    <td>解决方法</td>
                    <td>600</td>
                </tr>
                <tr class="even">
                    <td>Duplex</td>
                    <td>单工</td>
                </tr>
                <tr class="odd">
                    <td>色彩空间</td>
                    <td>sRGB</td>
                </tr>
                <tr class="even">
                    <td>Copies</td>
                    <td>1</td>
                </tr>
                <tr class="odd">
                    <td>修饰功能</td>
                    <td>无</td>
                </tr>
                <tr class="even">
                    <td>调整到页面</td>
                    <td>False</td>
                </tr>
                <tr class="odd">
                    <td>方向</td>
                    <td>纵向</td>
                </tr>
                <tr class="even">
                    <td>PrintQuality</td>
                    <td>常规</td>
                </tr>
            </tbody>
        </table>
    </li>
    <li><p>设备必须支持分辨率为 300 dpi 时接收内容</p></li>
    <li><p>设备必须支持接收内容压缩使用纯平、 运行长度编码或 DCTDecode</p></li>
    </ol>
    <p><strong>OXPS</strong></p>
    <p>打印机支持 OpenXPS 必须符合行业标准，并实现以下要求。</p>
    <ol style="list-style-type: decimal">
        <li><p>如果该设备实现了 OpenXPS 支持，它必须遵循 ECMA-388 所述的所有规则</p></li>
        <li>
            <p>设备必须在下面的优先级顺序处理 PrintTickets (最权威的&gt;最权威):</p>
            <ol style="list-style-type: lower-alpha">
                <li><p>页级 PrintTicket 文档中嵌入</p></li>
                <li><p>文档级 PrintTicket 文档中嵌入</p></li>
                <li><p>CreatePrintJob2 职位等级 PrintTicket</p></li>
                <li><p>职位等级 PrintTicket 文档中嵌入</p></li>
            </ol>
        </li>
    </ol>
    <p><strong>Microsoft XPS</strong></p>
    <p>打印机支持 Microsoft XPS 必须遵循以记录规范。</p>
    <ol style="list-style-type: decimal">
        <li><p>打印机支持 Microsoft XPS 必须符合并遵循 Microsoft XML 纸张规范 1.0 中所述的所有规则</p></li>
    </ol>
</html>

<a name="device.imaging.printer.mobile.wsd20"></a>
## <a name="deviceimagingprintermobilewsd20"></a>Device.Imaging.Printer.Mobile.WSD20

### <a name="deviceimagingprintermobilewsd20pdc-if-implemented"></a>Device.Imaging.Printer.Mobile.WSD20.PDC （如果实现）

支持 PrintDeviceCapabilities (PDC) 的打印机必须支持以下各项的说明中

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

1.  打印机支持 PrintDeviceCapabilities 必须遵守的所有规则设定的打印架构规范 2.0 版，以及 WDK。

2.  仅当前可用的功能可能会暴露在 PrintDeviceCapabilities 文件中。 打印机必须描述其目前的功能、 选项和 PrintDeviceCapabilities 文件中的参数。

    如果任何功能、 选项或参数条件，则有一个可安装的选项，如分页装订器的状态，则这些项必须只公开在 PrintDeviceCapabilities 文件中如果当前安装的系统必备的安装选项。

3.  PageMediaSize 中的所有选项必须在 PrintDeviceCapabilities 文件中都公开。 打印机必须说明在 PrintDeviceCapabilities 文件中使用 psk:PageMediaSize 功能的所有支持的纸张大小。

4.  PageResolution 中的所有选项必须在 PrintDeviceCapabilities 文件中都公开。 打印机必须说明在 PrintDeviceCapabilities 文件中使用 psk:PageResolution 功能及其支持的设备解决方案。

5.  打印机必须描述至少一个使用 psk:JobInputBin、 psk:DocumentInputBin 或 psk:PageInputBin 功能的送的纸盒。

6.  打印机支持 PWG 光栅必须包含 PrintDeviceCapabilities 文件来描述受支持的颜色格式中的 PwgRasterDocumentTypesSupported 元素。

7.  这种情况表明在 PrintDeviceCapabilities 文件中的 deviceProcessing 属性的打印机必须支持这些功能，而无需主机的交互。 如果打印机指示在使用 deviceProcessing 的硬件处理选项或参数 ="true"属性，然后它必须处理该选项或参数而无需主机的参与。

### <a name="deviceimagingprintermobilewsd20wsd20support-if-implemented"></a>Device.Imaging.Printer.Mobile.WSD20.WSD20support （如果实现）

打印机支持打印 WS 2.0 必须实现以下要求

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

<html>
    <ol style="list-style-type: decimal">
        <li>
            <p>打印机支持打印 WS 2.0 版必须描述和支持以下的 MIME 类型，包括打印机的 wprt:PrintCapabilities 元素下的 wprt2:PrinterFormats 元素。</p>
            <ul>
                <li>
                    <p>PrintDeviceCapabilities</p>
                    <ul>
                        <li><p>应用程序/vnd.ms-PrintDeviceCapabilities + xml</p></li>
                    </ul>
                </li>
                <li>
                    <p>PrintJobTicket</p>
                    <ul>
                        <li><p>应用程序/vnd.ms-PrintSchemaTicket + xml</p></li>
                    </ul>
                </li>
                <li>
                    <p>PrintDeviceResource</p>
                    <ul>
                        <li><p>应用程序/vnd.ms-resx + xml</p></li>
                    </ul>
                </li>
            </ul>
        </li>
        <li><p>打印机支持打印 WS 2.0 版必须处理 PrintDeviceCapabilitiesChangeID。 打印机必须描述 wprt:PrinterConfiguration 元素中的 PrintDeviceCapabilitiesChangeID 元素，如果更改了当前 PrintDeviceCapabilitiesChangeID 创建的事件。</p>
            <ul>
                <li><p>PrintDeviceCapabilitiesChangeID 必须是跨设备的电源周期一致，除非该打印机的状态更改 （例如，一个可安装的选项被添加或删除）。</p></li>
            </ul>
        </li>
        <li><p>打印机支持打印 WS 2.0 版必须支持以下 PDLs 之一通过描述 wprt:PrinterCapabilities wprt:Format 元素中的相应的 MIME 类型。</p>
            <ul>
                <li><p>应用程序/oxps</p></li>
                <li><p>应用程序/vnd.ms-用于</p></li>
                <li><p>图像/pwg-光栅</p></li>
                <li><p>应用程序/pclm</p></li>
            </ul>
        </li>

        <li><p>支持 WS 打印 v2.0 的打印机必须支持使用 GetPrintDeviceResources 操作按以下格式的资源文件中的检索或必须返回 NoLocalizedResources SOAP 错误。</p>
            <ul>
                <li><p>应用程序/vnd.ms-resx + xml</p></li>
            </ul>
        </li>

        <li><p>打印机的打印 WS 2.0 版实现必须支持 WS 打印 v2.0 规范中所描述的所有新操作︰</p>
            <ul>
                <li><p>CreatePrintJob2</p></li>
                <li><p>PrepareToPrint</p></li>
                <li><p>GetBidiSchemaExtensions</p></li>
                <li><p>GetPrintDeviceResources</p></li>
                <li><p>GetPrintDeviceCapabilities</p></li>
            </ul>
        </li>

        <li><p>打印机支持打印 WS 2.0 版必须处理 PrintJobTicket 元素，如果它包含在 CreatePrintJob2 请求。 打印机必须支持 PrintJobTickets 在下列格式中的格式。</p>
            <ul>
                <li><p>应用程序/vnd.ms-PrintSchemaTicket + xml</p></li>
            </ul>
        </li>

        <li><p>支持 Windows Mobile 的打印机必须实现 WS 打印 v2.0 根据 WDK 的指导原则。</p></li>
    </ol>
</html>

<a name="device.imaging.printer.oxps"></a>
##Device.Imaging.Printer.OXPS

### <a name="deviceimagingprinteroxpsoxps"></a>Device.Imaging.Printer.OXPS.OXPS

*V4 驱动程序支持 OpenXPS 必须根据 WDK 中指定的规则来实现。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

对于 Windows 10 正确实现的版本 4 的打印驱动程序将满足 XPS 要求。  MSXPS 或打开 XPS，v4 驱动程序可以支持。
V4 打印驱动程序支持 OpenXPS，要么以独占模式或双格式支持模式使用 XPS，必须满足以下要求︰

-   驱动程序清单必须指定"XpsFormat = OpenXPS"，"XpsFormat = OpenXPS，XPS"或"XpsFormat = XPS，OpenXPS"DriverRender 部分中。

-   第一个筛选器必须能够使用 OpenXPS 文档格式时提供此类打印过滤器管道管理器。

-   所有筛选器都必须符合 ECMA 打开 XML 纸张规范 v 中的呈现规则。 1.0 (Ecma 388)。

-   所有筛选器都必须符合 PrintSchema 规范 1.0 中的 PrintTicket 处理规则。

-   V4 驱动程序筛选管线必须生成目标打印设备可以解释 PDL。

-   支持 OpenXPS v4 驱动管道中的筛选器必须完成以下任务︰

    <!-- -->

    -   为任何功能，调入公共语言运行时 (CLR) 或 WinFX 运行时组件。

    -   显示用户界面 (UI) 的内容。

    <!-- -->

-   OpenXPS 支持的驱动程序必须遵守所有其他 v4 规则。  双重格式驱动程序必须遵守 OpenXPS 和 MSXPS 的要求，并成功地处理这两种格式。

<a name="device.imaging.printer.usb"></a>
## <a name="deviceimagingprinterusb"></a>Device.Imaging.Printer.USB

### <a name="deviceimagingprinterusbcompatid"></a>Device.Imaging.Printer.USB.CompatID

*WDK 中指定的规则根据其 IEEE1284 字符串中，打印机必须实现兼容 ID。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

打印机必须通过 USB 和使用端口监视器 MIB WSD 连接的设备其 IEEE1284 字符串中实现兼容 ID。
兼容 ID 必须指出︰

-   制造商的名称或代码

-   设备类别描述

<!-- -->

建议︰

<!-- -->

-   包括 PDL

-   任何其他相关的设备类信息

-   示例︰ Fabrikam\_XPS\_A3\_激光

在 2012 年 6 月 1 日之前收到的 Windows 7 徽标的设备不受这一要求。
兼容 ID 白皮书的链接︰ <http://msdn.microsoft.com/en-us/windows/hardware/gg463313.aspx>

### <a name="deviceimagingprinterusbjsbidiextender"></a>Device.Imaging.Printer.USB.JSBidiExtender

*根据在 WDK 指南实现 USB JavaScript 双向扩展程序。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

根据在 WDK 指南实现 USB JavaScript 双向扩展程序︰

-   它们必须包含在该驱动程序包，并且不能包中的子目录中。

-   他们可能只是附带版本 4 打印驱动程序。

-   他们应该安全地设计和验证任何不可靠的数据，将对其进行分析。

-   这些必须在 v4 清单文件引用。

他们必须使用语法上有效的 JavaScript，根据 WDK 实现。

<a name="device.imaging.printer.wsd"></a>
## <a name="deviceimagingprinterwsd"></a>Device.Imaging.Printer.WSD

### <a name="deviceimagingprinterwsdcompatid"></a>Device.Imaging.Printer.WSD.CompatID

*WDK 中指定的规则根据其 IEEE1284 字符串中，打印机必须实现兼容 ID。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

打印机必须通过 USB 和使用端口监视器 MIB WSD 连接的设备其 IEEE1284 字符串中实现兼容 ID。
兼容 ID 必须指出︰

-   制造商的名称或代码

-   设备类别描述

建议︰

-   包括 PDL

-   任何其他相关的设备类信息

-   示例︰ Fabrikam\_XPS\_A3\_激光

了解[如何实现兼容 Id 在打印设备中的](http://msdn.microsoft.com/en-us/windows/hardware/gg463313.aspx)，一份白皮书。

<a name="device.imaging.printer.xps"></a>
## <a name="deviceimagingprinterxps"></a>Device.Imaging.Printer.XPS

### <a name="deviceimagingprinterxpsxps"></a>Device.Imaging.Printer.XPS.XPS

*打印机必须正确地实现 XPSDrv 打印机驱动程序体系结构的驱动程序。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

MSXPS 或打开 XPS，v4 驱动程序可以支持。
支持 MSXPS，V4 打印驱动程序以独占方式或在双格式支持模式下打开 XPS，必须满足以下要求︰

-   驱动程序清单必须指定"XpsFormat = OpenXPS"，"XpsFormat = OpenXPS，XPS"或"XpsFormat = XPS，OpenXPS"DriverRender 部分中。

-   第一个筛选器必须能够使用 XPS 文档格式时提供此类打印过滤器管道管理器。

-   所有筛选器都必须符合 XML 纸张规范中的呈现规则。

-   所有筛选器都必须符合 PrintSchema 规范 1.0 中的 PrintTicket 处理规则。

-   V4 驱动程序筛选管线必须生成目标打印设备可以解释 PDL。

-   支持 XPS v4 驱动管道中的筛选器必须完成以下任务︰

<!-- -->

    -   为任何功能，调入公共语言运行时 (CLR) 或 WinFX 运行时组件。

    -   显示用户界面 (UI) 的内容。

<!-- -->

-   XPS 支持驱动程序必须遵守所有其他 v4 规则。  双重格式驱动程序必须遵守 OpenXPS 和 MSXPS 的要求，并成功地处理这两种格式。

打印机必须正确地实现 XPSDrv 打印机驱动程序体系结构的驱动程序。 

实现是 XPSDrv 打印机驱动程序体系结构的驱动程序必须完成以下任务︰

-   实现一个 GDI 呈现模块。

-   实现的打印处理器。

如果是 XPSDrv 驱动程序支持可以为打印机描述语言 (PDL) 使用 XPS 文档格式打印设备，没有筛选器是必需的。 否则为或者如果驱动程序提供的筛选器，则驱动程序必须满足以下要求︰

-   XPSDrv 驱动程序筛选器管道中的第一个筛选器必须使用 XPS 文档格式。

-   XPSDrv 驱动程序筛选管线必须生成目标打印设备可以解释 PDL。

-   XPSDrv 驱动程序筛选管线中的筛选器必须执行以下操作︰

<!-- -->

    -   符合 XML 纸张规范中呈现规则。

    -   符合 XML 纸张规范中的 PrintTicket 处理规则。

<!-- -->

-   XPSDrv 驱动程序筛选管线中的筛选器必须完成以下任务︰

<!-- -->

    -   为任何功能，调入公共语言运行时 (CLR) 或 WinFX 运行时组件。

    -   显示用户界面 (UI) 的内容。

    XPSDrv 必须完全支持的 PrintTicket 和 PrintCapabilities 对象。 在所述 printTicket 要求下，XPSDrv 驱动程序还必须支持以下附加的关键字。

    -   PageScaling

    -   JobDigitalSignatureProcessing

    -   PagePhotoPrintingIntent

    -   PageOutputQuality

    