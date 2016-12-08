---
author: Justinha
Description: "DISM 是什么？"
ms.assetid: ad08e68c-616f-404a-bfc6-c7bf1a4666f0
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 是什么？"
ms.openlocfilehash: 48ff493c511b89811c6cff3baa33d854a590e9ed
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="what-is-dism"></a>DISM 是什么？


部署映像服务和管理 (DISM.exe) 是一个命令行工具可以用来提供服务，并准备 Windows 映像，包括那些用于[Windows PE](winpe-intro.md)、 [Windows 恢复环境 (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)和[Windows 安装程序](windows-setup-technical-reference.md)。 DISM 可以用于服务的 Windows 映像 (.wim) 或虚拟硬盘 （.vhd 或.vhdx）。

DISM 可以通过命令行或从 Windows PowerShell。 有关 DISM 中使用 PowerShell 的详细信息，请参阅[部署映像服务管理 (DISM) 在 Windows PowerShell 的 Cmdlet](http://go.microsoft.com/fwlink/?LinkId=393917)。

本主题包括︰

-   [系统要求](#bkmk-reqs)
-   [优点](#bkmk-benefits)
-   [常见的处理和管理方案](#bkmk-common)
-   [限制](#bkmk-limitations)

## <a name="span-idbkmkreqsspanspan-idbkmkreqsspanspan-idbkmkreqsspanimage-requirements"></a><span id="BKMK_reqs"></span><span id="bkmk_reqs"></span><span id="BKMK_REQS"></span>图像的要求


DISM 可以用于到安装和服务的 Windows 映像.wim 文件、.vhd 文件或.vhdx 文件中，或在某些情况下中, 更新正在运行的操作系统。 它可以用较早 Windows 映像文件 （.wim 文件）。 但是，它不使用比安装的 Windows 评估和部署工具包 (Windows ADK) 的分布式 DISM 版本更新的 Windows 映像。 DISM 还会同时安装与 Windows 10、 Windows 8.1 和 Windows 8 操作系统。

WIM 的完整的技术说明，请参阅[Windows 图像文件格式 (WIM) 白皮书](http://go.microsoft.com/fwlink/?LinkId=92227)。

DISM 可以用于服务下列操作系统︰

-   （家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10
-   Windows 服务器 2016年技术预览
-   Windows 8.1
-   Windows 8
-   Windows Server 2012 R2
-   Windows Server 2012
-   Windows 7
-   Windows Server 2008 R2
-   Windows Server 2008 SP2
-   Windows PE 为 Windows 10
-   Windows PE 5.0
-   Windows PE 4.0
-   Windows 预安装环境 (Windows PE) 3.0
-   [Windows 恢复环境 (Windows RE)](windows-recovery-environment--windows-re--technical-reference.md)

**请注意**  DISM 无法在 Windows Vista® Service Pack 1 (SP1) 或 Windows Server 2008 上装载了从 VHD 的 Windows 映像。 您必须将附加 VHD 使用 DiskPart 工具之前，您可以使用 DISM 映像提供服务。 当服务使用 DiskPart 工具已附加 VHD 映像时，所做的更改与每个操作自动提交，不能放弃。

 

有关支持的平台和体系结构类型的列表，请参阅[DISM 支持的平台](dism-supported-platforms.md)。

## <a name="span-idbkmkbenefitsspanspan-idbkmkbenefitsspanspan-idbkmkbenefitsspanbenefits"></a><span id="BKMK_benefits"></span><span id="bkmk_benefits"></span><span id="BKMK_BENEFITS"></span>优点


DISM 可以使用.wim 文件︰

-   捕获和应用 Windows 映像。
-   添加和删除.wim 文件中的图像。
-   将.wim 文件拆分为几个较小的文件。

DISM 可以使用.wim、.vhd 或.vhdx 文件︰

-   添加、 删除和枚举程序包、 驱动程序、 语言。
-   启用或禁用 Windows 功能。
-   应用基于 Unattend.xml 应答文件的**offlineServicing**部分的更改。
-   配置国际设置。
-   升级到不同版本的 Windows 映像。
-   准备 Windows PE 映像。
-   为故障诊断提供了详细的日志。
-   提供服务的窗口，例如 Windows 早期版本 8.x，Windows 7，Windows Server 2008 R2，Windows Vista。
-   所有平台 （32 位，64 位） 的都服务。
-   服务从 64 位主机的 32 位图像，并处理 64 位映像从 32 位主机。 有关详细信息，请参阅"限制"一节以后本主题。
-   请使用旧的程序包管理器脚本。

## <a name="span-idbkmkcommonspanspan-idbkmkcommonspanspan-idbkmkcommonspancommon-servicing-and-management-scenarios"></a><span id="BKMK_common"></span><span id="bkmk_common"></span><span id="BKMK_COMMON"></span>常见的处理和管理方案


映像服务和管理解决方案分为两个主要类别︰

-   管理 Windows 映像，如枚举或编制的组件、 更新、 驱动程序或应用程序映像中包含清单、 捕获或分割图像、 附加或删除图像在.wim 文件中，或装载一个图像中所包含的信息或数据。
-   服务本身，包括添加或删除驱动程序软件包和驱动程序、 修改语言设置、 启用或禁用 Windows 功能和升级到更高版本的 Windows 映像。

以下是一些常见的图像处理和管理方案︰

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><strong>任务</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>捕获映像并将其保存为.wim 文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p>列出.wim、.vhd 或.vhdx 文件中的所有图像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>通过追加、 删除或枚举这些图像来管理单个.wim 文件中的多个图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>准备 Windows PE 映像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>有关 Windows PE 映像的列表信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p>安装的 Windows 映像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>列出有关装载.wim、.vhd 或.vhdx 文件，包括装载位置、 安装状态，并每个图像的索引，在.wim 文件中的图像的特定信息。</p></td>
</tr>
<tr class="even">
<td align="left"><p>列出所有驱动程序中的图像或特定驱动程序的信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>添加用于支持新硬件的现成的或启动关键驱动程序。</p></td>
</tr>
<tr class="even">
<td align="left"><p>添加操作系统更新，如热修复程序和 Windows 功能。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>添加或删除语言包，并配置国际设置。</p></td>
</tr>
<tr class="even">
<td align="left"><p>列出所有国际设置和图像中的语言。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>解答集成状态和日志记录。</p></td>
</tr>
<tr class="even">
<td align="left"><p>管理多个映像版本。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>列出包或特定信息的 Windows 功能中的所有功能。</p></td>
</tr>
<tr class="even">
<td align="left"><p>检查 Windows® Installer.msp 文件的适用性。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>更新多个 Windows 版本更新单个图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p>升级到更高版本的 Windows。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>列出所有图像都可以升级到此 Windows 版本。</p></td>
</tr>
<tr class="even">
<td align="left"><p>应用 Unattend.xml 答案文件中的设置。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>将大型.wim 文件拆分为几个较小的文件以适合所选媒体上。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idbkmklimitationsspanspan-idbkmklimitationsspanspan-idbkmklimitationsspanlimitations"></a><span id="BKMK_limitations"></span><span id="bkmk_limitations"></span><span id="BKMK_LIMITATIONS"></span>限制


**版本兼容性。** DISM 可以用较早的 Windows 操作系统的目标图像，但不是与目标图像的更多的操作系统 Windows ADK 的 DISM 中的已安装版本比新分布。 例如，从 Windows 10 DISM 版本 1511年可以服务窗口 10、 1511年版本和版本 1507年但没有版本 1607年。 若要了解详细信息，请参阅[DISM 支持的平台](dism-supported-platforms.md)。

**远程安装。** 不支持通过网络程序包安装到远程计算机。 Windows 映像必须在本地系统上存在。 DISM 可以访问网络共享上的包，但它必须将它们复制到临时的、 可写目录 （称为*暂存目录*）。 我们建议您安装每个软件包的唯一暂存目录在本地驱动器上使用。 安装完成后，可以删除暂存目录中的内容。

**答案文件。** 当您指定答案文件 (Unattend.xml) 的图像时，应用仅在**offlineServicing**配置阶段中指定的设置。 在应答文件中的所有其他设置将被忽略。 有关详细信息，请参阅[无人参与服务 DISM 命令行选项](dism-unattended-servicing-command-line-options.md)

**服务包。** 必须联机使用 Windows 更新独立安装程序安装服务包。 有关 Windows 更新独立安装程序的详细信息，请参阅[Windows 更新独立安装程序在 Windows 的说明](http://go.microsoft.com/fwlink/?LinkId=90850)。

**使用答案文件以确保包的依赖项。** 某些软件包需要首先安装其他程序包。 由于此依存关系要求，则应使用答案文件，如果要安装多个程序包。 通过使用 DISM 应用答案文件，多个程序包可以按正确的顺序安装。 这是安装多个程序包的首选的方法。

**程序包的安装顺序。** 在命令行中列出的顺序安装软件包。 在下面的示例、 1.inf、 2.inf 和 3.将在命令行中列出的顺序安装 inf。

``` syntax
DISM.exe /image:"c:\images\Image1" /Add-Driver /ForceUnsigned /DriverName:"C:\Drivers\1.inf" /DriverName:"C:\Drivers\2.inf" /DriverName:"C:\Drivers\3.inf"
```

**支持服务的命令是动态的。** 命令和选项的程序可用于处理映像取决于在 Windows 操作系统上处理的以及该图像是否脱机或当前正在运行的操作系统。

**不支持多个无人参与文件。** 您可以在命令行上指定多个驱动程序或程序包。 但是，不支持多个 Unattend.xml 答案文件。 任何命令行上只能指定一个答案文件。

**不支持多个服务命令。** 您可以指定多个驱动程序 （1.inf，2.inf） 或多个程序包，但您不能在同一个命令行上指定多个命令 （如**/Add-Driver** **/Remove-Driver**或**/Add-Driver** **/Add-Package**）。

**登录到网络共享。** 当您使用的计算机未加入到网络域时，使用带有域凭据**net use**来设置访问权限，然后指定存储在网络共享上的 DISM 日志的路径。

**通配符。** DISM 命令行中不支持通配符。

**不要更新之后安装语言包。** 如果您安装的更新 (修补程序后，常规分发版本\[GDR\]，或服务包\[SP\]) 在安装语言包之前包含依赖于语言的资源，不会应用更新中包含的特定于语言的更改。 一定要安装该更新之前安装语言包。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 引用 (部署映像服务和管理)](dism-reference--deployment-image-servicing-and-management.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

[设备驱动程序和部署概述](device-drivers-and-deployment-overview.md)

[语言包](language-packs-and-windows-deployment.md)

[了解处理策略](understanding-servicing-strategies.md)

 

 






