---
author: Justinha
Description: "DISM 命令行语法的全局选项"
ms.assetid: b902ff42-6718-48ca-878b-f3824d3229d4
MSHAttr: PreferredLib:/library/windows/hardware
title: "DISM 命令行语法的全局选项"
ms.openlocfilehash: cb9563c0f2a1692dd494d48b468b4dbb6f93f61d
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-global-options-for-command-line-syntax"></a>DISM 命令行语法的全局选项


可以将全局选项添加到大多数部署映像服务和管理 (DISM) 工具中的选项的处理和成像。 这些选项可用于访问命令行帮助，指定位置的文件来使用，并控制日志记录。

## <a name="span-idbasicsyntaxforservicingcommandsspanspan-idbasicsyntaxforservicingcommandsspanspan-idbasicsyntaxforservicingcommandsspanbasic-syntax-for-servicing-commands"></a><span id="Basic_Syntax_for_Servicing_Commands"></span><span id="basic_syntax_for_servicing_commands"></span><span id="BASIC_SYNTAX_FOR_SERVICING_COMMANDS"></span>服务命令的基本语法


装载或应用 Windows® 图像以使其可用后离线为平面文件结构，您可以指定任何全局 DISM 选项，将更新您的图像或脱机映像的位置服务选项。 您可以使用每个命令行只能有一个服务选项。

如果处理的正在运行的计算机，您可以使用**/Online**选项而不是指定脱机 Windows 映像的位置。 命令和可用于处理图像的选项取决于在 Windows 操作系统上处理的。 它们还取决于是否脱机映像或运行的操作系统。 在脱机 Windows 映像上工作的所有命令。 这些命令的子集是可用于处理运行的操作系统。

有关 DISM 服务命令的基本语法是︰

**DISM.exe** {**/图像︰**&lt;*路径\_到\_图像*&gt; | **/Online**} \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

服务命令的详细信息，请参阅[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)。

## <a name="span-idbasicsyntaxforimagingcommandsspanspan-idbasicsyntaxforimagingcommandsspanspan-idbasicsyntaxforimagingcommandsspanbasic-syntax-for-imaging-commands"></a><span id="Basic_Syntax_for_Imaging_Commands"></span><span id="basic_syntax_for_imaging_commands"></span><span id="BASIC_SYNTAX_FOR_IMAGING_COMMANDS"></span>图像处理的命令的基本语法


许多的全局选项也是可用的图像处理的命令。 DISM 成像命令的基本语法是︰

**DISM.exe** \[ **dism\_全局\_选项**\] {**服务\_选项**} \[ &lt;*服务\_参数*&gt;\]

有关使用 DISM 的映像管理，如应用或装入图像，详细信息请参阅[DISM 图像管理命令行选项](dism-image-management-command-line-options-s14.md)。

## <a name="span-idglobaloptionsforservicingandimagingcommandsspanspan-idglobaloptionsforservicingandimagingcommandsspanspan-idglobaloptionsforservicingandimagingcommandsspanglobal-options-for-servicing-and-imaging-commands"></a><span id="Global_Options_for_Servicing_and_Imaging_Commands"></span><span id="global_options_for_servicing_and_imaging_commands"></span><span id="GLOBAL_OPTIONS_FOR_SERVICING_AND_IMAGING_COMMANDS"></span>全局选项的处理和图像处理命令


DISM 全局有下列选项可用于脱机映像。

**DISM.exe /image:**&lt;*path\_to\_offline\_image\_directory*&gt; \[**/WinDir:**&lt;*path\_to\_%WINDIR%*&gt;\] \[**/LogPath:**&lt;*path\_to\_log\_file.log*&gt;\] \[**/LogLevel:**&lt;n&gt;\] \[**/SysDriveDir:**&lt;*path\_to\_bootMgr\_file*&gt;\] \[**/Quiet**\] \[**/NoRestart**\] \[**/ScratchDir:**&lt;*path\_to\_scratch\_directory*&gt;\] \[**/English**\] \[ **/格式︰**&lt;*输出\_格式*&gt;\]

DISM 全局有下列选项可用于正在运行的操作系统。

**DISM.exe / 在线**\[**/LogPath:**&lt;*path\_to\_log\_file*&gt;\] \[**/LogLevel:**&lt;*n*&gt;\] \[**/SysDriveDir:**&lt;*path\_to\_bootMgr\_file*&gt;\] \[**/Quiet**\] \[**/NoRestart**\] \[**/ScratchDir:**&lt;*path\_to\_scratch\_directory*&gt;\] \[**/English**\] \[**/Format:**&lt;*output\_format*&gt;\]

下表描述了可以如何使用每个 DISM 全局选项。 这些选项不是区分大小写的。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">全局选项</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ 获取帮助</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>显示有关可用 DISM 命令行选项和参数的信息。</p>
<p>使用<strong>/？</strong> 或不指定图像文件<strong>/Get-Help</strong>选项，如<strong>/Mount-Image</strong>的图像管理命令获得帮助。</p>
<p>示例：</p>
<p><strong>Dism /？</strong></p>
<p>指定的图像文件<strong>/图像︰</strong>&lt;<em>path_to_an_image</em> &gt;选项，或使用<strong>/Online</strong>选项来获得关于图像，如<strong>/Get-Packages</strong>中的服务命令的帮助。 可用于处理图像的选项取决于在您的映像中可用的处理技术。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /？</strong></p>
<p><strong>Dism / 在线 /？</strong></p>
<p>通过指定命令行选项，您可以显示其他帮助。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Add-Driver /？</strong></p>
<p><strong>Dism /image:C:\test\offline /Add-Package /？</strong></p>
<p><strong>Dism 在线 / /Get-Drivers /？</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ LogPath:</strong>&lt;<em>file.log 日志路径</em>&gt;</p></td>
<td align="left"><p>指定要记录到的完整路径和文件名称。 如果未设置，默认值是︰ <strong>%WINDIR%\Logs\Dism\dism.log</strong></p>
<div class="alert">
<strong>重要</strong>  
<p>在 Windows PE 中，默认目录是 RAMDISK 暂存空间可以是 32 MB 为低。</p>
<p>日志文件会自动存档。 将在文件名后附加.bak 保存存档的日志文件，并将生成新的日志文件。 日志文件是每次存档.bak 文件将被覆盖。</p>
</div>
<div>
 
</div>
<p>当使用未加入到域的网络共享时，使用与域凭据的<strong>net use</strong>命令来设置访问权限，设置 DISM 日志的日志路径之前。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /LogPath:AddPackage.log /Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 日志级别︰</strong>&lt;<em>n</em>&gt;</p></td>
<td align="left"><p>指定日志中显示的最大输出级别。 默认的日志级别为 3。 可接受的值如下所示︰</p>
<p>1 = 只是错误</p>
<p>2 = 错误和警告</p>
<p>3 = 错误、 警告和信息性</p>
<p>4 = 所有以前，列出的信息以及调试输出</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /LogPath:AddPackage.log /LogLevel:1 /Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 图像︰</strong>&lt;<em>path_to_offline_image_directory</em>&gt;</p></td>
<td align="left"><p>这是将服务脱机 Windows 映像的根目录的完整路径。 如果指定窗口的目录不是根目录的子目录，则必须指定<strong>/WinDir</strong> 。</p>
<p>此选项不能用于<strong>/Online</strong>。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /LogPath:AddPackage.log /LogLevel:1 /Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ WinDir:</strong>&lt;<em>path_to_ %WINDIR%</em>&gt;</p></td>
<td align="left"><p>使用<strong>/Image</strong>选项指定 Windows 目录相对于图像路径的路径。 这不能是完整路径到 Windows 目录;它应该是一个相对路径。 如果未指定，则默认值为脱机映像目录的根目录中的 Windows 目录。</p>
<p>此选项不使用<strong>/Online</strong>选项。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /WinDir:WinNT /Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>在线 /</strong></p></td>
<td align="left"><p>指定当前正在运行的操作系统上所采取的操作。</p>
<p>此选项不能使用<strong>/Image</strong>或<strong>/WinDir</strong>选项。 在使用<strong>/Online</strong>时联机映像的 Windows 目录将自动检测。</p>
<p>示例：</p>
<p><strong>Dism / 在线 /Get-Packages</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ SysDriveDir:</strong>&lt;<em>path_to_sysdrive_directory</em>&gt;</p></td>
<td align="left"><p>使用<strong>/SysDriveDir</strong>服务在 Windows PE 环境中已安装的 Windows 映像。</p>
<p><strong>/SysDriveDir</strong>选项指定 BootMgr 文件的位置的路径。 仅当 BootMgr 文件位于您所运行的命令不分区，这是必要的。</p>
<p>例如，在 Windows PE 命令提示符下，键入︰</p>
<p><strong>Dism /image:C:\Windows /SysDriveDir:C: \</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 安静</strong></p></td>
<td align="left"><p>关闭信息和进度输出到控制台。 只将错误消息将显示。</p>
<p>要在安静模式下运行时，此选项必须是设置每次运行命令行实用程序。</p>
<div class="alert">
<strong>请注意</strong>  
<p>不要使用<strong>/get</strong>命令使用<strong>/quiet</strong>选项。 将不显示任何信息。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /Add-Package /PackagePath:C:\packages\package.cab /quiet</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ NoRestart</strong></p></td>
<td align="left"><p>取消重新启动。 如果不需要重新启动，则此命令将没有任何效果。 此选项将保持从提示重新启动应用程序 （或保持它如果使用<strong>/quiet</strong>选项会自动重新启动）。</p>
<p>示例：</p>
<p><strong>Dism / 在线 /Add-Package /PackagePath:C:\packages\package.cab 只显示 /quiet</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ ScratchDir:</strong>&lt;<em>path_to_scratchdirectory</em>&gt;</p></td>
<td align="left"><p>指定提取文件的在服务期间临时使用时，将使用的临时目录。 该目录必须位于本地。 如果未指定，\Windows\<em>%temp%</em>目录将与一起使用，每次运行 DISM 的子目录名称随机生成的十六进制值。 每次操作后，会删除暂存目录中的项目。</p>
<p>不应作为临时目录使用网络共享位置展开安装程序包 （.cab 或.msu 文件）。 用于在服务期间提取临时使用的文件的目录应该是本地目录。</p>
<p>示例：</p>
<p><strong>Dism /image:C:\test\offline /ScratchDir:C:\Scratch /Add-Package /PackagePath:C:\packages\package.cab</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ 英文</strong></p></td>
<td align="left"><p>用英文显示命令行输出。</p>
<div class="alert">
<strong>请注意</strong>  
<p>有些资源不能以英语显示。</p>
<p>当您使用不支持此选项<strong>DISM /？</strong> 命令。</p>
</div>
<div>
 
</div>
<p>示例：</p>
<p><strong>Dism /Get-ImageInfo /ImageFile:C:\test\offline\install.wim /index:1 /English</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ 格式: {表 |列表}</strong></p></td>
<td align="left"><p>指定的报表输出格式。</p>
<p>示例：</p>
<p><strong>Dism /Image:C:\test\offline 获取应用程序 /Format:table</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[部署映像服务和管理 (DISM) 命令行选项](deployment-image-servicing-and-management--dism--command-line-options.md)

[DISM 应用程序服务命令行选项](dism-application-servicing-command-line-options.md)

[DISM Windows 版本服务命令行选项](dism-windows-edition-servicing-command-line-options.md)

[DISM 语言和国际服务命令行选项](dism-languages-and-international-servicing-command-line-options.md)

[DISM 操作系统程序包服务命令行选项](dism-operating-system-package-servicing-command-line-options.md)

[DISM 驱动程序服务命令行选项](dism-driver-servicing-command-line-options-s14.md)

[DISM 无人参与服务命令行选项](dism-unattended-servicing-command-line-options.md)

[DISM Windows PE 服务命令行选项](dism-windows-pe-servicing-command-line-options.md)

 

 






