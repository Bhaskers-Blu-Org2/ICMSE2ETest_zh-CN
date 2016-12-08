---
author: Justinha
Description: "BCDBoot 命令行选项"
ms.assetid: 294a0181-f3e9-42c1-8e7f-5a5c28323e25
MSHAttr: PreferredLib:/library/windows/hardware
title: "BCDBoot 命令行选项"
ms.openlocfilehash: 0c87080c867c883d9a7950e921e02e92938d2e2c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="bcdboot-command-line-options"></a>BCDBoot 命令行选项


BCDBoot 是一个命令行工具，用来配置运行 Windows 操作系统的 PC 或设备上的引导文件。 在下列情况中，可以使用该工具︰

-   **应用新的 Windows 映像后将启动文件添加到一台电脑。** 在典型的基于映像的 Windows 部署中，使用 BCDBoot 将固件和系统分区设置为您的映像启动。 若要了解详细信息，请参阅[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)。
-   **设置为启动到虚拟硬盘 (VHD) 文件，其中包含 Windows 映像的 PC。** 若要了解详细信息，请参阅[引导至 VHD （本机引导）︰ 将虚拟硬盘添加到引导菜单](boot-to-vhd--native-boot--add-a-virtual-hard-disk-to-the-boot-menu.md)。
-   **修复系统分区。** 如果已损坏的系统分区，您可以使用 BCDBoot 若要通过使用 Windows 分区从这些文件的新副本重新创建系统分区文件。
-   **设置或修复双启动计算机上的启动菜单。** 如果已经在一台 PC 上安装了 Windows 的多个副本，您可以使用 BCDBoot 添加或修复启动菜单。

## <a name="span-idfilelocationsspanspan-idfilelocationsspanspan-idfilelocationsspanfile-locations"></a><span id="File_Locations"></span><span id="file_locations"></span><span id="FILE_LOCATIONS"></span>文件位置


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>在窗口和 Windows 预安装环境 (WinPE)</p></td>
<td align="left"><p>%WINDIR%\System32\BCDBoot.exe</p></td>
</tr>
<tr class="even">
<td align="left"><p>在 Windows 评估和部署工具包 (Windows ADK):</p></td>
<td align="left"><p>C:\Program 文件 (x86) \Windows Kits\10\Assessment 和部署 Kit\Deployment Tools\amd64\BCDBoot\BCDBoot.exe</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idsupportedoperatingsystemsspanspan-idsupportedoperatingsystemsspanspan-idsupportedoperatingsystemsspansupported-operating-systems"></a><span id="Supported_operating_systems"></span><span id="supported_operating_systems"></span><span id="SUPPORTED_OPERATING_SYSTEMS"></span>支持的操作系统


BCDBoot 可以将引导环境文件复制 Windows 10、 Windows 8.1、 Windows 8，Windows 7，Windows Vista、 Windows 服务器 2016年技术预览、 Windows Server 2012 R2、 Windows Server 2012，Windows Server 2008 R2 或 Windows Server 2008 的图像。

## <a name="span-idhowitworksspanspan-idhowitworksspanspan-idhowitworksspanhow-it-works"></a><span id="How_It_Works"></span><span id="how_it_works"></span><span id="HOW_IT_WORKS"></span>它的工作原理


要配置系统分区，请 BCDBoot 复制一小套的引导环境文件从安装的 Windows 映像到系统分区。

BCDBoot 可以使用最新版本的 Windows 文件系统分区上创建引导配置数据 (BCD) 存储区︰

-   BCDBoot 创建新的 BCD 存储和初始化 BCD 的引导环境的文件系统分区，包括 Windows 启动管理器，使用 %WINDIR%\\System32\\配置\\BCD 模板文件。
-   Windows 10 中的新增功能︰ 在升级期间，BCDBoot 保留任何其他现有启动项目，如**debugsettings**，当创建新的存储。 使用**/c**选项来忽略旧设置并开始使用新的 BCD 存储。
-   如果已存在此 Windows 分区，默认情况下，引导项 BCDBoot 将清除旧的启动项目，它的值。 **/M**选项用于更新系统文件时保留现有启动项目的值。
-   默认情况下，BCDBoot 将所选的 Windows 分区的启动条目移动到 Windows 启动管理器启动顺序的顶部。 使用**/d**选项可保留现有的引导顺序。

UEFI Pc 上 BCDBoot 可以更新该设备的 NVRAM 中的固件条目︰

-   BCDBoot NVRAM 点到 Windows 启动管理器中添加固件条目。 默认情况下，该项将作为引导列表中的第一个项目。 使用**/p**选项可保留现有 UEFI 引导顺序。 使用**/addlast**以将其添加到启动顺序列表的底部。

## <a name="span-idcommand-lineoptionsspanspan-idcommand-lineoptionsspanspan-idcommand-lineoptionsspancommand-line-options"></a><span id="Command-Line_Options"></span><span id="command-line_options"></span><span id="COMMAND-LINE_OPTIONS"></span>命令行选项


下面的命令行选项是可用的 BCDBoot.exe。

**BCDBOOT**&lt;*source*&gt; \[**/l** &lt;*locale*&gt;\] \[**/s** &lt;*volume-letter*&gt; \[**/f** &lt;*firmware type*&gt;\]\] \[**/v**\] \[**/m** \[{*OS Loader GUID*}\]\] \[**/addlast** or **/p**\] \[**/d**\] \[**/c**\]

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
<td align="left"><p><em>&lt;来源&gt;</em></p></td>
<td align="left"><p>必需。 指定要用作源的将引导环境文件复制的 Windows 目录的位置。</p>
<p>下面的示例通过从 C:\Windows 文件夹使用 BCD 文件初始化系统分区︰</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/l <em>&lt;区域设置&gt;</em></p></td>
<td align="left"><p>可选项。 指定的区域设置。 默认设置为美国英语 (<code>en-us</code>)。</p>
<p>下面的示例将默认的 BCD 区域设置设置为日语︰</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /l ja-jp</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/s <em>&lt;卷号&gt;</em></p></td>
<td align="left"><p>可选项。 指定系统分区的卷号。 不应在典型的部署方案中使用此选项。</p>
<p>使用此设置指定一个系统分区，如 USB 闪存驱动器或辅助硬盘配置将在另一台计算机上，启动驱动器时。</p>
<p><strong>（uefi)</strong>:</p>
<ul>
<li><p>BCDBoot 将引导文件复制到 EFI 系统分区或由 /s 选项指定的分区。</p>
<p>BCDBoot 创建 BCD 存储在同一个分区中。</p>
<p>默认情况下，BCDBoot 中固件上的 NVRAM 以找出系统分区上的引导文件创建 Windows 启动管理器项。 如果使用 /s 选项，则不会创建此项。 相反，BCDBoot 依赖默认固件设置，以确定在系统分区上的启动文件。 通过 UEFI 2.3.1 规范，默认固件设置应打开文件︰ \efi\boot\bootx64.efi 在 EFI 系统分区 (ESP)。</p></li>
</ul>
<p><strong>BIOS</strong>:</p>
<ol>
<li><p>BCDBoot 将引导文件复制到主硬盘上的活动分区或由 /s 选项指定的分区。</p></li>
<li><p>BCDBoot 创建 BCD 存储在同一个分区中。</p></li>
</ol>
<p>下面的示例将 C:\Windows 文件夹从 BCD 文件复制到系统分区上的辅助硬盘驱动器将启动另一台计算机上。 当辅助驱动器上的系统分区分配卷字母<em>S</em>:</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /s S:</code></pre>
<p>下面的示例创建卷字母 F，包括启动文件，以支持基于 UEFI 的或基于 BIOS 的计算机的 USB 闪存驱动器上的启动条目︰</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /s S: /f ALL</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/f <em>&lt;固件类型&gt;</em></p></td>
<td align="left"><p>可选项。 指定固件类型。 有效值包括<code>UEFI</code>， <code>BIOS</code>，和<code>ALL</code>。</p>
<ul>
<li><p>在基于 BIOS/MBR 的系统中，默认值是<code>BIOS</code>。 此选项在系统分区上创建<strong>\Boot</strong>目录，并将所有所需的引导环境文件复制到此目录。</p></li>
<li><p>基于 UEFI/GPT 的系统上，默认值是<code>UEFI</code>。 此选项将创建<strong>\Efi\Microsoft\Boot</strong>目录，并将所有所需的引导环境文件复制到此目录。</p></li>
<li><p>当您指定<code>ALL</code>值，BCDBoot 创建<strong>\Boot</strong>和<strong>\Efi\Microsoft\Boot</strong>目录并复制所有所需的引导环境文件的 BIOS 和 （uefi） 添加到这些目录。</p></li>
</ul>
<p>如果您指定<strong>/f</strong>选项，您还必须指定<strong>/s</strong>选项来标识系统分区的卷号。</p>
<p>下面的示例复制支持基于 UEFI 的或从 C:\Windows 文件夹到 USB 闪存驱动器分配卷字母<em>F</em>的基于 BIOS 的计算机的启动的 BCD 文件︰</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /s S: /f ALL </code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/v</p></td>
<td align="left"><p>可选项。 启用详细模式。 示例：</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /v</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/m [<em>{OS 加载程序 GUID}</em>]</p></td>
<td align="left"><p>可选项。 将合并成一个新的启动条目一个现有启动项目的值。</p>
<p>默认情况下，此选项仅合并全局对象。 如果指定<em>操作系统加载程序 GUID</em>时，此选项将合并系统模板来生成一个可启动的项目中的加载程序对象。</p>
<p>下面的示例合并指定的 GUID 标识新的 BCD 存储中的当前 BCD 存储中的操作系统加载程序︰</p>
<pre class="syntax" space="preserve"><code>bcdboot c:\Windows /m {xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/addlast</p></td>
<td align="left"><p>可选项。 指定应最后添加的 Windows 启动管理器固件条目。 默认行为是首先添加该控件。 不能使用 /p。</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /addlast</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/p</p></td>
<td align="left"><p>可选项。 指定现有的 Windows 启动管理器固件入口位置应该被保留在 UEFI 引导顺序。 如果条目不存在，在第一个位置添加一个新项。 不能用于 /addlast。</p>
<p>默认情况下，升级 BCDBoot 期间移动 Windows 启动管理器来 UEFI 启动顺序中的第一项。</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /p
bcdboot C:\Windows /p /d</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p>/d</p></td>
<td align="left"><p>可选项。 保留现有的默认操作系统项 {bootmgr} 对象在 Windows 启动管理器中。</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /d</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>/c</p></td>
<td align="left"><p>可选项。 指定现有的所有 BCD 元素应该不会都迁移。</p>
<p>新的 Windows 10︰ 默认情况下，升级过程中，如<strong>debugsettings</strong>或<strong>flightsigning</strong>的 BCD 元素将被保留。</p>
<pre class="syntax" space="preserve"><code>bcdboot C:\Windows /c</code></pre></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrepairthesystempartitionspanspan-idrepairthesystempartitionspanspan-idrepairthesystempartitionspanrepair-the-system-partition"></a><span id="Repair_the_system_partition"></span><span id="repair_the_system_partition"></span><span id="REPAIR_THE_SYSTEM_PARTITION"></span>修复系统分区


如果已损坏的系统分区，您可以使用 BCDBoot 若要通过使用 Windows 分区从这些文件的新副本重新创建系统分区文件。

1.  启动您的 PC 到命令行。 例如，从 Windows 安装磁盘启动并按 Shift + F10，或者引导到 Windows PE ([WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md))。

2.  使用 Diskpart，可以确定哪个驱动器号包含 Windows 的分区和系统分区 (`diskpart, list vol, exit`)。

3.  可选︰ 设置您的系统分区的格式︰`format (drive letter of your system partition) /q`

4.  添加启动项的 Windows 分区︰`bcdboot D:\Windows`

5.  重新启动计算机。 应显示窗口。

## <a name="span-idsetuporrepairthebootmenuonadual-bootpcspanspan-idsetuporrepairthebootmenuonadual-bootpcspanspan-idsetuporrepairthebootmenuonadual-bootpcspanset-up-or-repair-the-boot-menu-on-a-dual-boot-pc"></a><span id="Set_up_or_repair_the_boot_menu_on_a_dual-boot_PC"></span><span id="set_up_or_repair_the_boot_menu_on_a_dual-boot_pc"></span><span id="SET_UP_OR_REPAIR_THE_BOOT_MENU_ON_A_DUAL-BOOT_PC"></span>设置或修复双启动计算机上的启动菜单


当设置启动多个操作系统的 PC，有时可能会丢失能够引导至操作系统之一。 BCDBoot 选项允许您快速地添加一个基于 Windows 操作系统的启动选项。 若要设置双启动计算机︰

1.  安装单独的硬盘或准备一个单独的分区，每个操作系统。

2.  安装操作系统。 例如，如果您的 PC 有 Windows 7，到其他硬盘或分区上安装 Windows 10。

3.  重新启动计算机。 显示启动菜单应列出这两个操作系统。

    如果没有列出这两个操作系统︰

    1.  打开命令行，请以管理员身份从窗口内, 或通过启动到命令行使用 Windows 安装媒体，然后按 Shift + F10，通过引导至 Windows PE ([WinPE︰ 创建 USB 可启动驱动器](winpe-create-usb-bootable-drive.md))。
    2.  添加 Windows 操作系统的引导选项。

        ``` syntax
        bcdboot D:\Windows
        ```

    3.  重新启动计算机。 现在，启动菜单将显示两个菜单选项。

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>故障排除


有关修复启动文件与 Windows XP 及较新版本的如 Windows 7 的 Windows PC 上的信息，请参阅 Microsoft 知识库文章[2277998](http://go.microsoft.com/fwlink/?LinkId=234039)。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[捕获和应用 Windows、 系统和恢复分区](capture-and-apply-windows-system-and-recovery-partitions.md)

[配置基于 BIOS/MBR 硬盘分区](configure-biosmbr-based-hard-drive-partitions.md)

[配置基于 UEFI/GPT 的硬盘分区](configure-uefigpt-based-hard-drive-partitions.md)

[BCDedit](http://go.microsoft.com/fwlink/?LinkId=128459)

[Bootsect 命令行选项](bootsect-command-line-options.md)

[Diskpart 命令行语法](http://go.microsoft.com/fwlink/?LinkId=128458)

 

 






