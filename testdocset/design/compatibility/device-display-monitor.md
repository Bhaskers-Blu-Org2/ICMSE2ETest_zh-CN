---
title: Device.Display.Monitor
Description: "对于显示的要求旨在确保改善最终用户体验。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 7f97d30e15d7cfd1c7d9a522a9c3a850e2be2f1d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Display.Monitor

 - [Device.Display.Monitor](#device.display.monitor)
-->

<a name="device.display.monitor"></a>
##Device.Display.Monitor

### <a name="devicedisplaymonitorbase"></a>Device.Display.Monitor.Base

*显示基本要求必须确保良好的用户体验。*

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

显示器上的所有连接器必须被默认都设置为一种模式，不会应用 CE 样式自定大小或 underscan。 它是监视程序提供一个选项，允许用户配置自定大小/underscan 使用上的屏幕显示确定。

HDMI 接口，提供的所有视频显示必须支持宋标志，HDMI 规范中定义。

数字显示的所有所需有一个从低到高设备上连接和加电 HPD 信号转换。 不允许定期切换的 HPD 信号连接或电源后向上。 

多个转换的潜在顾客来源通知操作系统的多个设备到达和删除事件。导致出现令人不快的模式设置闪烁。

### <a name="devicedisplaymonitordigitallinkprotection"></a>Device.Display.Monitor.DigitalLinkProtection

*支持数字输入的显示器必须支持所有的数字输入数字链接的保护。*

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

显示数字的输入，如数字视频接口 (DVI)、 高清晰度多媒体接口 (HDMI)，DisplayPort，等等... 必须支持数字显示器链路保护机制如高带宽数字内容保护 (HDCP)。

### <a name="devicedisplaymonitoredid"></a>Device.Display.Monitor.EDID

*显示设备必须实现的 EDID 数据结构。*

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

显示器的 EDID 结构，其中包含所有必填的字段，如 VESA 增强扩展显示标识数据标准 (E EDID)，发行的第 3 部分中定义必须传输。 此 EDID 还必须包含唯一的制造商名称、 产品代码 ID 和序列号。 （序列号不需要在手机上的集成的面板或在一个系统中所有。）

对于模拟老式，EDID 内容必须表明至少一个 VESA 模式以 75hz 或更高的每个受支持的分辨率。

所有监视器都必须都支持 E EDID 通过实施 EDID 1.3 或更高版本的数据结构︰

-   在计时包括首选的显示模式的计时数据\#1。

<!-- -->

-   对于液晶屏或其他固定格式显示，此显示模式是面板的本机、 渐进式扫描模式。

-   对于其他显示类型，这是设备的最佳的、 渐进式扫描显示模式所根据的大小和功能，并且必须满足上面定义的刷新率的要求。

<!-- -->

-   实现屏幕大小或纵横比字段，每个受支持的 EDID 版本，具有准确尺寸 0x15 和 0x16 字节。

-   设置字节 0x18，位 1，以指示每个受支持的 EDID 版本的首选的模式意义。

-   在 ID 的序列号字段或显示产品序列号字符串的基本块 18 字节说明符之一的至少一个包含一个唯一的序列号。

-   实现一个基本块 18 字节描述符，可选集成面板中显示产品名称字符串。 此字符串必须适合于用户界面的使用。

-   显示的范围限制在一个基实现阻止 18 个字节的说明符，除非该设备是一个非连续的频率 （多模式） 显示。

移动设备和其他多功能一体系统必须传输 EDID 结构三种方法之一︰

-   液晶显示面板提供了一个，这是类似于外接显示器。

-   如果液晶屏不提供一个，则负责定义和向操作系统 WDDM 微型端口。

-   WDDM 驱动程序可能会执行 ACPI \_DDC 方法与检索系统 BIOS 中的 EDID 内部面板关联的子设备。

为了确保这些功能都可以表示为操作系统和应用程序，实现超过 8 位，每种主要颜色的功能的显示设备必须使用 EDID 1.4。

*设计备注*

ACPI 规范中定义的方法来获取 BIOS 实现等效的功能中 ACPI 2.0b，附录 B 中规定从 EDID 或更高版本。

### <a name="devicedisplaymonitormodes"></a>Device.Display.Monitor.Modes

*对显示设备的分辨率支持要求*

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

显示设备可以有多个连接器。 下面是所需的模式显示必须支持每个连接器上并指示通过 EDID （显示的是可用以支持其他模式和 EDID 也出调用它们） 的支持。

注意︰ Windows 10 中没有最低刷新率是必需的。 对于本机的显示分辨率，推荐的最小值为 60 Hz 渐进式或适用于该区域最近的频率。 较低的刷新率可能会导致较差的用户体验。

**集成面板︰**面板的本机分辨率必须大于或等于 1024 x 768。
 
**HD15、 DVI、 HDMI 和 DisplayPort 连接器︰**

面板的本机分辨率必须大于或等于 1024 x 768。

必须支持显示和 EDID 中已建立计时中包括下列模式︰

-   640 x 480，60hz 渐进式 （字节 23 小时，而在已建立计时位 5）

-   800 x 600 处 60 Hz 连续 （字节 23 小时，已建立计时中的位 0）

-   1024 x 768 @ 60 Hz 连续 （字节 24h，位在已建立计时 3）

这些模式可以支持全屏或居中。

**S 视频、 组件和复合像所有其他连接器的︰**连接器必须支持最大允许的模式，标准的规范中定义。

### <a name="devicedisplaymonitorstereoscopic3dmodes"></a>Device.Display.Monitor.Stereoscopic3DModes

*外部的立体 3D 显示或内部移动面板必须支持立体声模式等效为本机或首选的分辨率。*

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

立体 3D 显示本机或首选分辨率必须具有等效的立体声模式。 通过其 EDID 公开本机或首选的显示分辨率。

示例︰ 如果立体 3D 显示器的原始分辨率为 1920 x 1200 的单声道，然后它还必须支持相同的本机分辨率立体模式。

