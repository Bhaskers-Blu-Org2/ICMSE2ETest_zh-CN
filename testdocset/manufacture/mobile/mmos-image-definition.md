---
author: kpacquer
Description: "MMO 图像定义"
ms.assetid: 3b548778-0551-4ca0-9768-725d0f33dfca
MSHAttr: PreferredLib:/library/windows/hardware
title: "MMO 图像定义"
ms.openlocfilehash: 5e9b0a5644ca2222abfb365b3f8c167b568dea21
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mmos-image-definition"></a>MMO 图像定义


本节说明如何创建 Windows 10 移动 MMO 图像。 此过程非常类似于创建主操作系统映像的过程。

## <a name="span-idcreatinganmmosimagespanspan-idcreatinganmmosimagespanspan-idcreatinganmmosimagespancreating-an-mmos-image"></a><span id="Creating_an_MMOS_image"></span><span id="creating_an_mmos_image"></span><span id="CREATING_AN_MMOS_IMAGE"></span>创建一个 MMO 图像


在此过程中创建的 MMO 映像需要从 SoC 制造商和除由 Microsoft 提供的 OEM 包。 在 MfgOEMInput.xml 配置文件中的示例包括 OEM 包是仅用于说明目的。 Oem 应该删除这些示例软件包并将它们替换为自己的 OEM 包。 由 OEM 来确定哪一组包含在 MMO。 Oem 可以添加包含测试应用程序的其他 OEM 包和测试控制器等。

**重要**  
所有的图像处理和包装工具位于 %WPDKCONTENTROOT%\\工具\\bin\\i386。 此路径必须包含在您的环境的工具的路径来处理。 您必须运行这些工具从 Visual Studio 命令行窗口作为具有访问权限的管理员到 MakeCat.exe 环境路径中。

 

### <a name="span-idcreatingoempackagesspanspan-idcreatingoempackagesspanspan-idcreatingoempackagesspancreating-oem-packages"></a><span id="Creating_OEM_packages"></span><span id="creating_oem_packages"></span><span id="CREATING_OEM_PACKAGES"></span>创建 OEM 包

将内容添加到图像是通过创建您自己的包。 可以通过使用 Windows 图像处理和配置设计器 (ICD) 创建映像之前修改 MfgOEMInput.xml 文件的图像添加 OEM 包。

有关创建对象包的说明，请参阅[创建程序包](https://msdn.microsoft.com/library/dn756642)。

### <a name="span-idspecifyingfeaturesinmmosspanspan-idspecifyingfeaturesinmmosspanspan-idspecifyingfeaturesinmmosspanspecifying-features-in-mmos"></a><span id="Specifying_features_in_MMOS"></span><span id="specifying_features_in_mmos"></span><span id="SPECIFYING_FEATURES_IN_MMOS"></span>在 MMO 指定功能

可用于**功能**元素在 MfgOEMInput.xml 文件中包含由 Microsoft 提供的可选包。 您可以修改要 MMO 在支持不同的功能，为开发、 制造和零售服务需求的输入的 XML 文件。

**制造开发和调试环境**

下面的功能定义和制造开发和调试环境中受支持。 这种环境可以用于制造中创建用于测试应用程序。

**重要**  
以下功能仅用于测试签名的包，并将不包括在客户关注 WIM 映像。

 

**常规功能**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能 </th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_BOOT_KEYS_TEST</p></td>
<td align="left"><p>可以通过按下并按住电源按钮启动的引导菜单。 使用音量键导航和照相机键选择。 此功能是互相排斥的<strong>ENABLE_BOOT_KEYS_RETAIL</strong>。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MOBILECOREBOOTSH</p></td>
<td align="left"><p>使 bootsh 服务 (bootshscv)，以便可以使用 startup.bsc，如 telnet 和 ftp 中的功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>LABIMAGE</p></td>
<td align="left"><p>此功能会导致设备在设备启动时，自动输入 FFU 下载模式。 更多的信息，请参阅[的使用由 Microsoft 提供的闪烁的工具](https://msdn.microsoft.com/library/windows/hardware/dn789235)。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MFGTSHELL</p></td>
<td align="left"><p>使 TShell MMO 和制造模式中。 如果您使用此开关，您需要设置为自动制造配置文件中的 TestSirepServer 服务。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>OPTIMIZED_BOOT</p></td>
<td align="left"><p>修改操作系统启动过程以启动某些系统进程和服务之前启动的所有设备驱动程序的行为。 启用此功能可能会减少启动时间，但在引导行为，在某些情况下可能会发生衰退。</p></td>
</tr>
<tr class="even">
<td align="left"><p>BOOTKEYACTIONS_RETAIL</p></td>
<td align="left"><p>此功能启用了一套零售设备中使用的按钮操作。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DISABLE_FFU_PLAT_ID_CHECK</p></td>
<td align="left"><p>禁用设备平台验证闪烁 Microsoft 应用程序中。 关于闪烁在平台检查的详细信息，请参阅[的使用由 Microsoft 提供的闪烁的工具](https://msdn.microsoft.com/library/windows/hardware/dn789235)。</p>
<div class="alert">
<strong>重要</strong>  
<p>必须禁用零售图像中闪烁的设备平台验证。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>PERF_TRACING_TOOLS</p></td>
<td align="left"><p>包含用于进行性能分析，如停止和合并 ETL 跟踪工具的工具。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ENABLE_BOOT_PERF_BASIC_TRACING</p></td>
<td align="left"><p>启用启动性能跟踪事件生成。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ENABLE_BOOT_PERF_CPU_PROFILING_TRACING</p></td>
<td align="left"><p>使 CPU 分析在 ENABLE_BOOT_PERF_BASIC_TRACING 的实现的事件。</p></td>
</tr>
</tbody>
</table>

 

**调试功能**

使用以下设置指定用于调试的传输。 如果不指定调试功能，则不启用 MMO 在中调试。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能 </th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>KDNETUSB_ON</p></td>
<td align="left"><p>包括所有内核调试器传输并使 KDNET 可以通过 USB。</p></td>
</tr>
<tr class="even">
<td align="left"><p>KDUSB_ON</p></td>
<td align="left"><p>包括所有内核调试器传输，使 KDUSB。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果您需要在图像中启用 USB 相比 MTP 或 IP，不要包括 KDUSB_ON 或 KDNETUSB_ON。 在图像中启用了内核调试器和调试运输用来连接到手机，如果内核调试器已独占使用 USB 端口并防止 MTP 和 IP 通过 USB 工作。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>KDSERIAL_ON</p></td>
<td align="left"><p>包括所有内核调试器传输和下面的设置启用 KDSERIAL︰ 为 115200 波特、 8 位、 无奇偶校验。</p></td>
</tr>
<tr class="even">
<td align="left"><p>KD</p></td>
<td align="left"><p>在图像中，包括所有的内核调试器传输但不启用内核调试器。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MFGCRASHDUMPSUPPORT</p></td>
<td align="left"><p>此功能使脱机崩溃转储功能的 MMO 图像使用 wpcrdmp 方法。 当设备发生故障时，它激活 wpcrdmp，并将内存和 SOC 子系统的转储保存到的磁盘离线调查。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MWDBGSRV</p></td>
<td align="left"><p>此功能增加用户模式调试服务器的支持。</p></td>
</tr>
</tbody>
</table>

 

以前的 DEBUGGERON 功能已被否决。

**其他调试功能**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能 </th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>设置功能的以下三种功能的 Dumpsize 必须只用于测试和运行状况图像类型。 这些功能必须不能用于零售的图像。 可以一次选择一个 dumpsize 设置。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DUMPSIZE512MB</p></td>
<td align="left"><p>指定一个预分配的崩溃转储文件大小为 592 MB。 这适用于具有 512 MB 内存的电话。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DUMPSIZE1G</p></td>
<td align="left"><p>指定一个预分配的崩溃转储文件大小为 1104 MB。 这适用于具有 1024 MB 内存的电话。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DUMPSIZE2G</p></td>
<td align="left"><p>指定一个预分配的崩溃转储文件大小为 2128 MB。 这适用于具有 2048 MB 内存的电话。</p></td>
</tr>
<tr class="odd">
<td align="left"><p></p></td>
<td align="left"><p>转储数据存储位置-接下来的两个设置控件，如果崩溃转储的数据存储在 eMMC 上或者崩溃转储的数据存储在 SD 卡上。 这些设置中的只有一个可以一次选择。 只有必须与测试、 运行状况和 Selfhost 的图像类型使用这两种功能。 这些功能必须不能用于零售的图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DEDICATEDDUMPONEMMC</p></td>
<td align="left"><p>指定 c:\crashdump\dedicateddump.sys DedicatedDumpFile 的位置。</p>
<div class="alert">
<strong>请注意</strong> 这不能用于 DEDICATEDDUMPONSDCARD。
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>DEDICATEDDUMPONSD</p></td>
<td align="left"><p>DEDICATEDDUMPONSD – 指定为 d:\dedicateddump.sys 的 DedicatedDumpFile 位置</p>
<p>使用 DEDICATEDDUMPONSD 时，如果用户删除该 SD 卡或卡没有引导设备时，将禁用故障转储。 要重新启用故障转储︰</p>
<ol>
<li><p>设置此注册表项<code>HKLM\System\CurrentControlSet\Control\CrashControl\CrashDumpEnabled</code>的值 <code>HKLM\System\CurrentControlSet\Control\CrashControl\ExpectedCrashDumpEnabled</code></p></li>
<li><p>重新启动设备。</p></li>
</ol>
<div class="alert">
<strong>请注意</strong> 这不能用于 DEDICATEDDUMPONEEMC。
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>DBGCHKDISABLE</p></td>
<td align="left"><p>此功能禁用调试器连接检查和调试程序连接状态将被忽略。</p>
<p>对调试器行为的影响是不同的具体取决于正在使用的 SoC。</p>
<ul>
<li><p>对于 QC8x26 和 QC8974 的设备，包括 DBGCHKDISABLE，以确保将生成脱机转储，即使该设备连接到调试器。 否则为将不会创建脱机转储 （错误检查代码 0x14C 转储），但仍将创建原始转储。</p></li>
<li><p>对于 8960 设备，包括 DBGCHKDISABLE，以确保将生成脱机转储，即使该设备连接到调试器。 否则，将不创建脱机转储 （即错误检查代码 0x14C 转储）。</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p>MSVCRT_DEBUG</p></td>
<td align="left"><p>此功能增加了对图像中包括 msvcp120d.dll 和 msvcr120d.dll 的显式链接调试 c 运行时库支持。 详细信息，请参阅本主题在 MSDN 上︰ [CRT 库功能](http://msdn.microsoft.com/library/abx4dbyh.aspx)。</p></td>
</tr>
<tr class="even">
<td align="left"><p>MWDBGSRV</p></td>
<td align="left"><p>此功能增加用户模式调试服务器的支持。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>NOLIVEDUMPS</p></td>
<td align="left"><p>禁用内核出现非致命错误报告。  这些报告包含操作系统和驱动程序开发人员的调试信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p>TELEMETRYONSDCARD</p></td>
<td align="left"><p>此功能允许调试日志和 SD 卡上的文件临时存储。  此功能只是适合于测试/自助主机图像且仅在具有不超过 8 GB 的可用空间的主存储设备上。</p></td>
</tr>
</tbody>
</table>

 

**客户服务 WIM 映像**

在 MMO 制造生产中支持以下功能的环境。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">功能 </th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_BOOT_KEYS_RETAIL</p></td>
<td align="left"><p>使一组零售设备中使用手机上的按钮。 此功能是互相排斥的<strong>ENABLE_BOOT_KEYS_TEST</strong> （请参见上表）。</p></td>
</tr>
<tr class="even">
<td align="left"><p>ENABLE_IP_OVER_USB</p></td>
<td align="left"><p>通过 USB 启用 IP。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>ENABLE_USB_COMPOSITE</p></td>
<td align="left"><p>使系统芯片 (SoC) 提供复合 USB 堆栈中 MMO。</p></td>
</tr>
</tbody>
</table>

 

**双功能**

这些 MMO 功能可以用于测试或零售客户医疗图像。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_MMOS_CHARGING</p></td>
<td align="left"><p>使电池充电 MMO 中运行时。</p></td>
</tr>
</tbody>
</table>

 

UEFI 充电必须禁用或启用的 MMO 工作。 一次，可以设置这些选项中的只有一个。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>ENABLE_UEFI_CHARGING</p></td>
<td align="left"><p>使电池充电 （uefi） 中运行时。</p></td>
</tr>
<tr class="even">
<td align="left"><p>DISABLE_UEFI_CHARGING</p></td>
<td align="left"><p>电池充电 （uefi） 在运行时将禁用。</p></td>
</tr>
</tbody>
</table>

 

没有操作系统的其他 MMO 中不支持的图像类型中定义的其他功能。 此列表并不详尽，但它提供了制造或零售环境中不支持的功能的示例︰

-   TESTINFRASTRUCTURE

-   IMGFAKELED

-   LABIMAGE

-   LOCATIONFRAMEWORKAPP

### <a name="span-idaddingspanspan-idaddingspanspan-idaddingspanconfiguring-the-mmos-mfgoeminputxml-file"></a><span id="Adding"></span><span id="adding"></span><span id="ADDING"></span>配置 MMO MfgOEMInput.xml 文件

1.  打开示例 MfgOEMInput.xml 文件使用文本编辑器。 默认情况下，该文件安装到 %WPDKCONTENTROOT%\\OEMInputSamples\\8960Fluid。

2.  如上文所述，请添加所需的 MMO 功能。

3.  向文件中添加任何所需的 OEM 包。

4.  找到**产品**元素并确认它已设置为"`Manufacturing OS`"。

    您可以选择更新记录信息的 OS 映像的描述。

    ``` syntax
    <Description>Manufacturing OS generation for ARM.fre</Description>
    <Product>Manufacturing OS</Product>
    ```

5.  找到的**SOC**和**设备**元素，并根据需要进行更改。

6.  添加 %WPDKCONTENTROOT%\\工具\\bin\\i386 到**Path**环境变量。

 

 





