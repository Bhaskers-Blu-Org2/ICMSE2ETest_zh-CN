---
author: Justinha
Description: "（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 只。"
ms.assetid: b5f9740e-070c-48c0-9f79-42b25dfeb219
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 功能程序包服务命令行选项"
ms.openlocfilehash: 97da6bb10c30114b207ae50641defdb15b43f01f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="span-iddismcapabilitiespackageservicingcommand-lineoptionsspandism-capabilities-package-servicing-command-line-options"></a><span id="dism_capabilities_package_servicing_command-line_options"></span>DISM 功能程序包服务命令行选项


（家庭、 Pro、 企业和教育） 的桌面版本的 Windows 10 只。 使用部署映像服务和管理 (DISM.exe) 处理 Windows 功能。 功能是封装类型允许您请求未指定版本的.NET 或语言等服务窗口。 使用 DISM 搜索类似 Windows Update 或您公司的服务器来查找并安装最新版本的多个源。

若要查看可用的功能，请转到[第 2 版的功能上的需求 （功能）](features-on-demand-v2--capabilities.md)。

## <a name="span-iddismcommand-lineoptionsspanspan-iddismcommand-lineoptionsspanspan-iddismcommand-lineoptionsspandism-command-line-options"></a><span id="DISM_Command-Line_Options"></span><span id="dism_command-line_options"></span><span id="DISM_COMMAND-LINE_OPTIONS"></span>DISM 命令行选项


下面是如何使用每个 DISM 选项。 这些选项不是区分大小写的。

请注意，每个这些命令要求任何一个**/Online**或**/图像︰**&lt;*路径\_到\_脱机\_图像\_文件*&gt;参数。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Options</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ 添加功能</strong></p>
<p><strong>/ 名称︰</strong>&lt;<em>capability_name</em> &gt; <strong>[/ 源︰</strong>&lt;<em>源</em>&gt;<strong>] [/LimitAccess]</strong></p></td>
<td align="left">将功能添加到图像中。
<pre class="syntax" space="preserve"><code>Dism /Online /Add-Capability /Name:Language.Basic~~~en-US~0.0.1.0</code></pre>
<div class="alert">
<strong>请注意</strong> DISM 将检查按以下顺序使用资源文件︰
<ol>
<li>如果指定了<strong>/Source</strong> ，DISM 首先在指定的位置。</li>
<li>如果未指定<strong>/Source</strong> ，或在指定的位置找不到源文件，DISM 将检查是否已设置了组策略。 如果是这样，DISM 将检查由组策略指定的位置。</li>
<li>如果仍未找到这些文件，并且如果 DISM 处理联机映像，并且未指定<strong>/LimitAccess</strong> ，它看起来上 Windows 更新的文件。</li>
</ol>
</div>
<div>
 
</div>
<p><strong>/ 源</strong>︰ 允许您选择一个位置，例如服务器，使用功能资源文件的位置。 您可以使用多个<strong>/Source</strong>参数。</p>
<pre class="syntax" space="preserve"><code>Dism /Online /Add-Capability /Name:Language.Basic~~~en-US~0.0.1.0 /Source:\\server\share /Source:\\server2\share</code></pre>
<p><strong>/ LimitAccess</strong>︰ 告诉 DISM 不检查 Windows 更新或使用功能资源文件的 Windows 服务器更新服务。</p>
<pre class="syntax" space="preserve"><code>Dism /Online /Add-Capability /Name:Language.Basic~~~en-US~0.0.1.0 /Source:\\server\share /LimitAccess</code></pre></td>
</tr>
<tr class="even">
<td align="left"><strong>/ 获取能力</strong></td>
<td align="left"><p>在图像中获得能力。 示例：</p>
<pre class="syntax" space="preserve"><code>DISM /Online /Get-Capabilities</code></pre></td>
</tr>
<tr class="odd">
<td align="left">/<strong>/ Get-CapabilityInfo/CapabilityName:</strong>&lt;<em>capability_name</em>&gt;</td>
<td align="left"><p>获取有关特定功能的信息。 示例：</p>
<pre class="syntax" space="preserve"><code>DISM /Online /Get-CapabilityInfo
 /CapabilityName:Language.Basic~~~en-US~0.0.1.0</code></pre></td>
</tr>
<tr class="even">
<td align="left"><strong>/ 删除功能</strong>
<p>所需的其他参数︰</p>
<strong>/ CapabilityName:</strong>&lt;<em>capability_name_in_image</em>&gt;</td>
<td align="left"><pre class="syntax" space="preserve"><code>Dism /Online /Remove-Capability /Name:Language.Basic~~~en-US~0.0.1.0
Dism /Image:C:\test\offline /Remove-Capability /Name:Language.Basic~~~en-US~0.0.1.0</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[功能需求 V2 （功能）](features-on-demand-v2--capabilities.md)

[DISM 的部署 windows 映像服务和管理技术参考](dism---deployment-image-servicing-and-management-technical-reference-for-windows.md)

[DISM 是什么？](what-is-dism.md)

[DISM 命令行语法的全局选项](dism-global-options-for-command-line-syntax.md)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

 

 






