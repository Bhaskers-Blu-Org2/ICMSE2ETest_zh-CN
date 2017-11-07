---
author: Justinha
Description: "Oscdimg 命令行选项"
ms.assetid: 4c64a7fe-3bab-4ab9-97ed-1b14e820b0c8
MSHAttr: PreferredLib:/library/windows/hardware
title: "Oscdimg 命令行选项"
ms.openlocfilehash: bc4e934f1d027de1e93046f5cfc7cf009ca7a6f1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="oscdimg-command-line-options"></a>Oscdimg 命令行选项


Oscdimg 是一个命令行工具，可用于创建自定义的 32 位或 64 位版本的 Windows 预安装环境 (Windows PE) 映像 (.iso) 文件。 然后可以刻录到 CD 或 DVD 的.iso 文件。 Oscdimg 支持 ISO 9660、 Joliet 和通用磁盘格式 (UDF) 文件系统。

本主题︰

-   [文件系统选项](#file)

-   [CD 或 DVD 启动选项](#bootoptions)

-   [优化选项](#optim)

-   [顺序选项](#order)

-   [DVD 视频和音频选项](#video)

-   [邮件选项](#mess)

-   [常规映像创建选项](#general)

-   [示例](#examples)

## <a name="span-idoscdimgcommand-lineoptionsspanspan-idoscdimgcommand-lineoptionsspanspan-idoscdimgcommand-lineoptionsspanoscdimg-command-line-options"></a><span id="Oscdimg_Command-Line_Options"></span><span id="oscdimg_command-line_options"></span><span id="OSCDIMG_COMMAND-LINE_OPTIONS"></span>Oscdimg 命令行选项


下面的命令行选项都可用于 Oscdimg。

**Oscdimg**\[*&lt;选项&gt;*\] * &lt;sourceLocation&gt; * * &lt;destinationFile&gt; *

### <a name="span-idfilespanspan-idfilespanfile-system-options"></a><span id="file"></span><span id="FILE"></span>文件系统选项

Oscdimg 工具和 Microsoft Windows 映像掌握三个 API (IMAPI) 支持文件系统格式︰ ISO 9660、 Joliet 和 UDF。

### <a name="span-idisospanspan-idisospaniso-9660-options"></a><span id="iso"></span><span id="ISO"></span>ISO 9660 选项

不能 Joliet 或 UDF 选项与组合 ISO 9660 选项。 结合长度的文件扩展名的文件名称的长度不能超过 30 个字符的 ISO 9660 文件系统中。

**-D**和**nt**选项不能一起使用。

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
<td align="left"><p><strong>-d</strong></p></td>
<td align="left"><p>允许写文件的名称。 不会强制为大写的小写字母文件名。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-n</strong></p></td>
<td align="left"><p>允许超过 DOS 8.3 文件名的文件名称。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-nt</strong></p></td>
<td align="left"><p>允许与 Windows NT 3.51 的长文件名。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idjolietspanspan-idjolietspanjoliet-options"></a><span id="joliet"></span><span id="JOLIET"></span>Joliet 选项

Joliet 是 ISO 9660 文件系统的扩展。 Joliet 允许较长的文件名称、 Unicode 字符和目录深度大于 8。 不能使用 ISO 9660 选项组合 Joliet 选项。

**-J2** Joliet 选项不能与 UDF 中的任何选项一起使用。

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
<td align="left"><p><strong>-j1</strong></p></td>
<td align="left"><p>允许这两个文件系统，若要查看磁盘上的所有数据。 使用此选项不重复图像上的所有文件。 此选项将编码 Joliet Unicode 文件名和 ISO 9660 命名空间中生成兼容 DOS 8.3 文件名。 通过 Joliet 系统或传统的 ISO 9660 系统，可以读取这些文件的名称。 但是，Oscdimg 可能会更改某些 DOS 8.3 和 ISO 9660 命名限制遵守 ISO 9660 命名空间中的文件名。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-j2</strong></p></td>
<td align="left"><p>对 Joliet Unicode 文件名不带标准 ISO 9660 名称进行编码。 使用此选项来生成包含 Joliet 文件系统映像。  无法读取 Joliet 任何系统可以看到只有一个默认文本文件，通知用户该图像仅是支持 Joliet 计算机上可用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>js —</strong></p></td>
<td align="left"><p>重写默认的文件，当用户指定时，使用<strong>的 j2</strong>选项。 例如︰</p>
<pre class="syntax" space="preserve"><code>-jsC:\readme.txt</code></pre></td>
</tr>
</tbody>
</table>

 

### <a name="span-idudfspanspan-idudfspanudf-options"></a><span id="udf"></span><span id="UDF"></span>UDF 选项

UDF 选项不能与 ISO 9660 选项结合使用。 **-Ue**、 **-uf**，和**-我们**他们正在一起使用时仅应用选项**-u2**选项。

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
<td align="left"><p><strong>-u1</strong></p></td>
<td align="left"><p>生成具有 UDF 文件系统和 ISO 9660 文件系统的映像。 ISO 9660 文件系统写入使用 DOS 兼容的 8.3 文件名。 UDF 文件系统写入使用 Unicode 文件名。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-u2</strong></p></td>
<td align="left"><p>生成包含 UDF 文件系统的映像。 无法读取 UDF 任何系统可以看到只有一个默认文本文件，通知用户该图像仅是在支持 UDF 的计算机上可用。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-udfver102</strong></p></td>
<td align="left"><p>指定 UDF 文件系统版本 1.02。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-ue</strong></p></td>
<td align="left"><p>创建嵌入的文件。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-uf</strong></p></td>
<td align="left"><p>将嵌入到 UDF 文件标识符项。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-您</strong></p></td>
<td align="left"><p>重写默认文本一起使用的文件<strong>-u2</strong>选项。 例如︰</p>
<pre class="syntax" space="preserve"><code>-urC:\Readme.txt</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-我们</strong></p></td>
<td align="left"><p>创建稀疏文件，如果可用，以使磁盘空间的使用效率更高。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-yl</strong></p></td>
<td align="left"><p>指定长分配的描述，而不是短分配描述符。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idbootoptionsspanspan-idbootoptionsspanspan-idbootoptionsspancd-or-dvd-boot-options"></a><span id="bootOptions"></span><span id="bootoptions"></span><span id="BOOTOPTIONS"></span>CD 或 DVD 启动选项

启动选项可用于创建可引导 CD 或 DVD 映像。 下面的启动选项可以用于生成单一启动项。 有关详细信息，请参阅[使用单一启动条目来创建可引导映像](#example-singleboot)。

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
<td align="left"><p><strong>-b</strong><em>&lt;bootSectorFile&gt;</em></p></td>
<td align="left"><p>指定将写入扇区的磁盘的引导扇区中的 El Torito 引导扇区文件。 不要使用空格。 例如︰</p>
<p>在 UEFI: <code>-bC:\winpe_x86\Efisys.bin</code></p>
<p>在 BIOS: <code>-bC:\winpe_x86\Etfsboot.com</code></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-e</strong></p></td>
<td align="left"><p>禁用软盘仿真在 El Torito 目录中。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-p</strong></p></td>
<td align="left"><p>指定要用于 El Torito 目录中的平台 ID 的值。 默认 ID 为 0xEF 来表示统一可扩展固件接口 (UEFI) 系统。 0x00 表示 BIOS 系统。</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>&lt;sourceLocation&gt;</em></p></td>
<td align="left"><p>必需。 指定要置入.iso 映像的文件的位置。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>&lt;targetFile&gt;</em></p></td>
<td align="left"><p>指定.iso 映像文件的名称。</p></td>
</tr>
</tbody>
</table>

 

**重要**  
不能在同一个命令中组合单一启动项和多重引导项。

 

下面的启动选项可以用于生成多个启动项目。 有关详细信息，请参阅[使用多引导条目以创建图像文件](#examples-multi-boot)。

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
<td align="left"><p><strong>b</strong><em>&lt;bootSectorFile&gt;</em></p></td>
<td align="left"><p>指定将写入扇区的磁盘的引导扇区中的 El Torito 引导扇区文件。 不要使用空格。 例如︰</p>
<p>在 UEFI: <code>bEfisys.bin</code></p>
<p>在 BIOS: <code>bEtfsboot.com</code></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-bootdata:</strong><em>&lt;号&gt;</em></p></td>
<td align="left"><p>指定一个多重引导图像，跟引导条目数。 不要使用空格。 例如︰</p>
<pre class="syntax" space="preserve"><code>-bootdata:&lt;3&gt;#&lt;defaultBootEntry&gt;#&lt;bootEntry1&gt;#&lt;bootEntryN&gt;</code></pre>
<p>其中<em>&lt;3&gt;</em>是遵循的启动条目数。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>e</strong></p></td>
<td align="left"><p>禁用软盘仿真在 El Torito 目录中。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>p</strong></p></td>
<td align="left"><p>指定要用于 El Torito 目录中的平台 ID 的值。 默认 ID 为 0xEF 来表示 （uefi） 系统。 0x00 表示 BIOS 系统。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>t</strong></p></td>
<td align="left"><p>指定 El Torito 加载段。 如果未指定，则此选项默认为 0x7C0。</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>&lt;sourceLocation&gt;</em></p></td>
<td align="left"><p>必需。 指定要置入.iso 映像的文件的位置。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>&lt;targetFile&gt;</em></p></td>
<td align="left"><p>指定.iso 映像文件的名称。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idoptimspanspan-idoptimspanoptimization-options"></a><span id="optim"></span><span id="OPTIM"></span>优化选项

优化选项可用来优化存储进行一次编码重复的文件。

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
<td align="left"><p><strong>-o</strong></p></td>
<td align="left"><p>使用 MD5 哈希算法来比较文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-oc</strong></p></td>
<td align="left"><p>使用二进制比较的每个文件，而且比<strong>-o</strong>选项。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-oi</strong></p></td>
<td align="left"><p>比较文件时，忽略菱形压缩时间戳。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idorderspanspan-idorderspanorder-options"></a><span id="order"></span><span id="ORDER"></span>顺序选项

顺序选项指定磁盘上的文件顺序。 文件顺序没有列出所有文件。 而会通常不会出现在此文件中的任何文件顺序 （即，如果订购文件不存在）。 有关详细信息，请参阅[指定启动顺序](#example-bootorder)。

**-Yo**选项优先于**-y5**选项。

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
<td align="left"><p><strong>-y5</strong></p></td>
<td align="left"><p>指定磁盘上的文件布局。 此选项可将文件写在第一个 i386 目录和反向排序顺序。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-yo</strong>&lt;bootOrder.txt&gt;</p></td>
<td align="left"><p>指定文本文件，其中包含要放在映像中的文件的布局。 不要使用空格。 例如︰</p>
<pre class="syntax" space="preserve"><code>-yoC:\temp\bootOrder.txt</code></pre></td>
</tr>
</tbody>
</table>

 

### <a name="span-idvideospanspan-idvideospandvd-video-and-audio-options"></a><span id="video"></span><span id="VIDEO"></span>DVD 视频和音频选项

DVD 视频和音频磁盘创建选项不能与 ISO 9660、 Joliet 或 UDF 选项结合使用。

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
<td align="left"><p><strong>-ut</strong></p></td>
<td align="left"><p>将图像的 ISO 9660 部分截断 DVD 视频和音频磁盘创建过程。 使用此选项时，只会将可见从 ISO 9660 文件系统的 VIDEO_TS、 AUDIO_TS 和 JACKET_P 目录。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-uv</strong></p></td>
<td align="left"><p>在 DVD 视频和音频磁盘创建过程中指定 UDF 视频区兼容性。 在创建期间，UDF 1.02 和 ISO 9660 将写入磁盘。 第一次写入 VIDEO_TS、 AUDIO_TS 和 JACKET_P 目录中的所有文件。 这些目录将优先于所有其他排序规则，用于此映像。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idmessspanspan-idmessspanmessaging-options"></a><span id="mess"></span><span id="MESS"></span>邮件选项

邮件选项自定义文件和目录信息的显示方式。

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
<td align="left"><p><strong>-a</strong></p></td>
<td align="left"><p>显示的分配摘要文件和目录。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-os</strong></p></td>
<td align="left"><p>显示重复的文件系统在创建映像时。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-w1</strong></p></td>
<td align="left"><p>报告所有的文件名或目录不是符合 ISO 标准或 Joliet 兼容。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-w2</strong></p></td>
<td align="left"><p>报告不是 DOS 兼容的所有文件名。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-w3</strong></p></td>
<td align="left"><p>报告所有零长度文件。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-w4</strong></p></td>
<td align="left"><p>报告每个复制到映像的文件名称。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-码</strong></p></td>
<td align="left"><p>禁止显示警告的非完全相同的文件具有相同的初始 64000 个字节。</p></td>
</tr>
</tbody>
</table>

 

### <a name="span-idgeneralspanspan-idgeneralspangeneral-image-creation-options"></a><span id="general"></span><span id="GENERAL"></span>常规映像创建选项

常规的图像创建选项可以与单一启动项选项或多启动项选项，用于创建可引导 CD 或 DVD 映像。 有关详细信息，请参阅[启动选项](#bootoptions)和[示例](#examples)。

不能同时使用**-m**和**-maxsize**选项。

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
<td align="left"><p><strong>-c</strong></p></td>
<td align="left"><p>指定系统必须使用 ANSI 文件名而不是 OEM 文件名称。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-g</strong></p></td>
<td align="left"><p>将时间值为通用协调时间 (UCT) 编码的所有文件，而不是本地时间。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-h</strong></p></td>
<td align="left"><p>在图像的源路径中包括隐藏的文件和目录。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-k</strong></p></td>
<td align="left"><p>即使无法打开某些源代码文件创建一个图像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-l</strong><em>&lt;volumeLabel&gt;</em></p></td>
<td align="left"><p>指定的卷标。 不要使用空格。 例如︰</p>
<pre class="syntax" space="preserve"><code>-l&lt;volumeLabel&gt;</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-m</strong></p></td>
<td align="left"><p>会忽略图像的最大大小限制。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-maxsize:</strong><em>&lt;限制&gt;</em></p></td>
<td align="left"><p>重写默认最大大小的图像。 默认值是 74 分钟 CD。 但是，如果使用 UDF 时，默认有无最大大小。 不要使用空格。 例如︰</p>
<pre class="syntax" space="preserve"><code>-maxsize:&lt;4096&gt;</code></pre>
<p>其中<em>&lt;4096&gt;</em>限制为 4096 MB 图像。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-q</strong></p></td>
<td align="left"><p>扫描的源代码文件。 此选项不会创建图像。</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-r</strong></p></td>
<td align="left"><p>新的 Windows 8。 解析为其目标位置的符号链接。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-t</strong><em>&lt;mm/dd/yyyy︰ 分︰ 秒&gt;</em></p></td>
<td align="left"><p>指定所有文件和目录的时间的戳。 不要使用空格。 您可以使用任何项之间的分隔符。 例如︰</p>
<pre class="syntax" space="preserve"><code>-t12/31/2000,15:01:00</code></pre></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>-y6</strong></p></td>
<td align="left"><p>指定目录记录必须在结束扇区完全对齐。</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>-yw</strong></p></td>
<td align="left"><p>打开具有写共享源代码文件。</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idexamplesspanspan-idexamplesspanexamples"></a><span id="examples"></span><span id="EXAMPLES"></span>示例


这些示例说明了如何执行以下操作︰

-   通过使用单一启动项基于 UEFI 的计算机创建可引导 CD 或 DVD。

-   通过使用多启动项基于 UEFI 的或基于 BIOS 的计算机创建可引导 CD 或 DVD。

-   在磁盘上指定启动文件顺序。

### <a name="span-idexamplesinglebootspanspan-idexamplesinglebootspanuse-a-single-boot-entry-to-create-a-bootable-image"></a><span id="example_singleboot"></span><span id="EXAMPLE_SINGLEBOOT"></span>单启动项用于创建可引导映像

Oscdimg 工具可用于创建可引导 CD 或 DVD 使用单一启动项。

**若要使用单一启动项**

-   创建基于 UEFI 的计算机的图像文件。 例如︰

    ``` syntax
    Oscdimg -bC:\winpe_amd64\Efisys.bin -pEF -u1 -udfver102 C:\winpe_amd64\media C:\winpe_amd64\winpeamd64.iso
    ```

    其中 c:\\winpe\_amd64\\介质所在的源文件和 c:\\winpe\_amd64\\winpeamd64.iso 为.iso 文件的路径。

### <a name="span-idexamplesmulti-bootspanspan-idexamplesmulti-bootspanuse-multi-boot-entries-to-create-a-bootable-image"></a><span id="examples_multi-boot"></span><span id="EXAMPLES_MULTI-BOOT"></span>使用多引导条目以创建可引导映像

Oscdimg 工具可用于创建可引导 CD 或 DVD 时使用多引导项。 当您这样做时，请注意以下问题︰

-   **Bootdata**选项后面必须跟在命令中的启动条目数 (**-bootdata:***&lt;号&gt;*)。

-   必须使用哈希符号分隔每个多启动项 (\#)。

-   启动项目的每个选项必须用逗号 （，） 分隔。

-   每个启动条目都必须指定平台 id。

**若要使用多引导条目**

-   创建一个图像文件是基于 UEFI 的或基于 BIOS 的计算机使用多引导命令。 例如︰

    ``` syntax
    Oscdimg -bootdata:2#p0,e,bEtfsboot.com#pEF,e,bEfisys.bin -u1 
    -udfver102 C:\winpe_amd64\media C:\winpe_amd64\winpeamd64.iso
    ```

    其中该命令启动的 BIOS 映像，Etfsboot.com 启动文件，然后启动 UEFI 图像的 Efisys.bin 启动文件。

### <a name="span-idexamplebootorderspanspan-idexamplebootorderspanspecify-the-boot-order"></a><span id="example_bootorder"></span><span id="EXAMPLE_BOOTORDER"></span>指定的启动顺序

对于图像大于 4.5 GB，必须创建启动顺序文件以确保启动文件都位于图像的开始处。

文件排序的规则如下所示︰

-   顺序文件必须为 ansi。

-   顺序文件必须以一个新行结束。

-   顺序文件必须有一个文件每行。

-   相对于根目录下的图像，必须指定每个文件。

-   每个文件必须指定为一个长文件名。 允许没有短名称。

-   每个文件路径长度不能超过最大值\_路径。 这包括的卷名。

例如，d:\\cdimage 将如下所示 （其中 D 是光驱的盘符）︰

-   D:\\cdimage\\1\\1.txt

-   D:\\cdimage\\2\\txt 2.

-   D:\\cdimage\\3\\txt 3.

-   D:\\cdimage\\3\\3\_txt 5.

-   D:\\cdimage\\*&lt;longFileName&gt;*.txt

**若要创建引导顺序文件**

-   创建一个引导顺序文件。 例如︰

    ``` syntax
    Oscdimg -m -n -yoC:\temp\bootOrder.txt 
    -bC:\winpe_amd64\Efisys.bin C:\winpe_amd64\winpeamd64.iso
    ```

    其中 BootOrder.txt 包含以下文件的列表︰

    ``` syntax
    boot\bcd
    boot\boot.sdi
    boot\bootfix.bin
    boot\bootsect.exe
    boot\etfsboot.com
    boot\memtest.efi
    boot\memtest.exe
    boot\en-us\bootsect.exe.mui
    boot\fonts\chs_boot.ttf
    boot\fonts\cht_boot.ttf
    boot\fonts\jpn_boot.ttf
    boot\fonts\kor_boot.ttf
    boot\fonts\wgl4_boot.ttf
    sources\boot.wim
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[WinPE︰ 创建可引导 USB 驱动器](winpe-create-usb-bootable-drive.md)

[Windows 部署命令行工具参考](windows-deployment-command-line-tools-reference.md)

 

 






