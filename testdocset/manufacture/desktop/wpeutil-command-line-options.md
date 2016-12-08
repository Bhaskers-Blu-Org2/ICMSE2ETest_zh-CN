---
author: Justinha
Description: "Wpeutil 命令行选项"
ms.assetid: 6537713a-510e-40cd-8518-d1150422bfe8
MSHAttr: PreferredLib:/library/windows/hardware
title: "Wpeutil 命令行选项"
ms.openlocfilehash: 6bd9d321c2954e6c69857461b2a7da2afbcc350c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="wpeutil-command-line-options"></a>Wpeutil 命令行选项


Windows® PE 实用程序 (Wpeutil) 是一个命令行工具，可用于在 Windows PE 会话过程中运行命令。 例如，您可以关闭或重新启动 Windows PE、 启用或禁用防火墙，设置语言设置并初始化网络。

## <a name="span-idwpeutilcommand-lineoptionsspanspan-idwpeutilcommand-lineoptionsspanspan-idwpeutilcommand-lineoptionsspanwpeutil-command-line-options"></a><span id="Wpeutil_Command-Line_Options"></span><span id="wpeutil_command-line_options"></span><span id="WPEUTIL_COMMAND-LINE_OPTIONS"></span>Wpeutil 命令行选项


Wpeutil 使用以下约定。

**Wpeutil**{命令}\[*参数*\]

例如︰

``` syntax
Wpeutil Shutdown
Wpeutil Enablefirewall
Wpeutil SetMuiLanguage de-DE
```

**请注意**  
Wpeutil 只能接受一个命令，每行。

 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">命令</th>
<th align="left">说明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>CreatePageFile [/ 路径 =&lt;路径&gt;] [/ 大小 =&lt;大小&gt;]</strong></p></td>
<td align="left"><p>创建指定的路径和大小的页面文件。 默认路径是 C:\pagefile.sys，默认大小为 64 兆字节。 必须指定至少一个选项。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil CreatePageFile /path=C:\pagefile.sys</code></pre>
<p>-或者-</p>
<pre class="syntax" space="preserve"><code>Wpeutil CreatePageFile /path=C:\pagefile.sys /size=128</code></pre>
<div class="alert">
<strong>重要</strong>  
<p>如果页面文件存在， <strong>/CreatePageFile</strong>选项必须设置为等于或大于当前的页面文件大小或该命令将失败。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><strong>DisableExtendedCharactersForVolume &lt;path_on_target_volume&gt;</strong></p></td>
<td align="left"><p>禁用扩展字符的 DOS 兼容文件名 （8.3 格式） 包含<em>路径在目标卷上</em>的卷的支持。 此命令仅对 NTFS 卷中。 <em>目标卷上的路径</em>必须指定的卷的根目录。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil DisableExtendedCharactersForVolume C:\</code></pre>
<p>如果禁用，则所有已创建包含扩展字符的文件将转换为短文件名。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>DisableFirewall</strong></p></td>
<td align="left"><p>禁用防火墙。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil DisableFirewall</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>EnableExtendedCharactersForVolume</strong> <em>&lt;path_on_target_volume&gt;</em></p></td>
<td align="left"><p>允许 8.3 格式的文件名中包含扩展的字符，包含<em>目标卷上的路径</em>的卷上。 此命令仅对 NTFS 卷中。 <em>目标卷上的路径</em>必须指定的卷的根目录。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil EnableExtendedCharactersForVolume C:\</code></pre>
<div class="alert">
<strong>请注意</strong>  
<p>如果您正在安装的扩展启用默认情况下，例如 JA-JP 或 KO-KR，或使用一份 Windows PE 在没有启用，例如 EN-US，扩展的字符的语言中的字符的语言的操作系统安装将在第一次启动过程中导致 Chkdsk 错误。 启用此选项之前将安装到该卷将会阻止运行 Chkdsk 命令。</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>EnableFirewall</strong></p></td>
<td align="left"><p>启用防火墙。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil EnableFirewall</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>InitializeNetwork</strong></p></td>
<td align="left"><p>初始化网络组件和驱动程序，并将计算机名设置为随机选择的值。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil InitializeNetwork</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>ListKeyboardLayouts</strong> <em>&lt;LCID&gt;</em></p></td>
<td align="left"><p>对于一个给定的区域设置 ID (LCID) 值列出支持的键盘布局 （名称和 ID）。 键盘布局也将更新在注册表项下︰<strong>置此变量 \SOFTWARE\Microsoft\Windows NT\CurrentVersion\WinPE\KeyboardLayouts</strong>。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil ListKeyboardLayouts 0x0409</code></pre>
<p>-或者-</p>
<pre class="syntax" space="preserve"><code>Wpeutil ListKeyboardLayouts 1033</code></pre>
<p>有关有效区域设置 Id 的列表，请参阅[图表区域设置 ID (LCID)](http://go.microsoft.com/fwlink/?LinkId=209839)。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>重新启动</strong></p></td>
<td align="left"><p>重新启动当前的 Windows PE 会话。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil Reboot</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SaveProfile</strong></p></td>
<td align="left"><p>停止日志记录，并保存到的位置的自定义配置文件使用<strong>Dism /enable-profiling</strong>命令前面指定的用户。 <strong>/Enable-profiling</strong>命令行选项的详细信息，请参阅[DISM Windows PE 服务命令行选项](dism-windows-pe-servicing-command-line-options.md)。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil SaveProfile profile_file_name &quot;short description&quot;</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SetKeyboardLayout</strong> <em>&lt;keyboard_layout_ID&gt;</em></p></td>
<td align="left"><p>在当前的 Windows PE 会话设置的键盘布局。 此命令成功后会对进程的效果。 若要获得支持的键盘布局列表，请输入︰</p>
<pre class="syntax" space="preserve"><code>ListKeyboardLayouts LCID</code></pre>
<p>要设置键盘的 EN-US，例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil SetKeyboardLayout 0409:00000409</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SetMuiLanguage</strong> <em>&lt;语言名称&gt;</em>[<strong>;</strong><em>&lt;语言名称&gt;</em>]</p></td>
<td align="left"><p>设置的语言。 <em>&lt;语言名称&gt;</em>使用的国际语言代码格式 (例如，EN-US 用于美国英语)。 用分号分隔，可以按照优先级顺序指定多种语言。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil SetMuiLanguage de-DE;en-US</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>SetUserLocale</strong> <em>&lt;语言名称&gt;</em>[<strong>;</strong><em>&lt;语言名称&gt;</em>]</p></td>
<td align="left"><p>设置用户区域设置。 <em>&lt;语言名称&gt;</em>使用的国际语言代码格式 (例如，EN-US 用于美国英语)。 用分号分隔，可以按照优先级顺序指定多种语言。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil SetUserLocale de-DE;en-US</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>关机</strong></p></td>
<td align="left"><p>在当前的 Windows PE 会话将关闭。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil Shutdown</code></pre>
<div class="alert">
<strong>请注意</strong>  
<p>您还可以执行下列操作在命令提示符窗口中︰</p>
<ul>
<li><p>单击<strong>关闭</strong>按钮</p></li>
<li><p>类型退出</p></li>
</ul>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p><strong>UpdateBootInfo</strong></p></td>
<td align="left"><p>注册表包含 Windows PE 启动方式有关的信息来填充。</p>
<p>运行此命令后，查询注册表。 例如︰</p>
<pre class="syntax" space="preserve"><code>wpeutil UpdateBootInfo
reg query HKLM\System\CurrentControlSet\Control /v PEBootType</code></pre>
<p>此操作的结果可能会改变之后加载额外的驱动程序的支持。</p>
<p>若要确定在其中通过启动 Windows PE 时，请检查下列︰</p>
<ul>
<li><strong>PEBootType</strong>︰ 错误、 平板、 远程、 Ramdisk:SourceIdentified Ramdisk:SourceUnidentified、 Ramdisk:OpticalDrive</li>
<li><strong>PEBootTypeErrorCode</strong>: HRESULT 代码</li>
<li><strong>PEBootServerName</strong>: Windows 部署服务服务器名称</li>
<li><strong>PEBootServerAddr</strong>: Windows 部署服务服务器的 IP 地址</li>
<li><strong>PEBootRamdiskSourceDrive</strong>︰ 源驱动器号，如果有的话。</li>
<li><strong>PEFirmwareType</strong>︰ 固件启动模式︰ bios，对于 UEFI 0x2 0x1。</li>
</ul>
<p>如果无法启动 Windows 部署服务，确定从启动 Windows PE 的地方的最好办法是先检查 PEBootRamdiskSourceDrive 注册表项。 如果不存在，正确 PEBootType 的驱动器扫描，寻找某种类型的识别启动驱动器的标记文件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>WaitForNetwork</strong></p></td>
<td align="left"><p>等待要初始化的网卡。 创建脚本时使用此命令，以确保已完全在继续操作之前初始化网卡。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>WaitForRemovableStorage</strong></p></td>
<td align="left"><p>在 Windows PE 启动序列，此命令将阻塞，直到可移动存储设备，例如 USB 硬盘启动，但被初始化。 例如︰</p>
<pre class="syntax" space="preserve"><code>Wpeutil WaitForRemovableStorage</code></pre>
<div class="alert">
<strong>请注意</strong>  
<p><strong>WaitForRemovableStorage</strong>此拼写是正确的。</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)

[DISM Windows PE 服务命令行选项](dism-windows-pe-servicing-command-line-options.md)

 

 






