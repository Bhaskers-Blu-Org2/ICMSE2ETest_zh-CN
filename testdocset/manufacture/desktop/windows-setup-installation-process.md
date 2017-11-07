---
author: Justinha
Description: "Windows 安装程序安装过程"
ms.assetid: e88c0c88-cc6d-436c-a1c0-b109c923ab7e
MSHAttr: PreferredLib:/library/windows/hardware
title: "Windows 安装程序安装过程"
ms.openlocfilehash: 7114e79a1592618ee4b7aa85e1cb04c7ae647789
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-installation-process"></a>Windows 安装程序安装过程


Windows® 安装程序安装 Windows 更新或升级现有的 Windows 安装程序。 这也是以下安装和升级方法的基础︰

-   交互式安装

-   自动的安装

-   Windows 部署服务

本主题︰

-   [Windows 安装程序安装类型](#installationtypes)

-   [Windows 安装程序过程中](#windowssetupprocess)

## <a name="span-idinstallationtypesspanspan-idinstallationtypesspanspan-idinstallationtypesspan-windows-setup-installation-types"></a><span id="InstallationTypes"></span><span id="installationtypes"></span><span id="INSTALLATIONTYPES"></span>Windows 安装程序安装类型


Windows 安装程序可执行全新和升级安装。 但是，它不执行计算机的迁移。 相反，您必须使用 Windows 轻松传送，用户状态迁移工具 (USMT) 或其他迁移工具将数据从以前的安装移动到新的操作系统。

-   **自定义安装。** Windows 安装程序可以执行自定义安装，也称为全新安装，将保存您以前的 Windows 安装，但不会迁移您的设置。 以前的 Windows 安装在干净安装后将不能启动。

-   **升级安装。** Windows 安装程序可以执行在升级操作系统时保留您的设置和首选项安装。

## <a name="span-idwindowssetupprocessspanspan-idwindowssetupprocessspanspan-idwindowssetupprocessspan-windows-setup-process"></a><span id="WindowsSetupProcess"></span><span id="windowssetupprocess"></span><span id="WINDOWSSETUPPROCESS"></span>Windows 安装程序过程中


Windows 安装程序启动和重新启动计算机、 收集信息、 复制文件，并创建或调整配置设置。 下表显示为 Windows 安装程序的整个过程︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Windows 安装程序阶段</th>
<th align="left">设置操作</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>下层</strong>（用于自定义安装和升级）</p>
<p>-或-</p>
<p><strong>Windows PE</strong> （用于启动 Windows DVD 或启动自定义的 Windows PE 映像）</p></td>
<td align="left"><ol>
<li><p>通过使用 Windows 安装程序对话框 （交互式） 或应答文件 （无人参与） 或两者的组合指定 Windows 安装程序配置。 Windows 安装程序配置包括添加产品密钥和配置磁盘。</p></li>
<li><p>应用答案文件设置在[windowsPE](windowspe.md)配置阶段中的配置安装行为和用户体验。</p></li>
<li><p>配置磁盘。</p></li>
<li><p>将 Windows 映像复制到磁盘。</p></li>
<li><p>准备启动信息。</p></li>
<li><p>处理的[offlineServicing](offlineservicing.md)配置阶段中的答案文件设置。 设置应用于 Windows 映像之前，Windows 映像启动。 计算机第一次引导时，任何可选组件，处理驱动程序、 更新或语言包。</p></li>
</ol></td>
</tr>
<tr class="even">
<td align="left"><p><strong>联机配置</strong></p></td>
<td align="left"><p>创建特定的配置，使唯一的 Windows 安装。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Windows 欢迎</strong></p></td>
<td align="left"><ol>
<li><p>应用在[oobeSystem](oobesystem.md)配置阶段中的答案文件设置。</p></li>
<li><p>应用 Oobe.xml 文件中的内容的文件设置。</p></li>
<li><p>启动欢迎使用 Windows。</p></li>
</ol></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[Windows 安装程序技术参考](windows-setup-technical-reference.md)

[自动执行 Windows 安装程序](automate-windows-setup.md)

[用于自动执行 OOBE 设置](settings-for-automating-oobe.md)

[Windows 安装程序方案和最佳做法](windows-setup-scenarios-and-best-practices.md)

[Windows 安装程序自动化概述](windows-setup-automation-overview.md)

[审核模式概述](audit-mode-overview.md)

[Windows 安装程序配置阶段](windows-setup-configuration-passes.md)

[Windows 安装程序支持的平台和跨平台部署](windows-setup-supported-platforms-and-cross-platform-deployments.md)

 

 






