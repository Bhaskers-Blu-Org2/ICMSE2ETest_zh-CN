---
author: Justinha
Description: "Windows 10 DISM 命令行选项"
ms.assetid: 56e2f629-ee86-4ee3-9ba6-f8864cdf4ca3
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 10 DISM 命令行选项"
ms.openlocfilehash: 9581438c4f342b56f06cf5479a880a8921a82509
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-10-dism-command-line-options"></a>Windows 10 DISM 命令行选项


部署映像服务和管理 (DISM.exe) 装载 Windows 映像 (.wim) 文件或虚拟硬盘 （.vhd 或.vhdx） 来处理。 您还可以使用 DISM 安装、 卸载、 配置和更新的功能和脱机 Windows 映像和脱机 Windows 预安装环境 (WinPE) 映像中的程序包。 有关 DISM 的常见方案的详细信息，请参阅[DISM 是什么？](what-is-dism.md)。

除了命令行工具，DISM 是可使用 PowerShell。 有关详细信息，请参阅[部署映像服务管理 (DISM) 在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=239926)。

DISM 将替换包括 PEImg，则 intlcfg 将、 程序包管理器和 ImageX 工具。

## <a name="span-idinthissectionspanspan-idinthissectionspanspan-idinthissectionspanin-this-section"></a><span id="In_This_Section"></span><span id="in_this_section"></span><span id="IN_THIS_SECTION"></span>在这一节


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)</p></td>
<td align="left"><p>如捕获、 应用以及安装的 Windows 映像的映像管理命令。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM 命令行语法的全局选项](dism-global-options-for-command-line-syntax.md)</p></td>
<td align="left"><p>基本的命令行语法和处理函数的通用选项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)</p></td>
<td align="left"><p>用于添加、 删除和枚举.cab 和.msu 文件包和启用、 禁用和枚举功能程序包服务命令。</p></td>
</tr>
<tr class="even">
<td align="left">[DISM 调配包 (.ppkg) 的命令行选项](dism-provisioning-package-command-line-options.md)</td>
<td align="left"><p>使用 Windows 提供的软件包 (.ppkg)</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM 功能程序包服务命令行选项](dism-capabilities-package-servicing-command-line-options.md)</p></td>
<td align="left"><p>服务命令添加语言、.NET 和其他 Windows 功能的能力。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM 应用程序包 （.appx 或.appxbundle） 服务命令行选项](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)</p></td>
<td align="left"><p>为命令添加、 删除和枚举程序包的应用程序提供服务。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM 应用程序服务命令行选项](dism-application-servicing-command-line-options.md)</p></td>
<td align="left"><p>服务可以用于检查 Windows 安装程序应用程序修补程序 （.msp 文件） 的适用性并查询您脱机映像安装的 MSI 应用程序和应用程序修补程序 （.msp 文件） 有关信息的命令。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM 默认应用程序关联服务命令行选项](dism-default-application-association-servicing-command-line-options.md)</p></td>
<td align="left"><p>服务命令用于导入、 导出、 删除和枚举指定哪个应用程序打开的文件，根据文件扩展名或协议的设置</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)</p></td>
<td align="left"><p>用于调整国际设置和配置国际服务命令。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)</p></td>
<td align="left"><p>用于添加、 删除和枚举驱动程序.inf 文件的特定驱动程序服务命令。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM 无人参与服务命令行选项](dism-unattended-servicing-command-line-options.md)</p></td>
<td align="left"><p>服务可用于应用 Unattend.xml 文件的命令。</p></td>
</tr>
<tr class="even">
<td align="left"><p>[DISM Windows PE 服务命令行选项](dism-windows-pe-servicing-command-line-options.md)</p></td>
<td align="left"><p>为准备 WinPE 映像 WinPE-特定服务的命令。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[DISM Windows 版本服务命令行选项](dism-windows-edition-servicing-command-line-options.md)</p></td>
<td align="left"><p>用于更改 Windows 映像的版本的版本服务命令。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[DISM 帮助主题 (部署映像服务和管理)](dism-how-to-topics--deployment-image-servicing-and-management.md)

[DISM 是什么？](what-is-dism.md)

 

 






