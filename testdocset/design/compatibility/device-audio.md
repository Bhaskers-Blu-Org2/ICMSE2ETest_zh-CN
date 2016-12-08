---
title: Device.Audio
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 8c98c341281d036e6b6ccca12808d851fbbddfe2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deviceaudio"></a>Device.Audio

 - [Device.Audio.APO](#device.audio.apo)
 - [Device.Audio.Base](#device.audio.base)
 - [Device.Audio.HardwareAudioProcessing](#device.audio.hardwareaudioprocessing)
 - [Device.Audio.HDAudio](#device.audio.hdaudio)
 - [Device.Audio.USB](#device.audio.usb)

<a name="device.audio.apo"></a>
## <a name="deviceaudioapo"></a>Device.Audio.APO

*此 APO 必须匹配所有 APO 测试。*

### <a name="deviceaudioapobestpractices"></a>Device.Audio.APO.BestPractices

*2] 应为 Windows APOs 遵循最佳做法*

<table>
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

所有本地 （音频处理对象） 应都按照在 Windows APO 最佳做法白皮书中所述的最佳实践。

这份白皮书可以在 MSDN 中找到︰ <http://go.microsoft.com/fwlink/?LinkId=716913>

### <a name="deviceaudioapomicarrayrawdata"></a>Device.Audio.APO.MicArrayRawData

*系统中的捕获路径的效果提供了从麦克风阵列时客户端所请求的原始数据。*

<table>
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

如果麦克风阵列处理算法提供音频处理对象 (APO) 流效果明显 (SFX) 实例化中 Windows 系统效果插入捕获路径中的点，它时必须提供所有单个音频流作为数组从通道一个客户端要求与通道等于数组中的麦克风元素数数格式。 这使得 APO 提供硬件补偿处理，并向客户端利用整个 APO，但允许客户端依赖于处理的麦克风阵列麦克风阵列处理位于更高向上音频子系统利用硬件补偿在 APO 但不是在其处理的数组。

强烈建议系统上的固定位置的板载麦克风阵列 （多个组合元素） 所遵循的一种优化的体验"语音平台设备建议规范"。

<a name="device.audio.base"></a>
## <a name="deviceaudiobase"></a>Device.Audio.Base

*此设备必须匹配所有基准测试。*

### <a name="deviceaudiobaseaudioprocessing"></a>Device.Audio.Base.AudioProcessing

*音频设备必须支持正确的音频处理发现和控制。*

<table>
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

驱动程序

至少，驱动程序必须支持 raw 模式或对任何默认模式针呈现的针脚。 至少，驱动程序必须支持 raw 模式，在捕获的针脚上。 提供对系统硬件的针脚上必须供应如果它支持 a） 混合后期混音音量或 b） 音频减轻。 另外，硬件必须提供在呈现方面，静音，如果它支持 a） 混合或 b） 音频卸载或 c） 压缩。

终结点效果必须是中性的方案。 终结点效果必须在所有情况下工作。 对于可能损害如实时通信方案或只能是一个方案非常有益的效果，效果必须放入特定于该方案的模式效果。 唯一允许终结点效果 (EFX) 和原始模式效果 (在原始模式中 MFX) 的扬声器补偿和演讲者的保护。

此外支持 RAW 模式的驱动程序都必须支持您的驱动程序的结构根据以下︰

-   支持不混合使用的驱动程序的卸载支持 （支持多个并发模式，但不支持卸载） 应包括 KSNODETYPE\_求和节点并没有 KSNODETYPE\_音频\_引擎节点。 节点应有来自软件 pin 工厂，一次输入的连接，代表混合针的多个实例的位置点。

-   KSNODETYPE\_音频\_引擎或 KSNODETYPE\_求和节点应在软件 pin 工厂和终结点的桥接器插针之间的路径中。 该节点应在同一筛选器设置为软件 pin 工厂。

-   该节点应支持 KSPROPERTY\_AUDIOSIGNALPROCESSING\_模式。

    -   对于端口类驱动程序，微型端口应支持 IMiniportAudioSignalProcessing。 该端口应添加 KSPROPERTY\_AUDIOSIGNALPROCESSING\_到适当的端口的模式。<br/><br/>

-   支持混合使用 （与卸载和/或多个模式） 的驱动程序应支持环回针。

-   环回针脚是否应在新 pin 类别 KSPINCATEGORY\_AUDIOLOOPBACK。 拓扑结构应具有的路径从软件 pin 工厂环回 pin 工厂。

-   不支持混合的驱动程序必须支持 KSPROPERTY\_AUDIOSIGNALPROCESSING\_上终结点的软件 pin 工厂的模式。

    -   对于端口类驱动程序，微型端口应支持 IMiniportAudioSignalProcessing。 该端口应添加 KSPROPERTY\_AUDIOSIGNALPROCESSING\_到适当的端口的模式。<br/><br/>

-   软件 pin 工厂数据范围应包括 KSATTRIBUTE\_音频\_SIGNALPROCESSINGMODE。 该属性不应来标记 KSATTRIBUTE\_要求。

-   Pin 创建代码应检查 KSDATAFORMAT\_数据中的属性设置格式和处理 KSATTRIBUTE\_AUDIOSIGNALPROCESSINGMODE 如果存在。

对于端口类驱动程序，驱动程序的 NewStream IMiniportWaveRT，IMiniportWavePci 或 IMiniportWaveCyclic 上实现应支持 KSDATAFORMAT\_属性。2]

-   如果驱动程序的本地支持默认卸载针应支持默认。

-   A p o s 应支持卸载针所支持的所有模式。

-   2] 应支持主机针所支持的所有模式。

发现

驱动程序必须公开所有的音频效果，通过 FXStreamCLSID、 FXModeCLSID，和 FXEndpointCLSID a p o s （或代理 a p o s）。 A p o s 必须向系统查询时发送准确列表中启用的效果。 驱动程序必须支持更改通知 APO 和 APO 更改发生时只通知系统。

环回

环回流应表示出演讲者的流。 驱动程序与硬件处理必须提供准确的环回流系统。

### <a name="deviceaudiobaseendpoints"></a>Device.Audio.Base.Endpoints

*音频子系统正确反映了当前系统配置*

<table>
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

**所有音频设备**

公开的任何音频设备枚举 Api 的任何音频设备必须反映其所有终结点的当前状态进行适当根本当系统通电时间。 当系统处于待机状态的连接，这包括这种情况。 内置扬声器和麦克风必须工作时系统运行正常。

如果终结点公开的任何设备枚举 Api，它的状态反映了连接和流处理的能力，它必须是功能 （能够捕获/呈现）。 公开的音频终点需要继续在起作用，即使系统状态更改，如︰

 - 在电源时源从外部更改到电池反之亦然

 - 同时从集成 GPU 切换到 descrete GPU，反之亦然

**使用 Windows 10 移动设备**

音频驱动程序不得执行隐藏的流重定向、 路由、 交换、 拆分、 混合、 复用到其他公开或隐藏逻辑音频设备、 应用程序或其他实体，但它必须确保音频流从一个特定的逻辑设备的音频系统终结点仅指向该应用程序由 Windows 用户在 Windows 声音控制面板中设置数据流，该特定的逻辑设备。

**耳机接头、 扬声器接头、 HDMI 接口、 DisplayPort 连接器，通过坞站，无线连接的设备和网络连接的音频设备**

驱动程序需要正确表达相应设备的连接状态。

如果没有插入连接器，或将无线或网络设备未连接的可用状态，则驱动程序必须是︰

1.  设置 KSJACK\_说明。为 FALSE 时，IsConnected 成员或

2.  禁用 KS 筛选器接口

    -   AvStream 驱动程序︰ 连接线拔下通过实现以下的属性和事件声明︰

        -   KSPROPSETID\_插孔

            -   KSPROPERTY\_插座\_说明

            -   KSPROPERTY\_插座\_DESCRIPTION2

        -   KSEVENTSETID\_PinCapsChange

            -   KSEVENT\_PINCAPS\_JACKINFOCHANGE

    -   对于端口类驱动程序︰ 通过调用 PcUnregisterSubdevice 注销端口类子

同样，当接通电源连接器，或将无线或网络设备连接处于可用状态，然后该驱动程序必须是︰

1.  设置 KSJACK\_说明。IsConnected 成员为 TRUE 时，或

2.  启用 KS 筛选器接口︰

    -   AvStream 驱动程序︰ 连接器插入通过实施以下的属性和事件声明︰

        -   KSPROPSETID\_插孔

            -   KSPROPERTY\_插座\_说明

            -   KSPROPERTY\_插座\_DESCRIPTION2

        -   KSEVENTSETID\_PinCapsChange

            -   KSEVENT\_PINCAPS\_JACKINFOCHANGE

    -   对于端口类驱动程序︰ 通过调用 PcRegisterSubdevice 注册端口类子

驱动程序时更改 KSJACK\_说明。IsConnected 成员，则驱动程序必须生成事件 KSEVENTSETID\_PinCapsChange / KSEVENT\_PINCAPS\_JACKINFOCHANGE。

上述的行为可确保 Windows 路由到连接器或设备音频，真正可用于流时。

连接器和无线或网络设备、 机制 (a) 是首选。 这使得设备系统用户界面 （例如，Windows 声音控制面板） 中可见，即使它可能不是立即可用，并且它确保设备将显示正确的状态。

在可拆卸的坞站设备，建议机制 (b)。

是可分离的坞站上的连接线，机制 (b) 建议以反映连接坞站。 (A) 机制建议以反映接头是否已插入。

*设计备注︰*有关需要插座检测指定的插头连接器，请参阅附加说明 Microsoft UAA HD 音频插针配置编程指南 》 白皮书。

http://go.microsoft.com/fwlink/?LinkId=716908

### <a name="deviceaudiobasefunctionspostupgrade"></a>Device.Audio.Base.FunctionsPostUpgrade

*音频设备功能正常后已升级操作系统*

<table>
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

为了支持频繁升级 Windows 操作系统，所有的音频驱动程序应正确地迁移作为 Windows 升级过程的一部分。 升级时，音频设备应正常工作并过帐具有相等或更好的功能，因为它未升级前。

为了满足这一要求，任何的功能应不取决于任何内容 （文件、 注册表设置等） 安装驱动程序包除了其他系统上的驱动程序或操作系统组件。 例如，驱动程序的自定义项 （例如，预设、 麦克风阵列的几何信息，OEM 自定义） 应该音频驱动程序软件包中而不在工厂系统上直接安装。 理想情况下，应明确使用仅 INF 指令安装驱动程序的安装。

### <a name="deviceaudiobasehardwarearchitecture"></a>Device.Audio.Base.HardwareArchitecture

*音频子系统必须使用与 Windows 兼容的技术。*

<table>
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

**集成音频设备**

*集成音频设备*是一个支持内部组件或端口以独占方式用于媒体内容。 集成音频设备的示例如下︰

-   扬声器

-   麦克风和麦克风阵列

-   模拟音频插孔 （耳机插座，音频输出接口，麦克风插孔中的行）

-   S/PDIF

-   数字输出接口，HDMI 和 DisplayPort 等

对于这些设备，可以使用任何音频硬件体系结构提供至少*一个*下列情况也是如此︰

-   该设备提供所有终结点与任何音频类驱动程序与 Windows 打包在一起使用时的基本的功能。

-   驱动程序可通过 Windows 更新，以使该设备的所有终结点的基本功能。

**外部连接的音频设备**

*外部连接的音频设备*是一种不集成到系统，已经不是特定于音频或媒体的连接。 下面是一些外部音频设备的示例︰

-   USB 音频

-   Bluetooth 音频

对于这些设备，可以使用任何音频硬件体系结构，但我们强烈建议这些设备符合标准的规范并且 Windows 音频类别驱动程序提供的基本功能。 不允许第三方驱动程序的安装的某些 Windows 设备，在函数外部音频设备的唯一方式是如果是类驱动程序与兼容。

**所有音频设备**

如果音频设备的即插即用 ID 与音频类驱动程序与 Windows 打包在一起的任何兼容，设备时使用该驱动程序必须提供其终结点的所有基本功能。

设备提供*基本功能*，当它满足所有的 Windows 硬件认证的音频设备要求。

**以获取详细信息**

[音频设备技术](http://msdn.microsoft.com/en-us/library/windows/hardware/gg454527.aspx)︰ http://go.microsoft.com/fwlink/?LinkId=716909

### <a name="deviceaudiobasepowermanagement"></a>Device.Audio.Base.PowerManagement

*音频设备必须遵守相关的电源管理规范。*

<table>
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

**所有音频设备和驱动程序**

音频设备必须遵守音频设备类电源管理参考技术指标，它为这些设备提供的设备的电源状态 (D0 – D3) 的定义。 规范还涵盖预期每个电源的状态和可能唤醒事件定义为类的设备功能。 设备和驱动程序必须实现支持的电源状态 D3。 对其他设备电源管理状态的支持是可选的。

**Bluetooth 音频设备**

Bluetooth 音频设备必须向下打开电源之前完成 HCIDisconnect。

HCIDisconnect 被要求及时通知到系统允许此设备不再可用。 这用来重排音频到备用的音频接收器无缝 Bluetooth 音频设备电源关闭时。

**引用**

ACPI 规范︰ <http://www.acpi.info/>

Bluetooth 规格︰ <https://www.bluetooth.org/en-us/specification/adopted-specifications>

MSDN: http://go.microsoft.com/fwlink/?LinkId=716910

### <a name="deviceaudiobasesamplepositionaccuracy"></a>Device.Audio.Base.SamplePositionAccuracy

*音频驱动程序报告呈现流同步定义精确的示例位置。*

<table>
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

对于所有音频的终结点，IAudioClock::GetPosition 应报告用的时间戳︰

-   | 偏向 |&lt;= 1 毫秒

-   | 扭曲 |&lt;= 1%

-   抖动&lt;= 1 毫秒

此要求适用呈现和对于所有格式，捕获模式和针脚 （主机、 卸载、 环回）。

### <a name="deviceaudiobasestreamingformats"></a>Device.Audio.Base.StreamingFormats

*音频子系统必须使用由 Windows 支持的格式。*

<table>
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

**所有音频设备**

此要求适用于输入 （捕获） 和输出 （渲染） 设备。

音频设备必须公开支持至少一个 PCM （脉冲编码调制） 编码与 Windows 兼容的格式。

必须使用至少一个下面的位深度和容器︰

-   8 位 （无符号）
-   16 位
-   20 位 24 位容器中
-   24 位
-   24 位 32 位容器中
-   32 位

这些示例必须为整数或浮点数 IEEE 754。

任何采样速率将使用 windows 音频管道;但是，我们建议在媒体方案中的最佳电源性能支持 48 kHz 和 44.1 kHz。

如果设备支持输入和输出能力，音频设备必须支持的格式的独立选择并支持并发流在任意选定的格式。

通道配置必须至少下列情况之一:

-   （单声道）
-   （立体声）
-   2.1
-   3.1
-   4.0
-   5.0
-   5.1
-   7.1

如果音频设备支持多声道音频格式，音频设备驱动程序必须处理通道掩码与内容和当前所选的扬声器配置一致。

环回针脚应符合其相应的默认模式主机呈现旋转的格式。

**数字与外部连接的设备**

对于其中存在的源和接收器的关系 （例如 HDMI 和 Bluetooth） 的设备，在源设备必须支持并公开所有接收器所需的格式。 例如，HDMI 要求接收器支持 48 kHz*或*44.1 kHz;因此，HDMI 源必须支持 （至少） 两个 48 kHz*和*44.1 kHz，以便任何 HDMI 接收器设备连接是否正常工作。 我们建议来源的最佳的用户体验支持所有可能的接收器格式。

**硬件加速 （卸载）**

利用 DSP 的音频将卸载的设备必须支持的格式都支持相同的设备上的主机 （系统） 销的超集。 这样可以确保将尽可能使用和避免不必要回退到主机针。

**引用**

MSDN: <http://go.microsoft.com/fwlink/?LinkId=716911>

MSDN: <https://msdn.microsoft.com/en-us/library/windows/hardware/ff537083.aspx>

### <a name="deviceaudiobasesupportwindowsapis"></a>Device.Audio.Base.SupportWindowsAPIs

*与所有 Windows 音频 Api 驱动程序应正常工作*

<table>
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

使用任何 Windows 音频 Api 时，驱动程序应正确传输。 这包括但不限于以下︰

-   媒体基础 Api

<!-- -->

-   XAudio2 的 Api

-   WASAPI

-   MediaCapture 的 Api

### <a name="deviceaudiobasevolumecontrol"></a>Device.Audio.Base.VolumeControl

*音频驱动程序音量控制线性，并且具有足够的分辨率。*

<table>
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

在将音量控制在 3%的公差范围内的线性信号响应 （如通过电气或数字信号电平测量） 的更改。 例如︰ 10 dB 的音量滑块更改会导致 9.7 dB 10.3 dB 之间测得的卷进行更改 + 或-0.3dB。

拓扑结构卷节点必须等同于或优于 1.5 dB 的分辨率和卷级别定义 Windows 驱动程序工具包中的驱动程序支持。

请参阅 Windows 驱动程序工具包，"KSPROPERTY\_音频\_VOLUMELEVEL"的更多详细信息。

<a name="device.audio.hardwareaudioprocessing"></a>
## <a name="deviceaudiohardwareaudioprocessing"></a>Device.Audio.HardwareAudioProcessing

*HardwareAudioProcessing*

### <a name="deviceaudiohardwareaudioprocessingaudiohardwareoffloading"></a>Device.Audio.HardwareAudioProcessing.AudioHardwareOffloading

*支持卸载音频呈现处理的硬件必须满足这一要求。*

<table>
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

**如果硬件解决方案支持卸载音频渲染处理，则驱动程序必须公开 KS 筛选器和一个 KSNODETYPE\_音频\_引擎节点与适当的 pin 工厂连接。**

如果将音频呈现处理、 混合、 或解码硬件解决方案支持的情况下，驱动程序必须公开 KS 筛选器。 每个渲染路径通过该筛选器支持硬件卸载该驱动程序必须公开单个 KSNODETYPE\_音频\_引擎节点，只有以下 pin 工厂直接连接︰

-   两种 KS 水池 pin 工厂

-   用于引用流支持单个 KS 源 pin 工厂

**如果一个驱动程序公开 KSNODETYPE\_音频\_引擎节点、 驱动程序和硬件必须支持基层的功能。**

如果一个驱动程序公开 KSNODETYPE\_音频\_引擎节点、 驱动程序和硬件必须支持下列功能︰

-   具有至少 3 个输入 （2 卸载和 1 主机进程） 的音频混音器

-   前和后混合的音量和静音功能

-   引用流 (支持发送音频流后混合回 Windows 音频堆栈)

-   提供引用流应该是最终的输出到音频设备，或者如果编码正在进行，在编码之前。

**如果硬件支持测量报告 （支持查询每个流高峰值，前期和后期混音）**

-   为流测量 （预混合）、 计量级别应报告在 SFX 之后和之前音量控制

-   终结点测光 （后期混合），测定级别应报告︰

    -   音量控制和 EFX，EFX 时编码器之前

    -   在 EFX 之后和音量控制，当 EFX 不可编码器之前

**如果一个驱动程序公开 KSNODETYPE\_音频\_引擎的节点，则驱动程序必须公开某些 pin 工厂。**

如果一个驱动程序公开 KSNODETYPE\_音频\_引擎的节点，则驱动程序必须公开以下 pin 工厂︰

-   主机进程 pin 工厂

    -   必须支持至少一个实例

-   减轻负担的 pin 工厂

    -   必须支持至少两个实例

-   环回 pin 工厂

    -   必须支持至少一个实例

此外，以下必须满足︰

-   环回针脚必须︰

    -   有"全球的可能的实例"至少 1

    -   无论什么支持至少 1 实例正在运行的系统中

-   若要启用方案如交叉淡入淡出、 卸载功能终结点 1 环回针实例 + 的插针 1 的主机实例必须支持 + 以下以隔离方式，假定其他各项减轻终结点正在使用时︰

    -   任何受支持的 PCM 格式 + 任何受支持的 PCM 格式 （相同或不同）

<!-- -->

-   必须支持环回针

    -   硬件组合格式

    -   设备格式 （这可以公开从终结点属性存储查询）

**如果硬件解决方案支持卸载音频呈现处理，硬件 （例如，处理、 效果等） 中提供的相同功能必须可用主机插针上。**

为了提供一致的用户体验和用户启用或配置只是硬件或仅软件中存在的功能时防止混淆，必须相等的硬件和软件提供的功能。

**其他考虑事项**

已卸载音频设备必须接受并正确响应操作系统从结尾段 (EOS) 的通信。

如果硬件解决方案支持卸载音频呈现处理，则驱动程序必须实现 IMiniportAudioEngineNode 和 IMiniportStreamAudioEngineNode2

IMiniportAudioEngineNode 包含与目标通过 KS 筛选器句柄的音频引擎节点卸载 KS 属性相关的方法的列表。 微型端口类需要不仅从 IMiniportWaveRT 接口继承的微型端口驱动程序的 WaveRT，它还需要继承 IMiniportAudioEngineNode 接口和实现定义的所有方法。

<a name="device.audio.hdaudio"></a>
## <a name="deviceaudiohdaudio"></a>Device.Audio.HDAudio

*此音频设备使用高清晰度音频驱动程序。*

### <a name="deviceaudiohdaudiohdaudiospeccompliance"></a>Device.Audio.HDAudio.HDAudioSpecCompliance

*高清晰度音频编解码器的音频必须遵守英特尔高保真音频规范。*

<table>
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

**高清晰度音频编解码器**必须遵守以下规范︰

-   英特尔高清晰度音频技术指标和 DCNs

-   高清晰度音频设备的即插准则

此外，代码必须实现以下功能，没有必要由英特尔高定义音频规范要求︰

扬声器补偿是唯一有效的音频信号的编解码器，音频流的处理方案，然后它才有效扬声器是硬连线到针复杂，其中包含处理节点 （如便携式计算机集成的扬声器）。 此要求不适用于解密受保护的音频流。

<ol style="list-style-type: decimal">
<li><p>所有 HDAudio 编码解码器的小部件配置时处于良性的处理状态，编解码器可对通过音频流执行任何非线性或时变的处理。</p></li>
<li><p>HDAudio 编码解码器必须只能通过 HDAudio 总线控制器。 编解码器必须公开寄存器或内存或 I/O 地址空间通过访问其他硬件机制。 HDMI 或 DisplayPort，无法不满足这一要求。 对于 HDMI 或 DisplayPort，请参考 HD 音频 HDMI DCN。</p></li>
<li><p>不能组合调制解调器和音频功能。 虽然调制解调器和音频设备，可容纳相同的硅，函数必须是单独的设备，并不能共享的任何软件或硬件资源 （如 ADCs 或 Dac）。</p></li>
<li><p>运行状态 （HD 音频控制器为 D0） 高质音频链接时，HD 音频编解码器必须响应命令，即使在所有必需的设备电源管理状态中关闭。 实际上，编解码器的数字部分必须保持通电。</p></li>
<li><p>即使在一个不存在的构件解决或者动词本身无效，编解码器必须响应动词。</p></li>
<li><p>函数组节点时节点 Id 必须为 0 到 127 范围内。 此限制不适用于构件节点的节点 Id。</p></li>
<li><p>高清晰度音频编解码器针配置寄存器中的默认数据必须不谎报的硬件功能，并配置默认注册不得为空 （零）。</p></li>
<li><p>HDAudio 编码解码器中的函数组必须公开一个非零的子系统 id。 如有必要，BIOS 将覆盖子系统 ID。 如果 BIOS 无法编写子系统 ID; 如果是错误地，硬件必须提供一个默认供应商特定子系统 id。</p></li>
<li><p>高清晰度音频编解码器的每个端口连接到一个且仅一个音频源、 目标或插孔。 与类驱动程序的兼容性，请不要不双幅不到类驱动程序通过针配置寄存器中的信息公开的方式的输入 / 输出端口上。 加载类驱动程序时，使用第三方功能的驱动程序的控制下 GPIOs 的设计必须默认为相应的硬件配置。</p></li>
<li><p>HD 音频编码解码器驱动程序必须不退出函数组处于 D3Cold 状态时卸载。 由 IRP_MJ_PNP/IRP_MN_REMOVE_DEVICE 的 IRP 处理退出，HD 音频编码解码器驱动程序必须具有︰</p>
<ol style="list-style-type: lower-alpha">
<li><p>记住，或发现函数组的当前电源状态</p></li>
<li><p>如果函数组的当前电源状态 D3 冷，驱动程序必须具有更改到不同的电源状态。 在退出时的函数组电源状态需要 D3。</p></li>
</ol></li>
</ol>

**高清晰度音频控制器必须符合下列要求︰**

1.  英特尔高定义音频控制器规范

2.  进行更新，以符合未来规范修订

3.  遵守最新高清晰音频规范 ECRs 按照围绕新硬件需求的策略。

4.  高清晰度音频硬件符合 HD 音频规范版本 1.0 必须在相应寄存器设置正确的版本号。 VMAJ 和 VMIN 寄存器必须指定 01h 的主要版本号和次要版本号为 00h。

<a name="device.audio.usb"></a>
## <a name="deviceaudiousb"></a>Device.Audio.USB

*此音频设备使用的 USB 音频驱动程序。*

### <a name="deviceaudiousbhidcontrols"></a>Device.Audio.USB.HIDControls

*USB 音频设备使用 USB HID 音频控件保留通知的用户与设备交互的操作系统。*

<table>
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

USB 音频设备必须使用 USB HID 规范符合 HID 控制基本功能。 如果音量调整控制实现 USB 音频设备上，它必须将其自身声明作为使用者控制设备 （使用 0x01），如 USB 使用表中的使用者页 （页 0x0C） 中定义的 HID 电源设备，版本 1.1 中，并在 Windows 支持的基于 HID 的音频控件。

实现隐藏了 USB 接口的通信设备必须是符合人体学接口设备 (HID)、 版本 1.1 和 USB 使用表的 HID 电源设备，版本 1.12 USB 设备类定义。

设备不能使用保留的使用实例，从任何标准用法页。

详细设计信息在<http://go.microsoft.com/fwlink/?LinkId=40491>的 Windows 驱动程序工具包、"隐藏和窗口"看到"隐藏音频控件和窗口"。

### <a name="deviceaudiousbusb"></a>Device.Audio.USB.USB

*USB 音频设备必须遵循 UAA USB 音频设计准则。*

<table>
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

说明︰ 符合 Device.Audio.Base.HardwareArchitecture USB 基于音频的音频设备中一个独立的外部形式因素，AVR 或在其他排列。

特别注意应当如下︰

-   USB 音频设备必须正确设置说明符指示根据 USB 规范<http://www.usb.org/developers/devclass_docs/termt10.pdf>设备的目的。

-   外部连接的 USB 基于的麦克风阵列设备必须遵守音频设备 2.0 中，USB 设备类定义，并且必须实现根据准则中"麦克风阵列的支持在 Windows Vista 中。" 该设备必须报告本身和根据 Microsoft USB 音频麦克风阵列设计指南中的设计原则及其功能。

**引用︰**

通用串行总线设备类定义音频设备 2.0 在[*http://www.usb.org/developers/docs/devclass\_文档 /*](http://www.usb.org/developers/docs/devclass_docs/)
