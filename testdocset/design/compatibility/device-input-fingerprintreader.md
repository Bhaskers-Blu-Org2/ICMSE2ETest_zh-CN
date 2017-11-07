---
title: Device.Input.FingerPrintReader
Description: "生物指纹识别器的一般要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 557aa6c2868514606ea77e6c5827c46e4b1634bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.FingerPrintReader
 - [Device.Input.FingerPrintReader](#device.input.fingerprintreader)
-->

<a name="device.input.fingerprintreader"></a>
##Device.Input.FingerPrintReader 

### <a name="deviceinputfingerprintreaderbase"></a>Device.Input.FingerPrintReader.Base

*生物指纹读取器的一般要求*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

必须通过 Windows 生物识别框架 (WBF) 公开认证在此计划下的生物特征指纹识别器。 WBF 插件组件必须实现所有入口点并遵守在 MSDN ([*http://msdn.microsoft.com/library/dd401553.aspx*](http://msdn.microsoft.com/library/dd401553.aspx)) 记载的 WBF 插件接口。

必须满足下列一般条件︰

<html>
    <ul>
        <li><p>该驱动程序包必须包含 WBDI 驱动程序，以及插件的适配器的组合。</p></li>
        <li><p>在高级模式下运行的设备可以实现复合适配器。 复合的适配器可能包含专用传感器、 引擎和数据库适配器的任意组合。</p></li>
        <li><p>WBDI 驱动程序和插件组件不得包含任何恶意软件，如特洛伊木马或后门程序软件。</p></li>
    </ul>
    <p>插件组件中不能包含任何恶意软件，如特洛伊木马或后门程序软件。</p>
    <p>下表列出了指纹传感器的硬件要求。</p>
    <table>
        <thead>
            <tr class="header">
                <th>要求</th>
                <th colspan="2">对齐方式中的笔记</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>传感器类型</td>
                <td>如果实现建议的触摸</td>
                <td>触摸传感器类型是首选的选项比较到刷传感器。 由于性质、 位置和固定的方向的刷传感器，特别是上可以有多个方向 （例如，可以在横向和纵向模式下工作的平板电脑） 的设备，所以导致人体工学的用户可能会导致无法捕获准确的指纹，从而导致对多个刷卡的需求难题。</td>
            </tr>
            <tr class="even">
                <td>功耗</td>
                <td>（期间捕获） 运行 100mW</td>
                <td>所需的连接的备用设备和其他人建议。</td>
            </tr>
            <tr class="odd">
                <td></td>
                <td>当指纹读取器不捕获指纹图像无论如果系统本身处于睡眠状态或不-1mW</td>
                <td>所需的连接的备用设备和其他人建议。</td>
            </tr>
            <tr class="even">
                <td>表现</td>
                <td colspan="2">建议使用&lt;1 %frr @ 0.01%远处由指纹传感器规范</td>

            </tr>
            <tr class="odd">
                <td>Liveness Detection</td>
                <td colspan="2">Recommended to be able to provide a minimum of one of the anti-spoofing measures based on the fingerprint sensor specification</td>

            </tr>
            <tr class="even">
                <td>WBF Compliant with HCK</td>
                <td colspan="2">Yes</td>

            </tr>
        </tbody>
    </table>
    <p><em>Design Notes: </em></p>
    <p>Biometric devices measure an unchanging physical characteristic to uniquely identify an individual. Fingerprints are one of the most common biometric characteristic measured. Beginning with Windows 7, a new set of components, the Windows Biometric Framework, provides support for fingerprint biometric devices. These components, created using the Windows Biometric Framework API, can perform the following tasks:</p>
    <ul>
        <li><p>Capture biometric samples and use them to create a template.</p></li>
        <li><p>Securely save and retrieve biometric templates.</p></li>
        <li><p>Map each template to a unique identifier such as a GUID (globally unique identifier) or SID (system identifier).</p></li>
        <li><p>Enroll new biometric templates.</p></li>
    </ul>
    <p>For more complete information about WBF and its components, see &quot;Introduction to the Windows Biometric Framework (WBF),&quot; a white paper, at <em><a href="http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx" class="uri">http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx</a>.</em></p>
</html>

### <a name="deviceinputfingerprintreaderextensions"></a>Device.Input.FingerPrintReader.Extensions

*供应商提供的驱动程序或其他扩展组件必须不换其他的扩展组件。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

驱动程序和适配器插件扩展 Windows 生物识别框架必须不换行，其他驱动程序或适配器插件除非练习明确允许通过由 Microsoft 提供的组件文档。

### <a name="deviceinputfingerprintreadermanagementapps"></a>Device.Input.FingerPrintReader.ManagementApps

*生物指纹读取器管理应用程序*

<table>
<tr>
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
    <table>
        <thead>
            <tr class="header">
                <th></th>
                <th>ARM 的设备</th>
                <th>x86/x64 设备</th>
            </tr>
        </thead>
        <tbody>
            <tr class="odd">
                <td>注册体验 (FMA)</td>
                <td>不允许使用。 用户设置页面与集成在一起的收件箱注册体验才可用。</td>
                <td>
                    <p>不建议这样做。 注册体验会提供收件箱并集成在一起用户设置页。 可能附带 WBF 包和系统上安装，但是它将无法集成到用户设置页面或控制面板的自定义注册体验。</p>
                    <p>不允许注册非域中的用户自定义注册体验。</p>
                </td>
            </tr>
        </tbody>
    </table>
    <p><strong>例外情况</strong>
    <p>针对使用者使用的设备不能有 FMA 安装任何第三方。 第三方 FMAs 可能安装和启用 Windows 设备专门针对业务 （企业和中小型企业）。 在这种情况下，应清楚地通知用户如果核收箱经验会受到负面影响的第三方 FMA 使用在注册过程中。</p>
<html>

### <a name="deviceinputfingerprintreadersensorenginedb"></a>Device.Input.FingerPrintReader.SensorEngineDB

*指纹读取器传感器、 引擎和存储插件要求*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

-   必须实现接口的所有入口点，并且每个元素都必须遵守其各自的适配器的插件接口的定义。

-   插件组件必须支持它们所产生的所有顶级窗口生物识别框架 (WBF) Api 调用的接口顺序进行调用。

-   WBF 凭据提供程序用于 Windows 登录 WBF API 调用的顺序必须是已完成在 1.5 秒或更少。

-   所有适配器必须经过数字都签名，Windows 生物识别框架中所述︰ 在[*http://msdn.microsoft.com/library/windows/hardware/gg463093.aspx*](http://msdn.microsoft.com/library/windows/hardware/gg463093.aspx)代码签名指南 》 白皮书。

-   适配器必须在应用程序验证工具下运行，而不会产生任何错误。

驱动程序包可以支持多个设备，但必须将证书条件分别传递每个受支持的指纹读取器。 必须为每个受支持的设备进行单独提交。

| 适配器要求 | 注释                                                                                                                                             |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| 引擎适配器       | 必填，除非该设备是可以匹配设备的高级的设备。                                                                        |
| 存储适配器      | 除非有特定需要包括诸如高级传感器的自定义存储适配器，建议依赖于收件箱存储适配器。 |
| 传感器适配器       | 除非有特定需要提供自定义传感器适配器，建议依赖于收件箱传感器适配器。                                |

### <a name="deviceinputfingerprintreaderwbdi"></a>Device.Input.FingerPrintReader.WBDI

*生物指纹读取器 WBDI 驱动程序要求*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>Windows 10 移动 ARM</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 服务器 2016 x64</p>
</td></tr></table>

**说明**

Windows 生物识别驱动程序接口 (WBDI) 的驱动程序必须符合以下条件︰

-   所有必填字段 Ioctl 必须完全实现和符合 WBDI 规范。

-   如果实现可选的 IOCTL 时，它必须符合 WBDI 规范。

-   WBDI 驱动程序必须支持生物 IOCTL 调用序列。

-   如果生物指纹读取器不是即插即用设备，则必须创建到达和出发事件为 WBDI 规范中推荐。

-   WBDI INF 安装程序必须设置相关联的插件组件，以及指纹驱动程序软件包中包括的管理应用程序。

在这一要求的原则同样适用也给内核模式和用户模式的驱动程序。 必须支持以下︰

-   向后和向前兼容性。 驱动程序必须具有一种机制，用于确定用户模式和内核模式组件的不同版本。 如果已经在 PC 上安装了相同驱动程序的两个版本，内核组件必须确定正确的驱动程序进行谈话。 在远程处理方案中，这种不匹配可能会出现甚至单个驱动程序。

不能使用以下各项︰

-   带外通信。 在同一台 PC 上运行的用户模式和内核模式驱动程序，因为它们可能耦合于一起通过 I/O 管理器 Api 从不同的渠道。 目标是确保驱动程序不具有隐式或显式的带外通信。

以下是一些具体的示例，可以防止终端服务重定向︰

-   不得使用直接用户模式应用程序和用户模式或内核模式驱动程序之间共享的内存。 发送和接收每个数据项目，必须有相应的 I/O 请求。 通过映射文件或锁定的页的一个直接 I/O 调用共享内存。

-   注册表的通讯 （也就是说，任何注册表项会从用户模式驱动程序设置和读取从内核模式驱动程序，反之亦然）。 当应用程序运行在服务器上，因为注册表设置在服务器上，而不是客户端驱动程序在客户端加载时，它会带来问题。

-   内核对象 （在 I/O 缓冲区，如事件或信号量的句柄传递任何内核对象的句柄）。

-   数据指针 （在 I/O 缓冲区传递数据指针）。 例如，驱动程序可能会尝试从内核读取链接的列表或其他复杂的数据结构。

-   32 位和 64 位平台实现的输入/输出请求数据包 (IRP) 请求 （编译有所不同，根据不同位元的数据结构中的字段） 之间的不兼容问题。 根据这些结构的不同偏移量和数据大小的位元导致结构的不兼容问题。 当终端服务客户端和服务器都不相同的平台，将不被正确地解释数据。

-   依靠严格计时期望有关内核驱动程序的响应速度。 由于驱动程序通过网络远程处理，额外延迟是从硬件添加到响应。 该延迟可能是介于多种秒到 10 毫秒。 慢速网络或数据包丢失，可能是这的可能原因。 如果驱动程序设计用来实现进入时间小于常规网络延迟响应，远程处理将失败。

    设置访问控制列表 (ACL) 或任何其他可以防止从打开的设备驱动程序的任何应用程序的运行时安全检查。 例如，驱动程序可以接受只能从特定的服务调用。 因为所有的调用远程处理客户端进程的安全上下文下的 TS 客户端 PC 上完成的它们可能会失败。

**设计备注** 

生物识别设备测量来唯一标识单个不变的物理特征。 指纹是最常见的生物特性测量。 借助 Windows 7，一组新的组件，Windows 生物识别框架 (WBF) 开始提供指纹生物识别设备支持。 用 WBF API 创建的这些组件可执行以下任务︰

-   捕获生物样本，并使用它们来创建模板。

-   安全地存储和检索生物模板。

-   将每个模板映射到一个唯一的标识符，如 GUID （全局唯一标识符） 或 SID （标识符）。

-   注册新的生物特征模板。

-   若要公开通过 WBF 设备，设备必须公开通过驱动程序实现的 WBDI 驱动程序，以及合适的传感器、 引擎和数据库插件组件组合。 有关 WBF 及其组件的详细信息，请参阅"简介到 Windows 生物识别框架 (WBF)，"为主题的白皮书，在[*http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx*](http://msdn.microsoft.com/library/windows/hardware/gg463089.aspx)。


