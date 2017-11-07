---
author: Justinha
Description: "DPI 相关 Api 和注册表设置"
ms.assetid: 23b0e272-a09e-4081-a129-d330b6878d8e
MSHAttr: PreferredLib:/library/windows/hardware
title: "DPI 相关 Api 和注册表设置"
ms.openlocfilehash: c1ec3558a4217cea24fea244fc44ba55557dad54
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dpi-related-apis-and-registry-settings"></a>DPI 相关 Api 和注册表设置


如果您需要执行部署自定义任务，以下部分介绍的注册表项和安装后脚本可能需要访问的系统参数。

**本主题︰**

-   [主显示器的原始分辨率](#native)

-   [主显示器 DPI 比例因子](#scale)

-   [缩放模式](#scalingmode)

-   [在 Windows 8.1 缩放模式下缩放重写](#override)

-   [系统范围内的比例因子缩放模式 Windows 8 中](#system)


## <a name="span-idnativespanspan-idnativespanprimary-display-native-resolution"></a><span id="native"></span><span id="NATIVE"></span>主显示器的原始分辨率


*表 1 Windows 8.1 缩放级别*，而不是详尽的提供有关信息 Windows 8.1 缩放级别的大量常见显示。 **面板 DPI**表示物理像素密度的面板，并**缩放级别**指示将用于该显示的缩放比例。

**表 1 8.1 窗口缩放级别**

<table>
<colgroup>
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
<col width="16%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">显示大小</th>
<th align="left">显示分辨率</th>
<th align="left">水平 （像素）</th>
<th align="left">垂直 （像素）</th>
<th align="left">面板 DPI</th>
<th align="left">缩放级别</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>10.6&quot;</p></td>
<td align="left"><p>FHD</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1080</p></td>
<td align="left"><p>208</p></td>
<td align="left"><p>150%</p></td>
</tr>
<tr class="even">
<td align="left"><p>10.6&quot;</p></td>
<td align="left"><p>高清晰度</p></td>
<td align="left"><p>1366</p></td>
<td align="left"><p>768</p></td>
<td align="left"><p>148</p></td>
<td align="left"><p>100%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>11.6&quot;</p></td>
<td align="left"><p>WUXGA</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1200</p></td>
<td align="left"><p>195</p></td>
<td align="left"><p>150%</p></td>
</tr>
<tr class="even">
<td align="left"><p>11.6&quot;</p></td>
<td align="left"><p>高清晰度</p></td>
<td align="left"><p>1366</p></td>
<td align="left"><p>768</p></td>
<td align="left"><p>135</p></td>
<td align="left"><p>100%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>13.3&quot;</p></td>
<td align="left"><p>WUXGA</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1200</p></td>
<td align="left"><p>170</p></td>
<td align="left"><p>150%</p></td>
</tr>
<tr class="even">
<td align="left"><p>13.3&quot;</p></td>
<td align="left"><p>QHD</p></td>
<td align="left"><p>2560</p></td>
<td align="left"><p>1440</p></td>
<td align="left"><p>221</p></td>
<td align="left"><p>200%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>13.3&quot;</p></td>
<td align="left"><p>高清晰度</p></td>
<td align="left"><p>1366</p></td>
<td align="left"><p>768</p></td>
<td align="left"><p>118</p></td>
<td align="left"><p>100%</p></td>
</tr>
<tr class="even">
<td align="left"><p>15.4&quot;</p></td>
<td align="left"><p>FHD</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1080</p></td>
<td align="left"><p>143</p></td>
<td align="left"><p>125%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>15.6&quot;</p></td>
<td align="left"><p>QHD +</p></td>
<td align="left"><p>3200</p></td>
<td align="left"><p>1800</p></td>
<td align="left"><p>235</p></td>
<td align="left"><p>200%</p></td>
</tr>
<tr class="even">
<td align="left"><p>17&quot;</p></td>
<td align="left"><p>FHD</p></td>
<td align="left"><p>1920</p></td>
<td align="left"><p>1080</p></td>
<td align="left"><p>130</p></td>
<td align="left"><p>125%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>23"</p></td>
<td align="left"><p>QFHD (4K)</p></td>
<td align="left"><p>3840</p></td>
<td align="left"><p>2160</p></td>
<td align="left"><p>192</p></td>
<td align="left"><p>200%</p></td>
</tr>
<tr class="even">
<td align="left"><p>24&quot;</p></td>
<td align="left"><p>QHD</p></td>
<td align="left"><p>2560</p></td>
<td align="left"><p>1440</p></td>
<td align="left"><p>122</p></td>
<td align="left"><p>125%</p></td>
</tr>
</tbody>
</table>

 

若要以编程方式查找此信息，以便任何设备，您可以编写报告返回的数据的实用程序。 本机主要的解决方法被通过调用 API 使用的[GetDeviceCaps() 函数](http://go.microsoft.com/fwlink/p/?linkid=331144)，hdc 的桌面和 HORZRES 和 VERZRES 索引︰

``` syntax
// Get desktop dc
desktopDc = GetDC(NULL);
// Get native resolution
horizontalResolution = GetDeviceCaps(desktopDc,HORZRES);
verticalResolution = GetDeviceCaps(desktopDc,VERZRES);
```

GetDC 有关的详细信息，请参阅[GetDC() 函数](http://go.microsoft.com/fwlink/p/?linkid=331145)。

## <a name="span-idscalespanspan-idscalespanprimary-display-dpi-scale-factor"></a><span id="scale"></span><span id="SCALE"></span>主显示器 DPI 比例因子


同样，可以使用 LOGPIXELSX 和 LOGPIXELSY 索引来获取像素密度︰

``` syntax
// Get desktop dc
desktopDc = GetDC(NULL);
// Get native resolution
horizontalDPI = GetDeviceCaps(desktopDc,LOGPIXELSX);
verticalDPI = GetDeviceCaps(desktopDc,LOGPIXELSY);
```

这些结果在一个坐标系中的 96 对应于 100%，如*表 2 DPI 比例因素*中所示。

**表 2 DPI 缩放比例**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">DPI</th>
<th align="left">缩放比例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>96</p></td>
<td align="left"><p>100</p></td>
</tr>
<tr class="even">
<td align="left"><p>120</p></td>
<td align="left"><p>125</p></td>
</tr>
<tr class="odd">
<td align="left"><p>144</p></td>
<td align="left"><p>150</p></td>
</tr>
<tr class="even">
<td align="left"><p>192</p></td>
<td align="left"><p>200</p></td>
</tr>
</tbody>
</table>

 

**请注意**  
此 API 将返回不同的结果，取决于您的应用程序的 DPI 识别模式。 配置的认知模式需要将 XML 添加到应用程序清单，如下所述︰

| DPI 识别模式 | 清单设置 | 返回的值 |
| ------------------ | ---------------- | -------------- |
| 无               | 无             |  对于所有显示的缩放比例无关的 96 |
| 系统识别 DPI      | \<dpiAware > 真\</dpiAware > | （当用户首次登录到 Windows） 启动 DPI 的主显示在 Windows 会话的时间 |
| 每个监视器识别 DPI | \<dpiAware > 真/PM\</dpiAware > | （当用户首次登录到 Windows） 启动 DPI 的主显示在 Windows 会话的时间。 若要获取显示该应用程序所在的 DPI，使用[GetWindowDpi()](https://msdn.microsoft.com/en-us/library/windows/desktop/mt748624.aspx)或[GetDpiForMonitor()](https://msdn.microsoft.com/en-us/library/windows/desktop/dn280510.aspx) |


有关此清单设置的详细信息，请参阅[SetProcessDPIAware 函数](http://go.microsoft.com/fwlink/p/?linkid=331146)。

## <a name="span-idscalingmodespanspan-idscalingmodespanscaling-mode"></a><span id="scalingmode"></span><span id="SCALINGMODE"></span>缩放模式


**控件面板\\外观和个性化\\显示**用户界面 (UI) 包括一个复选框︰**让我来选择一个缩放级别为所有的显示器**，用于控制是否系统适用于 （如在 Windows 8 和更早版本的 Windows） 的所有显示的单个的缩放比例或不同比例的因素，考虑到每个显示屏 （Windows 8.1 默认值） 的像素密度。 此复选框配置**HKCU\\控制面板\\桌面\\Win8DpiScaling** Windows 8.1 中的注册表项。

**表 3 HKCU\\控制面板\\桌面\\Win8DpiScaling 值**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">键值</th>
<th align="left">含义</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0</p></td>
<td align="left"><p>为每个显示不同的缩放比例︰ Windows 8.1 默认。移至另一个显示的内容将是适当的大小，但可以是位图缩放。</p></td>
</tr>
<tr class="even">
<td align="left"><p>1</p></td>
<td align="left"><p>相同的缩放比例将应用于所有显示︰ Windows 8 和更早的 Windows 版本行为。 移至另一个显示的内容可能会错误的尺寸。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idoverridespanspan-idoverridespanscaling-override-in-windows-81-scaling-mode"></a><span id="override"></span><span id="OVERRIDE"></span>在 Windows 8.1 缩放模式下缩放重写


如果**让我选择一个缩放级别为所有的显示器**复选框被清除，系统正在运行 Windows 8.1 缩放模式中，用户提供了一个滑块，以便重写当前缩放因子，从较小，为中为较大。 在此设置配置**HKCU\\控制面板\\桌面\\DesktopDPIOverride**注册表项。

**表 4 HKCU\\控制面板\\桌面\\DesktopDPIOverride 值**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">键值</th>
<th align="left">含义</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>&lt;0</p></td>
<td align="left"><p>通过此值从默认值减少每个显示的缩放比例 (例如，如果默认缩放比例的 150%，-1 对应于 125%到 100%-2)。</p></td>
</tr>
<tr class="even">
<td align="left"><p>0</p></td>
<td align="left"><p>为每个显示中使用的默认值。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0&gt;</p></td>
<td align="left"><p>每个显示系数增大此值 （使用缩放 200%与前面的示例中，+ 1）。</p></td>
</tr>
</tbody>
</table>

 

在此模式下的所有显示缩放比例被都限制为四个值之一︰ 100%、 125%、 150%、 200%。 此外，应用缩放后，应用程序会有至少 720 行有效分辨率 （即物理的垂直分辨率显示除以比例因子）;这可以进一步限制允许的显示缩放比例的范围。 *表 5 显示值*显示哪些值允许为不同尺寸的显示︰

**表 5 显示值**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">垂直线条</th>
<th align="left">支持的缩放比例</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>&lt;900</p></td>
<td align="left"><p>100%</p></td>
</tr>
<tr class="even">
<td align="left"><p>&gt;= 900 和&lt;1080年</p></td>
<td align="left"><p>100%、 125%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>&gt;= 1080年和&lt;1440年</p></td>
<td align="left"><p>100%、 125%、 150%</p></td>
</tr>
<tr class="even">
<td align="left"><p>&gt;= 1440</p></td>
<td align="left"><p>100%、 125%、 150%、 200%</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsystemspanspan-idsystemspansystem-wide-scale-factor-in-windows-8-scaling-mode"></a><span id="system"></span><span id="SYSTEM"></span>系统范围内的比例因子缩放模式 Windows 8 中


如果**让我选择一个缩放级别我所有显示的**复选框，用户可以指定适用于所有的显示，而不考虑每个显示屏的像素密度的比例因子。 通过使用自定义设置，用户可以选择以外的值 100%、 125%、 150%、 200%，尽管它们只限于使用范围 （100%-500%)。 在此设置配置**HKCU\\ControlPanel\\桌面\\LogPixels**注册表项。

**表 6 HKCU\\ControlPanel\\桌面\\LogPixels 值**

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">键值</th>
<th align="left">含义</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>96</p></td>
<td align="left"><p>在每个显示器上缩放 100%</p></td>
</tr>
<tr class="even">
<td align="left"><p>120</p></td>
<td align="left"><p>在每个显示器上扩展的 125%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>144</p></td>
<td align="left"><p>在每个显示器上扩展的 150%</p></td>
</tr>
<tr class="even">
<td align="left"><p>192</p></td>
<td align="left"><p>在每个显示器上缩放 200%</p></td>
</tr>
<tr class="odd">
<td align="left"><p>&lt;其他&gt;</p></td>
<td align="left"><p>&lt;其他&gt;* 100/96 缩放每个显示屏上</p></td>
</tr>
</tbody>
</table>

 
## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题

[开发高 DPI 的应用程序的文档](https://msdn.microsoft.com/library/windows/desktop/dd464646.aspx)

[面向 IT 专业人员的高 DPI 支持](high-dpi-support-for-it-professionals.md)

 

 






