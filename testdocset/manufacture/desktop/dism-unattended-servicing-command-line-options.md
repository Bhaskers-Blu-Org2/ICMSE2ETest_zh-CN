---
author: Justinha
Description: "DISM 无人参与服务命令行选项"
ms.assetid: 698c8ad3-e292-45b2-9f74-d0e8885a7971
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 无人参与服务命令行选项"
ms.openlocfilehash: 3277792aff652a3fb73bf215259ced6b7d033b8e
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-unattended-servicing-command-line-options"></a>DISM 无人参与服务命令行选项


如果要安装多个程序包 Windows® 图像，使用 DISM 将 unattend.xml 答案文件应用于映像。 某些软件包需要首先安装其他程序包。 如果存在依存关系要求，以确保正确顺序的最佳方式是安装的使用答案文件。 当您使用 DISM unattend.xml 应答文件应用到图像时， **offlineServicing**配置阶段中的无人参与的设置应用于 Windows 映像。

服务使用 DISM 的 Windows 映像的基本语法如下︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_图像\_目录*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

下列服务选项可以用来将 unattend.xml 答案文件应用于脱机 Windows 映像︰

**DISM.exe /Image:**&lt;*路径\_到\_图像\_目录*&gt; **/Apply-Unattend:**&lt;*路径\_到\_unattend.xml*&gt;

下列服务选项可以用来将 unattend.xml 答案文件应用于正在运行的操作系统︰

**DISM.exe / 在线****/Apply-Unattend:**&lt;*路径\_到\_unattend.xml*&gt;

下表描述了可以如何使用无人参与的服务选项。 这些选项不是区分大小写的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ 获取帮助</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>无人参与服务命令行选项后紧接着使用，显示的选项和参数的信息。 其他主题可能会在指定了映像之后变为可用。</p>
<p>示例︰</p>
<p><strong>Dism 在线 / /Apply-Unattend /？</strong></p>
<p><strong>Dism /image:C:\test\offline /Apply-Unattend /？</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 应用的无人参与的︰</strong>&lt;<em>path_to_unattend.xml</em>&gt;</p></td>
<td align="left"><p>Unattend.xml 文件应用到图像。</p>
<p>如果您要更新的设备驱动程序使用无人参与的答案文件，必须将答案文件应用到脱机映像，并指定<strong>offlineServicing</strong>配置中的设置将传递。</p>
<p>如果您正在更新程序包或使用无人参与的应答文件的其他设置，您可以应用答案文件脱机或联机映像。 在<strong>offlineServicing</strong>配置阶段中指定的设置。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Apply-Unattend:C:\test\answerfiles\myunattend.xml</strong></p>
<p><strong>Dism / 在线 /Apply-Unattend:C:\test\answerfiles\myunattend.xml</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idlimitationsspanspan-idlimitationsspanspan-idlimitationsspanlimitations"></a><span id="Limitations"></span><span id="limitations"></span><span id="LIMITATIONS"></span>限制


-   不能包含无人参与服务命令相同的命令行上使用其他服务命令。

-   只有一个单一 unattend.xml 应答文件可以指定任何命令行上。

-   当您将程序包添加到映像，使用无人参与的答案文件时，将不检查程序包的适用性。 将应用答案文件，并且该操作将完成即使有包在答案文件中指定不应用于图像。 如果您必须将其添加到图像时，请检查程序包的适用性，，使用**DISM**命令和不使用**/ignorecheck**选项的**/Add-Package**选项。 有关详细信息，请参阅[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)。

-   如果您要更新的设备驱动程序使用无人参与的答案文件，必须应答文件应用到脱机映像。

-   当您使用 DISM.exe 将答案文件应用于正在运行的操作系统时，应答文件只应包含**offlineServicing**的配置阶段中的元素。 这是因为专业化配置阶段中的某些设置可能应用到操作系统。 我们建议使用 DISM 的应答文件只包含在**offlineServicing**配置阶段的设置。

-   创建答案文件的推荐的方式是创建它们在 Windows 系统映像管理器 （Windows sim 卡）。 但是，如果您使用手动创建的答案文件，则必须验证应答文件在 Windows SIM 中验证它的工作。 有关详细信息，请参阅[创作答案文件的最佳做法](https://msdn.microsoft.com/library/windows/hardware/dn915073)。

-   通过使用 DISM 应用答案文件时，目标计算机上没有缓存的答案文件。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

[DISM Windows 版本服务命令行选项](dism-windows-edition-servicing-command-line-options.md)

[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)

 

 






