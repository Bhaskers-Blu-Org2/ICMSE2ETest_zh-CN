---
title: Device.Streaming.HMFT
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 22f4c577b2cf087e1d293cc21fbc3c4db1512e76
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Streaming.HMFT

 - [Device.Streaming.HMFT](#device.streaming.hmft)
 -->
 
<a name="device.streaming.hmft"></a>
##Device.Streaming.HMFT

### <a name="devicestreaminghmftdecoding"></a>Device.Streaming.HMFT.Decoding

*硬件介质基础转换 (HMFT) 必须支持视频解码。*

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

**受支持的格式**

MPEG-4 第 2 部分和问题的 MJPEG 仅支持 HMFT 视频解码器。 这两种格式都如果实现。

**媒体基础法规遵从性**视频解码器硬件介质基础转换 (HMFT) 必须完全符合以下媒体基础变换 (MFT) 接口︰

-   IMFTransform
-   IMFMediaEventGenerator
-   IMFShutdown
-   IMFQualityAdvise
-   IMFRealTimeClientEx

HMFT 视频解码器必须使用通过**IMFRealTimeCLientEx::SetWorkQueue**的媒体基础工作队列支持 （无线程创建）。 这可确保︰

-   为播放和捕获/编码支持多媒体类计划程序服务 (MMCSS)
-   改进了的核心的可扩展性

HMFT 视频解码器必须支持**IMF2DBuffer2**为了增强安全性，但也处理输入的缓冲区类型**IMF2DBuffer**和**IMFMediaBuffer**首选项的顺序。

**DirectX 呈现**

视频解码器 HMFT 必须支持 DirectX (DX) 9 和，DX11 设备，它必须避免或缩小 DX11 组件的副本。

在 MFT\_设置\_D3D\_管理器中，HMFT 必须首先查询 DirectX 图形基础结构 (DXGI) 经理和 DXGI 管理器找不到查询 D3D9 管理器的视频解码器。

HMFT 视频解码器必须支持系统内存输出，因为管线中的某些转换可能支持仅系统内存缓冲区。

如果 HMFT 视频解码器基于 GPU，它必须支持 DX11。

**内存使用情况**

HMFT 视频解码器必须是异步的 MFT。 这就减少了大约 50%的工作集内存。

**业绩受信任的证书和验证**

视频解码器 HMFT 必须支持受信任值得认证和验证过程中，定义跨 Windows 硬件认证工具包。

每个 HMFT 视频解码器必须作为一个独立的二进制文件提供，必须分别签名。

HMFT 视频解码器必须公布支持多个压缩标准。

所有 HMFTs 必须在系统中注册 MFT 时都设置下列媒体基础属性︰

-   MFT\_枚举\_硬件\_URL\_特性
-   MFT\_枚举\_硬件\_供应商\_ID\_特性

**格式要求**

HMFT 视频解码器必须公布支持通过 DirectX 视频加速 (DXVA) （H.264、 H.264、 WMV) MPEG2 的收件箱格式的支持。

**如果实现**︰ mpeg-4 第 2 部分的 HMFT 视频解码器必须支持简单和高级简单配置文件 （如果不支持全局运动补偿 (GMC)，则必须拒绝媒体类型以允许软件解码器，用于播放），和所有级别。

-   解码器必须是完全一致的格式定义的规范。

-   此外，MPEG-4 第 2 部分解码器必须完全支持 H.263 基准内容并公布此媒体类型的支持。

除了上述的要求，我们建议消除马赛克功能和 deringing 后处理的解码器支持。

供应商可能会提供格式不是其他 HMFTs 视频解码器支持收件箱，但有没有验证测试或徽标认证。

**注意︰**建议和本文档中定义的要求适用于所有格式。

**功能**

视频解码器 HMFT 必须支持以下功能︰

-   格式和分辨率的动态更改
-   欺骗模式 （播放速率控制，细化模式） 寻求

**隔行扫描的支持**

HMFT 视频解码器必须支持这两种交错式和渐进式的位流的输入的格式。 它必须不取消隔行扫描。 它可能支持反相电视电影 (IVTC)。

**多个实例**

HMFT 视频解码器必须支持多个实例的解码器中的并行 （进程内和进程外） 以启用相同或不同的应用程序中的多个并发的视频播放流。

**设计备注**

必须安装并通过满足 Windows 安全要求的设备驱动程序卸载 HMFT 视频解码器。  驱动程序不会导致操作系统崩溃或挂起，而必须禁止内存冲突。

HMFT 中的每个组件必须是单独的二进制、 单独认证和签名。

### <a name="devicestreaminghmftencoding"></a>Device.Streaming.HMFT.Encoding

*硬件介质基础转换 (HMFT) 必须支持视频编码。*

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

**答︰ H.264 编码**


如果您的硬件支持 H.264 编码，您必须︰

**A.1 输入的格式支持**

编码器必须支持 NV12 格式输入帧数。 （可选） 编码器可以支持 IYUV 和 YUY2 格式。

编码器必须实现支持[IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx)， [IMF2DBuffer](http://msdn.microsoft.com/en-us/library/ms699894.aspx)，和[IMF2DBuffer2](http://msdn.microsoft.com/en-us/library/hh447827.aspx)媒体缓冲区接口。

**A.2 配置文件支持**

编码器必须能够创建一致到下面的配置文件的输出内容︰

 - 基线配置文件
 - 受约束的基准配置文件
 - 主配置文件
 - 受约束的高配置文件

编码器必须能够生成适当的头语法元素，以信号编码到上面列出的配置文件。

**A.3 接口支持需求**

H.264 编码器必须支持以下接口︰

A.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

下面的[IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)接口方法的实现是必需的︰

A.3.1.1 [IMFTransform::ProcessEvent::GetAttributes](http://msdn.microsoft.com/en-us/library/ms703141.aspx)

A.3.1.2 [IMFTransform::GetInputAvailableType](http://msdn.microsoft.com/en-us/library/ms704814.aspx)

A.3.1.3 [IMFTransform::GetInputCurrentType](http://msdn.microsoft.com/en-us/library/ms705607.aspx)

A.3.1.4 [IMFTransform::GetInputStatus](http://msdn.microsoft.com/en-us/library/ms697478.aspx)

A.3.1.5 [IMFTransform::GetInputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703894.aspx)

A.3.1.6 [IMFTransform::GetOutputAvailableType](http://msdn.microsoft.com/en-us/library/ms703812.aspx)

A.3.1.7 [IMFTransform::GetOutputCurrentType](http://msdn.microsoft.com/en-us/library/ms696985.aspx)

A.3.1.8 [IMFTransform::GetOutputStatus](http://msdn.microsoft.com/en-us/library/ms696269.aspx)

A.3.1.9 [IMFTransform::GetOutputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703886.aspx)

A.3.1.10 [IMFTransform::GetStreamCount](http://msdn.microsoft.com/en-us/library/ms697018.aspx)

A.3.1.11 [IMFTransform::GetStreamLimits](http://msdn.microsoft.com/en-us/library/ms697040.aspx)

A.3.1.12 [IMFTransform::ProcessEvent](http://msdn.microsoft.com/en-us/library/ms695394.aspx)

必须处理 MEEncodingParameters 事件

A.3.1.13 [IMFTransform::ProcessMessage](http://msdn.microsoft.com/en-us/library/ms701863.aspx)

A.3.1.14 [IMFTransform::ProcessInput](http://msdn.microsoft.com/en-us/library/ms703131.aspx)

A.3.1.15 [IMFTransform::ProcessOutput](http://msdn.microsoft.com/en-us/library/ms704014.aspx)

A.3.1.16 [IMFTransform::SetInputType](http://msdn.microsoft.com/en-us/library/ms700113.aspx)

A.3.1.17 [IMFTransform::SetOutputType](http://msdn.microsoft.com/en-us/library/ms702016.aspx)

A.3.1.18 [IMFTransform::SetOutputBounds](http://msdn.microsoft.com/en-us/library/ms693812.aspx)

A.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

编码器必须支持某些方法和属性的 ICodecAPI 接口的 Guid。

A.3.2.1 所需的方法

下面的 ICodecAPI 接口方法的实现是必需的︰

A.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

A.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

A.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

A.3.2.1.4 [GetParameterRange](http://msdn.microsoft.com/en-us/library/dd311956.aspx)

A.3.2.1.5 [GetParameterValues](http://msdn.microsoft.com/en-us/library/dd311957.aspx)

A.3.2.2 所需属性

对下面的 ICodecAPI 属性的 Guid 的支持是必需的

A.3.2.2.1 CODECAPI\_AVEncCommonRateControlMode

A.3.2.2.2 CODECAPI\_AVEncCommonQuality

A.3.2.2.3 CODECAPI\_AVEncCommonMeanBitRate

A.3.2.2.4 CODECAPI\_AVEncCommonMaxBitRate

A.3.2.2.5 CODECAPI\_AVEncCommonBufferSize

A.3.2.2.6 CODECAPI\_AVEncMPVGOPSize

A.3.2.2.8 CODECAPI\_AVLowLatencyMode

A.3.2.2.9 CODECAPI\_AVEncCommonQualityVsSpeed

A.3.2.2.10 CODECAPI\_AVEncVideoForceKeyFrame

A.3.2.2.11 CODECAPI\_AVEncVideoEncodeQP

A.3.2.2.12 CODECAPI\_AVEncVideoTemporalLayerCount

A.3.2.2.13 CODECAPI\_AVEncVideoSelectLayer

A.3.2.3 的可选属性

对下面的 ICodecAPI 属性的 Guid 的支持是可选的。

A.3.2.3.1 CODECAPI\_AVEncH264CABACEnable

A.3.2.3.2 CODECAPI\_AVEncMPVDefaultBPictureCount

A.3.2.3.3 CODECAPI\_AVEncVideoEncodeFrameTypeQP

A.3.2.3.4 CODECAPI\_AVEncSliceControlMode

A.3.2.3.5 CODECAPI\_AVEncSliceControlSize

A.3.2.3.6 CODECAPI\_AVEncVideoMaxNumRefFrame

A.3.2.3.7 CODECAPI\_AVEncVideoMeanAbsoluteDifference

A.3.2.3.8 CODECAPI\_AVEncVideoROIEnabled

A.3.2.3.9 CODECAPI\_AVEncVideoMinQP

A.3.2.3.10 CODECAPI\_AVEncVideoMaxQP

A.3.2.3.11 CODECAPI\_AVEncVideoLTRBufferControl

A.3.2.3.12 CODECAPI\_AVEncVideoMarkLTRFrame

A.3.2.3.13 CODECAPI\_AVEncVideoUseLTRFrame

A.3.2.3.14 CODECAPI\_AVEncLowPowerEncoder

A.3.2.3.15 CODECAPI\_AVScenarioInfo

A.3.2.3.16 CODECAPI\_AVEncMPVGOPSizeMin

A.3.2.3.17 CODECAPI\_AVEncMPVGOPSizeMax

A.3.2.3.18 CODECAPI\_AVEncVideoMaxTem

A.3.2.3.19 CODECAPI\_AVEncMaxFrameRate

A.3.2.3.20 CODECAPI\_VideoEncoderDisplayContentType

A.3.2.3.22 CODECAPI\_AVEncEnableVideoProcessing

A.3.2.3.23 CODECAPI\_AVEncVideoGradualIntraRefresh

A.3.2.4 可选属性说明

如果 H.264 编码器实现长术语参考框架，则应该 （在一帧延迟完成） 实现下面的 CodecAPI 接口︰

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

如果 H.264 编码器实现长术语参考框架，则必须支持 LongTermReferenceFrameInfo 的 IMFSample 属性。

**A.4 MF 媒体类型特性要求**

支持以下的 MF 介质类型属性是必需的︰

A.4.1 [MF\_MT\_交错\_模式](http://msdn.microsoft.com/library/ms694868.aspx)

A.4.2 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

A.4.3 [MF\_MT\_子类型](http://msdn.microsoft.com/library/ms700208.aspx)

A.4.4 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

A.4.5 [MF\_MT\_框架\_速率](http://msdn.microsoft.com/library/ms700140.aspx)

A.4.6 [MF\_MT\_框架\_大小](http://msdn.microsoft.com/en-us/library/ms701619.aspx)

A.4.7 [MF\_MT\_平均\_比特率](http://msdn.microsoft.com/library/ms703792.aspx)

A.4.8 [MF\_MT\_MPEG2\_配置文件](http://msdn.microsoft.com/library/ms700193.aspx) *(MF\_MT\_视频\_配置文件)*

A.4.9 [MF\_MT\_MPEG2\_级](http://msdn.microsoft.com/library/ms700203.aspx) *(MF\_MT\_视频\_级别)*

A.4.10 [MF\_MT\_像素\_纵横\_比](http://msdn.microsoft.com/library/ms704767.aspx)

A.4.11 [MF\_MT\_视频\_额定\_范围](http://msdn.microsoft.com/en-us/library/ms699008.aspx)

A.4.12 [MF\_MT\_视频\_原色](http://msdn.microsoft.com/en-us/library/ms697241.aspx)

A.4.13 [MF\_MT\_传输\_函数](http://msdn.microsoft.com/en-us/library/ms703086.aspx)

A.4.14 [MF\_MT\_YUV\_矩阵](http://msdn.microsoft.com/en-us/library/ms702203.aspx)

A.4.15 [MF\_MT\_视频\_色度\_SITING](http://msdn.microsoft.com/en-us/library/ms694178.aspx)

A.4.16 [MF\_NALU\_长度\_设置](http://msdn.microsoft.com/en-us/library/hh870258.aspx)

**A.5 MF 样本特性支持需求**

A.5.1 所需的属性示例

根据是否设置了 ICodecAPI 或 MF 的媒体类型特性，以下示例属性必须有输入或输出的示例︰

A.5.1.1 MFSampleExtension\_MeanAbsoluteDifference

MFSampleExtension\_MeanAbsoluteDifference 示例属性需要输出样本，如果 CODECAPI\_AVEncVideoMeanAbsoluteDifference 属性已设置为非零值。 请注意，由于 CODECAPI\_AVEncVideoMeanAbsoluteDifference 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoMeanAbsoluteDifference 支持。

A.5.1.2 MFSampleExtension\_LongTermReferenceFrameInfo

MFSampleExtension\_LongTermReferenceFrameInfo 示例属性需要输出样本，如果 CODECAPI\_AVEncVideoLTRBufferControl 表明可能存在一个或多个长期的参考框架。 请注意，由于 CODECAPI\_AVEncVideoLTRBufferControl 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoLTRBufferControl 支持。

MF A.5.1.3\_NALU\_长度\_信息

MF\_NALU\_长度\_如果都需要输出样本信息示例属性 MF\_NALU\_长度\_设置媒体类型属性已设置为非零值。

A.5.1.4 MFSampleExtension\_ROIRectangle

输入的示例可能包含 MFSampleExtension\_ROIRectangle 采样特性，如果 CODECAPI\_AVEncVideoROIEnabled 属性已设置为非零值。 请注意，由于 CODECAPI\_AVEncVideoROIEnabled 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoROIEnabled 支持。

A.5.2 示例可选属性

可能存在下面的输入的样本特性。 它是可选的编码器是否利用这些属性所包含的信息。

A.5.2.1 MFSampleExtension\_DirtyRects

A.5.2.2 MFSampleExtension\_MoveRegions

**A.6 MFT 特性**

编码器需要支持[IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx)将返回的[IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx)接口，它允许访问与 MFT 的特性。 支持用于处理以下的 MFT MF 属性是必需的︰

A.6.1 [MFT\_枚举\_硬件\_URL\_属性](http://msdn.microsoft.com/library/dd388664.aspx)

A.6.2 [MFT\_枚举\_硬件\_供应商\_ID\_属性](http://msdn.microsoft.com/en-us/library/windows/desktop/hh162798.aspx)

A.6.3 [MFT\_编码器\_支持\_配置\_事件](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302174.aspx)

A.6.4 [MF\_视频\_最大\_MB\_PER\_秒](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302206.aspx)

A.6.5 MFT\_GFX\_驱动程序\_版本\_ID\_特性

A.6.6 MFT\_编码器\_错误

**A.7 功能支持需求**

H.264 编码器必须支持以下功能︰

A.7.1 VBR 峰值约束率控制模式

编码器将使用的值的 CODECAPI\_AVEncCommonMeanBitRate、 CODECAPI\_AVEncCommonMaxBitRate 和 CODECAPI\_AVEncCommonBufferSize 属性，以确保理论的缓冲区不会违反了在峰值比特率 (CODECAPI\_AVEncCommonMaxBitRate) 同时汇聚成 CODECAPI 的比特率\_AVEncCommonMeanBitRate 整个视频剪辑。

A.7.2 基于质量的 VBR 率控制模式

编码器将使用的值 CODECAPI\_AVEncCommonQuality 或 CODECAPI\_AVEncVideoEncodeQP 以获得恒定的压缩视频的质量。 编码器将为所有框架使用常量 QP。

A.7.3 CBR 率控制模式

编码器将使用的值的 CODECAPI\_AVEncCommonMeanBitRate 或 MF\_MT\_平均\_比特率和 CODECAPI\_AVEncCommonBufferSize 属性，以确保理论的缓冲区不会违反了在指定的比特率 (CODECAPI\_AVEncCommonMeanBitRate 或 MF\_MT\_平均\_比特率)。

A.7.4 GOP 的距离

编码器将 CODECAPI 的值所指定的帧间隔生成关键帧\_AVEncMPVGOPSize 属性。 此属性的值为 IntMAX 表示只有第一个框架应为关键帧。

A.7.5 基于帧的 QP 控件

必须支持在小 QP 介于 20 到 40 个。 设置一个无效值 (例如，52) 时，则必须返回一个错误。

A.7.6 强制关键帧控件

IDR 的前面必须加上 SP/放映 时的瞬时层数&gt;1，关键帧必须插入下一步的基本临时层框架中为保留的临时结构。 为单个图层 bitstream，必须在下一帧中插入关键帧。

A.7.7 质量与速度控制

A.7.8 低延迟控制

编码器必须支持的功能设为低滞后时间模式。 在此模式下，编码器不应缓冲任何输入的示例。 它必须是可产生输出示例中为每个输入的示例。

编码器还必须强制 POC 类型 2 或设置 VUI bitstream\_限制标志为 TRUE 并且 VUI num\_重新排序\_框架为 0。

A.7.8 临时层支持

需要编码器支持分层 P 帧编码，能产生 bitreams 的 1、 2 或 3 的按时间顺序无关层。

A.7.9 长期参考框架支持

如果 H.264 编码器实现长术语参考框架，则应该 （在一帧延迟完成） 实现下面的 CodecAPI 接口︰

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

**A.8 MFT 异步支持**

建议您执行[异步 MFT](http://msdn.microsoft.com/library/dd317909.aspx)。 异步的 MFT 要求实现[IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx) [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx)接口。

**A.9 IMFRealTimeClientEx**

注册机上的 IMFRealTimeCLientEx::SetWorkQueue 通过 MMC 至关重要，以满足性能目标，因此，实现[IMFRealTimeClientEx](http://msdn.microsoft.com/en-us/library/windows/desktop/hh448047.aspx)接口的建议。

**A.9 多实例要求**

它是必需的 H.264 编码器必须支持至少 4 并发实例。 编码器不应置于任何限制的实例数。 它应受的内存使用情况。

这种情况可能会在同一进程中或在不同的进程。

**A.10 业绩验证**

它是必需的 H.264 编码器支持受信任的值得验证过程。

它是必需的 H.264 编码器，分别是独立的二进制文件，认证和签名。

**A.11 附加要求**

H.264 编码器必须使用[Windows MP4 文件接收器](http://msdn.microsoft.com/library/dd757763.aspx)。

H.264 编码器必须实现的编码配置正确的顺序。

H.264 编码器必须可产生有效 bitstreams 与最多 3 个临时的图层。

您的 H.264 编码器前缀 NALU 前面添加每个扇区，与 1-3 瞬时层 bitstreams 与正确的语法。

H.264 编码器必须发送一个批的 GPU 请求每个框架。

H.264 编码器必须插入每个帧前 AUD NALU。

H.264 编码器必须在会话 0 中正常工作。

**A.12 安装**

它是必需的 H.264 编码器注册和未注册的以及在编码器中使用的设备驱动程序。

**A.113 动态格式更改**

它是必需的 H.264 编码器支持动态格式的更改，在下列情况︰

更改配置文件

分辨率和帧速率变化

添加和删除临时的图层

最大允许参考帧数

当多个更改请求在产生的输出帧前时，应遵守上一次更改。

**B.vc-1 编码**

如果您的硬件支持 VC-1 编码，您必须︰

**B.1 上输入︰**

B.1.1 支持 NV12

B.1.2 如果您的硬件支持︰

B.1.2.1 支持 IYUV 和 YUY2

B.1.3 支持的输入的缓冲 （和查询按此顺序）︰

B.1.3.1 IMF2DBuffer2

B.1.3.2 [IMF2DBuffer](http://msdn.microsoft.com/library/ms699894.aspx)

B.1.3.3 [IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx)

**B.2 上输出︰**

B.2.1 支持简单配置文件

B.2.2 支持主配置文件

B.2.3 支持高级配置文件

**B.3 您 vc-1 编码器必须公开下面的接口︰**

B.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

B.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

B.3.2.1 ICodecAPI 要求实现以下功能︰

B.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

B.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

B.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

B.3.2.2 ICodecAPI 要求必须支持以下属性︰

B.3.2.2.1 峰值约束 VBR 模式

B.3.2.2.2 基于质量的 VBR 模式

B.3.2.2.3 采用 CBR 编码方式

B.3.2.2.4 GOP 的距离

B.3.2.2.5 框架 QP 控件

B.3.2.2.6 自适应的比特率控制

B.3.2.2.7 强制关键帧控件

B.3.2.2.8 QualityVsSpeed 控件

B.3.2.2.9 低延迟编码

B.3.2.3 建议您另外实现以下功能︰

B.3.2.3.1 [GetDefaultValue](http://msdn.microsoft.com/library/dd311955.aspx)

B.3.2.3.2 [GetParameterRange](http://msdn.microsoft.com/library/dd311956.aspx)

B.3.2.3.3 [GetParameterValues](http://msdn.microsoft.com/library/dd311957.aspx)

B.3.2.3.4 [IsModifiable](http://msdn.microsoft.com/library/dd311959.aspx)

B.3.2.3.5 [SetAllDefaults](http://msdn.microsoft.com/library/dd311962.aspx)

B.3.3 [IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx)

通过[IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx) B.3.3.1

B.3.3.2 所需的两个属性是︰

B.3.3.2.1 [MFT\_枚举\_硬件\_URL\_属性](http://msdn.microsoft.com/library/dd388664.aspx)

B.3.3.2.2 MFT\_枚举\_硬件\_供应商\_ID\_特性

建议您执行[异步 MFT](http://msdn.microsoft.com/library/dd317909.aspx)的 B.3.4。

B.3.4.1 异步 Mft 需要以下附加接口︰

B.3.4.1.1 [IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx)

B.3.4.1.2 [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx)

B.3.4.2 异步 Mft 最好避免创建线程和建议使用 MF 线程池。

通过 IMFRealTimeCLientEx::SetWorkQueue 的 MMC B.3.4.2.1 注册至关重要，以满足性能目标。

建议使用 B.3.5 IMFRealTimeClientEx

**B.4 编码设置**

B.4.1 通过输入的介质类型协商、 vc-1 编码器必须支持︰

B.4.1.1 [MF\_MT\_交错\_模式](http://msdn.microsoft.com/library/ms694868.aspx)

B.4.1.1.1 编码器必须保留隔行扫描输入输出或拒绝从隔行扫描。

B.4.1.2 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

B.4.2 通过输出介质类型协商，vc-1 编码器必须支持︰

B.4.2.1 [MF\_MT\_子类型](http://msdn.microsoft.com/library/ms700208.aspx)

B.4.2.2 [MF\_MT\_框架\_大小](http://msdn.microsoft.com/library/ms701619.aspx)

BC.4.2.3 [MF\_MT\_框架\_速率](http://msdn.microsoft.com/library/ms700140.aspx)

B.4.2.4 [MF\_MT\_平均\_比特率](http://msdn.microsoft.com/library/ms703792.aspx)

B.4.2.5 [MF\_MT\_像素\_纵横\_比](http://msdn.microsoft.com/library/ms704767.aspx)

B.4.3 建议 vc-1 编码器支持︰

B.4.3.1。 B 帧编码

**B.5 多个实例**

B.5.1 是必需 vc-1 编码器必须支持最少的 3 个并发实例。 编码器不应置于任何限制的实例数。 它应受的内存使用情况。

这些实例在同一进程中或在不同的进程可能是 B.5.1.1。

**B.6 业绩验证**

B.6.1 是必需 vc-1 编码器支持受信任的值得验证过程。

B.6.2 是必需 vc-1 编码器分别进行独立的二进制文件，认证和签名。

**B.7 的附加要求**

B.7.1 您的 vc-1 编码器必须使用[Windows ASF 文件接收器](http://msdn.microsoft.com/library/ee663576.aspx)。

B.7.2 您的 vc-1 编码器必须实现编码配置的正确顺序。

B.7.3 您的 vc-1 编码器必须在会话 0 中正常工作。

**B.8 安装**

B.8.1 是必需的 vc-1 编码器注册和未注册的以及在编码器中使用的设备驱动程序。

**C.H.265 编码**

如果您的硬件支持 H.265 编码，您必须︰

**C.1 输入的格式支持**

编码器必须支持 NV12 格式输入帧数。 （可选） 编码器可以支持 IYUV 和 YUY2 格式。

编码器必须实现支持[IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx)， [IMF2DBuffer](http://msdn.microsoft.com/en-us/library/ms699894.aspx)，和[IMF2DBuffer2](http://msdn.microsoft.com/en-us/library/hh447827.aspx)媒体缓冲区接口。

**C.2 配置文件支持**

编码器必须能够创建一致的主配置文件的输出内容。

编码器必须能够生成适当的头语法元素发送信号到主配置文件进行编码。

**C.3 接口支持需求**

H.265 编码器必须支持以下接口︰

C.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

下面的[IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)接口方法的实现是必需的︰

C.3.1.1 [IMFTransform::ProcessEvent::GetAttributes](http://msdn.microsoft.com/en-us/library/ms703141.aspx)

C.3.1.2 [IMFTransform::GetInputAvailableType](http://msdn.microsoft.com/en-us/library/ms704814.aspx)

C.3.1.3 [IMFTransform::GetInputCurrentType](http://msdn.microsoft.com/en-us/library/ms705607.aspx)

C.3.1.4 [IMFTransform::GetInputStatus](http://msdn.microsoft.com/en-us/library/ms697478.aspx)

C.3.1.5 [IMFTransform::GetInputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703894.aspx)

C.3.1.6 [IMFTransform::GetOutputAvailableType](http://msdn.microsoft.com/en-us/library/ms703812.aspx)

C.3.1.7 [IMFTransform::GetOutputCurrentType](http://msdn.microsoft.com/en-us/library/ms696985.aspx)

C.3.1.8 [IMFTransform::GetOutputStatus](http://msdn.microsoft.com/en-us/library/ms696269.aspx)

C.3.1.9 [IMFTransform::GetOutputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703886.aspx)

C.3.1.10 [IMFTransform::GetStreamCount](http://msdn.microsoft.com/en-us/library/ms697018.aspx)

C.3.1.11 [IMFTransform::GetStreamLimits](http://msdn.microsoft.com/en-us/library/ms697040.aspx)

C.3.1.12 [IMFTransform::ProcessEvent](http://msdn.microsoft.com/en-us/library/ms695394.aspx)

必须处理 MEEncodingParameters 事件︰

C.3.1.13 [IMFTransform::ProcessMessage](http://msdn.microsoft.com/en-us/library/ms701863.aspx)

C.3.1.14 [IMFTransform::ProcessInput](http://msdn.microsoft.com/en-us/library/ms703131.aspx)

C.3.1.15 [IMFTransform::ProcessOutput](http://msdn.microsoft.com/en-us/library/ms704014.aspx)

C.3.1.16 [IMFTransform::SetInputType](http://msdn.microsoft.com/en-us/library/ms700113.aspx)

C.3.1.17 [IMFTransform::SetOutputType](http://msdn.microsoft.com/en-us/library/ms702016.aspx)

C.3.1.18 [IMFTransform::SetOutputBounds](http://msdn.microsoft.com/en-us/library/ms693812.aspx)

C.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

编码器必须支持某些方法和属性的 ICodecAPI 接口的 Guid。

A.3.2.1 所需的方法

下面的 ICodecAPI 接口方法的实现是必需的︰

C.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

C.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

C.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

C.3.2.1.4 [GetParameterRange](http://msdn.microsoft.com/en-us/library/dd311956.aspx)

C.3.2.1.5 [GetParameterValues](http://msdn.microsoft.com/en-us/library/dd311957.aspx)

C.3.2.2 所需属性

对下面的 ICodecAPI 属性的 Guid 的支持是必需的︰

C.3.2.2.1 CODECAPI\_AVEncCommonRateControlMode

C.3.2.2.2 CODECAPI\_AVEncCommonQuality

C.3.2.2.3 CODECAPI\_AVEncCommonMeanBitRate

C.3.2.2.4 CODECAPI\_AVEncCommonMaxBitRate

C.3.2.2.5 CODECAPI\_AVEncCommonBufferSize

C.3.2.2.6 CODECAPI\_AVEncMPVGOPSize

C.3.2.2.8 CODECAPI\_AVLowLatencyMode

C.3.2.2.10 CODECAPI\_AVEncVideoForceKeyFrame

C.3.2.2.11 CODECAPI\_AVEncVideoEncodeQP

C.3.2.3 的可选属性

对下面的 ICodecAPI 属性的 Guid 的支持是可选的。

C.3.2.3.1 CODECAPI\_AVEncCommonQualityVsSpeed

C.3.2.3.2 CODECAPI\_AVEncVideoTemporalLayerCount

C.3.2.3.3 CODECAPI\_AVEncVideoSelectLayer

C.3.2.3.4 CODECAPI\_AVEncMPVDefaultBPictureCount

C.3.2.3.5 CODECAPI\_AVEncVideoEncodeFrameTypeQP

C.3.2.3.6 CODECAPI\_AVEncSliceControlMode

C.3.2.3.7 CODECAPI\_AVEncSliceControlSize

C.3.2.3.8 CODECAPI\_AVEncVideoMaxNumRefFrame

C.3.2.3.9 CODECAPI\_AVEncVideoMeanAbsoluteDifference

C.3.2.3.10 CODECAPI\_AVEncVideoROIEnabled

C.3.2.3.11 CODECAPI\_AVEncVideoMinQP

C.3.2.3.12 CODECAPI\_AVEncVideoMaxQP

C.3.2.3.13 CODECAPI\_AVEncVideoLTRBufferControl

C.3.2.3.14 CODECAPI\_AVEncVideoMarkLTRFrame

C.3.2.3.15 CODECAPI\_AVEncVideoUseLTRFrame

C.3.2.3.16 CODECAPI\_AVEncLowPowerEncoder

C.3.2.3.17 CODECAPI\_AVScenarioInfo

C.3.2.3.18 CODECAPI\_AVEncMPVGOPSizeMin

C.3.2.3.19 CODECAPI\_AVEncMPVGOPSizeMax

C.3.2.3.20 CODECAPI\_AVEncVideoMaxTem

C.3.2.3.21 CODECAPI\_AVEncMaxFrameRate

C.3.2.3.22 CODECAPI\_VideoEncoderDisplayContentType

C.3.2.3.23 CODECAPI\_AVEncEnableVideoProcessing

C.3.2.3.24 CODECAPI\_AVEncVideoGradualIntraRefresh

C.3.2.4 可选属性说明

如果 H.265 编码器实现长术语参考框架，则应该 （在一帧延迟完成） 实现下面的 CodecAPI 接口︰

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

如果 H.265 编码器实现长术语参考帧，则必须支持 LongTermReferenceFrameInfo 的 IMFSample 属性。

**C.4 MF 媒体类型特性要求**

支持以下的 MF 介质类型属性是必需的︰

C.4.1 [MF\_MT\_交错\_模式](http://msdn.microsoft.com/library/ms694868.aspx)

C.4.2 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

C.4.3 [MF\_MT\_子类型](http://msdn.microsoft.com/library/ms700208.aspx)

C.4.4 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

C.4.5 [MF\_MT\_框架\_速率](http://msdn.microsoft.com/library/ms700140.aspx)

C.4.6 [MF\_MT\_框架\_大小](http://msdn.microsoft.com/en-us/library/ms701619.aspx)

C.4.7 [MF\_MT\_平均\_比特率](http://msdn.microsoft.com/library/ms703792.aspx)

C.4.8 [MF\_MT\_MPEG2\_配置文件](http://msdn.microsoft.com/library/ms700193.aspx) *(MF\_MT\_视频\_配置文件)*

C.4.9 [MF\_MT\_MPEG2\_级](http://msdn.microsoft.com/library/ms700203.aspx) *(MF\_MT\_视频\_级别)*

C.4.10 [MF\_MT\_像素\_纵横\_比](http://msdn.microsoft.com/library/ms704767.aspx)

C.4.11 [MF\_MT\_视频\_额定\_范围](http://msdn.microsoft.com/en-us/library/ms699008.aspx)

C.4.12 [MF\_MT\_视频\_原色](http://msdn.microsoft.com/en-us/library/ms697241.aspx)

C.4.13 [MF\_MT\_传输\_函数](http://msdn.microsoft.com/en-us/library/ms703086.aspx)

C.4.14 [MF\_MT\_YUV\_矩阵](http://msdn.microsoft.com/en-us/library/ms702203.aspx)

C.4.15 [MF\_MT\_视频\_色度\_SITING](http://msdn.microsoft.com/en-us/library/ms694178.aspx)

C.4.16 [MF\_NALU\_长度\_设置](http://msdn.microsoft.com/en-us/library/hh870258.aspx)

**C.5 MF 样本特性支持需求**

C.5.1 所需的属性示例

根据是否设置了 ICodecAPI 或 MF 的媒体类型特性，以下示例属性必须有输入或输出的示例︰

C.5.1.1 MFSampleExtension\_MeanAbsoluteDifference

MFSampleExtension\_MeanAbsoluteDifference 示例属性需要输出样本，如果 CODECAPI\_AVEncVideoMeanAbsoluteDifference 属性已设置为非零值。 请注意，由于 CODECAPI\_AVEncVideoMeanAbsoluteDifference 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoMeanAbsoluteDifference 支持。

C5.1.2 MFSampleExtension\_LongTermReferenceFrameInfo

MFSampleExtension\_LongTermReferenceFrameInfo 示例属性需要输出样本，如果 CODECAPI\_AVEncVideoLTRBufferControl 表明可能存在一个或多个长期的参考框架。 请注意，由于 CODECAPI\_AVEncVideoLTRBufferControl 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoLTRBufferControl 支持。

MF C5.1.3\_NALU\_长度\_信息

MF\_NALU\_长度\_如果都需要输出样本信息示例属性 MF\_NALU\_长度\_设置媒体类型属性已设置为非零值。

C.5.1.4 MFSampleExtension\_ROIRectangle

输入的示例可能包含 MFSampleExtension\_ROIRectangle 采样特性，如果 CODECAPI\_AVEncVideoROIEnabled 属性已设置为非零值。 请注意，由于 CODECAPI\_AVEncVideoROIEnabled 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoROIEnabled 支持。

C.5.2 示例可选属性

可能存在下面的输入的样本特性。 它是可选的编码器是否利用这些属性所包含的信息。

C.5.2.1 MFSampleExtension\_DirtyRects

MFSampleExtension\_DirtyRects 特性是 BLOB 类型具有以下结构︰

```
typedef struct \_DIRTYRECT\_INFO
{
UINT FrameNumber;
UINT NumDirtyRects;
RECT DirtyRects\[1\];
} DIRTYRECT\_INFO;
```

此属性旨在用于压缩屏幕内容，并可使该窗口管理器在屏幕帧传递信息已更新矩形。

C.5.2.2 MFSampleExtension\_MoveRegions

MFSampleExtension\_MoveRegions 特性是 BLOB 类型具有以下结构︰

```
typedef struct \_MOVE\_RECT
{
POINT SourcePoint;
RECT DestRect;
} MOVE\_RECT;

typedef struct \_MOVEREGION\_INFO
{
UINT FrameNumber;
UINT NumMoveRegions;
MOVE\_RECT MoveRegions\[1\];
} MOVEREGION\_INFO;
```

**C.6 MFT 特性**

编码器需要支持[IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx)将返回的[IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx)接口，它允许访问与 MFT 的特性。 支持用于处理以下的 MFT MF 属性是必需的︰

A.6.1 [MFT\_枚举\_硬件\_URL\_属性](http://msdn.microsoft.com/library/dd388664.aspx)

C.6.2 [MFT\_枚举\_硬件\_供应商\_ID\_属性](http://msdn.microsoft.com/en-us/library/windows/desktop/hh162798.aspx)

C.6.3 [MFT\_编码器\_支持\_配置\_事件](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302174.aspx)

C.6.4 [MF\_视频\_最大\_MB\_PER\_秒](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302206.aspx)

C.6.5 MFT\_GFX\_驱动程序\_版本\_ID\_特性

C.6.6 MFT\_编码器\_错误

**C.7 功能支持需求**

H.265 编码器必须支持以下功能︰

C.7.1 峰值约束 VBR ratecontrol 模式

编码器将使用的值的 CODECAPI\_AVEncCommonMeanBitRate、 CODECAPI\_AVEncCommonMaxBitRate 和 CODECAPI\_AVEncCommonBufferSize 属性，以确保理论的缓冲区不会违反了在峰值比特率 (CODECAPI\_AVEncCommonMaxBitRate) 同时汇聚成 CODECAPI 的比特率\_AVEncCommonMeanBitRate 整个视频剪辑。

C.7.2 基于质量的 VBR ratecontrol 模式

编码器将使用的值 CODECAPI\_AVEncCommonQuality 或 CODECAPI\_AVEncVideoEncodeQP 以获得恒定的压缩视频的质量。 编码器将为所有框架使用常量 QP。

C.7.3 CBR ratecontrol 模式

编码器将使用的值的 CODECAPI\_AVEncCommonMeanBitRate 或 MF\_MT\_平均\_比特率和 CODECAPI\_AVEncCommonBufferSize 属性，以确保理论的缓冲区不会违反了在指定的比特率 (CODECAPI\_AVEncCommonMeanBitRate 或 MF\_MT\_平均\_比特率)。

C.7.4 GOP 的距离

编码器将 CODECAPI 的值所指定的帧间隔生成关键帧\_AVEncMPVGOPSize 属性。 此属性的值为 IntMAX 表示只有第一个框架应为关键帧。

C.7.5 基于帧的 QP 控件

必须支持在小 QP 介于 20 到 40 个。 设置一个无效值 (例如，52) 时，则必须返回一个错误。

C.7.6 强制关键帧控件

IDR 的前面必须加上 SP/放映 时的瞬时层数&gt;1，关键帧必须插入下一步的基本临时层框架中为保留的临时结构。 为单个图层 bitstream，必须在下一帧中插入关键帧。

C.7.7 质量与速度控制

C.7.8 低延迟控制

编码器必须支持的功能设为低滞后时间模式。 在此模式下，编码器不应缓冲任何输入的示例。 它必须是可产生输出示例中为每个输入的示例。

编码器还必须强制 POC 类型 2 或设置 VUI bitstream\_限制标志为 TRUE 并且 VUI num\_重新排序\_框架为 0。

C.7.8 临时层支持

需要编码器支持分层 P 帧编码，能产生 bitreams 的 1、 2 或 3 的按时间顺序无关层。

C.7.9 长期参考框架支持

如果 H.265 编码器实现长术语参考框架，则应该 （在一帧延迟完成） 实现下面的 CodecAPI 接口︰

CODECAPI\_AVEncVideoLTRBufferControl

CODECAPI\_AVEncVideoMarkLTRFrame

CODECAPI\_AVEncVideoUseLTRFrame

**C.8 MFT 异步支持**

建议您执行[异步 MFT](http://msdn.microsoft.com/library/dd317909.aspx)。 异步的 MFT 要求实现[IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx) [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx)接口。

**C.9 IMFRealTimeClientEx**

IMFRealTimeCLientEx::SetWorkQueue 通过 MMC 使用注册很重要，以满足性能目标;因此，建议[IMFRealTimeClientEx](http://msdn.microsoft.com/en-us/library/windows/desktop/hh448047.aspx)接口的实现。

**C.9 多实例要求**

它是必需的 H.265 编码器必须支持最少的 3 个并发实例。 编码器不应置于任何限制的实例数。 它应受的内存使用情况。

这种情况可能会在同一进程中或在不同的进程。

**C.10 业绩验证**

它是必需的 H.265 编码器支持受信任的值得验证过程。

它是必需的 H.265 编码器分别进行独立的二进制文件，认证和签名。

**C.11 附加要求**

H.265 编码器必须使用[Windows MP4 文件接收器](http://msdn.microsoft.com/library/dd757763.aspx)。

H.265 编码器必须实现编码配置的正确顺序。

必须能够产生瞬时的最多 3 层有效 bitstreams H.265 编码器。

您的 H.265 编码器前缀 NALU 前面添加每个扇区，与 1-3 瞬时层 bitstreams 与正确的语法。

H.265 编码器必须发送一个批的 GPU 请求每个框架。

H.265 编码器必须插入每个帧前 AUD NALU。

H.265 编码器必须在会话 0 中正常工作。

**C.12 安装**

它是必需的 H.265 编码器注册和未注册的以及在编码器中使用的设备驱动程序。

**C.113 动态格式更改**

它是必需的 H.265 编码器支持动态格式的更改，在下列情况︰

更改配置文件

分辨率和帧速率变化

添加和删除临时的图层

最大允许参考帧数

当多个更改请求在产生的输出帧前时，应遵守上一次更改。

**D.VP9/VP8 编码**

如果您的硬件支持 VP9/VP8 编码，您必须︰

**D.1 输入的格式支持**

编码器必须支持 NV12 格式输入帧数。 （可选） 编码器可以支持 IYUV 和 YUY2 格式。

编码器必须实现支持[IMFMediaBuffer](http://msdn.microsoft.com/library/ms696261.aspx)， [IMF2DBuffer](http://msdn.microsoft.com/en-us/library/ms699894.aspx)，和[IMF2DBuffer2](http://msdn.microsoft.com/en-us/library/hh447827.aspx)媒体缓冲区接口。

**D.2 配置文件支持**

编码器必须能够创建到 Profile0 的一致的输出内容。

编码器必须能够生成适当的头语法元素，以信号编码为 Profile0。

**D.3 接口支持需求**

VP9/VP8 编码器必须支持以下接口︰

D.3.1 [IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)

下面的[IMFTransform](http://msdn.microsoft.com/library/ms696260.aspx)接口方法的实现是必需的︰

D.3.1.1 [IMFTransform::ProcessEvent::GetAttributes](http://msdn.microsoft.com/en-us/library/ms703141.aspx)

D.3.1.2 [IMFTransform::GetInputAvailableType](http://msdn.microsoft.com/en-us/library/ms704814.aspx)

D.3.1.3 [IMFTransform::GetInputCurrentType](http://msdn.microsoft.com/en-us/library/ms705607.aspx)

D.3.1.4 [IMFTransform::GetInputStatus](http://msdn.microsoft.com/en-us/library/ms697478.aspx)

D.3.1.5 [IMFTransform::GetInputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703894.aspx)

D.3.1.6 [IMFTransform::GetOutputAvailableType](http://msdn.microsoft.com/en-us/library/ms703812.aspx)

D.3.1.7 [IMFTransform::GetOutputCurrentType](http://msdn.microsoft.com/en-us/library/ms696985.aspx)

D.3.1.8 [IMFTransform::GetOutputStatus](http://msdn.microsoft.com/en-us/library/ms696269.aspx)

D.3.1.9 [IMFTransform::GetOutputStreamInfo](http://msdn.microsoft.com/en-us/library/ms703886.aspx)

D.3.1.10 [IMFTransform::GetStreamCount](http://msdn.microsoft.com/en-us/library/ms697018.aspx)

D.3.1.11 [IMFTransform::GetStreamLimits](http://msdn.microsoft.com/en-us/library/ms697040.aspx)

D.3.1.12 [IMFTransform::ProcessEvent](http://msdn.microsoft.com/en-us/library/ms695394.aspx)

必须处理 MEEncodingParameters 事件︰

D.3.1.13 [IMFTransform::ProcessMessage](http://msdn.microsoft.com/en-us/library/ms701863.aspx)

D.3.1.14 [IMFTransform::ProcessInput](http://msdn.microsoft.com/en-us/library/ms703131.aspx)

D.3.1.15 [IMFTransform::ProcessOutput](http://msdn.microsoft.com/en-us/library/ms704014.aspx)

D.3.1.16 [IMFTransform::SetInputType](http://msdn.microsoft.com/en-us/library/ms700113.aspx)

D.3.1.17 [IMFTransform::SetOutputType](http://msdn.microsoft.com/en-us/library/ms702016.aspx)

D.3.1.18 [IMFTransform::SetOutputBounds](http://msdn.microsoft.com/en-us/library/ms693812.aspx)

D.3.2 [ICodecAPI](http://msdn.microsoft.com/library/dd311953.aspx)

编码器必须支持某些方法和属性的 ICodecAPI 接口的 Guid。

A.3.2.1 所需的方法

下面的 ICodecAPI 接口方法的实现是必需的︰

D.3.2.1.1 [IsSupported](http://msdn.microsoft.com/library/dd311960.aspx)

D.3.2.1.2 [GetValue](http://msdn.microsoft.com/library/dd311958.aspx)

D.3.2.1.3 [SetValue](http://msdn.microsoft.com/library/dd311966.aspx)

D.3.2.1.4 [GetParameterRange](http://msdn.microsoft.com/en-us/library/dd311956.aspx)

D.3.2.1.5 [GetParameterValues](http://msdn.microsoft.com/en-us/library/dd311957.aspx)

D.3.2.2 所需属性

对下面的 ICodecAPI 属性的 Guid 的支持是必需的︰

D.3.2.2.1 CODECAPI\_AVEncCommonRateControlMode

D.3.2.2.2 CODECAPI\_AVEncCommonQuality

D.3.2.2.3 CODECAPI\_AVEncCommonMeanBitRate

D.3.2.2.4 CODECAPI\_AVEncCommonMaxBitRate

D.3.2.2.5 CODECAPI\_AVEncCommonBufferSize

D.3.2.2.6 CODECAPI\_AVEncMPVGOPSize

D.3.2.2.8 CODECAPI\_AVLowLatencyMode

D.3.2.2.10 CODECAPI\_AVEncVideoForceKeyFrame

D.3.2.2.11 CODECAPI\_AVEncVideoEncodeQP

D.3.2.3 的可选属性

对下面的 ICodecAPI 属性的 Guid 的支持是可选的。

D.3.2.3.1 CODECAPI\_AVEncCommonQualityVsSpeed

**D.4 MF 媒体类型特性要求**

支持以下的 MF 介质类型属性是必需的︰

D.4.1 [MF\_MT\_交错\_模式](http://msdn.microsoft.com/library/ms694868.aspx)

D.4.2 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

D.4.3 [MF\_MT\_子类型](http://msdn.microsoft.com/library/ms700208.aspx)

D.4.4 [MF\_MT\_最小\_显示\_口径](http://msdn.microsoft.com/library/ms700173.aspx)

D.4.5 [MF\_MT\_框架\_速率](http://msdn.microsoft.com/library/ms700140.aspx)

D.4.6 [MF\_MT\_框架\_大小](http://msdn.microsoft.com/en-us/library/ms701619.aspx)

D.4.7 [MF\_MT\_平均\_比特率](http://msdn.microsoft.com/library/ms703792.aspx)

D.4.8 [MF\_MT\_MPEG2\_配置文件](http://msdn.microsoft.com/library/ms700193.aspx) *(MF\_MT\_视频\_配置文件)*

D.4.9 [MF\_MT\_MPEG2\_级](http://msdn.microsoft.com/library/ms700203.aspx) *(MF\_MT\_视频\_级别)*

D.4.10 [MF\_MT\_像素\_纵横\_比](http://msdn.microsoft.com/library/ms704767.aspx)

D.4.11 [MF\_MT\_视频\_额定\_范围](http://msdn.microsoft.com/en-us/library/ms699008.aspx)

D.4.12 [MF\_MT\_视频\_原色](http://msdn.microsoft.com/en-us/library/ms697241.aspx)

D.4.13 [MF\_MT\_传输\_函数](http://msdn.microsoft.com/en-us/library/ms703086.aspx)

D.4.14 [MF\_MT\_YUV\_矩阵](http://msdn.microsoft.com/en-us/library/ms702203.aspx)

D.4.15 [MF\_MT\_视频\_色度\_SITING](http://msdn.microsoft.com/en-us/library/ms694178.aspx)

**D.5 MF 样本特性支持需求**

D.5.1 所需的属性示例

根据是否设置了 ICodecAPI 或 MF 的媒体类型特性，以下示例属性必须有输入或输出的示例︰

D.5.1.1 MFSampleExtension\_MeanAbsoluteDifference

MFSampleExtension\_MeanAbsoluteDifference 示例属性需要输出样本，如果 CODECAPI\_AVEncVideoMeanAbsoluteDifference 属性已设置为非零值。 请注意，由于 CODECAPI\_AVEncVideoMeanAbsoluteDifference 是一个可选属性，此属性仅对支持所需的这种情况在 CODECAPI\_AVEncVideoMeanAbsoluteDifference 支持。

D.5.2 示例可选属性

可能存在下面的输入的样本特性。 它是可选的编码器是否利用这些属性所包含的信息。

D.5.2.1 MFSampleExtension\_DirtyRects

MFSampleExtension\_DirtyRects 特性是 BLOB 类型具有以下结构︰

```
typedef struct \_DIRTYRECT\_INFO
{
UINT FrameNumber;
UINT NumDirtyRects;
RECT DirtyRects\[1\];
} DIRTYRECT\_INFO;
```

此属性旨在用于压缩屏幕内容，并可使该窗口管理器在屏幕帧传递信息已更新矩形。

D.5.2.2 MFSampleExtension\_MoveRegions

MFSampleExtension\_MoveRegions 特性是 BLOB 类型具有以下结构︰

```
typedef struct \_MOVE\_RECT
{
POINT SourcePoint;
RECT DestRect;
} MOVE\_RECT;

typedef struct \_MOVEREGION\_INFO
{
UINT FrameNumber;
UINT NumMoveRegions;
MOVE\_RECT MoveRegions\[1\];
} MOVEREGION\_INFO;
```

**D.6 MFT 特性**

编码器需要支持[IMFTransform::GetAttributes](http://msdn.microsoft.com/library/ms703141.aspx)将返回的[IMFAttributes](http://msdn.microsoft.com/library/ms704598.aspx)接口，它允许访问与 MFT 的特性。 支持用于处理以下的 MFT MF 属性是必需的︰

A.6.1 [MFT\_枚举\_硬件\_URL\_属性](http://msdn.microsoft.com/library/dd388664.aspx)

D.6.2 [MFT\_枚举\_硬件\_供应商\_ID\_属性](http://msdn.microsoft.com/en-us/library/windows/desktop/hh162798.aspx)

D.6.3 [MFT\_编码器\_支持\_配置\_事件](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302174.aspx)

D.6.4 [MF\_视频\_最大\_MB\_PER\_秒](http://msdn.microsoft.com/en-us/library/windows/desktop/dn302206.aspx)

D.6.5 MFT\_GFX\_驱动程序\_版本\_ID\_特性

D.6.6 MFT\_编码器\_错误

**D.7 功能支持需求**

VP9/VP8 编码器必须支持以下功能︰

D.7.1 峰值约束 VBR ratecontrol 模式

编码器将使用的值的 CODECAPI\_AVEncCommonMeanBitRate、 CODECAPI\_AVEncCommonMaxBitRate 和 CODECAPI\_AVEncCommonBufferSize 属性，以确保理论的缓冲区不会违反了在峰值比特率 (CODECAPI\_AVEncCommonMaxBitRate) 同时汇聚成 CODECAPI 的比特率\_AVEncCommonMeanBitRate 整个视频剪辑。

D.7.2 基于质量的 VBR ratecontrol 模式

编码器将使用的值 CODECAPI\_AVEncCommonQuality 或 CODECAPI\_AVEncVideoEncodeQP 以获得恒定的压缩视频的质量。 编码器将为所有框架使用常量 QP。

D.7.3 CBR ratecontrol 模式

编码器将使用的值的 CODECAPI\_AVEncCommonMeanBitRate 或 MF\_MT\_平均\_比特率和 CODECAPI\_AVEncCommonBufferSize 属性，以确保理论的缓冲区不会违反了在指定的比特率 (CODECAPI\_AVEncCommonMeanBitRate 或 MF\_MT\_平均\_比特率)。

D.7.4 GOP 的距离

编码器将 CODECAPI 的值所指定的帧间隔生成关键帧\_AVEncMPVGOPSize 属性。 此属性的值为 IntMAX 表示只有第一个框架应为关键帧。

D.7.5 基于帧的 QP 控件

必须支持在小 QP 介于 20 到 40 个。 设置一个无效值 (例如，52) 时，则必须返回一个错误。

D.7.6 强制关键帧控件

IDR 的前面必须加上 SP/放映 时的瞬时层数&gt;1，关键帧必须插入下一步的基本临时层框架中为保留的临时结构。 为单个图层 bitstream，必须在下一帧中插入关键帧。

D.7.7 质量与速度控制

D.7.8 低延迟控制

编码器必须支持的功能设为低滞后时间模式。 在此模式下，编码器不应缓冲任何输入的示例。 它必须是可产生输出示例中为每个输入的示例。

**D.8 MFT 异步支持**

建议您执行[异步 MFT](http://msdn.microsoft.com/library/dd317909.aspx)。 异步的 MFT 要求实现[IMFMediaEventGenerator](http://msdn.microsoft.com/library/ms701755.aspx) [IMFShutdown](http://msdn.microsoft.com/library/ms703054.aspx)接口。

**D.9 IMFRealTimeClientEx**

IMFRealTimeCLientEx::SetWorkQueue 通过 MMC 使用注册很重要，以满足性能目标;因此，建议[IMFRealTimeClientEx](http://msdn.microsoft.com/en-us/library/windows/desktop/hh448047.aspx)接口的实现。

**D.9 多实例要求**

它是必需的 VP9/VP8 编码器必须支持最少的 3 个并发实例。 编码器不应置于任何限制的实例数。 它应受的内存使用情况。

这种情况可能会在同一进程中或在不同的进程。

**D.10 业绩验证**

它是必需的 VP9/VP8 编码器支持受信任的值得验证过程。

它是必需的 VP9/VP8 编码器分别进行独立的二进制文件，认证和签名。

**D.11 附加要求**

VP9/VP8 编码器必须实现编码配置的正确顺序。

VP9/VP8 编码器必须发送一个批的 GPU 请求每个框架。

VP9/VP8 编码器必须在会话 0 中正常工作。

**D.12 安装**

需要注册和未注册的以及在编码器中使用的设备驱动程序 VP9/VP8 编码器。

**D.113 动态格式更改**

它是必需的 VP9/VP8 编码器支持动态格式的更改，在下列情况︰

更改配置文件

分辨率和帧速率变化

当多个更改请求在产生的输出帧前时，应遵守上一次更改。
