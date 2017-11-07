---
title: Device.Streaming.Camera
Description: "要求。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: cda409d9cac1228cf658f3aca8906051708e8ea3
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="devicestreamingcamera"></a>Device.Streaming.Camera

 - [Device.Streaming.Camera.Base](#device.streaming.camera.base)
 - [Device.Streaming.Camera.Base.Sharing](#device.streaming.camera.base.sharing)
 - [Device.Streaming.Camera.UVC](#device.streaming.camera.uvc)

<a name="device.streaming.camera.base"></a>
## <a name="devicestreamingcamerabase"></a>Device.Streaming.Camera.Base

### <a name="devicestreamingcamerabaseavstreamclassinterfaceandwdm"></a>Device.Streaming.Camera.Base.AVStreamClassInterfaceAndWDM 

*相机实施必须基于 AVStream 类和 WDM，并且必须满足接口要求*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

相机实现必须基于 Windows 驱动程序模型 (WDM) 与 AVStream 类接口如 Windows 驱动程序工具包中所定义。 AVStream 是流类接口，不再受支持的替代技术。

照相机驱动程序必须支持所有必需的针脚、 属性和设置 Windows 驱动程序工具包中所规定。

*相机配置文件*（如果实现）*:*

该驱动程序可能公布的相机功能可保证能同时处理组合的配置文件。 WDK 中找不到照相机配置文件的详细信息。

*独立的针脚︰*

广告的摄像头驱动程序的所有针脚都必须能够独立地根据广告的设备配置文件中列出的功能组合。 如果该设备不支持配置文件，则并发流的针脚对于所有媒体类型的所有已公布功能应该支持。 如果将不能够同时传输照相机记录和图像针脚，则驱动程序必须明确公布这通过设置 KSPROPERTY\_CAMERACONTROL\_图像\_针\_功能\_独占\_WITH\_记录和 KSPROPERTY\_CAMERACONTROL\_图像\_针\_功能\_序列\_独占\_WITH\_驱动程序 INF 中的记录标志 (请参阅此处的这些标志有关的附加文档︰ https://msdn.microsoft.com/en-us/library/windows/hardware/jj553707.aspx。 必须支持所有其他针组合。

基于 USB 摄像头必须为 USB 视频类 (UVC) 符合**Device.Streaming.Camera.UVC.UVCDriver**和**Device.Streaming 中定义。Camera.UVC.USBClassDriver**。

**错误条件**

错误情况包括 （但不是限于） 强制 pin 无效连接，无效的属性设置，缓冲区无效数据、 空指针和错误条件与从上面或下面的驱动程序堆栈上

### <a name="devicestreamingcamerabasedirectshow"></a>Device.Streaming.Camera.Base.DirectShow

*RGB 相机实现必须支持 DirectShow。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
</td></tr></table>

**说明**

RGB 照相机必须与 Microsoft DirectShow 合作来支持遗留应用程序。

### <a name="devicestreamingcamerabasekscategoryvideocameraregistration"></a>Device.Streaming.Camera.Base.KSCategoryVideoCameraRegistration

*RGB 照相机必须注册下 KSCategory\_视频\_相机*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

RGB 照相机必须注册下 KSCategory\_视频\_相机为 Windows 检测相机

### <a name="devicestreamingcamerabasemediafoundation"></a>Device.Streaming.Camera.Base.MediaFoundation

*照相机的实现必须支持媒体基础体系结构。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

照相机必须使用 Microsoft 媒体基础以支持旧式 (Win32) 和 Windows 应用商店应用程序。

### <a name="devicestreamingcamerabasemultipleclientappsupport"></a>Device.Streaming.Camera.Base.MultipleClientAppSupport

*照相机的实现必须支持多个 KS 过滤器实例和独立流*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

*同一设备的多个筛选器范例︰*

每个摄像机必须允许创建多个筛选器实例。 设备可能只允许一个要主动流的筛选器实例。

### <a name="devicestreamingcamerabasenonrgbcameras"></a>Device.Streaming.Camera.Base.NonRGBCameras

*非 RGB 照相机必须注册下 KSCategory\_传感器\_相机*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

若要区分间 RGB 照相机和其他类型的传感器的功能，不是 RGB 视频流照相机的相机必须注册类别 KSCategory 下\_传感器\_相机

### <a name="devicestreamingcamerabasepnpandpowerpolicies"></a>Device.Streaming.Camera.Base.PnPandPowerPolicies 

*相机实现必须遵循 Microsoft PNP 和电源策略。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

照相机必须符合 Microsoft PNP 和配置待机电源策略以及连接的支持。

在下面的链接可以找到更多的信息︰

-   <http://go.microsoft.com/fwlink/?LinkID=733968>

### <a name="devicestreamingcamerabasesurpriseremoval"></a>Device.Streaming.Camera.Base.SurpriseRemoval

*可热插拔的照相机必须支持意外删除。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

所有的热插拔照相机必须支持他们在意外删除主机总线从。

### <a name="devicestreamingcamerabaseusageindicator"></a>Device.Streaming.Camera.Base.UsageIndicator

*照相机必须具有可视的指示器，指示使用情况*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

照相机必须表明流式传输时的可视指示器。 可视指示器必须设备数据流时打开和关闭时该设备不数据流。 如果有多个相机系统，但只有一个单一的指标上，标记上时必须有设备进行流式处理。

强烈建议硬件使用率指示灯 （物理）。 而不是一个物理的指示灯可能设置了以下注册密钥︰

<dl><dt>Path</dt><dd><p>HKLM\\软件\\Microsoft\\OEM\\设备\\捕获</p></dd><dt>项</dt><dd><p>NoPhysicalCameraLED (REG\_dword 值)。</p></dd><dt>0x1</dt><dd><p>打开 （= 无物理系统上的摄像头 led 灯） 的功能。</p></dd><dt>0x0</dt><dd><p>默认。 请关闭功能 （= 在系统上的物理摄像头 led 灯）</p></dd></dl>

设置完成后，操作系统将能够显示用户界面，表明如果相机的流处理。

<a name="device.streaming.camera.base.sharing"></a>
## <a name="devicestreamingcamerabasesharing"></a>Device.Streaming.Camera.Base.Sharing

### <a name="devicestreamingcamerabasesharingcustommediasource"></a>Device.Streaming.Camera.Base.Sharing.CustomMediaSource

*媒体基础体系结构和接口必须支持自定义的媒体源*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

照相机和充当照相机必须使用 Microsoft 媒体基础来支持 Windows 应用程序的扩展自定义的媒体源。 除了正常的 MediaSource 接口和属性，自定义的媒体源必须是可安装驱动程序包的一部分。

### <a name="devicestreamingcamerabasesharingdevicemft"></a>Device.Streaming.Camera.Base.Sharing.DeviceMFT

*共享相机的 DeviceMFT 和 MFT0 必须在进程外运行作为用户模式应用程序*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

支持共享经验、 设备驱动程序和用户不同于用户模式应用程序使用的 Api 的捕获进程用尽模式组件驱动程序 （DeviceMFT 或 MFT0） 相关联。 这意味着用户模式组件可以不依赖于与用户模式应用程序在进程中运行。 从应用程序或采取对 CaptureEngine 对象的引用的一些例子是 DeviceMFT 专用接口。

### <a name="devicestreamingcamerabasesharingfaceauthmode"></a>Device.Streaming.Camera.Base.Sharing.FaceAuthMode

*若要支持的方式支持面临身份验证 DDI，Windows Hello 附加要求，还必须满足*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

为公布面临身份验证由一种设备，其他 Windows Hello 必须满足要求。 其中包括最小分辨率和帧速率。 可爱的表面身份验证方案，请参见 Windows 硬件指南 (2.0 版或更高) 文档以获得详细信息。

### <a name="devicestreamingcamerabasesharingmemoryallocation"></a>Device.Streaming.Camera.Base.Sharing.MemoryAllocation

*驱动程序的内存分配必须页边界对齐到 4k （4096 字节）。*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

驱动程序的内存分配必须对齐 4k 页面边界。  它建议该驱动程序的用户模式组件使用 MF （媒体基础） 分配器。

### <a name="devicestreamingcamerabasesharingnonconsumabledata"></a>Device.Streaming.Camera.Base.Sharing.NonConsumableData

*必须隐藏流不能供用户使用*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
<p>Windows 10 Mobile x86</p>
<p>Windows 10 Mobile x64</p>
</td></tr></table>

**说明**

公开该驱动程序的所有流应该都可以使用应用程序的某些方面。 正在很好地理解流的数据类型不是必需的但是流应该能正常工作流的所有其他方面。 如果流中的数据不能由另一个组件或应用程序，这必须标记在针上，以便它将不显示在应用程序。

<a name="device.streaming.camera.uvc"></a>
## <a name="devicestreamingcamerauvc"></a>Device.Streaming.Camera.UVC

# # Device.Streaming.Camera.UVC.USBClassDriver 

*流式传输的 USB 摄像机必须符合 USB 视频类技术指标和使用 Microsoft UVC 驱动程序 (USBVideo.sys)*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
</td></tr></table>

**说明**

所有 USB 流视频照相机都必须符合 Microsoft USB 视频类驱动程序 (USBVideo.sys)。

### <a name="devicestreamingcamerauvcuvcdriver"></a>Device.Streaming.Camera.UVC.UVCDriver

*流式传输视频照相机的 USB 必须符合 USB 视频类规范*

<table>
<tr>
<th>适用于</th>
<td>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x86</p>
<p>（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 x64</p>
</td></tr></table>

**说明**

所有 USB 流视频相机，包括那些不自然地使用 Microsoft USB 视频类驱动程序 (USBVideo.sys)，必须都符合 USB 视频类规范。 至少，必须实现所有必需的属性和命令。 所有实施的命令必须符合技术指标。

*非 Microsoft 驱动程序 （如果实现）*

不要使用 Microsoft USB 视频类驱动程序的 USB 相机实现仍然必须符合 USBVideo.sys （每个**Device.Streaming.Camera.UVC.USBClassDriver**)

*本机 H264 支持 (如果实现*) *

如果照相机本身支持 H.264 格式，实现必须符合 USB 视频类规范。 请参考︰ <http://go.microsoft.com/fwlink/?LinkId=233063>。 此外，H.264 bitstream 必须符合媒体基础。

在最小的 2 针必须支持︰

1. 预览将锁定与压缩的输出类型相同的设备上，YUY2 和/或 NV12

2. H.264 格式必须是在一个单独的视频捕获 pin

