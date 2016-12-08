---
title: Device.Input.Keyboard
Description: "徽标要求详细说明重要的 Microsoft 操作系统的键盘的实现细节。"
ms.assetid: 
MSHAttr: 
author: beneluxboy
ms.openlocfilehash: 559c7879ef863dd83b80d50a57229db3d7ff1d26
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
<!--
# Device.Input.Keyboard

 - [Device.Input.Keyboard](#device.input.keyboard)
-->

<a name="device.input.keyboard"></a>
##Device.Input.Keyboard

*徽标要求详细说明重要的 Microsoft 操作系统的键盘的实现细节。*

### <a name="deviceinputkeyboardbrowsermultimediakeysusemsapis"></a>Device.Input.Keyboard.BrowserMultimediaKeysUseMSApis

*互联网浏览器和多媒体键必须使用 Microsoft 的 Api。*

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

如果键盘或外设实现多媒体或 Internet 浏览器键，它必须使用注册表项与 WM\_APPCOMMAND API 来访问这些功能，Windows 驱动程序工具包中所述。 注册表项可以进行编程，通过使用 INF 文件安装为默认值的特殊项目或通过自定义界面提供给用户。

*设计备注*

请参阅 Microsoft 平台 SDK"WM\_APPCOMMAND。"

### <a name="deviceinputkeyboardcharmskey"></a>Device.Input.Keyboard.CharmsKey

*如果任一 Windows 的魅力键在键盘上实现，，它必须实现正确的扫描代码和相应的 glypths。*

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

实现按钮来启动任何 Windows 魅力的键盘必须在这些按钮上使用正确的扫描代码和标志符号。 转到按钮的标志符号中对可用在[硬件的 Windows 徽标许可协议的补充说明 Windows 标志符号定义*http://go.microsoft.com/fwlink/?LinkId=279574。*](http://go.microsoft.com/fwlink/?LinkId=279574.)

超级按钮按钮必须发送到超级按钮相对应的正确扫描代码。 没有其他标志符号可用的按钮上时使用的扫描代码与调用 Windows 8 的魅力之一。

### <a name="deviceinputkeyboarddynamickeyboards"></a>Device.Input.Keyboard.DynamicKeyboards

*动态的键盘必须满足下面列出的要求。*

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

-   系统显示安全桌面上，能够改变以反映不同的字形键帽键盘或图例动态必须出示时以匹配当前的用户语言的键盘布局在系统上有活动。

-   当使用能够改变键帽键盘来动态地反映不同的字形或图例，键盘必须重新启动到默认的系统语言布局作为选在控制面板-&gt;区域和语言选项-&gt;键盘和语言。

-   当使用能够改变键帽键盘以动态地反映不同的字形或图例，必须更改键盘，键盘布局，用户可以在登录屏幕中选定的语言。

-   当使用能够改变键帽键盘来动态地反映不同的字形或图例，键盘必须反映当前所选的布局和语言首选项，Windows 桌面具有焦点时。

-   当使用能够改变键帽键盘来动态地反映不同的字形或图例，使得键盘重新定位的 Windows 键;但是，该密钥必须保持所有的配置布局中的用户看到。 默认情况下，此密钥必须之间的控制和可选键时在登录、 欢迎或密码的输入屏幕键盘的左下角。 一旦用户已经登录，可能会使用用户首选项将密钥的位置重新定位。

-   当使用能够改变键帽键盘以动态地反映不同的字形或图例，所显示的键盘布局和语言必须匹配的操作系统安装的语言。

-   必须允许自备电源能够改变以反映不同的字形或图例动态，键帽键盘键盘重置通过交换机或击键序列，独立于软件重置或电源循环设备。

### <a name="deviceinputkeyboardhotkeyfunctionapi"></a>Device.Input.Keyboard.HotKeyFunctionAPI

*实现热键功能的设备必须实现相应的 API 通知。*

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

指向和绘图设备和键盘，实现按钮用作应用程序或功能的热键存在 WM\_APPCOMMAND API 应实现相应的 API 通知。 这包括但不限于以下函数︰

-   向上/向下卷

-   静音

-   浏览器后退/前进

-   播放/暂停

*设计备注*

在<http://msdn.microsoft.com/en-us/library/ms997498.aspx>找指点和绘图设备和键盘支持的最佳做法。
API 的 WM\_APPCOMMAND 通知可以在<http://msdn.microsoft.com/en-us/library/ms646275.aspx>上找到。
这些功能的 HID 的使用页和 ID 信息可以位于<http://www.microsoft.com/whdc/archive/scancode.mspx>和<http://www.usb.org/developers/hidpage>。
 

### <a name="deviceinputkeyboardkernelmodedriversusewdfkmdf"></a>Device.Input.Keyboard.KernelModeDriversUseWdfKmdf

*键盘的内核模式驱动程序必须使用 WDF KMDF。*

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

第三方键盘内核模式驱动程序必须将其带入 WDF KMDF 模型。

### <a name="deviceinputkeyboardlogoflagkey"></a>Device.Input.Keyboard.LogoFlagKey

*在所有支持 50 多个键的键盘上实现 Windows 符号键。Windows 符号设计后需要 12 月 31<sup>日</sup>，2013年。*

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

所有支持 50 多个键的键盘必须实现 Windows 符号键。 主要设计打印的 Windows 标志徽标版本可能徽标适用于移动计算系统和独立键盘的过渡日期之前。 Windows 标志商标必须清楚地区分主要根据*Microsoft Windows 徽标键徽标许可协议*和<http://go.microsoft.com/fwlink/?LinkId=116451>"键支持、 键盘扫描代码和窗口的"文档顶部。

### <a name="deviceinputkeyboardmultiplekeyboard"></a>Device.Input.Keyboard.MultipleKeyboard

*无干扰发生之间的多个键盘。*

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

如果系统中包含不止一种键盘，必须有任何冲突。 例如，固定的移动计算机可以有多个键盘连接到系统。 移动计算机和坞站上的键盘端口必须能够解决在移动计算机插接的两个端口之间的冲突。

### <a name="deviceinputkeyboardscancode"></a>Device.Input.Keyboard.ScanCode

*扫描代码必须符合行业标准。*

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

包括 Windows 徽标的任何键的键盘设计方案的要求如下︰

-   键盘必须开发根据技术要求，在"密钥支持、 键盘扫描代码和窗口"。

-   键盘在 Windows 虚拟键代码级别必须是兼容的。

-   Windows 徽标键必须作为一个修饰符 （CTRL、 班次或 ALT）。

-   键盘制造商必须使用者控件或特定供应商、 顶级集合用于 HID 热按钮。

*设计备注*

在<http://go.microsoft.com/fwlink/?LinkId=36767>中看到"关键支持、 键盘扫描代码和窗口"。
可以编写额外的软件或驱动程序提供软件重新映射功能。

