---
author: Justinha
Description: "DISM Windows 版本服务命令行选项"
ms.assetid: e7faf4eb-7de8-49f7-9d42-caededf1b289
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM Windows 版本服务命令行选项"
ms.openlocfilehash: ed1a129352f38303a6b8671cd56eeebf3d0f1efe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-windows-edition-servicing-command-line-options"></a>DISM Windows 版本服务命令行选项


Windows® 版服务命令可用于更改为相同的版本系列中较高版本的一个版本的 Windows 8。 每个潜在的目标版本的版本程序包在 Windows 映像中转移。 这被称为版本系列图像。 由于转移目标版本，可以处理单个映像，并且更新将适当地应用于图像中的每个版本。 这可以帮助减少需要管理的映像的数目，但出厂时间或最终用户必须在**specialize**配置阶段中花费的时间可能会增加。

脱机更改不需要产品密钥。 如果您改为使用脱机服务较高版本，您可以添加产品密钥使用下列方法之一︰

-   过程的全新体验 (OOBE) 中输入产品密钥。

-   使用无人参与的答案文件在**specialize**配置阶段输入的产品密钥。

-   使用部署映像服务和管理 (DISM) 和 Windows 版本服务命令行选项**/Set-ProductKey**脱机设置版本之后。

本主题︰

[命令行语法](#bkmk-syntax)

[限制](#bkmk-limitations)

## <a name="span-idbkmksyntaxspanspan-idbkmksyntaxspanspan-idbkmksyntaxspancommand-line-syntax"></a><span id="BKMK_Syntax"></span><span id="bkmk_syntax"></span><span id="BKMK_SYNTAX"></span>命令行语法


服务使用 DISM 的 Windows 映像的基本语法如下︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_图像\_目录*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

您可以使用脱机映像列出版本或将 Windows 映像更改为较高版本的下列版本服务选项︰

**DISM.exe /Image:**&lt;*路径\_到\_图像\_目录*&gt; {**/Get-CurrentEdition** | **/Get-TargetEditions** | **/Optimize-Image /WIMBoot** | **/Set-Edition** | **/Set-ProductKey**:&lt;*产品\_键*&gt;}

正在运行的 Windows 操作系统的下列版服务选项有︰

**DISM.exe / 在线**{**/Get-CurrentEdition** | **/Get-TargetEditions** | **/Set-ProductKey**:&lt;*产品\_键*&gt; | **/Set-Edition**:&lt;*目标\_版*&gt; {**/GetEula**:&lt; *路径*&gt; | **/AcceptEula** **/ProductKey**:&lt;产品\_键&gt;}}

下表提供了如何使用每个版服务选项的说明。 这些选项不是区分大小写的。

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
<td align="left"><p>版服务命令行选项后紧接着使用，显示的选项和参数的信息。 其他帮助主题可能会在指定了映像之后变为可用。</p>
<p>示例︰</p>
<p><strong>Dism /Image:C:\test\offline /Get-CurrentEdition /？</strong></p>
<p><strong>Dism 在线 / /Get-CurrentEdition /？</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Get CurrentEdition</strong></p></td>
<td align="left"><p>显示指定映像的版本。</p>
<p>示例︰</p>
<p><strong>Dism /Image:C:\test\offline /Get-CurrentEdition</strong></p>
<p><strong>Dism / 在线 /Get-CurrentEdition</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Get TargetEditions</strong></p></td>
<td align="left"><p>显示将出现的 Windows 版本，可以将映像更改为。</p>
<p>示例︰</p>
<p><strong>Dism /Image:C:\test\offline /Get-TargetEditions</strong></p>
<p><strong>Dism / 在线 /Get-TargetEditions</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 一组版</strong>:&lt;<em>target_edition_ID</em> &gt; [{<strong>/GetEula</strong>:&lt;<em>路径</em> | <strong>/AcceptEula</strong> <strong>/ProductKey</strong>:&lt;<em>product_key</em>&gt;}]</p></td>
<td align="left"><p>使用不带参数的<strong>/Set-Edition</strong>选项将脱机 Windows 映像更改为较高版本。</p>
<p>若要更改为较高版本的联机的 Windows Server 操作系统，必须使用<strong>/AcceptEula</strong>和<strong>/ProductKey</strong>参数使用<strong>/Set-Edition</strong>选项。</p>
<div class="alert">
<strong>重要</strong>  
<p>不应使用在图像已更改为较高版本的<strong>/Set-Edition</strong>选项。 建议使用此版本系列中可用的最低版本的选项。</p>
</div>
<div>
 
</div>
<p>使用<strong>/GetEula</strong>上联机映像复制到指定路径的最终用户许可协议。</p>
<p><strong>/AcceptEula</strong>参数接受最终用户许可协议，并需更改为联机映像上的 Windows 版本。</p>
<p>示例：</p>
<p><strong>Dism /Image:C:\test\offline /Set-Edition:</strong><em>&lt;版名称&gt;</em></p>
<p>在运行 Windows Server 操作系统只能︰</p>
<p><strong>Dism / 在线 /Set-Edition:</strong><em>&lt;版名称&gt;</em> <strong>/GetEula:c:\eulapathDism / 在线 /Set-Edition:</strong><em>&lt;版名称&gt;</em><strong>/AcceptEula /ProductKey:12345-67890-12345-67890-12345</strong></p>
<p>其中<em>&lt;版名称&gt;</em>是您想要更改为更高版本。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 产品密钥集</strong>:&lt;<em>的产品密钥</em>&gt;</p></td>
<td align="left"><p><strong>/Set-ProductKey</strong>选项仅用于脱机 Windows 映像更改为较高版本使用<strong>/Set-Edition</strong>选项后，脱机 Windows 映像中输入的当前版本的产品密钥。</p>
<p>示例：</p>
<p><strong>Dism /Image:C:\test\offline /Set-ProductKey:12345-67890-12345-67890-12345</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idbkmklimitationsspanspan-idbkmklimitationsspanspan-idbkmklimitationsspanlimitations"></a><span id="BKMK_Limitations"></span><span id="bkmk_limitations"></span><span id="BKMK_LIMITATIONS"></span>限制


-   如果在设置脱机映像的版本时未输入产品密钥，您必须在 OOBE，期间输入的产品密钥或使用无人参与的答案文件在**specialize**配置阶段输入的产品密钥。

-   不能在 Windows 预安装环境 (Windows PE) 映像上使用版服务命令。

-   若要维护特定于版本的自定义项，应该在版本升级后应用版本特定的答案文件。

-   如果您想要运行的 64 位图像与 30 多个语言包**/Set-Edition**选项，您必须从 64 位计算机运行。 否则，您可能会收到内存不足错误。 如果想要从 32 位计算机的 64 位图像只能存在此限制。 运行时映像的体系结构匹配的计算机上的该选项不存在这种限制。

-   不能设置为更低版本的 Windows 映像。 当您运行**/Get-TargetEditions**选项时，不会出现的最低版本。

-   不应使用在图像已更改为较高版本的**/Set-Edition**选项。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[DISM 是什么？](what-is-dism.md)

[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)

[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

[将 Windows 映像更改为较高版本使用 DISM](change-the-windows-image-to-a-higher-edition-using-dism.md)

 

 






