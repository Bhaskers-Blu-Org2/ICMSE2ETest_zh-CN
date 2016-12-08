---
title: "开始使用 Windows 10"
description: "构建创新的和有差异的设备与 Windows 10。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e9ebd4e2-f05e-40fb-9dc3-925f96dce182
ms.openlocfilehash: ba4410422bbba82efb8ef8fa428a7cee473b3f2e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="get-started-with-windows-10"></a>开始使用 Windows 10

构建创新的和有差异的设备与 Windows 10。 在更广泛的设备上运行的 Windows 10 — — 从台式机、 笔记本、 电话和互联网内容 (IoT) 设备。 操作系统的通用核心根本工作跨平台的 80 英寸屏幕、 4 英寸的屏幕或有任何屏幕的设备。

您可以创建使用触摸屏输入/笔、 鼠标/键盘、 控制器/笔势的设备 — — 也可以生成这些输入类型之间切换。

## <a name="start-here"></a>从这里开始

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong><em>我对这新 ！</em></strong></td>
<td><strong><em>我回来了！</em></strong></td>
</tr>
<tr class="even">
<td><p>了解不同的工具包用于生成 Windows 设备。</p>
<p>[熟悉的工具包和工具](kits-and-tools-overview.md)</p>
<p>下载每个这里的工具包︰</p>
<ul>
<li>[Windows 驱动程序工具包 (WDK) 10](https://go.microsoft.com/fwlink/p/?LinkId=733614)</li>
<li>[对于 Windows 10 的 Windows 硬件实验室工具包 (HLK)](https://go.microsoft.com/fwlink/p/?LinkId=733613)</li>
<li>[Windows 评估和部署工具包 (ADK) 窗口 10](https://go.microsoft.com/fwlink/p/?LinkId=733615)</li>
</ul></td>
<td><p>欢迎回来！ 以下是最新信息︰</p>
<ul>
<li>[...Windows 10](what-s-new-in-windows.md)</li>
<li>[...Windows ADK](what-s-new-in-kits-and-tools.md)</li>
<li>[...Windows 性能 Toolkit](https://msdn.microsoft.com/en-us/library/windows/hardware/dn927303(v=vs.85).aspx)</li>
<li>[...硬件实验室工具包](https://msdn.microsoft.com/library/windows/hardware/mt187880.aspx)</li>
<li>[...驱动程序开发](https://msdn.microsoft.com/windows/hardware/drivers/what-s-new-in-driver-development)</li>
<li>[...设计](https://msdn.microsoft.com/library/windows/hardware/mt703371.aspx)</li>
<li>[...自定义项](https://msdn.microsoft.com/library/windows/hardware/mt723363(v=vs.85).aspx)</li>
<li>[...制造](manufacture/whats-new-in-windows-manufacturing.md)</li>
<li>[...无人参与设置](https://msdn.microsoft.com/library/windows/hardware/mt750416.aspx)</li>
<li>[...MDM 注册和管理](https://msdn.microsoft.com/library/windows/hardware/mt299056.aspx)</li>
<li>[...Windows PE](manufacture/desktop/whats-new-in-windows-pe-s14.md)</li>
</ul></td>
</tr>
</tbody>
</table>

在开发过程的任何阶段，您可以优化 Windows 10 的硬件。 这些分步指南将指导您完成使用开发板，构建通用的 Windows 驱动程序的各种设备，并确保您的硬件组件、 外围设备和技术都与 Windows 10 兼容。

## <a name="design-hardware-with-the-latest-features"></a>最新的功能与设计硬件

从 Cortana 到核心体系结构的统一体，此版本包括大量平台的新功能和改进，能够帮助您创建任何外形上极具吸引力的用户体验。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>连续切换中和外出时的&quot;tablet 模式&quot;、 调整和优化应用程序和 Windows 外壳程序基于物理的外形和客户的首选项。</p>
<p>[阅读更多有关实现连续体系](https://msdn.microsoft.com/en-us/library/windows/hardware/dn917883(v=vs.85).aspx)</p></td>
<td><p>所有 Windows 10 设备现在都支持 Cortana，在 Windows Phone 8.1，引入个人助理技术。 了解设备的建议，并在这些文章中测试设置。</p>
<p>[阅读更多关于包括 Cortana](https://msdn.microsoft.com/en-us/library/windows/hardware/dn915051(v=vs.85).aspx)</p></td>
<td><p>Windows Hello 允许用户安全地登录到使用生物特征指纹读取器或红外相机等设备的设备。</p>
<p>[了解更多有关生物要求 Windows Hello](https://msdn.microsoft.com/en-us/library/windows/hardware/mt587095(v=vs.85).aspx)</p></td>
</tr>
</tbody>
</table>
 
## <a name="develop-windows-universal-drivers"></a>开发通用的 Windows 驱动程序

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>了解有关驱动程序的基本概念。</p>
<p>[开始使用 Windows 驱动程序](https://msdn.microsoft.com/en-us/library/windows/hardware/ff554690(v=vs.85).aspx)</p></td>
<td><p>构建基于 Shark Cove 开发板的通用传感器驱动程序。 了解如何加载 Windows 10 图像和调配这些主板驱动程序部署，调试和测试。</p>
<p>[使用 Shark Cove 硬件开发板](https://msdn.microsoft.com/en-us/library/windows/hardware/dn745910(v=vs.85).aspx)</p></td>
<td><p>创建跨多个不同的设备类型，对平板电脑和台式计算机的嵌入式系统中运行单独的驱动程序。 UMDF 和 KMDF 模板都包括在 Visual Studio 中，以帮助您入门。</p>
<p>[开始使用通用的 Windows 驱动程序](http://go.microsoft.com/fwlink/p/?LinkId=526095)</p></td>
</tr>
</tbody>
</table>

## <a name="customize-windows-images-to-reflect-your-brand"></a>自定义 Windows 映像，以反映您的品牌

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>创建可以收集您设置、 语言、 驱动程序，并将其应用于 Windows 映像以及配置设计器 (ICD) 的新设备的同时提供软件包。</p>
<p>Oem 可以将包应用到新设备。 企业可以将它们应用到设备，员工将从主页快速将其配置为使用该公司的网络。</p>
<p>[有关 Windows ICD 入门](https://msdn.microsoft.com/en-us/library/windows/hardware/dn916112(v=vs.85).aspx)</p></td>
<td><p>对于桌面 Pc，可以使用您现有的设置文件 (Unattend.xml) 在 Windows 安装过程中添加设置。</p>
<p>[构建一个 Windows 安装程序无人参与文件](manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs.md)</p></td>
</tr>
</tbody>
</table>

## <a name="test-system-components-for-compatibility-and-performance"></a>兼容性和性能的测试系统组件

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>编写和运行测试自动化的测试编写和执行框架 (TAEF)。 在学科和团队之间共享您的测试。</p>
<p>[入门测试创作和执行框架 (TAEF)](https://msdn.microsoft.com/en-us/library/windows/hardware/hh439627(v=vs.85).aspx)</p></td>
<td><p>测试您的硬件与 Windows 硬件实验室工具包。</p>
<p>[有关 Windows 硬件实验室工具包入门](https://msdn.microsoft.com/en-us/library/windows/hardware/dn915002(v=vs.85).aspx)</p></td>
<td><p>分析使用 Windows 性能 Toolkit 的系统和应用程序性能。</p>
<p>[开始使用 Windows 性能逐步式指南](https://msdn.microsoft.com/en-us/library/windows/hardware/mt634257(v=vs.85).aspx)</p></td>
</tr>
</tbody>
</table>

## <a name="a-href-idmanufacturing---putting-it-all-togetheramanufacturing-putting-it-all-together"></a><a href="" id="manufacturing---putting-it-all-together"></a>生产--放在一起

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>对于桌面 Pc，学习策略，以生成一组特定的市场，以满足不同客户的需要的图像。 应用经典的和现代的 Windows 应用程序、 驱动程序、 语言和其他自定义设置，并混合搭配您的自定义通过自动化的脚本或熟悉的 Windows 界面发布新的 Windows 版本。</p>
<p>[生成和部署桌面设备](manufacture/desktop/oem-windows-deployment-and-imaging-walkthrough.md)</p></td>
<td><p>构建 IoT 核心设备，应用到新设备的应用程序、 驱动程序和设置。</p>
<p>[生成和部署 IoT 核心设备](manufacture/iot/iot-core-manufacturing-guide.md)</p></td>
<td><p>Oem 和 Odm 可以生成并测试移动设备和驱动程序。</p>
<p>[生成和部署电话](manufacture/mobile/mobile-deployment-and-imaging.md)</p></td>
</tr>
</tbody>
</table>

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bwdknodes\wdknodes%5D:%20Get%20started%20with%20Windows%C2%A010%20%20RELEASE:%20%286/20/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")
