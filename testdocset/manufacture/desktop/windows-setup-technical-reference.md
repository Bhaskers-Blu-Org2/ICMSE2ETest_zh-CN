---
author: Justinha
Description: "Windows 安装程序技术参考"
ms.assetid: f0fa0e04-e8ca-43b8-a789-0ef854e09333
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序技术参考"
ms.openlocfilehash: 3174512fbf67482f3f647be4ea95be79213e0154
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-technical-reference"></a>Windows 安装程序技术参考


Windows 安装程序将安装 Windows 操作系统的引导程序。

## <a name="span-idbkmkappspanspan-idbkmkappspanpractical-applications"></a><span id="BKMK_APP"></span><span id="bkmk_app"></span>实际应用


-   您可以安装或升级 Windows 操作系统的电脑上装入一个 USB 密钥从。ISO 文件、 DVD 或网络设备。
-   您可以自动执行 Windows 安装过程中，通过从[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445)创建答案文件中包括驱动程序、 程序包、 文件和 Windows 系统设置的配置。
-   为安装程序提供 Windows 安装程序可用于您自己的自定义 Windows 映像。
-   可以使用 Windows 安装程序中的菜单准备安装前的硬驱。

## <a name="span-idwhatsnewspanspan-idwhatsnewspanspan-idwhatsnewspanwhats-new"></a><span id="What_s_New"></span><span id="what_s_new"></span><span id="WHAT_S_NEW"></span>新增功能


-   Windows 8.1 升级是不同于以前的 Windows 升级方案。 有关详细信息，请参阅[Windows 8.1 Oem 升级方案](windows-81-upgrade-scenarios-for-oems.md)。

-   Windows 安装程序不能用于执行自动的升级到大多数版本的 Windows 8.1。

    对于批量许可版本的 Windows 中，我们已经添加了一个新的命令行选项， `setup /auto`，以帮助您实现升级。 请注意，我们只打算升级到 Windows 8.1，请使用此选项，我们可能会在 Windows 的将来版本中删除的选项。 有关详细信息，请参阅[Windows 安装程序命令行选项](windows-setup-command-line-options.md)。

-   [自动执行 OOBE 设置](settings-for-automating-oobe.md)︰ [NetworkLocation](https://msdn.microsoft.com/library/windows/hardware/dn923171)设置不再需要自动执行 OOBE。 已更改的[ProtectYourPC](https://msdn.microsoft.com/library/windows/hardware/dn915741)设置的功能。

## <a name="span-idbkmklinksspanspan-idbkmklinksspansee-also"></a><span id="BKMK_LINKS"></span><span id="bkmk_links"></span>请参见


下表包含与此方案相关的资源的链接。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">内容类型</th>
<th align="left">参考</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>规划</strong></p></td>
<td align="left"><p>[Windows 安装程序方案和最佳做法](windows-setup-scenarios-and-best-practices.md) | [Windows 安装自动化概述](windows-setup-automation-overview.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>部署</strong></p></td>
<td align="left"><p>[Windows 安装程序安装过程](windows-setup-installation-process.md) | [Windows 8.1 Oem 升级方案](windows-81-upgrade-scenarios-for-oems.md) | [从 DVD 启动](boot-from-a-dvd.md) | [从 USB 闪存驱动器安装 Windows](install-windows-from-a-usb-flash-drive.md) | [部署自定义映像](deploy-a-custom-image.md) | [WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>操作</strong></p></td>
<td align="left"><p>[自动执行 Windows 安装程序](automate-windows-setup.md) | [的配置集使用 Windows 安装程序使用](use-a-configuration-set-with-windows-setup.md)| [添加到 Windows 安装过程中 Windows 设备驱动程序](add-device-drivers-to-windows-during-windows-setup.md) | [添加到 Windows 安装程序的自定义脚本](add-a-custom-script-to-windows-setup.md) | [多语言 Windows 映像创建](multilingual-windows-image-creation.md) | [启动 Windows 审核模式还是 OOBE](boot-windows-to-audit-mode-or-oobe.md)</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>工具和设置</strong></p></td>
<td align="left"><p>[Windows 安装程序命令行选项](windows-setup-command-line-options.md) | [Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md) | [Windows 安装程序状态](windows-setup-states.md) | [版配置和产品 ID 文件 （EI.cfg 和 PID.txt），Windows 安装程序](windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt.md) | [Windows 安装程序日志文件和事件日志](windows-setup-log-files-and-event-logs.md) | [Windows 安装程序配置阶段](windows-setup-configuration-passes.md)</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>相关的技术</strong></p></td>
<td align="left"><p>[Windows 系统映像管理器技术参考](https://msdn.microsoft.com/library/windows/hardware/dn922445) | [无人参与的 Windows 安装参考](http://go.microsoft.com/fwlink/?LinkId=206281) | [Sysprep （系统准备） 概述](sysprep--system-preparation--overview.md) | [WinPE 窗口 10](winpe-intro.md)</p></td>
</tr>
</tbody>
</table>

 

 

 






